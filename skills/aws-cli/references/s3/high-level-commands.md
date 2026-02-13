# High-Level Commands (`aws s3`)

### 1.1 `cp`

Copies files and objects to/from local filesystem and S3.

**Synopsis:**
```bash
aws s3 cp <LocalPath> <S3Uri>
aws s3 cp <S3Uri> <LocalPath>
aws s3 cp <S3Uri> <S3Uri>
    [--dryrun] [--quiet] [--recursive]
    [--include <value>] [--exclude <value>]
    [--acl <value>] [--storage-class <value>]
    [--sse <value>] [--sse-c <value>] [--sse-c-key <value>]
    [--sse-kms-key-id <value>]
    [--content-type <value>] [--cache-control <value>]
    [--metadata <value>] [--grants <value>]
    [--no-guess-mime-type] [--only-show-errors]
    [--no-progress] [--expected-size <value>]
    [--follow-symlinks | --no-follow-symlinks]
    [--copy-props <value>] [--checksum-algorithm <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `paths` | **Yes** | string | -- | Source and destination. LocalPath or S3Uri (`s3://bucket/key`) |
| `--recursive` | No | boolean | false | Operate on all files under specified directory/prefix |
| `--dryrun` | No | boolean | false | Display operations without executing |
| `--quiet` | No | boolean | false | Suppress output except errors |
| `--include` | No | string | None | Include files matching pattern (overrides `--exclude`) |
| `--exclude` | No | string | None | Exclude files matching pattern |
| `--acl` | No | string | None | `private`, `public-read`, `public-read-write`, `authenticated-read`, `aws-exec-read`, `bucket-owner-read`, `bucket-owner-full-control` |
| `--storage-class` | No | string | `STANDARD` | `STANDARD`, `REDUCED_REDUNDANCY`, `STANDARD_IA`, `ONEZONE_IA`, `INTELLIGENT_TIERING`, `GLACIER`, `DEEP_ARCHIVE`, `GLACIER_IR` |
| `--sse` | No | string | None | Server-side encryption: `AES256` or `aws:kms` |
| `--sse-c` | No | string | None | Customer-provided encryption algorithm (`AES256`) |
| `--sse-c-key` | No | blob | None | Customer-provided encryption key |
| `--sse-kms-key-id` | No | string | None | KMS key ID for SSE-KMS |
| `--content-type` | No | string | auto-detected | MIME type of the object |
| `--cache-control` | No | string | None | Cache-Control header value |
| `--content-disposition` | No | string | None | Content-Disposition header |
| `--content-encoding` | No | string | None | Content-Encoding header |
| `--content-language` | No | string | None | Content-Language header |
| `--expires` | No | string | None | Expires header (ISO 8601) |
| `--metadata` | No | map | None | Custom metadata key-value pairs |
| `--grants` | No | string | None | Grant permissions: `Permission=Grantee_Type=Grantee_ID` |
| `--website-redirect` | No | string | None | Redirect location for website buckets |
| `--no-guess-mime-type` | No | boolean | false | Disable MIME type guessing |
| `--only-show-errors` | No | boolean | false | Show only errors and warnings |
| `--no-progress` | No | boolean | false | Hide transfer progress |
| `--follow-symlinks` | No | boolean | true | Follow symbolic links on upload |
| `--copy-props` | No | string | `default` | S3-to-S3 copy properties: `none`, `metadata-directive`, `default` |
| `--checksum-algorithm` | No | string | None | `CRC32`, `CRC32C`, `SHA1`, `SHA256` |
| `--expected-size` | No | string | None | Expected size for stream uploads (required for >50GB) |
| `--source-region` | No | string | None | Source region for cross-region S3-to-S3 copies |

**Output:** Progress display to stdout. No JSON output.

---

### 1.2 `mv`

Moves files and objects to/from local filesystem and S3. Same parameters as `cp`.

**Synopsis:**
```bash
aws s3 mv <LocalPath> <S3Uri>
aws s3 mv <S3Uri> <LocalPath>
aws s3 mv <S3Uri> <S3Uri>
    [--dryrun] [--quiet] [--recursive]
    [--include <value>] [--exclude <value>]
    [--acl <value>] [--storage-class <value>]
    [--sse <value>] [--sse-kms-key-id <value>]
    [--content-type <value>] [--metadata <value>]
```

**Parameters:** Same as `cp` (see 1.1). Performs a copy followed by a delete of the source.

**Output:** Progress display to stdout. No JSON output.

---

### 1.3 `rm`

Deletes S3 objects.

**Synopsis:**
```bash
aws s3 rm <S3Uri>
    [--dryrun] [--quiet] [--recursive]
    [--include <value>] [--exclude <value>]
    [--only-show-errors] [--page-size <value>]
    [--request-payer <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `S3Uri` | **Yes** | string | -- | S3 URI of object to delete (`s3://bucket/key`) |
