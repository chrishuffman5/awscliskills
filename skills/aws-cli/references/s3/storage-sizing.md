# Measuring S3 Bucket Storage Size

> **There is no single "bucket size."** Two legitimate numbers answer two different
> questions, and they routinely differ by 2×–50×. **Always compute and return BOTH**,
> and explain any gap. Reporting only one — especially without saying which — is the
> single most common way size reports go wrong.

| # | "Size" | Question it answers | Source |
|---|--------|---------------------|--------|
| **A** | **Logical / object size** | "How big are the *current* files I can `ls`/download right now?" | Object enumeration (`s3 ls`, `list-objects-v2`) |
| **B** | **Billable storage** | "What is AWS charging me to store?" | CloudWatch `BucketSizeBytes` |

**B − A is real, not error.** Billable storage additionally counts: noncurrent object
versions (versioned buckets), delete markers, and **orphaned incomplete multipart-upload
parts**. So a non-versioned bucket can still bill far more than its `ls` size.

---

## Method A — Real-time object enumeration (logical size)

Counts **current objects only**. Accurate to the second, but cost/time scales with object count.

### A1. Simplest — `s3 ls` (preferred for one bucket / human output)
```bash
aws s3 ls s3://BUCKET --recursive --summarize --human-readable
# tail shows:  Total Objects: N   Total Size: X
```

### A2. Scriptable exact bytes
```bash
# ROBUST — s3 ls sums correctly across ALL pages internally:
aws s3 ls s3://BUCKET --recursive --summarize | awk '/Total Size:/{print $3}'

# OR list-objects-v2 + re-sum. The CLI applies --query PER 1,000-object PAGE, so you MUST
# add the per-page results, NOT read the first line:
aws s3api list-objects-v2 --bucket BUCKET --query 'sum(Contents[].Size)' --output text \
  | awk '{s+=$1} END{print s+0}'      # empty bucket -> "None" -> 0
```
> **⛔ Pagination gotcha (verified) — `sum(Contents[].Size)` does NOT return one total for
> buckets > 1,000 objects.** CLI v2 applies `--query` to each 1,000-object page *separately*,
> so a 2,699-object bucket prints THREE numbers on three lines (e.g.
> `14497433533` / `505159156` / `356800680`, which sum to the true `15359393369`). Reading it
> as a single value silently truncates to the first page (~94% loss possible). **Fix:** re-sum
> the lines with `awk '{s+=$1}'` (this works *because* each line now holds ONE field — the
> mirror image of the `Contents[*].Size` trap below), or just use `s3 ls --summarize`, which
> aggregates pages internally.

### ⛔ NEVER do this — the `$1` trap (silently wrong)
```bash
# WRONG — undercounts every multi-object bucket to its FIRST object only:
aws s3api list-objects-v2 --bucket BUCKET --query 'Contents[*].Size' --output text \
  | awk '{sum += $1} END {print sum}'
```
**Why it fails:** `--output text` prints a list projection as **one tab-separated line**
(e.g. 91 sizes → 1 line, 91 fields). `awk '{sum+=$1}'` adds only field `$1` per line — i.e.
the first object's size — and discards the rest. A 14 GiB / 2,699-object bucket reports as
~3 MB. It *looks* fine because single-object buckets happen to be correct.

If you must use `awk`/text, sum **all** fields or split to lines first:
```bash
... --query 'Contents[*].Size' --output text | awk '{for(i=1;i<=NF;i++) s+=$i} END{print s+0}'
... --query 'Contents[*].Size' --output text | tr '\t' '\n' | awk '{s+=$1} END{print s+0}'
```

### Method A downsides
- **Current versions only** — excludes noncurrent versions, delete markers, and incomplete
  multipart parts. Will *understate* billable storage on versioned/churny buckets.
- **Cost & latency scale with object count** — must page through every key. Slow and
  request-costly for buckets with millions of objects (the long pole in any sizing job).
- **No storage-class breakdown** without extra parsing.

---

## Method B — CloudWatch `BucketSizeBytes` (billable size)

Pre-aggregated daily metric. **O(1) per bucket regardless of object count** — fast and cheap
at any scale (a 14 GiB / millions-of-objects bucket costs the same as an empty one).

