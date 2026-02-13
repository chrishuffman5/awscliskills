# Inference

### 3.1 `create-inference-scheduler`

Creates an inference scheduler for running inference on sensor data at regular intervals.

**Synopsis:**
```bash
aws lookoutequipment create-inference-scheduler \
    --model-name <value> \
    --inference-scheduler-name <value> \
    --data-upload-frequency <value> \
    --data-input-configuration <value> \
    --data-output-configuration <value> \
    --role-arn <value> \
    [--data-delay-offset-in-minutes <value>] \
    [--server-side-kms-key-id <value>] \
    [--client-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--model-name` | **Yes** | string | -- | Name of the trained model |
| `--inference-scheduler-name` | **Yes** | string | -- | Scheduler name (1-200 chars) |
| `--data-upload-frequency` | **Yes** | string | -- | Upload frequency: `PT5M`, `PT10M`, `PT15M`, `PT30M`, `PT1H` |
| `--data-input-configuration` | **Yes** | structure | -- | S3 input configuration |
| `--data-output-configuration` | **Yes** | structure | -- | S3 output configuration |
| `--role-arn` | **Yes** | string | -- | IAM role with S3 access |
| `--data-delay-offset-in-minutes` | No | long | None | Delay in minutes (0-60) |
| `--server-side-kms-key-id` | No | string | None | KMS key for encryption |
| `--client-token` | No | string | Auto | Idempotency token |
| `--tags` | No | list | None | Tags (max 200) |

**DataInputConfiguration:**
```json
{
    "S3InputConfiguration": {
        "Bucket": "my-input-bucket",
        "Prefix": "inference/"
    },
    "InputTimeZoneOffset": "+00:00",
    "InferenceInputNameConfiguration": {
        "TimestampFormat": "yyyy-MM-dd-HH-mm-ss",
        "ComponentTimestampDelimiter": "_"
    }
}
```

**DataOutputConfiguration:**
```json
{
    "S3OutputConfiguration": {
        "Bucket": "my-output-bucket",
        "Prefix": "results/"
    },
    "KmsKeyId": "string"
}
```

**Output Schema:**
```json
{
    "InferenceSchedulerArn": "string",
    "InferenceSchedulerName": "string",
    "Status": "PENDING|RUNNING|STOPPING|STOPPED",
    "ModelQuality": "QUALITY_THRESHOLD_MET|CANNOT_DETERMINE_QUALITY|POOR_QUALITY_DETECTED"
}
```

---

### 3.2 `describe-inference-scheduler`

Describes an inference scheduler.

**Synopsis:**
```bash
aws lookoutequipment describe-inference-scheduler \
    --inference-scheduler-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--inference-scheduler-name` | **Yes** | string | -- | Name of the inference scheduler |

**Output Schema:**
```json
{
    "ModelArn": "string",
    "ModelName": "string",
    "InferenceSchedulerName": "string",
    "InferenceSchedulerArn": "string",
    "Status": "PENDING|RUNNING|STOPPING|STOPPED",
    "DataDelayOffsetInMinutes": "long",
    "DataUploadFrequency": "PT5M|PT10M|PT15M|PT30M|PT1H",
    "CreatedAt": "timestamp",
    "UpdatedAt": "timestamp",
    "DataInputConfiguration": {
        "S3InputConfiguration": {"Bucket": "string", "Prefix": "string"},
        "InputTimeZoneOffset": "string",
        "InferenceInputNameConfiguration": {
            "TimestampFormat": "string",
            "ComponentTimestampDelimiter": "string"
        }
    },
    "DataOutputConfiguration": {
        "S3OutputConfiguration": {"Bucket": "string", "Prefix": "string"},
        "KmsKeyId": "string"
    },
    "RoleArn": "string",
    "ServerSideKmsKeyId": "string",
    "LatestInferenceResult": "ANOMALOUS|NORMAL"
}
```

---

### 3.3 `list-inference-schedulers`

Lists inference schedulers. **Paginated operation.**