| `--recursive` | No | boolean | false | Delete all objects under specified prefix |
| `--dryrun` | No | boolean | false | Display operations without executing |
| `--quiet` | No | boolean | false | Suppress output except errors |
| `--include` | No | string | None | Include files matching pattern |
| `--exclude` | No | string | None | Exclude files matching pattern |
| `--only-show-errors` | No | boolean | false | Show only errors |
| `--page-size` | No | integer | 1000 | Results per API call |
| `--request-payer` | No | string | None | `requester` for requester-pays buckets |

**Output:** Progress display to stdout. No JSON output.

---

### 1.4 `sync`

Syncs directories and S3 prefixes. Only copies new and updated files.

**Synopsis:**
```bash
aws s3 sync <LocalPath> <S3Uri>
aws s3 sync <S3Uri> <LocalPath>
aws s3 sync <S3Uri> <S3Uri>
    [--dryrun] [--quiet] [--delete]
    [--include <value>] [--exclude <value>]
    [--acl <value>] [--storage-class <value>]
    [--sse <value>] [--sse-kms-key-id <value>]
    [--size-only] [--exact-timestamps]
    [--no-progress] [--only-show-errors]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `paths` | **Yes** | string | -- | Source and destination paths |
| `--delete` | No | boolean | false | Delete destination files/objects not in source |
| `--size-only` | No | boolean | false | Compare only file sizes (ignore timestamps) |
| `--exact-timestamps` | No | boolean | false | Match timestamps exactly (S3-to-local) |
| `--dryrun` | No | boolean | false | Display operations without executing |
| `--quiet` | No | boolean | false | Suppress output except errors |

All other parameters from `cp` (1.1) also apply: `--include`, `--exclude`, `--acl`, `--storage-class`, `--sse`, `--sse-kms-key-id`, `--content-type`, `--metadata`, `--cache-control`, `--no-progress`, `--only-show-errors`, `--follow-symlinks`, `--checksum-algorithm`.

**Output:** Progress display to stdout. No JSON output.

---

### 1.5 `ls`

Lists S3 buckets or objects/prefixes under a bucket.

**Synopsis:**
```bash
aws s3 ls [<S3Uri>]
    [--recursive] [--page-size <value>]
    [--human-readable] [--summarize]
    [--request-payer <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `S3Uri` | No | string | None | S3 URI. Omit to list buckets; provide to list objects |
| `--recursive` | No | boolean | false | List all objects recursively |
| `--page-size` | No | integer | 1000 | Results per API call |
| `--human-readable` | No | boolean | false | Show file sizes in human-readable format |
| `--summarize` | No | boolean | false | Display summary (total objects and total size) |
| `--request-payer` | No | string | None | `requester` for requester-pays buckets |

**Output:** Text listing to stdout. No JSON output.

---

### 1.6 `mb`

Creates an S3 bucket.

**Synopsis:**
```bash
aws s3 mb <S3Uri>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `S3Uri` | **Yes** | string | -- | Bucket URI: `s3://bucket-name` |

> **Note:** Use `--region` global option to specify the bucket region. For regions other than `us-east-1`, the `LocationConstraint` is set automatically.

**Output:** Confirmation message to stdout.

---

### 1.7 `rb`

Removes an S3 bucket. Bucket must be empty unless `--force` is used.

**Synopsis:**
```bash
aws s3 rb <S3Uri>
    [--force]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `S3Uri` | **Yes** | string | -- | Bucket URI: `s3://bucket-name` |
| `--force` | No | boolean | false | Delete all objects in the bucket first, then delete the bucket |

**Output:** Confirmation message to stdout.

---

### 1.8 `presign`

Generates a presigned URL for an S3 object.

**Synopsis:**
```bash
aws s3 presign <S3Uri>
    [--expires-in <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `S3Uri` | **Yes** | string | -- | S3 URI of the object (`s3://bucket/key`) |
| `--expires-in` | No | integer | 3600 | Expiration time in seconds (max 604800 = 7 days for IAM users; 12 hours max for IAM roles) |

**Output:** Presigned URL string to stdout.

---

### 1.9 `website`

Configures website hosting for an S3 bucket.

**Synopsis:**
```bash
aws s3 website <S3Uri>
    [--index-document <value>]
    [--error-document <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `S3Uri` | **Yes** | string | -- | Bucket URI: `s3://bucket-name` |
| `--index-document` | No | string | None | Index document suffix (e.g. `index.html`) |
| `--error-document` | No | string | None | Error document key (e.g. `error.html`) |

**Output:** None on success.

---

