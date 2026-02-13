# Custom Models

### `create-model-customization-job`

Creates a fine-tuning, continued pre-training, or distillation job to customize a base model. You provide training data and the resulting custom model is stored in your account.

**Synopsis:**
```bash
aws bedrock create-model-customization-job \
    --job-name <value> \
    --custom-model-name <value> \
    --role-arn <value> \
    --base-model-identifier <value> \
    --training-data-config <value> \
    --output-data-config <value> \
    [--client-request-token <value>] \
    [--customization-type <value>] \
    [--custom-model-kms-key-id <value>] \
    [--job-tags <value>] \
    [--custom-model-tags <value>] \
    [--validation-data-config <value>] \
    [--hyper-parameters <value>] \
    [--vpc-config <value>] \
    [--customization-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-name` | **Yes** | string | -- | Job name (1-63 chars). Pattern: `[a-zA-Z0-9](-*[a-zA-Z0-9\+\-\.])*` |
| `--custom-model-name` | **Yes** | string | -- | Name for the resulting custom model (1-63 chars) |
| `--role-arn` | **Yes** | string | -- | IAM role ARN for Amazon Bedrock to assume |
| `--base-model-identifier` | **Yes** | string | -- | Base model ID or ARN to customize (1-2048 chars) |
| `--training-data-config` | **Yes** | structure | -- | Training data S3 location. Structure: `s3Uri=string` |
| `--output-data-config` | **Yes** | structure | -- | Output S3 location. Structure: `s3Uri=string` |
| `--client-request-token` | No | string | None | Idempotency token (1-256 chars) |
| `--customization-type` | No | string | None | `FINE_TUNING`, `CONTINUED_PRE_TRAINING`, `DISTILLATION`, `REINFORCEMENT_FINE_TUNING` |
| `--custom-model-kms-key-id` | No | string | None | KMS key for custom model encryption (1-2048 chars) |
| `--job-tags` | No | list | None | Tags for the job (max 200) |
| `--custom-model-tags` | No | list | None | Tags for the resulting model (max 200) |
| `--validation-data-config` | No | structure | None | Validation dataset. Structure: `validators=[{s3Uri=string}]` |
| `--hyper-parameters` | No | map | None | Tuning hyperparameters (key-value pairs) |
| `--vpc-config` | No | structure | None | VPC config: `subnetIds` (1-16), `securityGroupIds` (1-5) |
| `--customization-config` | No | structure | None | Distillation or RFT configuration |

**Training Data Config Structure:**
```json
{
    "s3Uri": "s3://bucket/training-data.jsonl",
    "invocationLogsConfig": {
        "usePromptResponse": true|false,
        "invocationLogSource": {
            "s3Uri": "s3://bucket/logs/"
        },
        "requestMetadataFilters": {
            "equals": {"key": "value"},
            "notEquals": {"key": "value"}
        }
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

### `get-model-customization-job`

Retrieves information about a model customization job.

**Synopsis:**
```bash
aws bedrock get-model-customization-job \
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
    "outputModelName": "string",
    "outputModelArn": "string",
    "clientRequestToken": "string",
    "roleArn": "string",
    "status": "InProgress|Completed|Failed|Stopping|Stopped",
    "failureMessage": "string",
    "creationTime": "timestamp",
    "lastModifiedTime": "timestamp",
    "endTime": "timestamp",
    "baseModelArn": "string",
    "hyperParameters": {"string": "string"},
    "trainingDataConfig": {
        "s3Uri": "string"
    },
    "validationDataConfig": {
        "validators": [{"s3Uri": "string"}]
    },
    "outputDataConfig": {
        "s3Uri": "string"
    },
    "customizationType": "FINE_TUNING|CONTINUED_PRE_TRAINING|DISTILLATION|REINFORCEMENT_FINE_TUNING",
    "outputModelKmsKeyArn": "string",
    "trainingMetrics": {
        "trainingLoss": "float"
    },
    "validationMetrics": [
        {
            "validationLoss": "float"
        }
    ],
    "vpcConfig": {
        "subnetIds": ["string"],
        "securityGroupIds": ["string"]
    }
}
```

---

### `list-model-customization-jobs`

Lists model customization jobs in the account. **Paginated operation.**

**Synopsis:**
```bash
aws bedrock list-model-customization-jobs \
    [--creation-time-after <value>] \
    [--creation-time-before <value>] \
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
| `--creation-time-after` | No | timestamp | None | Filter by creation time (after) |
| `--creation-time-before` | No | timestamp | None | Filter by creation time (before) |
| `--status-equals` | No | string | None | Filter by status: `InProgress`, `Completed`, `Failed`, `Stopping`, `Stopped` |
| `--name-contains` | No | string | None | Filter by job name substring |
| `--sort-by` | No | string | None | Sort field: `CreationTime` |
| `--sort-order` | No | string | None | Sort order: `Ascending`, `Descending` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page (1-100) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "nextToken": "string",
    "modelCustomizationJobSummaries": [
        {
            "jobArn": "string",
            "jobName": "string",
            "status": "InProgress|Completed|Failed|Stopping|Stopped",
            "baseModelArn": "string",
            "customModelArn": "string",
            "customModelName": "string",
            "customizationType": "FINE_TUNING|CONTINUED_PRE_TRAINING|DISTILLATION|REINFORCEMENT_FINE_TUNING",
            "creationTime": "timestamp",
            "lastModifiedTime": "timestamp",
            "endTime": "timestamp"
        }
    ]
}
```

---

### `stop-model-customization-job`

Stops a running model customization job.

**Synopsis:**
```bash
aws bedrock stop-model-customization-job \
    --job-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-identifier` | **Yes** | string | -- | Job name or ARN |

**Output:** None (HTTP 200 on success)

---

### `create-custom-model`

Creates a custom model resource.

**Synopsis:**
```bash
aws bedrock create-custom-model \
    --model-name <value> \
    [--model-source-config <value>] \
    [--model-kms-key-arn <value>] \
    [--tags <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--model-name` | **Yes** | string | -- | Name for the custom model (1-63 chars) |
| `--model-source-config` | No | structure | None | Source configuration for the model |
| `--model-kms-key-arn` | No | string | None | KMS key ARN for encryption |
| `--tags` | No | list | None | Tags for the model (max 200) |
| `--client-request-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "modelArn": "string"
}
```

---

### `get-custom-model`

Gets details about a custom model.

**Synopsis:**
```bash
aws bedrock get-custom-model \
    --model-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--model-identifier` | **Yes** | string | -- | Model name or ARN |

**Output Schema:**
```json
{
    "modelArn": "string",
    "modelName": "string",
    "jobName": "string",
    "jobArn": "string",
    "baseModelArn": "string",
    "customizationType": "FINE_TUNING|CONTINUED_PRE_TRAINING|DISTILLATION|REINFORCEMENT_FINE_TUNING",
    "modelKmsKeyArn": "string",
    "hyperParameters": {"string": "string"},
    "trainingDataConfig": {"s3Uri": "string"},
    "validationDataConfig": {"validators": [{"s3Uri": "string"}]},
    "outputDataConfig": {"s3Uri": "string"},
    "trainingMetrics": {"trainingLoss": "float"},
    "validationMetrics": [{"validationLoss": "float"}],
    "creationTime": "timestamp"
}
```

---

### `list-custom-models`

Lists custom models in the account. **Paginated operation.**

**Synopsis:**
```bash
aws bedrock list-custom-models \
    [--creation-time-before <value>] \
    [--creation-time-after <value>] \
    [--name-contains <value>] \
    [--base-model-arn-equals <value>] \
    [--foundation-model-arn-equals <value>] \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--is-owned | --no-is-owned] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--creation-time-before` | No | timestamp | None | Filter by creation time |
| `--creation-time-after` | No | timestamp | None | Filter by creation time |
| `--name-contains` | No | string | None | Filter by name substring |
| `--base-model-arn-equals` | No | string | None | Filter by base model ARN |
| `--foundation-model-arn-equals` | No | string | None | Filter by foundation model ARN |
| `--sort-by` | No | string | None | Sort field: `CreationTime` |
| `--sort-order` | No | string | None | `Ascending`, `Descending` |
| `--is-owned` | No | boolean | None | Filter to owned models only |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "nextToken": "string",
    "modelSummaries": [
        {
            "modelArn": "string",
            "modelName": "string",
            "creationTime": "timestamp",
            "baseModelArn": "string",
            "baseModelName": "string",
            "customizationType": "FINE_TUNING|CONTINUED_PRE_TRAINING|DISTILLATION|REINFORCEMENT_FINE_TUNING",
            "ownerAccountId": "string"
        }
    ]
}
```

