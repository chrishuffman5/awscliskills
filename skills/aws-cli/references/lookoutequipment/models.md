# Models

### 2.1 `create-model`

Trains a new ML model for anomaly detection using a dataset of sensor data.

**Synopsis:**
```bash
aws lookoutequipment create-model \
    --model-name <value> \
    --dataset-name <value> \
    [--dataset-schema <value>] \
    [--labels-input-configuration <value>] \
    [--client-token <value>] \
    [--training-data-start-time <value>] \
    [--training-data-end-time <value>] \
    [--evaluation-data-start-time <value>] \
    [--evaluation-data-end-time <value>] \
    [--role-arn <value>] \
    [--data-pre-processing-configuration <value>] \
    [--server-side-kms-key-id <value>] \
    [--tags <value>] \
    [--off-condition <value>] \
    [--model-diagnostics-output-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--model-name` | **Yes** | string | -- | Model name (1-200 chars) |
| `--dataset-name` | **Yes** | string | -- | Dataset to train on |
| `--dataset-schema` | No | structure | None | Data schema with `InlineDataSchema` |
| `--labels-input-configuration` | No | structure | None | Label data location |
| `--client-token` | No | string | Auto | Idempotency token |
| `--training-data-start-time` | No | timestamp | None | Training data start time |
| `--training-data-end-time` | No | timestamp | None | Training data end time |
| `--evaluation-data-start-time` | No | timestamp | None | Evaluation data start time |
| `--evaluation-data-end-time` | No | timestamp | None | Evaluation data end time |
| `--role-arn` | No | string | None | IAM role for data access |
| `--data-pre-processing-configuration` | No | structure | None | Target sampling rate |
| `--server-side-kms-key-id` | No | string | None | KMS key for encryption |
| `--tags` | No | list | None | Tags (max 200) |
| `--off-condition` | No | string | None | Equipment off condition expression |
| `--model-diagnostics-output-configuration` | No | structure | None | S3 location for diagnostics output |

**DataPreProcessingConfiguration:**
```json
{
    "TargetSamplingRate": "PT1S|PT5S|PT10S|PT15S|PT30S|PT1M|PT5M|PT10M|PT15M|PT30M|PT1H"
}
```

**LabelsInputConfiguration:**
```json
{
    "S3InputConfiguration": {
        "Bucket": "string",
        "Prefix": "string"
    },
    "LabelGroupName": "string"
}
```

**Output Schema:**
```json
{
    "ModelArn": "string",
    "Status": "IN_PROGRESS|SUCCESS|FAILED|IMPORT_IN_PROGRESS"
}
```

---

### 2.2 `describe-model`

Describes a model including training metrics, status, and version information.

**Synopsis:**
```bash
aws lookoutequipment describe-model \
    --model-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--model-name` | **Yes** | string | -- | Name of the model |

**Output Schema:**
```json
{
    "ModelName": "string",
    "ModelArn": "string",
    "DatasetName": "string",
    "DatasetArn": "string",
    "Schema": "string",
    "LabelsInputConfiguration": {},
    "TrainingDataStartTime": "timestamp",
    "TrainingDataEndTime": "timestamp",
    "EvaluationDataStartTime": "timestamp",
    "EvaluationDataEndTime": "timestamp",
    "RoleArn": "string",
    "DataPreProcessingConfiguration": {
        "TargetSamplingRate": "string"
    },
    "Status": "IN_PROGRESS|SUCCESS|FAILED|IMPORT_IN_PROGRESS",
    "TrainingExecutionStartTime": "timestamp",
    "TrainingExecutionEndTime": "timestamp",
    "FailedReason": "string",
    "ModelMetrics": "string",
    "LastUpdatedTime": "timestamp",
    "CreatedAt": "timestamp",
    "ServerSideKmsKeyId": "string",
    "OffCondition": "string",
    "SourceModelVersionArn": "string",
    "ActiveModelVersion": "long",
    "ActiveModelVersionArn": "string",
    "ModelVersionActivatedAt": "timestamp",
    "PreviousActiveModelVersion": "long",
    "PreviousActiveModelVersionArn": "string",
    "PreviousModelVersionActivatedAt": "timestamp",
    "PriorModelMetrics": "string",
    "LatestScheduledRetrainingStatus": "IN_PROGRESS|SUCCESS|FAILED|IMPORT_IN_PROGRESS|CANCELED",
    "LatestScheduledRetrainingModelVersion": "long",
    "LatestScheduledRetrainingStartTime": "timestamp",
    "LatestScheduledRetrainingAvailableDataInDays": "integer",
    "NextScheduledRetrainingStartDate": "timestamp",
    "AccumulatedInferenceDataStartTime": "timestamp",
    "AccumulatedInferenceDataEndTime": "timestamp",
    "RetrainingSchedulerStatus": "PENDING|RUNNING|STOPPING|STOPPED",
    "ModelDiagnosticsOutputConfiguration": {
        "S3OutputConfiguration": {"Bucket": "string", "Prefix": "string"},
        "KmsKeyId": "string"
    },
    "ModelQuality": "QUALITY_THRESHOLD_MET|CANNOT_DETERMINE_QUALITY|POOR_QUALITY_DETECTED"
}
```

