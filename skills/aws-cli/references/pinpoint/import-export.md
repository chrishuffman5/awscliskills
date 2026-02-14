# Import & Export

### 9.1 `create-import-job`

Creates an import job to import endpoint definitions from an S3 bucket.

**Synopsis:**
```bash
aws pinpoint create-import-job \
    --application-id <value> \
    --import-job-request <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application/project ID |
| `--import-job-request` | **Yes** | structure | -- | Import job configuration |

**ImportJobRequest Fields:**
- `DefineSegment` (boolean): Create a segment from imported endpoints
- `ExternalId` (string): Custom ID for the segment
- `Format` (string, **required**): `CSV` or `JSON`
- `RegisterEndpoints` (boolean): Register imported endpoints
- `RoleArn` (string, **required**): IAM role ARN for S3 access
- `S3Url` (string, **required**): S3 URL (`s3://bucket/prefix/`)
- `SegmentId` (string): Existing segment to add endpoints to
- `SegmentName` (string): Name for new segment

**Output Schema:**
```json
{
    "ImportJobResponse": {
        "ApplicationId": "string",
        "Id": "string",
        "CreationDate": "string",
        "CompletionDate": "string",
        "JobStatus": "CREATED|PREPARING_FOR_INITIALIZATION|INITIALIZING|PROCESSING|PENDING_JOB|COMPLETING|COMPLETED|FAILING|FAILED",
        "Definition": {},
        "FailedPieces": "integer",
        "CompletedPieces": "integer",
        "TotalPieces": "integer",
        "TotalProcessed": "integer",
        "TotalFailures": "integer",
        "Type": "string",
        "Failures": ["string"]
    }
}
```

---

### 9.2 `get-import-job`

Gets information about an import job.

**Synopsis:**
```bash
aws pinpoint get-import-job \
    --application-id <value> \
    --job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application/project ID |
| `--job-id` | **Yes** | string | -- | Import job ID |

**Output Schema:** Same as `ImportJobResponse` above.

---

### 9.3 `get-import-jobs`

Lists import jobs for an application.

**Synopsis:**
```bash
aws pinpoint get-import-jobs \
    --application-id <value> \
    [--page-size <value>] \
    [--token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application/project ID |
| `--page-size` | No | string | None | Max items per page |
| `--token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "ImportJobsResponse": {
        "Item": [{"ImportJobResponse": "..."}],
        "NextToken": "string"
    }
}
```

---

### 9.4 `create-export-job`

Creates an export job to export endpoint definitions to an S3 bucket.

**Synopsis:**
```bash
aws pinpoint create-export-job \
    --application-id <value> \
    --export-job-request <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application/project ID |
| `--export-job-request` | **Yes** | structure | -- | Export job configuration |

**ExportJobRequest Fields:**
- `RoleArn` (string, **required**): IAM role ARN for S3 access
- `S3UrlPrefix` (string, **required**): S3 URL prefix for export files
- `SegmentId` (string): Export only endpoints from this segment
- `SegmentVersion` (integer): Segment version to export

**Output Schema:**
```json
{
    "ExportJobResponse": {
        "ApplicationId": "string",
        "Id": "string",
        "CreationDate": "string",
        "CompletionDate": "string",
        "JobStatus": "CREATED|PREPARING_FOR_INITIALIZATION|INITIALIZING|PROCESSING|PENDING_JOB|COMPLETING|COMPLETED|FAILING|FAILED",
        "Definition": {},
        "FailedPieces": "integer",
        "CompletedPieces": "integer",
        "TotalPieces": "integer",
        "TotalProcessed": "integer",
        "TotalFailures": "integer",
        "Type": "string"
    }
}
```

---

### 9.5 `get-export-job`

Gets information about an export job.

**Synopsis:**
```bash
aws pinpoint get-export-job \
    --application-id <value> \
    --job-id <value>
```

---

### 9.6 `get-export-jobs`

Lists export jobs for an application.

**Synopsis:**
```bash
aws pinpoint get-export-jobs \
    --application-id <value> \
    [--page-size <value>] \
    [--token <value>]
```
