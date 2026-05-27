# Pipelines

## 1. `create-pipeline`

Creates a SageMaker pipeline for orchestrating ML workflows.

**Synopsis:**
```bash
aws sagemaker create-pipeline \
    --pipeline-name <value> \
    --role-arn <value> \
    [--pipeline-display-name <value>] \
    [--pipeline-definition <value>] \
    [--pipeline-definition-s3-location <value>] \
    [--pipeline-description <value>] \
    [--client-request-token <value>] \
    [--parallelism-configuration <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pipeline-name` | **Yes** | string | -- | Unique name (1-256 chars) |
| `--role-arn` | **Yes** | string | -- | IAM role ARN |
| `--pipeline-display-name` | No | string | -- | Display name (1-256 chars) |
| `--pipeline-definition` | No | string | -- | Pipeline definition JSON (max 1048576 chars) |
| `--pipeline-definition-s3-location` | No | structure | -- | S3 location for pipeline definition (`Bucket`, `ObjectKey`, `VersionId`) |
| `--pipeline-description` | No | string | -- | Description (max 3072 chars) |
| `--client-request-token` | No | string | -- | Idempotency token |
| `--parallelism-configuration` | No | structure | -- | `MaxParallelExecutionSteps` |
| `--tags` | No | list | -- | Key-value tags |

**Output Schema:**
```json
{
    "PipelineArn": "string"
}
```

---

## 2. `describe-pipeline`

Returns details about a pipeline.

**Synopsis:**
```bash
aws sagemaker describe-pipeline \
    --pipeline-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pipeline-name` | **Yes** | string | -- | Pipeline name |

**Output Schema:**
```json
{
    "PipelineArn": "string",
    "PipelineName": "string",
    "PipelineDisplayName": "string",
    "PipelineDefinition": "string",
    "PipelineDescription": "string",
    "RoleArn": "string",
    "PipelineStatus": "Active|Deleting",
    "CreationTime": "timestamp",
    "LastModifiedTime": "timestamp",
    "LastRunTime": "timestamp",
    "CreatedBy": {"UserProfileArn": "string", "UserProfileName": "string", "DomainId": "string", "IamIdentity": {...}},
    "LastModifiedBy": {...},
    "ParallelismConfiguration": {"MaxParallelExecutionSteps": "integer"}
}
```

---

## 3. `list-pipelines`

Lists pipelines. **Paginated operation.**