---

### 2.3 `list-models`

Lists models. **Paginated operation.**

**Synopsis:**
```bash
aws lookoutequipment list-models \
    [--next-token <value>] \
    [--max-results <value>] \
    [--status <value>] \
    [--model-name-begins-with <value>] \
    [--dataset-name-begins-with <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results per page (1-500) |
| `--status` | No | string | None | Filter: `IN_PROGRESS`, `SUCCESS`, `FAILED`, `IMPORT_IN_PROGRESS` |
| `--model-name-begins-with` | No | string | None | Filter by model name prefix |
| `--dataset-name-begins-with` | No | string | None | Filter by dataset name prefix |

**Output Schema:**
```json
{
    "NextToken": "string",
    "ModelSummaries": [
        {
            "ModelName": "string",
            "ModelArn": "string",
            "DatasetName": "string",
            "DatasetArn": "string",
            "Status": "IN_PROGRESS|SUCCESS|FAILED|IMPORT_IN_PROGRESS",
            "CreatedAt": "timestamp",
            "ActiveModelVersion": "long",
            "ActiveModelVersionArn": "string",
            "LatestScheduledRetrainingStatus": "string",
            "LatestScheduledRetrainingModelVersion": "long",
            "LatestScheduledRetrainingStartTime": "timestamp",
            "NextScheduledRetrainingStartDate": "timestamp",
            "RetrainingSchedulerStatus": "PENDING|RUNNING|STOPPING|STOPPED",
            "ModelDiagnosticsOutputConfiguration": {},
            "ModelQuality": "QUALITY_THRESHOLD_MET|CANNOT_DETERMINE_QUALITY|POOR_QUALITY_DETECTED"
        }
    ]
}
```

---

### 2.4 `update-model`

Updates a model's label configuration, role, or diagnostics output.

**Synopsis:**
```bash
aws lookoutequipment update-model \
    --model-name <value> \
    [--labels-input-configuration <value>] \
    [--role-arn <value>] \
    [--model-diagnostics-output-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--model-name` | **Yes** | string | -- | Name of the model to update |
| `--labels-input-configuration` | No | structure | None | Updated label input configuration |
| `--role-arn` | No | string | None | Updated IAM role ARN |
| `--model-diagnostics-output-configuration` | No | structure | None | Updated diagnostics output S3 location |

**Output:** None

---

### 2.5 `delete-model`

Deletes a model.

**Synopsis:**
```bash
aws lookoutequipment delete-model \
    --model-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--model-name` | **Yes** | string | -- | Name of the model to delete |

**Output:** None

---

### 2.6 `describe-model-version`

Describes a specific version of a model.

**Synopsis:**
```bash
aws lookoutequipment describe-model-version \
    --model-name <value> \
    --model-version <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--model-name` | **Yes** | string | -- | Name of the model |
| `--model-version` | **Yes** | long | -- | Version number (min 1) |

**Output Schema:**
```json
{
    "ModelName": "string",
    "ModelArn": "string",
    "ModelVersion": "long",
    "ModelVersionArn": "string",
    "Status": "IN_PROGRESS|SUCCESS|FAILED|IMPORT_IN_PROGRESS|CANCELED",
    "SourceType": "TRAINING|RETRAINING|IMPORT",
    "DatasetName": "string",
    "DatasetArn": "string",
    "Schema": "string",
    "LabelsInputConfiguration": {},
    "TrainingDataStartTime": "timestamp",
    "TrainingDataEndTime": "timestamp",
    "EvaluationDataStartTime": "timestamp",
    "EvaluationDataEndTime": "timestamp",
    "RoleArn": "string",
    "DataPreProcessingConfiguration": {"TargetSamplingRate": "string"},
    "TrainingExecutionStartTime": "timestamp",
    "TrainingExecutionEndTime": "timestamp",
    "FailedReason": "string",
    "ModelMetrics": "string",
    "LastUpdatedTime": "timestamp",
    "CreatedAt": "timestamp",
    "ServerSideKmsKeyId": "string",
    "OffCondition": "string",
    "SourceModelVersionArn": "string",
    "ImportJobStartTime": "timestamp",
    "ImportJobEndTime": "timestamp",
    "ImportedDataSizeInBytes": "long",
    "PriorModelMetrics": "string",
    "RetrainingAvailableDataInDays": "integer",
    "AutoPromotionResult": "MODEL_PROMOTED|MODEL_NOT_PROMOTED|RETRAINING_INTERNAL_ERROR|RETRAINING_CUSTOMER_ERROR|RETRAINING_CANCELLED",
    "AutoPromotionResultReason": "string",
    "ModelDiagnosticsOutputConfiguration": {},
    "ModelDiagnosticsResultsObject": {"Bucket": "string", "Key": "string"},
    "ModelQuality": "QUALITY_THRESHOLD_MET|CANNOT_DETERMINE_QUALITY|POOR_QUALITY_DETECTED"
}
```

---

### 2.7 `list-model-versions`

Lists versions of a model. **Paginated operation.**

**Synopsis:**
```bash
aws lookoutequipment list-model-versions \
    --model-name <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--status <value>] \
    [--source-type <value>] \
    [--created-at-end-time <value>] \
    [--created-at-start-time <value>] \
    [--max-model-version <value>] \
    [--min-model-version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--model-name` | **Yes** | string | -- | Name of the model |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results per page (1-500) |
| `--status` | No | string | None | Filter by status |
| `--source-type` | No | string | None | Filter: `TRAINING`, `RETRAINING`, `IMPORT` |
| `--created-at-end-time` | No | timestamp | None | Filter by creation end time |
| `--created-at-start-time` | No | timestamp | None | Filter by creation start time |
| `--max-model-version` | No | long | None | Max version number filter |
| `--min-model-version` | No | long | None | Min version number filter |

**Output Schema:**
```json
{
    "NextToken": "string",
    "ModelVersionSummaries": [
        {
            "ModelName": "string",
            "ModelArn": "string",
            "ModelVersion": "long",
            "ModelVersionArn": "string",
            "CreatedAt": "timestamp",
            "Status": "IN_PROGRESS|SUCCESS|FAILED|IMPORT_IN_PROGRESS|CANCELED",
            "SourceType": "TRAINING|RETRAINING|IMPORT",
            "ModelQuality": "QUALITY_THRESHOLD_MET|CANNOT_DETERMINE_QUALITY|POOR_QUALITY_DETECTED"
        }
    ]
}
```

---

### 2.8 `update-active-model-version`

Sets the active model version used by inference schedulers.

**Synopsis:**
```bash
aws lookoutequipment update-active-model-version \
    --model-name <value> \
    --model-version <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--model-name` | **Yes** | string | -- | Name of the model |
| `--model-version` | **Yes** | long | -- | Version number to activate (min 1) |

**Output Schema:**
```json
{
    "ModelName": "string",
    "ModelArn": "string",
    "CurrentActiveVersion": "long",
    "PreviousActiveVersion": "long",
    "CurrentActiveVersionArn": "string",
    "PreviousActiveVersionArn": "string"
}
```

---

### 2.9 `import-model-version`

Imports a model version from another AWS account or region.

**Synopsis:**
```bash
aws lookoutequipment import-model-version \
    --source-model-version-arn <value> \
    --dataset-name <value> \
    [--model-name <value>] \
    [--labels-input-configuration <value>] \
    [--client-token <value>] \
    [--role-arn <value>] \
    [--server-side-kms-key-id <value>] \
    [--tags <value>] \
    [--inference-data-import-strategy <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-model-version-arn` | **Yes** | string | -- | ARN of the source model version |
| `--dataset-name` | **Yes** | string | -- | Dataset name for the imported model |
| `--model-name` | No | string | Source name | Name for the imported model |
| `--labels-input-configuration` | No | structure | None | Label data configuration |
| `--client-token` | No | string | Auto | Idempotency token |
| `--role-arn` | No | string | None | IAM role for data access |
| `--server-side-kms-key-id` | No | string | None | KMS key for encryption |
| `--tags` | No | list | None | Tags (max 200) |
| `--inference-data-import-strategy` | No | string | None | `NO_IMPORT`, `ADD_WHEN_EMPTY`, `OVERWRITE` |

**Output Schema:**
```json
{
    "ModelName": "string",
    "ModelArn": "string",
    "ModelVersionArn": "string",
    "ModelVersion": "long",
    "Status": "IN_PROGRESS|SUCCESS|FAILED|IMPORT_IN_PROGRESS|CANCELED"
}
```
