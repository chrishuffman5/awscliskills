# Batch Jobs

### 7.1 `create-batch-inference-job`

Creates a batch inference job to generate recommendations for a set of users or items from input data in S3.

**Synopsis:**
```bash
aws personalize create-batch-inference-job \
    --job-name <value> \
    --solution-version-arn <value> \
    --job-input <value> \
    --job-output <value> \
    --role-arn <value> \
    [--filter-arn <value>] \
    [--num-results <value>] \
    [--batch-inference-job-config <value>] \
    [--tags <value>] \
    [--batch-inference-job-mode <value>] \
    [--theme-generation-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-name` | **Yes** | string | -- | Job name (1-63 chars) |
| `--solution-version-arn` | **Yes** | string | -- | ARN of the solution version |
| `--job-input` | **Yes** | structure | -- | S3 input data path |
| `--job-output` | **Yes** | structure | -- | S3 output data path |
| `--role-arn` | **Yes** | string | -- | IAM role ARN with S3 access |
| `--filter-arn` | No | string | None | ARN of filter to apply |
| `--num-results` | No | integer | None | Number of recommendations per user/item |
| `--batch-inference-job-config` | No | structure | None | Configuration (item exploration) |
| `--tags` | No | list | None | Tags (max 200) |
| `--batch-inference-job-mode` | No | string | `BATCH_INFERENCE` | Mode: `BATCH_INFERENCE` or `THEME_GENERATION` |
| `--theme-generation-config` | No | structure | None | Theme generation configuration |

**JobInput/JobOutput Structure:**
```json
{
    "s3DataSource": {
        "path": "s3://bucket/input/",
        "kmsKeyArn": "string"
    }
}
```

**Output Schema:**
```json
{
    "batchInferenceJobArn": "string"
}
```

---

### 7.2 `describe-batch-inference-job`

Describes a batch inference job.

**Synopsis:**
```bash
aws personalize describe-batch-inference-job \
    --batch-inference-job-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--batch-inference-job-arn` | **Yes** | string | -- | ARN of the batch inference job |

**Output Schema:**
```json
{
    "batchInferenceJob": {
        "jobName": "string",
        "batchInferenceJobArn": "string",
        "filterArn": "string",
        "failureReason": "string",
        "solutionVersionArn": "string",
        "numResults": "integer",
        "jobInput": {"s3DataSource": {"path": "string", "kmsKeyArn": "string"}},
        "jobOutput": {"s3DataDestination": {"path": "string", "kmsKeyArn": "string"}},
        "batchInferenceJobConfig": {},
        "roleArn": "string",
        "batchInferenceJobMode": "BATCH_INFERENCE|THEME_GENERATION",
        "themeGenerationConfig": {},
        "status": "string",
        "creationDateTime": "timestamp",
        "lastUpdatedDateTime": "timestamp"
    }
}
```

---

### 7.3 `list-batch-inference-jobs`

Lists batch inference jobs. **Paginated operation.**

**Synopsis:**
```bash
aws personalize list-batch-inference-jobs \
    [--solution-version-arn <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--solution-version-arn` | No | string | None | Filter by solution version ARN |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call (max 100) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "batchInferenceJobs": [
        {
            "batchInferenceJobArn": "string",
            "jobName": "string",
            "status": "string",
            "creationDateTime": "timestamp",
            "lastUpdatedDateTime": "timestamp",
            "failureReason": "string",
            "solutionVersionArn": "string",
            "batchInferenceJobMode": "BATCH_INFERENCE|THEME_GENERATION"
        }
    ],
    "nextToken": "string"
}
```

---

### 7.4 `create-batch-segment-job`

Creates a batch segment job to identify users who will interact with items in an input dataset.

**Synopsis:**
```bash
aws personalize create-batch-segment-job \
    --job-name <value> \
    --solution-version-arn <value> \
    --job-input <value> \
    --job-output <value> \
    --role-arn <value> \
    [--filter-arn <value>] \
    [--num-results <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-name` | **Yes** | string | -- | Job name (1-63 chars) |
| `--solution-version-arn` | **Yes** | string | -- | ARN of the solution version (must use Item-Affinity or Item-Action-Affinity recipe) |
| `--job-input` | **Yes** | structure | -- | S3 input data path |
| `--job-output` | **Yes** | structure | -- | S3 output data path |
| `--role-arn` | **Yes** | string | -- | IAM role ARN with S3 access |
| `--filter-arn` | No | string | None | ARN of filter to apply |
| `--num-results` | No | integer | None | Number of users to return per item |
| `--tags` | No | list | None | Tags (max 200) |

**Output Schema:**
```json
{
    "batchSegmentJobArn": "string"
}
```

---

### 7.5 `describe-batch-segment-job`

Describes a batch segment job.

**Synopsis:**
```bash
aws personalize describe-batch-segment-job \
    --batch-segment-job-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--batch-segment-job-arn` | **Yes** | string | -- | ARN of the batch segment job |

**Output Schema:**
```json
{
    "batchSegmentJob": {
        "jobName": "string",
        "batchSegmentJobArn": "string",
        "filterArn": "string",
        "failureReason": "string",
        "solutionVersionArn": "string",
        "numResults": "integer",
        "jobInput": {},
        "jobOutput": {},
        "roleArn": "string",
        "status": "string",
        "creationDateTime": "timestamp",
        "lastUpdatedDateTime": "timestamp"
    }
}
```

---

### 7.6 `list-batch-segment-jobs`

Lists batch segment jobs. **Paginated operation.**

**Synopsis:**
```bash
aws personalize list-batch-segment-jobs \
    [--solution-version-arn <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--solution-version-arn` | No | string | None | Filter by solution version ARN |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call (max 100) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "batchSegmentJobs": [
        {
            "batchSegmentJobArn": "string",
            "jobName": "string",
            "status": "string",
            "creationDateTime": "timestamp",
            "lastUpdatedDateTime": "timestamp",
            "failureReason": "string",
            "solutionVersionArn": "string"
        }
    ],
    "nextToken": "string"
}
```