---

### `delete-custom-model`

Deletes a custom model.

**Synopsis:**
```bash
aws bedrock delete-custom-model \
    --model-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--model-identifier` | **Yes** | string | -- | Model name or ARN |

**Output:** None (HTTP 200 on success)

---

### `create-custom-model-deployment`

Creates a deployment for a custom model.

**Synopsis:**
```bash
aws bedrock create-custom-model-deployment \
    --deployment-name <value> \
    --model-id <value> \
    [--tags <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--deployment-name` | **Yes** | string | -- | Name for the deployment |
| `--model-id` | **Yes** | string | -- | The custom model ID or ARN to deploy |
| `--tags` | No | list | None | Tags for the deployment (max 200) |
| `--client-request-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "customModelDeploymentArn": "string"
}
```

---

### `get-custom-model-deployment`

Gets details of a custom model deployment.

**Synopsis:**
```bash
aws bedrock get-custom-model-deployment \
    --custom-model-deployment-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--custom-model-deployment-identifier` | **Yes** | string | -- | Deployment name or ARN |

**Output Schema:**
```json
{
    "customModelDeploymentArn": "string",
    "modelId": "string",
    "deploymentName": "string",
    "status": "CREATING|ACTIVE|FAILED|DELETING",
    "failureMessage": "string",
    "createdAt": "timestamp",
    "lastModifiedAt": "timestamp"
}
```

---

### `list-custom-model-deployments`

Lists custom model deployments. **Paginated operation.**

**Synopsis:**
```bash
aws bedrock list-custom-model-deployments \
    [--creation-time-before <value>] \
    [--creation-time-after <value>] \
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
| `--creation-time-before` | No | timestamp | None | Filter by creation time |
| `--creation-time-after` | No | timestamp | None | Filter by creation time |
| `--name-contains` | No | string | None | Filter by name substring |
| `--sort-by` | No | string | None | Sort field: `CreationTime` |
| `--sort-order` | No | string | None | `Ascending`, `Descending` |

**Output Schema:**
```json
{
    "nextToken": "string",
    "customModelDeploymentSummaries": [
        {
            "customModelDeploymentArn": "string",
            "deploymentName": "string",
            "modelId": "string",
            "status": "CREATING|ACTIVE|FAILED|DELETING",
            "createdAt": "timestamp",
            "lastModifiedAt": "timestamp"
        }
    ]
}
```

---

### `delete-custom-model-deployment`

Deletes a custom model deployment.

**Synopsis:**
```bash
aws bedrock delete-custom-model-deployment \
    --custom-model-deployment-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--custom-model-deployment-identifier` | **Yes** | string | -- | Deployment name or ARN |

**Output:** None (HTTP 200 on success)