### ⛔ Trap 1 — querying only `StandardStorage` undercounts
`BucketSizeBytes` is split by a `StorageType` dimension. A bucket in Intelligent-Tiering /
IA / Glacier has **0** in `StandardStorage`. You must query **every** storage-type dimension
and **sum** them per bucket:
```
StandardStorage  StandardIAStorage  OneZoneIAStorage  ReducedRedundancyStorage
IntelligentTieringFAStorage  IntelligentTieringIAStorage  IntelligentTieringAAStorage
IntelligentTieringAIAStorage  IntelligentTieringDAAStorage
GlacierInstantRetrievalStorage  GlacierStorage  DeepArchiveStorage  ExpressOneZoneStorage
```
(For exact billing also add the `*SizeOverhead` / `*ObjectOverhead` pseudo-types for IA/Glacier; for a size report the primary `*Storage` types above are sufficient.)

### ⛔ Trap 2 — wrong region returns "no data"
CloudWatch metrics are **per-region**. Query the bucket's own region or you get nothing:
```bash
aws s3api get-bucket-location --bucket BUCKET --query 'LocationConstraint' --output text
# null/None == us-east-1
```

### Recipe (one batched call for many buckets)
Build one `get-metric-data` query with `MetricStat.Stat=Average`, `Period=86400`, a 2–3 day
window (to guarantee a datapoint despite reporting lag), one query per (bucket × storage-type),
then sum per bucket. Results default to `TimestampDescending`, so the most recent datapoint is
`Values[0]`.
```bash
aws cloudwatch get-metric-data --region REGION \
  --metric-data-queries file://queries.json \
  --start-time "$(date -u -d '3 days ago' +%Y-%m-%dT%H:%M:%SZ)" \
  --end-time   "$(date -u +%Y-%m-%dT%H:%M:%SZ)"
```
Each query item:
```json
{"Id":"b0_0","Label":"BUCKET::StandardStorage",
 "MetricStat":{"Metric":{"Namespace":"AWS/S3","MetricName":"BucketSizeBytes",
   "Dimensions":[{"Name":"BucketName","Value":"BUCKET"},
                 {"Name":"StorageType","Value":"StandardStorage"}]},
   "Period":86400,"Stat":"Average"},"ReturnData":true}
```

### Method B downsides
- **Reporting lag (~24–48 h).** The metric is a daily snapshot; recent uploads/deletes are
  invisible. A bucket that grew today can read *smaller* than Method A. Check the datapoint
  timestamp before trusting it.
- **Empty / brand-new buckets emit no datapoint** → "no data" (not an error; treat as 0/empty).
- **Includes versions + delete markers + incomplete multipart parts** → *overstates* current
  logical content on versioned/churny buckets.
- **Per-region** — multi-region accounts need per-region queries.

---

## Why A and B differ — reconcile, don't pick

When the two numbers diverge, identify the cause instead of assuming one is "wrong":

| Symptom | Likely cause | Confirm with |
|---------|--------------|--------------|
| B ≫ A, bucket is versioned | Noncurrent versions counted by B, not A | `aws s3api get-bucket-versioning --bucket B` |
| B ≫ A, bucket **not** versioned | Orphaned incomplete multipart uploads | `aws s3api list-multipart-uploads --bucket B --query 'length(Uploads)'` (⚠ `Uploads[]` has **no `Size`** field — `sum(Uploads[].Size)`=0 always; for bytes, `list-parts` per upload and sum `Parts[].Size`, or just trust CloudWatch which already includes them) |
| B ≪ A (B smaller) | CloudWatch lag — data added after last daily snapshot | inspect metric `Timestamps` |
| "Empty" in B but A > 0 | New data since snapshot, or first key is a 0-byte folder marker | `s3 ls` the bucket |

---

## Recommended default behavior for "how big is bucket X / all buckets"

1. Run **Method B** (CloudWatch) for the fast, billing-aligned number across all buckets —
   summing **all** storage classes, in each bucket's region.
2. Run **Method A** (`s3 ls --summarize`, or `sum(Contents[].Size)` **re-summed per page** —
   see A2) for the live, current logical size. Parallelize across buckets; it is the slow part.
3. **Return both columns** (Logical size | Billable size) plus object count, and add a one-line
   note for any bucket where they diverge (versioning / multipart / lag).
4. **Sanity-check** before presenting: does the largest bucket's size match expectations
   (e.g. a bucket named `*backup*` shouldn't be a few KB)? An implausible total usually means
   a parsing bug like the `$1` trap above.
