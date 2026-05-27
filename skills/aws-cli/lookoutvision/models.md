# Models

### 2.1 `create-model`

Creates a new model version within a project. This is an asynchronous operation where Lookout for Vision trains, tests, and evaluates the model. If the project has a single dataset, Lookout for Vision internally splits it into training and test datasets.

**Synopsis:**
```bash
aws lookoutvision create-model \
    --project-name <value> \
    --output-config <value> \
    [--description <value>] \
    [--client-token <value>] \
    [--kms-key-id <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project-name` | **Yes** | string | -- | Project to create the model in |
| `--output-config` | **Yes** | structure | -- | S3 location for training output |
| `--description` | No | string | None | Model version description |
| `--client-token` | No | string | Auto | Idempotency token (active for 8 hours) |
| `--kms-key-id` | No | string | None | KMS key for encrypting training and test images |
| `--tags` | No | list | None | Tags to attach to the model |

**OutputConfig Structure:**
```json
{
    "S3Location": {
        "Bucket": "string",
        "Prefix": "string"
    }
}
```

**Output Schema:**
```json
{
    "ModelMetadata": {
        "CreationTimestamp": "timestamp",
        "ModelVersion": "string",
        "ModelArn": "string",
        "Description": "string",
        "Status": "TRAINING|TRAINED|TRAINING_FAILED|STARTING_HOSTING|HOSTED|HOSTING_FAILED|STOPPING_HOSTING|SYSTEM_UPDATING|DELETING",
        "StatusMessage": "string",
        "Performance": {
            "F1Score": "float",
            "Recall": "float",
            "Precision": "float"
        }
    }
}
```

---

### 2.2 `delete-model`

Deletes a model version from a project. The model must be stopped before it can be deleted. Deletion may take several seconds to complete.

**Synopsis:**
```bash
aws lookoutvision delete-model \
    --project-name <value> \
    --model-version <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project-name` | **Yes** | string | -- | Project containing the model |
| `--model-version` | **Yes** | string | -- | Version of the model to delete |
| `--client-token` | No | string | Auto | Idempotency token (active for 8 hours) |

**Output Schema:**
```json
{
    "ModelArn": "string"
}
```

---

### 2.3 `describe-model`

Describes a model version including training status, performance metrics, and configuration.

**Synopsis:**
```bash
aws lookoutvision describe-model \
    --project-name <value> \
    --model-version <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project-name` | **Yes** | string | -- | Project containing the model |
| `--model-version` | **Yes** | string | -- | Version of the model to describe |

**Output Schema:**
```json
{
    "ModelDescription": {
        "ModelVersion": "string",
        "ModelArn": "string",
        "CreationTimestamp": "timestamp",
        "Description": "string",
        "Status": "TRAINING|TRAINED|TRAINING_FAILED|STARTING_HOSTING|HOSTED|HOSTING_FAILED|STOPPING_HOSTING|SYSTEM_UPDATING|DELETING",
        "StatusMessage": "string",
        "Performance": {
            "F1Score": "float",
            "Recall": "float",
            "Precision": "float"
        },
        "OutputConfig": {
            "S3Location": {
                "Bucket": "string",
                "Prefix": "string"
            }
        },
        "EvaluationManifest": {
            "Bucket": "string",
            "Key": "string"
        },
        "EvaluationResult": {
            "Bucket": "string",
            "Key": "string"
        },
        "EvaluationEndTimestamp": "timestamp",
        "KmsKeyId": "string",
        "MinInferenceUnits": "integer",
        "MaxInferenceUnits": "integer"
    }
}
```

---

### 2.4 `list-models`

Lists model versions in a project. **Paginated operation.**

**Synopsis:**
```bash
aws lookoutvision list-models \
    --project-name <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project-name` | **Yes** | string | -- | Project containing the models |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Maximum total items to return |

**Output Schema:**
```json
{
    "Models": [
        {
            "CreationTimestamp": "timestamp",
            "ModelVersion": "string",
            "ModelArn": "string",
            "Description": "string",
            "Status": "TRAINING|TRAINED|TRAINING_FAILED|STARTING_HOSTING|HOSTED|HOSTING_FAILED|STOPPING_HOSTING|SYSTEM_UPDATING|DELETING",
            "StatusMessage": "string",
            "Performance": {
                "F1Score": "float",
                "Recall": "float",
                "Precision": "float"
            }
        }
    ],
    "NextToken": "string"
}
```

---

### 2.5 `start-model`

Starts hosting a model version for inference. You are charged for the time the model is running. Use `stop-model` to stop hosting. The model is ready when its status reaches `HOSTED`.

**Synopsis:**
```bash
aws lookoutvision start-model \
    --project-name <value> \
    --model-version <value> \
    --min-inference-units <value> \
    [--client-token <value>] \
    [--max-inference-units <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project-name` | **Yes** | string | -- | Project containing the model |
| `--model-version` | **Yes** | string | -- | Version of the model to start |
| `--min-inference-units` | **Yes** | integer | -- | Minimum inference units (1 unit = 1 hour of processing) |
| `--client-token` | No | string | Auto | Idempotency token (active for 8 hours) |
| `--max-inference-units` | No | integer | None | Maximum inference units for auto-scaling (omit to disable auto-scaling) |

**Output Schema:**
```json
{
    "Status": "STARTING_HOSTING|HOSTED"
}
```

---

### 2.6 `stop-model`

Stops a running model version. The model status becomes `TRAINED` after stopping. Use `describe-model` to monitor the stopping process.

**Synopsis:**
```bash
aws lookoutvision stop-model \
    --project-name <value> \
    --model-version <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project-name` | **Yes** | string | -- | Project containing the model |
| `--model-version` | **Yes** | string | -- | Version of the model to stop |
| `--client-token` | No | string | Auto | Idempotency token (active for 8 hours) |

**Output Schema:**
```json
{
    "Status": "STOPPING_HOSTING|TRAINED"
}
```

---

### 2.7 `detect-anomalies`

Detects anomalies in an image using a hosted model. Returns a boolean prediction and confidence score. For segmentation models, also returns per-pixel anomaly data and an anomaly mask. The model must be started with `start-model` before calling this command.

**Synopsis:**
```bash
aws lookoutvision detect-anomalies \
    --project-name <value> \
    --model-version <value> \
    --body <value> \
    --content-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project-name` | **Yes** | string | -- | Project containing the model |
| `--model-version` | **Yes** | string | -- | Version of the model to use |
| `--body` | **Yes** | streaming blob | -- | Image file path (no `file://` prefix) |
| `--content-type` | **Yes** | string | -- | Image MIME type: `image/png` or `image/jpeg` |

**Output Schema:**
```json
{
    "DetectAnomalyResult": {
        "Source": {
            "Type": "string"
        },
        "IsAnomalous": "boolean",
        "Confidence": "float",
        "Anomalies": [
            {
                "Name": "string",
                "PixelAnomaly": {
                    "TotalPercentageArea": "float",
                    "Color": "string"
                }
            }
        ],
        "AnomalyMask": "blob"
    }
}
```