**Synopsis:**
```bash
aws sagemaker list-pipelines \
    [--pipeline-name-prefix <value>] \
    [--created-after <value>] \
    [--created-before <value>] \
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
| `--pipeline-name-prefix` | No | string | -- | Filter by name prefix |
| `--created-after` | No | timestamp | -- | Filter by creation time |
| `--created-before` | No | timestamp | -- | Filter by creation time |
| `--sort-by` | No | string | `CreationTime` | `Name`, `CreationTime` |
| `--sort-order` | No | string | `Descending` | `Ascending`, `Descending` |

**Output Schema:**
```json
{
    "PipelineSummaries": [
        {
            "PipelineArn": "string",
            "PipelineName": "string",
            "PipelineDisplayName": "string",
            "PipelineDescription": "string",
            "RoleArn": "string",
            "CreationTime": "timestamp",
            "LastModifiedTime": "timestamp",
            "LastExecutionTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

## 4. `update-pipeline`

Updates a pipeline.

**Synopsis:**
```bash
aws sagemaker update-pipeline \
    --pipeline-name <value> \
    [--pipeline-display-name <value>] \
    [--pipeline-definition <value>] \
    [--pipeline-definition-s3-location <value>] \
    [--pipeline-description <value>] \
    [--role-arn <value>] \
    [--parallelism-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pipeline-name` | **Yes** | string | -- | Pipeline name |
| `--pipeline-display-name` | No | string | -- | Updated display name |
| `--pipeline-definition` | No | string | -- | Updated pipeline definition |
| `--pipeline-definition-s3-location` | No | structure | -- | Updated S3 definition location |
| `--pipeline-description` | No | string | -- | Updated description |
| `--role-arn` | No | string | -- | Updated IAM role |
| `--parallelism-configuration` | No | structure | -- | Updated parallelism |

**Output Schema:**
```json
{
    "PipelineArn": "string"
}
```

---

## 5. `delete-pipeline`

Deletes a pipeline.

**Synopsis:**
```bash
aws sagemaker delete-pipeline \
    --pipeline-name <value> \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pipeline-name` | **Yes** | string | -- | Pipeline name |
| `--client-request-token` | No | string | -- | Idempotency token |

**Output Schema:**
```json
{
    "PipelineArn": "string"
}
```

---

## 6. `start-pipeline-execution`

Starts a pipeline execution.

**Synopsis:**
```bash
aws sagemaker start-pipeline-execution \
    --pipeline-name <value> \
    [--pipeline-execution-display-name <value>] \
    [--pipeline-parameters <value>] \
    [--pipeline-execution-description <value>] \
    [--client-request-token <value>] \
    [--parallelism-configuration <value>] \
    [--selective-execution-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pipeline-name` | **Yes** | string | -- | Pipeline name |
| `--pipeline-execution-display-name` | No | string | -- | Display name for execution |
| `--pipeline-parameters` | No | list | -- | `[{Name, Value}]` parameter overrides |
| `--pipeline-execution-description` | No | string | -- | Description |
| `--client-request-token` | No | string | -- | Idempotency token |
| `--parallelism-configuration` | No | structure | -- | Override parallelism |
| `--selective-execution-config` | No | structure | -- | Run only selected steps |

**Output Schema:**
```json
{
    "PipelineExecutionArn": "string"
}
```

---

## 7. `describe-pipeline-execution`

Returns details about a pipeline execution.

**Synopsis:**
```bash
aws sagemaker describe-pipeline-execution \
    --pipeline-execution-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pipeline-execution-arn` | **Yes** | string | -- | Pipeline execution ARN |

**Output Schema:**
```json
{
    "PipelineArn": "string",
    "PipelineExecutionArn": "string",
    "PipelineExecutionDisplayName": "string",
    "PipelineExecutionStatus": "Executing|Stopping|Stopped|Failed|Succeeded",
    "PipelineExecutionDescription": "string",
    "PipelineExperimentConfig": {
        "ExperimentName": "string",
        "TrialName": "string"
    },
    "FailureReason": "string",
    "CreationTime": "timestamp",
    "LastModifiedTime": "timestamp",
    "CreatedBy": {...},
    "LastModifiedBy": {...},
    "ParallelismConfiguration": {"MaxParallelExecutionSteps": "integer"},
    "SelectiveExecutionConfig": {...}
}
```

---

## 8. `list-pipeline-executions`

Lists pipeline executions. **Paginated operation.**

**Synopsis:**
```bash
aws sagemaker list-pipeline-executions \
    --pipeline-name <value> \
    [--created-after <value>] \
    [--created-before <value>] \
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
| `--pipeline-name` | **Yes** | string | -- | Pipeline name |
| `--created-after` | No | timestamp | -- | Filter by creation time |
| `--created-before` | No | timestamp | -- | Filter by creation time |
| `--sort-by` | No | string | `CreationTime` | `CreationTime`, `PipelineExecutionArn` |
| `--sort-order` | No | string | `Descending` | `Ascending`, `Descending` |

**Output Schema:**
```json
{
    "PipelineExecutionSummaries": [
        {
            "PipelineExecutionArn": "string",
            "StartTime": "timestamp",
            "PipelineExecutionStatus": "Executing|Stopping|Stopped|Failed|Succeeded",
            "PipelineExecutionDescription": "string",
            "PipelineExecutionDisplayName": "string",
            "PipelineExecutionFailureReason": "string"
        }
    ],
    "NextToken": "string"
}
```

---

## 9. `stop-pipeline-execution`

Stops a pipeline execution.

**Synopsis:**
```bash
aws sagemaker stop-pipeline-execution \
    --pipeline-execution-arn <value> \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pipeline-execution-arn` | **Yes** | string | -- | Pipeline execution ARN |
| `--client-request-token` | No | string | -- | Idempotency token |

**Output Schema:**
```json
{
    "PipelineExecutionArn": "string"
}
```

---

## 10. `retry-pipeline-execution`

Retries a failed pipeline execution.

**Synopsis:**
```bash
aws sagemaker retry-pipeline-execution \
    --pipeline-execution-arn <value> \
    [--client-request-token <value>] \
    [--parallelism-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pipeline-execution-arn` | **Yes** | string | -- | Pipeline execution ARN |
| `--client-request-token` | No | string | -- | Idempotency token |
| `--parallelism-configuration` | No | structure | -- | Parallelism override |

**Output Schema:**
```json
{
    "PipelineExecutionArn": "string"
}
```

---

## 11. `list-pipeline-execution-steps`

Lists the steps of a pipeline execution. **Paginated operation.**

**Synopsis:**
```bash
aws sagemaker list-pipeline-execution-steps \
    --pipeline-execution-arn <value> \
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
| `--pipeline-execution-arn` | **Yes** | string | -- | Pipeline execution ARN |
| `--sort-order` | No | string | `Descending` | `Ascending`, `Descending` |

**Output Schema:**
```json
{
    "PipelineExecutionSteps": [
        {
            "StepName": "string",
            "StepDisplayName": "string",
            "StepDescription": "string",
            "StartTime": "timestamp",
            "EndTime": "timestamp",
            "StepStatus": "Starting|Executing|Stopping|Stopped|Failed|Succeeded",
            "CacheHitResult": {"SourcePipelineExecutionArn": "string"},
            "FailureReason": "string",
            "Metadata": {
                "TrainingJob": {"Arn": "string"},
                "ProcessingJob": {"Arn": "string"},
                "TransformJob": {"Arn": "string"},
                "TuningJob": {"Arn": "string"},
                "Model": {"Arn": "string"},
                "RegisterModel": {"Arn": "string"},
                "Condition": {"Outcome": "True|False"},
                "Callback": {"CallbackToken": "string", "SqsQueueUrl": "string", "OutputParameters": [...]},
                "Lambda": {"Arn": "string", "OutputParameters": [...]}
            },
            "AttemptCount": "integer",
            "SelectiveExecutionResult": {"SourcePipelineExecutionArn": "string"}
        }
    ],
    "NextToken": "string"
}
```

---

## 12. `list-pipeline-parameters-for-execution`

Lists parameters for a pipeline execution. **Paginated operation.**

**Synopsis:**
```bash
aws sagemaker list-pipeline-parameters-for-execution \
    --pipeline-execution-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pipeline-execution-arn` | **Yes** | string | -- | Pipeline execution ARN |

**Output Schema:**
```json
{
    "PipelineParameters": [
        {
            "Name": "string",
            "Value": "string"
        }
    ],
    "NextToken": "string"
}
```

---

## 13. `send-pipeline-execution-step-success`

Notifies a pipeline execution step of success (for callback steps).

**Synopsis:**
```bash
aws sagemaker send-pipeline-execution-step-success \
    --callback-token <value> \
    [--output-parameters <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--callback-token` | **Yes** | string | -- | Callback token from SQS message |
| `--output-parameters` | No | list | -- | `[{Name, Value}]` output parameters |
| `--client-request-token` | No | string | -- | Idempotency token |

**Output Schema:**
```json
{
    "PipelineExecutionArn": "string"
}
```

---

## 14. `send-pipeline-execution-step-failure`

Notifies a pipeline execution step of failure (for callback steps).

**Synopsis:**
```bash
aws sagemaker send-pipeline-execution-step-failure \
    --callback-token <value> \
    [--failure-reason <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--callback-token` | **Yes** | string | -- | Callback token from SQS message |
| `--failure-reason` | No | string | -- | Failure reason (max 256 chars) |
| `--client-request-token` | No | string | -- | Idempotency token |

**Output Schema:**
```json
{
    "PipelineExecutionArn": "string"
}
```
