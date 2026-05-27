# Bulk Import

### 10.1 `create-bulk-import-job`

Creates a bulk import job to ingest data from S3.

**Synopsis:**
```bash
aws iotsitewise create-bulk-import-job \
    --job-name <value> \
    --job-role-arn <value> \
    --files <value> \
    --error-report-location <value> \
    --job-configuration <value> \
    [--adaptive-ingestion | --no-adaptive-ingestion] \
    [--delete-files-after-import | --no-delete-files-after-import] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-name` | **Yes** | string | -- | Job name (1-256 chars) |
| `--job-role-arn` | **Yes** | string | -- | IAM role ARN for S3 access |
| `--files` | **Yes** | list | -- | S3 file locations |
| `--error-report-location` | **Yes** | structure | -- | S3 location for error reports |
| `--job-configuration` | **Yes** | structure | -- | File format config |
| `--adaptive-ingestion` | No | boolean | false | Ingest new data with notifications |
| `--delete-files-after-import` | No | boolean | false | Delete S3 files after import |

**Files Structure:**
```json
[
    {
        "bucket": "string",
        "key": "string",
        "versionId": "string"
    }
]
```

**Error Report Location:**
```json
{
    "bucket": "string",
    "prefix": "string"
}
```

**Job Configuration:**
```json
{
    "fileFormat": {
        "csv": {
            "columnNames": ["ALIAS", "ASSET_ID", "PROPERTY_ID", "DATA_TYPE", "TIMESTAMP_SECONDS", "TIMESTAMP_NANO_OFFSET", "QUALITY", "VALUE"]
        },
        "parquet": {}
    }
}
```

**Output Schema:**
```json
{
    "jobId": "string",
    "jobName": "string",
    "jobStatus": "PENDING|CANCELLED|RUNNING|COMPLETED|FAILED|COMPLETED_WITH_FAILURES"
}
```

---

### 10.2 `describe-bulk-import-job`

Describes a bulk import job.

**Synopsis:**
```bash
aws iotsitewise describe-bulk-import-job \
    --job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | Job ID (UUID) |

**Output Schema:**
```json
{
    "jobId": "string",
    "jobName": "string",
    "jobStatus": "PENDING|CANCELLED|RUNNING|COMPLETED|FAILED|COMPLETED_WITH_FAILURES",
    "jobRoleArn": "string",
    "files": [],
    "errorReportLocation": {"bucket": "string", "prefix": "string"},
    "jobConfiguration": {},
    "jobCreationDate": "timestamp",
    "jobLastUpdateDate": "timestamp",
    "adaptiveIngestion": "boolean",
    "deleteFilesAfterImport": "boolean"
}
```

---

### 10.3 `list-bulk-import-jobs`

Lists bulk import jobs. **Paginated operation.**

**Synopsis:**
```bash
aws iotsitewise list-bulk-import-jobs \
    [--filter <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filter` | No | string | `ALL` | `ALL`, `PENDING`, `RUNNING`, `CANCELLED`, `FAILED`, `COMPLETED_WITH_FAILURES`, `COMPLETED` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "jobSummaries": [
        {
            "id": "string",
            "name": "string",
            "status": "PENDING|CANCELLED|RUNNING|COMPLETED|FAILED|COMPLETED_WITH_FAILURES"
        }
    ],
    "nextToken": "string"
}
```
