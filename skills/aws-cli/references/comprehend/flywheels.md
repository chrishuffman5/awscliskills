# Flywheels

### 9.1 `create-flywheel`

Creates a flywheel for automated retraining of custom models.

**Synopsis:**
```bash
aws comprehend create-flywheel \
    --flywheel-name <value> \
    --data-access-role-arn <value> \
    --data-lake-s3-uri <value> \
    [--active-model-arn <value>] \
    [--task-config <value>] \
    [--model-type <value>] \
    [--data-security-config <value>] \
    [--client-request-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--flywheel-name` | **Yes** | string | -- | Name for the flywheel (max 63 chars, alphanumeric with hyphens) |
| `--data-access-role-arn` | **Yes** | string | -- | IAM role ARN granting Comprehend permissions to access flywheel data |
| `--data-lake-s3-uri` | **Yes** | string | -- | S3 location for the data lake |
| `--active-model-arn` | No | string | -- | ARN of existing model to associate. Do not use with `--task-config` or `--model-type` |
| `--task-config` | No | structure | -- | Model configuration for new models (see structure below) |
| `--model-type` | No | string | -- | Model type: `DOCUMENT_CLASSIFIER` or `ENTITY_RECOGNIZER` |
| `--data-security-config` | No | structure | -- | Data security/encryption config (see structure below) |
| `--client-request-token` | No | string | auto | Idempotency token (1-64 chars) |
| `--tags` | No | list | -- | Tags. Shorthand: `Key=string,Value=string ...` |

**Task Config Structure:**
```json
{
    "LanguageCode": "en|es|fr|de|it|pt|ar|hi|ja|ko|zh|zh-TW",
    "DocumentClassificationConfig": {
        "Mode": "MULTI_CLASS|MULTI_LABEL",
        "Labels": ["string"]
    },
    "EntityRecognitionConfig": {
        "EntityTypes": [
            {
                "Type": "string"
            }
        ]
    }
}
```

**Data Security Config Structure:**
```json
{
    "ModelKmsKeyId": "string",
    "VolumeKmsKeyId": "string",
    "DataLakeKmsKeyId": "string",
    "VpcConfig": {
        "SecurityGroupIds": ["string"],
        "Subnets": ["string"]
    }
}
```

**Output Schema:**
```json
{
    "FlywheelArn": "string",
    "ActiveModelArn": "string"
}
```

---

### 9.2 `delete-flywheel`

Deletes a flywheel. This does not delete the data lake or associated models.

**Synopsis:**
```bash
aws comprehend delete-flywheel \
    --flywheel-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--flywheel-arn` | **Yes** | string | -- | ARN of the flywheel to delete |

**Output:** None (HTTP 200 on success)

---

### 9.3 `describe-flywheel`

Gets the properties associated with a flywheel.

**Synopsis:**
```bash
aws comprehend describe-flywheel \
    --flywheel-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--flywheel-arn` | **Yes** | string | -- | ARN of the flywheel |

**Output Schema:**
```json
{
    "FlywheelProperties": {
        "FlywheelArn": "string",
        "ActiveModelArn": "string",
        "DataAccessRoleArn": "string",
        "TaskConfig": {},
        "DataLakeS3Uri": "string",
        "DataSecurityConfig": {},
        "Status": "CREATING|ACTIVE|UPDATING|DELETING|FAILED",
        "ModelType": "DOCUMENT_CLASSIFIER|ENTITY_RECOGNIZER",
        "Message": "string",
        "CreationTime": "timestamp",
        "LastModifiedTime": "timestamp",
        "LatestFlywheelIteration": "string"
    }
}
```

---

### 9.4 `list-flywheels`

Gets a list of flywheels. **Paginated operation.**

