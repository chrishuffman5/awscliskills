# Entity Detection Jobs

### 2.1 `start-entities-detection-v2-job`

Starts an asynchronous medical entity detection job. Processes documents stored in S3.

**Synopsis:**
```bash
aws comprehendmedical start-entities-detection-v2-job \
    --input-data-config <value> \
    --output-data-config <value> \
    --data-access-role-arn <value> \
    --language-code <value> \
    [--job-name <value>] \
    [--client-request-token <value>] \
    [--kms-key <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--input-data-config` | **Yes** | structure | -- | Input S3 location: `S3Bucket=string,S3Key=string` |
| `--output-data-config` | **Yes** | structure | -- | Output S3 location: `S3Bucket=string,S3Key=string` |
| `--data-access-role-arn` | **Yes** | string | -- | IAM role ARN with S3 access |
| `--language-code` | **Yes** | string | -- | Must be `en` (English only) |
| `--job-name` | No | string | None | Job name (1-256 chars) |
| `--client-request-token` | No | string | None | Idempotency token (1-64 chars) |
| `--kms-key` | No | string | None | KMS key for output encryption |

**Output Schema:**
```json
{
    "JobId": "string (1-32 chars)"
}
```

---

### 2.2 `describe-entities-detection-v2-job`

Gets details about an entity detection job.

**Synopsis:**
```bash
aws comprehendmedical describe-entities-detection-v2-job \
    --job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | Job ID (1-32 chars) |

**Output Schema:**
```json
{
    "ComprehendMedicalAsyncJobProperties": {
        "JobId": "string",
        "JobStatus": "SUBMITTED|IN_PROGRESS|COMPLETED|PARTIAL_SUCCESS|FAILED|STOP_REQUESTED|STOPPED",
        "Message": "string",
        "SubmitTime": "timestamp",
        "EndTime": "timestamp",
        "ExpirationTime": "timestamp",
        "InputDataConfig": {
            "S3Bucket": "string",
            "S3Key": "string"
        },
        "OutputDataConfig": {
            "S3Bucket": "string",
            "S3Key": "string"
        },
        "LanguageCode": "en",
        "DataAccessRoleArn": "string",
        "ManifestFilePath": "string",
        "KMSKey": "string",
        "ModelVersion": "string",
        "JobName": "string"
    }
}
```

---

### 2.3 `list-entities-detection-v2-jobs`

Lists entity detection jobs. Can filter by status. **Paginated operation.**

**Synopsis:**
```bash
aws comprehendmedical list-entities-detection-v2-jobs \
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
| `--filter` | No | structure | None | Filter: `{JobName=string,JobStatus=string,SubmitTimeBefore=timestamp,SubmitTimeAfter=timestamp}` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ComprehendMedicalAsyncJobPropertiesList": [
        {
            "JobId": "string",
            "JobStatus": "string",
            "JobName": "string",
            "SubmitTime": "timestamp",
            "EndTime": "timestamp",
            "InputDataConfig": {},
            "OutputDataConfig": {},
            "LanguageCode": "en",
            "DataAccessRoleArn": "string",
            "ModelVersion": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.4 `stop-entities-detection-v2-job`

Stops an in-progress entity detection job.

**Synopsis:**
```bash
aws comprehendmedical stop-entities-detection-v2-job \
    --job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | Job ID (1-32 chars) |

**Output Schema:**
```json
{
    "JobId": "string"
}
```
