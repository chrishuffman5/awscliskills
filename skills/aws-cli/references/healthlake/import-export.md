# Import & Export Jobs

## Import Jobs

### 2.1 `start-fhir-import-job`

Starts a FHIR import job to load data from S3 into a data store.

**Synopsis:**
```bash
aws healthlake start-fhir-import-job \
    --datastore-id <value> \
    --input-data-config <value> \
    --job-output-data-config <value> \
    --data-access-role-arn <value> \
    [--job-name <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--datastore-id` | **Yes** | string | -- | Target data store ID (1-32 chars) |
| `--input-data-config` | **Yes** | structure | -- | Input S3 location: `S3Uri=string` |
| `--job-output-data-config` | **Yes** | structure | -- | Output config: `S3Configuration={S3Uri=string,KmsKeyId=string}` |
| `--data-access-role-arn` | **Yes** | string | -- | IAM role ARN with S3 access (20-2048 chars) |
| `--job-name` | No | string | None | Job name (1-64 chars) |
| `--client-token` | No | string | None | Idempotency token (1-64 chars) |

**Output Schema:**
```json
{
    "JobId": "string",
    "JobStatus": "SUBMITTED",
    "DatastoreId": "string"
}
```

---

### 2.2 `describe-fhir-import-job`

Gets properties of a FHIR import job.

**Synopsis:**
```bash
aws healthlake describe-fhir-import-job \
    --datastore-id <value> \
    --job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--datastore-id` | **Yes** | string | -- | Data store ID (1-32 chars) |
| `--job-id` | **Yes** | string | -- | Import job ID (1-32 chars) |

**Output Schema:**
```json
{
    "ImportJobProperties": {
        "JobId": "string",
        "JobName": "string",
        "JobStatus": "SUBMITTED|QUEUED|IN_PROGRESS|COMPLETED_WITH_ERRORS|COMPLETED|FAILED|CANCEL_SUBMITTED|CANCEL_IN_PROGRESS|CANCEL_COMPLETED|CANCEL_FAILED",
        "SubmitTime": "timestamp",
        "EndTime": "timestamp",
        "DatastoreId": "string",
        "InputDataConfig": {
            "S3Uri": "string"
        },
        "JobOutputDataConfig": {
            "S3Configuration": {
                "S3Uri": "string",
                "KmsKeyId": "string"
            }
        },
        "JobProgressReport": {
            "TotalNumberOfScannedFiles": "long",
            "TotalSizeOfScannedFilesInMB": "double",
            "TotalNumberOfImportedFiles": "long",
            "TotalNumberOfResourcesScanned": "long",
            "TotalNumberOfResourcesImported": "long",
            "TotalNumberOfResourcesWithCustomerError": "long",
            "TotalNumberOfFilesReadWithCustomerError": "long",
            "Throughput": "double"
        },
        "DataAccessRoleArn": "string",
        "Message": "string"
    }
}
```

---

### 2.3 `list-fhir-import-jobs`

Lists FHIR import jobs for a data store with optional filters.

**Synopsis:**
```bash
aws healthlake list-fhir-import-jobs \
    --datastore-id <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--job-name <value>] \
    [--job-status <value>] \
    [--submitted-before <value>] \
    [--submitted-after <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--datastore-id` | **Yes** | string | -- | Data store ID (1-32 chars) |
| `--next-token` | No | string | None | Pagination token (max 8192 chars) |
| `--max-results` | No | integer | None | Max results (1-500) |
| `--job-name` | No | string | None | Filter by job name (1-64 chars) |
| `--job-status` | No | string | None | Filter by status (see job statuses) |
| `--submitted-before` | No | timestamp | None | Jobs submitted before this time |
| `--submitted-after` | No | timestamp | None | Jobs submitted after this time |

**Output Schema:**
```json
{
    "ImportJobPropertiesList": [
        {
            "JobId": "string",
            "JobName": "string",
            "JobStatus": "string",
            "SubmitTime": "timestamp",
            "EndTime": "timestamp",
            "DatastoreId": "string",
            "InputDataConfig": {},
            "JobOutputDataConfig": {},
            "JobProgressReport": {},
            "DataAccessRoleArn": "string",
            "Message": "string"
        }
    ],
    "NextToken": "string"
}
```

---

## Export Jobs

### 2.4 `start-fhir-export-job`

Starts a FHIR export job to export data from a data store to S3.

**Synopsis:**
```bash
aws healthlake start-fhir-export-job \
    --datastore-id <value> \
    --output-data-config <value> \
    --data-access-role-arn <value> \
    [--job-name <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--datastore-id` | **Yes** | string | -- | Data store ID (1-32 chars) |
| `--output-data-config` | **Yes** | structure | -- | Output config: `S3Configuration={S3Uri=string,KmsKeyId=string}` |
| `--data-access-role-arn` | **Yes** | string | -- | IAM role ARN with S3 access (20-2048 chars) |
| `--job-name` | No | string | None | Job name (1-64 chars) |
| `--client-token` | No | string | None | Idempotency token (1-64 chars) |

**Output Schema:**
```json
{
    "JobId": "string",
    "JobStatus": "SUBMITTED",
    "DatastoreId": "string"
}
```

---

### 2.5 `describe-fhir-export-job`

Gets properties of a FHIR export job.

**Synopsis:**
```bash
aws healthlake describe-fhir-export-job \
    --datastore-id <value> \
    --job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--datastore-id` | **Yes** | string | -- | Data store ID (1-32 chars) |
| `--job-id` | **Yes** | string | -- | Export job ID (1-32 chars) |

**Output Schema:**
```json
{
    "ExportJobProperties": {
        "JobId": "string",
        "JobName": "string",
        "JobStatus": "SUBMITTED|QUEUED|IN_PROGRESS|COMPLETED_WITH_ERRORS|COMPLETED|FAILED|CANCEL_SUBMITTED|CANCEL_IN_PROGRESS|CANCEL_COMPLETED|CANCEL_FAILED",
        "SubmitTime": "timestamp",
        "EndTime": "timestamp",
        "DatastoreId": "string",
        "OutputDataConfig": {
            "S3Configuration": {
                "S3Uri": "string",
                "KmsKeyId": "string"
            }
        },
        "DataAccessRoleArn": "string",
        "Message": "string"
    }
}
```

---

### 2.6 `list-fhir-export-jobs`

Lists FHIR export jobs for a data store with optional filters.

**Synopsis:**
```bash
aws healthlake list-fhir-export-jobs \
    --datastore-id <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--job-name <value>] \
    [--job-status <value>] \
    [--submitted-before <value>] \
    [--submitted-after <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--datastore-id` | **Yes** | string | -- | Data store ID (1-32 chars) |
| `--next-token` | No | string | None | Pagination token (max 8192 chars) |
| `--max-results` | No | integer | None | Max results (1-500) |
| `--job-name` | No | string | None | Filter by job name (1-64 chars) |
| `--job-status` | No | string | None | Filter by status (see job statuses) |
| `--submitted-before` | No | timestamp | None | Jobs submitted before this time |
| `--submitted-after` | No | timestamp | None | Jobs submitted after this time |

**Output Schema:**
```json
{
    "ExportJobPropertiesList": [
        {
            "JobId": "string",
            "JobName": "string",
            "JobStatus": "string",
            "SubmitTime": "timestamp",
            "EndTime": "timestamp",
            "DatastoreId": "string",
            "OutputDataConfig": {},
            "DataAccessRoleArn": "string",
            "Message": "string"
        }
    ],
    "NextToken": "string"
}
```