**Synopsis:**
```bash
aws comprehend list-flywheels \
    [--filter <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filter` | No | structure | -- | Filter by Status, CreationTimeAfter, CreationTimeBefore |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "FlywheelSummaryList": [
        {
            "FlywheelArn": "string",
            "ActiveModelArn": "string",
            "DataLakeS3Uri": "string",
            "Status": "CREATING|ACTIVE|UPDATING|DELETING|FAILED",
            "ModelType": "DOCUMENT_CLASSIFIER|ENTITY_RECOGNIZER",
            "Message": "string",
            "CreationTime": "timestamp",
            "LastModifiedTime": "timestamp",
            "LatestFlywheelIteration": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 9.5 `update-flywheel`

Updates the configuration of a flywheel, including the active model version.

**Synopsis:**
```bash
aws comprehend update-flywheel \
    --flywheel-arn <value> \
    [--active-model-arn <value>] \
    [--data-access-role-arn <value>] \
    [--data-security-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--flywheel-arn` | **Yes** | string | -- | ARN of the flywheel to update |
| `--active-model-arn` | No | string | -- | ARN of the new active model version |
| `--data-access-role-arn` | No | string | -- | Updated IAM role ARN |
| `--data-security-config` | No | structure | -- | Updated data security configuration |

**Output Schema:**
```json
{
    "FlywheelProperties": {
        "FlywheelArn": "string",
        "ActiveModelArn": "string",
        "DataAccessRoleArn": "string",
        "Status": "string",
        "ModelType": "string"
    }
}
```

---

### 9.6 `start-flywheel-iteration`

Starts a flywheel iteration to retrain a model using new data.

**Synopsis:**
```bash
aws comprehend start-flywheel-iteration \
    --flywheel-arn <value> \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--flywheel-arn` | **Yes** | string | -- | ARN of the flywheel |
| `--client-request-token` | No | string | auto | Idempotency token (1-64 chars) |

**Output Schema:**
```json
{
    "FlywheelArn": "string",
    "FlywheelIterationId": "string"
}
```

---

### 9.7 `describe-flywheel-iteration`

Gets the properties of a flywheel iteration, including training metrics.

**Synopsis:**
```bash
aws comprehend describe-flywheel-iteration \
    --flywheel-arn <value> \
    --flywheel-iteration-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--flywheel-arn` | **Yes** | string | -- | ARN of the flywheel |
| `--flywheel-iteration-id` | **Yes** | string | -- | Identifier of the flywheel iteration |

**Output Schema:**
```json
{
    "FlywheelIterationProperties": {
        "FlywheelArn": "string",
        "FlywheelIterationId": "string",
        "CreationTime": "timestamp",
        "EndTime": "timestamp",
        "Status": "TRAINING|EVALUATING|COMPLETED|FAILED|STOP_REQUESTED|STOPPED",
        "Message": "string",
        "EvaluatedModelArn": "string",
        "EvaluatedModelMetrics": {
            "AverageF1Score": "double",
            "AveragePrecision": "double",
            "AverageRecall": "double",
            "AverageAccuracy": "double"
        },
        "TrainedModelArn": "string",
        "TrainedModelMetrics": {
            "AverageF1Score": "double",
            "AveragePrecision": "double",
            "AverageRecall": "double",
            "AverageAccuracy": "double"
        },
        "EvaluationManifestS3Prefix": "string"
    }
}
```

---

### 9.8 `list-flywheel-iteration-history`

Gets the history of flywheel iterations for a flywheel. **Paginated operation.**

**Synopsis:**
```bash
aws comprehend list-flywheel-iteration-history \
    --flywheel-arn <value> \
    [--filter <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--flywheel-arn` | **Yes** | string | -- | ARN of the flywheel |
| `--filter` | No | structure | -- | Filter by CreationTimeAfter, CreationTimeBefore |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "FlywheelIterationPropertiesList": [
        {
            "FlywheelArn": "string",
            "FlywheelIterationId": "string",
            "CreationTime": "timestamp",
            "EndTime": "timestamp",
            "Status": "string",
            "Message": "string",
            "EvaluatedModelArn": "string",
            "TrainedModelArn": "string"
        }
    ],
    "NextToken": "string"
}
```
