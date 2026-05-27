# Media Analysis

### 6.1 `start-media-analysis-job`

Starts a media analysis job for batch processing of images (e.g., content moderation at scale).

**Synopsis:**
```bash
aws rekognition start-media-analysis-job \
    --operations-config <value> \
    --input <value> \
    --output-config <value> \
    [--client-request-token <value>] \
    [--job-name <value>] \
    [--kms-key-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--operations-config` | **Yes** | structure | -- | Analysis operations configuration |
| `--input` | **Yes** | structure | -- | Input manifest file S3 location |
| `--output-config` | **Yes** | structure | -- | S3 output location |
| `--client-request-token` | No | string | auto | Idempotency token (1-64 chars) |
| `--job-name` | No | string | -- | Job name (1-64 chars) |
| `--kms-key-id` | No | string | -- | KMS key for encryption |

**Operations Config Structure:**
```json
{
    "DetectModerationLabels": {
        "MinConfidence": "float (0-100)",
        "ProjectVersion": "string"
    }
}
```

**Input Structure:**
```json
{
    "S3Object": {
        "Bucket": "string",
        "Name": "string",
        "Version": "string"
    }
}
```

**Output Config Structure:**
```json
{
    "S3Bucket": "string",
    "S3KeyPrefix": "string"
}
```

**Output Schema:**
```json
{
    "JobId": "string"
}
```

---

### 6.2 `get-media-analysis-job`

Gets the details and results of a media analysis job.

**Synopsis:**
```bash
aws rekognition get-media-analysis-job \
    --job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | Job ID from start-media-analysis-job |

**Output Schema:**
```json
{
    "JobId": "string",
    "JobName": "string",
    "OperationsConfig": {},
    "Status": "CREATED|QUEUED|IN_PROGRESS|SUCCEEDED|FAILED",
    "FailureDetails": {
        "Code": "INTERNAL_ERROR|INVALID_S3_OBJECT|INVALID_MANIFEST|INVALID_OUTPUT_CONFIG|INVALID_KMS_KEY|ACCESS_DENIED|RESOURCE_NOT_FOUND|RESOURCE_NOT_READY|THROTTLED",
        "Message": "string"
    },
    "CreationTimestamp": "timestamp",
    "CompletionTimestamp": "timestamp",
    "Input": {},
    "OutputConfig": {},
    "KmsKeyId": "string",
    "Results": {
        "S3Object": {
            "Bucket": "string",
            "Name": "string"
        },
        "ModelVersions": {}
    },
    "ManifestSummary": {
        "S3Object": {}
    }
}
```

---

### 6.3 `list-media-analysis-jobs`

Lists media analysis jobs. **Paginated operation.**

**Synopsis:**
```bash
aws rekognition list-media-analysis-jobs \
    [--cli-input-json | --cli-input-yaml] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "NextToken": "string",
    "MediaAnalysisJobs": [
        {
            "JobId": "string",
            "JobName": "string",
            "Status": "CREATED|QUEUED|IN_PROGRESS|SUCCEEDED|FAILED",
            "CreationTimestamp": "timestamp",
            "CompletionTimestamp": "timestamp",
            "Input": {},
            "OutputConfig": {}
        }
    ]
}
```