**Synopsis:**
```bash
aws lookoutequipment list-inference-schedulers \
    [--next-token <value>] \
    [--max-results <value>] \
    [--inference-scheduler-name-begins-with <value>] \
    [--model-name <value>] \
    [--status <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results per page (1-500) |
| `--inference-scheduler-name-begins-with` | No | string | None | Filter by name prefix |
| `--model-name` | No | string | None | Filter by model name |
| `--status` | No | string | None | Filter: `PENDING`, `RUNNING`, `STOPPING`, `STOPPED` |

**Output Schema:**
```json
{
    "NextToken": "string",
    "InferenceSchedulerSummaries": [
        {
            "ModelName": "string",
            "ModelArn": "string",
            "InferenceSchedulerName": "string",
            "InferenceSchedulerArn": "string",
            "Status": "PENDING|RUNNING|STOPPING|STOPPED",
            "DataDelayOffsetInMinutes": "long",
            "DataUploadFrequency": "PT5M|PT10M|PT15M|PT30M|PT1H",
            "LatestInferenceResult": "ANOMALOUS|NORMAL"
        }
    ]
}
```

---

### 3.4 `update-inference-scheduler`

Updates an inference scheduler configuration. Scheduler must be stopped.

**Synopsis:**
```bash
aws lookoutequipment update-inference-scheduler \
    --inference-scheduler-name <value> \
    [--data-delay-offset-in-minutes <value>] \
    [--data-upload-frequency <value>] \
    [--data-input-configuration <value>] \
    [--data-output-configuration <value>] \
    [--role-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--inference-scheduler-name` | **Yes** | string | -- | Name of the inference scheduler |
| `--data-delay-offset-in-minutes` | No | long | None | Updated delay (0-60 minutes) |
| `--data-upload-frequency` | No | string | None | Updated frequency |
| `--data-input-configuration` | No | structure | None | Updated input configuration |
| `--data-output-configuration` | No | structure | None | Updated output configuration |
| `--role-arn` | No | string | None | Updated IAM role ARN |

**Output:** None

---

### 3.5 `delete-inference-scheduler`

Deletes an inference scheduler. Scheduler must be stopped.

**Synopsis:**
```bash
aws lookoutequipment delete-inference-scheduler \
    --inference-scheduler-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--inference-scheduler-name` | **Yes** | string | -- | Name of the scheduler to delete |

**Output:** None

---

### 3.6 `start-inference-scheduler`

Starts an inference scheduler.

**Synopsis:**
```bash
aws lookoutequipment start-inference-scheduler \
    --inference-scheduler-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--inference-scheduler-name` | **Yes** | string | -- | Name of the scheduler to start |

**Output Schema:**
```json
{
    "ModelArn": "string",
    "ModelName": "string",
    "InferenceSchedulerName": "string",
    "InferenceSchedulerArn": "string",
    "Status": "PENDING|RUNNING|STOPPING|STOPPED"
}
```

---

### 3.7 `stop-inference-scheduler`

Stops an inference scheduler.

**Synopsis:**
```bash
aws lookoutequipment stop-inference-scheduler \
    --inference-scheduler-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--inference-scheduler-name` | **Yes** | string | -- | Name of the scheduler to stop |

**Output Schema:**
```json
{
    "ModelArn": "string",
    "ModelName": "string",
    "InferenceSchedulerName": "string",
    "InferenceSchedulerArn": "string",
    "Status": "PENDING|RUNNING|STOPPING|STOPPED"
}
```

---

### 3.8 `list-inference-executions`

Lists inference executions for a scheduler. **Paginated operation.**

**Synopsis:**
```bash
aws lookoutequipment list-inference-executions \
    --inference-scheduler-name <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--data-start-time-after <value>] \
    [--data-end-time-before <value>] \
    [--status <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--inference-scheduler-name` | **Yes** | string | -- | Name of the inference scheduler |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results per page (1-500) |
| `--data-start-time-after` | No | timestamp | None | Filter by data start time |
| `--data-end-time-before` | No | timestamp | None | Filter by data end time |
| `--status` | No | string | None | Filter: `IN_PROGRESS`, `SUCCESS`, `FAILED` |

**Output Schema:**
```json
{
    "NextToken": "string",
    "InferenceExecutionSummaries": [
        {
            "ModelName": "string",
            "ModelArn": "string",
            "InferenceSchedulerName": "string",
            "InferenceSchedulerArn": "string",
            "ScheduledStartTime": "timestamp",
            "DataStartTime": "timestamp",
            "DataEndTime": "timestamp",
            "DataInputConfiguration": {},
            "DataOutputConfiguration": {},
            "CustomerResultObject": {"Bucket": "string", "Key": "string"},
            "Status": "IN_PROGRESS|SUCCESS|FAILED",
            "FailedReason": "string",
            "ModelVersion": "long",
            "ModelVersionArn": "string"
        }
    ]
}
```

---

### 3.9 `list-inference-events`

Lists detected anomaly events for a scheduler within a time range. **Paginated operation.**

**Synopsis:**
```bash
aws lookoutequipment list-inference-events \
    --inference-scheduler-name <value> \
    --interval-start-time <value> \
    --interval-end-time <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--inference-scheduler-name` | **Yes** | string | -- | Name of the inference scheduler |
| `--interval-start-time` | **Yes** | timestamp | -- | Start of time range |
| `--interval-end-time` | **Yes** | timestamp | -- | End of time range |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results per page (1-500) |

**Output Schema:**
```json
{
    "NextToken": "string",
    "InferenceEventSummaries": [
        {
            "InferenceSchedulerArn": "string",
            "InferenceSchedulerName": "string",
            "EventStartTime": "timestamp",
            "EventEndTime": "timestamp",
            "Diagnostics": "string",
            "EventDurationInSeconds": "long"
        }
    ]
}
```
