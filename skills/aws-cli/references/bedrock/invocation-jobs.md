# Invocation Jobs (Batch Inference)

### `create-model-invocation-job`

Creates a batch inference job to process multiple model invocations asynchronously from a JSONL file in S3.

**Synopsis:**
```bash
aws bedrock create-model-invocation-job \
    --job-name <value> \
    --role-arn <value> \
    --model-id <value> \
    --input-data-config <value> \
    --output-data-config <value> \
    [--client-request-token <value>] \
    [--vpc-config <value>] \
    [--timeout-duration-in-hours <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-name` | **Yes** | string | -- | Batch job name (1-63 chars) |
| `--role-arn` | **Yes** | string | -- | IAM role ARN with batch inference permissions |
| `--model-id` | **Yes** | string | -- | Model ID or ARN for batch inference (1-2048 chars) |
| `--input-data-config` | **Yes** | structure | -- | S3 input location (JSONL format) |
| `--output-data-config` | **Yes** | structure | -- | S3 output location |
| `--client-request-token` | No | string | None | Idempotency token (1-256 chars) |
| `--vpc-config` | No | structure | None | VPC config: `subnetIds`, `securityGroupIds` |
| `--timeout-duration-in-hours` | No | integer | None | Job timeout in hours (24-168) |
| `--tags` | No | list | None | Tags (max 200) |

**Input Data Config Structure:**
```json
{
    "s3InputDataConfig": {
        "s3InputFormat": "JSONL",
        "s3Uri": "s3://bucket/input/",
        "s3BucketOwner": "123456789012"
    }
}
```

**Output Data Config Structure:**
```json
{
    "s3OutputDataConfig": {
        "s3Uri": "s3://bucket/output/",
        "s3EncryptionKeyId": "arn:aws:kms:...",
        "s3BucketOwner": "123456789012"
    }
}
```

**Output Schema:**
```json
{
    "jobArn": "string"
}
```

---

### `get-model-invocation-job`

Gets details of a batch inference job.

**Synopsis:**
```bash
aws bedrock get-model-invocation-job \
    --job-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-identifier` | **Yes** | string | -- | Job name or ARN |

**Output Schema:**
```json
{
    "jobArn": "string",
    "jobName": "string",
    "modelId": "string",
    "clientRequestToken": "string",
    "roleArn": "string",
    "status": "Submitted|InProgress|Completed|Failed|Stopping|Stopped|PartiallyCompleted|Expired|Validating|Scheduled",
    "message": "string",
    "submitTime": "timestamp",
    "lastModifiedTime": "timestamp",
    "endTime": "timestamp",
    "inputDataConfig": {
        "s3InputDataConfig": {
            "s3InputFormat": "JSONL",
            "s3Uri": "string",
            "s3BucketOwner": "string"
        }
    },
    "outputDataConfig": {
        "s3OutputDataConfig": {
            "s3Uri": "string",
            "s3EncryptionKeyId": "string",
            "s3BucketOwner": "string"
        }
    },
    "vpcConfig": {
        "subnetIds": ["string"],
        "securityGroupIds": ["string"]
    },
    "timeoutDurationInHours": "integer",
    "jobExpirationTime": "timestamp"
}
```

---

### `list-model-invocation-jobs`

Lists batch inference jobs. **Paginated operation.**

**Synopsis:**
```bash
aws bedrock list-model-invocation-jobs \
    [--submit-time-after <value>] \
    [--submit-time-before <value>] \
    [--status-equals <value>] \
    [--name-contains <value>] \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--submit-time-after` | No | timestamp | None | Filter by submit time |
| `--submit-time-before` | No | timestamp | None | Filter by submit time |
| `--status-equals` | No | string | None | Filter by status |
| `--name-contains` | No | string | None | Filter by name substring |
| `--sort-by` | No | string | None | Sort field: `CreationTime` |
| `--sort-order` | No | string | None | `Ascending`, `Descending` |

**Output Schema:**
```json
{
    "nextToken": "string",
    "invocationJobSummaries": [
        {
            "jobArn": "string",
            "jobName": "string",
            "modelId": "string",
            "status": "Submitted|InProgress|Completed|Failed|Stopping|Stopped|PartiallyCompleted|Expired|Validating|Scheduled",
            "message": "string",
            "submitTime": "timestamp",
            "lastModifiedTime": "timestamp",
            "endTime": "timestamp",
            "inputDataConfig": {...},
            "outputDataConfig": {...},
            "vpcConfig": {...},
            "timeoutDurationInHours": "integer",
            "jobExpirationTime": "timestamp"
        }
    ]
}
```

---

### `stop-model-invocation-job`

Stops a running batch inference job.

**Synopsis:**
```bash
aws bedrock stop-model-invocation-job \
    --job-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-identifier` | **Yes** | string | -- | Job name or ARN |

**Output:** None (HTTP 200 on success)
