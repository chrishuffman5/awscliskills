# Entity Recognizers

### 7.1 `create-entity-recognizer`

Creates a custom entity recognizer for detecting domain-specific entities.

**Synopsis:**
```bash
aws comprehend create-entity-recognizer \
    --recognizer-name <value> \
    --data-access-role-arn <value> \
    --input-data-config <value> \
    --language-code <value> \
    [--version-name <value>] \
    [--tags <value>] \
    [--client-request-token <value>] \
    [--volume-kms-key-id <value>] \
    [--vpc-config <value>] \
    [--model-kms-key-id <value>] \
    [--model-policy <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--recognizer-name` | **Yes** | string | -- | Name for the recognizer (max 63 chars, alphanumeric with hyphens) |
| `--data-access-role-arn` | **Yes** | string | -- | IAM role ARN granting Comprehend read access to input data |
| `--input-data-config` | **Yes** | structure | -- | Training data config (see structure below) |
| `--language-code` | **Yes** | string | -- | Language code: `en`, `es`, `fr`, `de`, `it`, `pt`, `ar`, `hi`, `ja`, `ko`, `zh`, `zh-TW` |
| `--version-name` | No | string | -- | Version name (max 63 chars) |
| `--tags` | No | list | -- | Tags. Shorthand: `Key=string,Value=string ...` |
| `--client-request-token` | No | string | auto | Idempotency token (1-64 chars) |
| `--volume-kms-key-id` | No | string | -- | KMS key for encrypting storage volume |
| `--vpc-config` | No | structure | -- | VPC configuration |
| `--model-kms-key-id` | No | string | -- | KMS key for encrypting trained models |
| `--model-policy` | No | string | -- | Resource-based policy JSON (max 20000 chars) |

**Input Data Config Structure:**
```json
{
    "DataFormat": "COMPREHEND_CSV|AUGMENTED_MANIFEST",
    "EntityTypes": [
        {
            "Type": "string"
        }
    ],
    "Documents": {
        "S3Uri": "string",
        "TestS3Uri": "string",
        "InputFormat": "ONE_DOC_PER_FILE|ONE_DOC_PER_LINE"
    },
    "Annotations": {
        "S3Uri": "string",
        "TestS3Uri": "string"
    },
    "EntityList": {
        "S3Uri": "string"
    },
    "AugmentedManifests": [
        {
            "S3Uri": "string",
            "Split": "TRAIN|TEST",
            "AttributeNames": ["string"],
            "AnnotationDataS3Uri": "string",
            "SourceDocumentsS3Uri": "string",
            "DocumentType": "PLAIN_TEXT_DOCUMENT|SEMI_STRUCTURED_DOCUMENT"
        }
    ]
}
```

**Output Schema:**
```json
{
    "EntityRecognizerArn": "string"
}
```

---

### 7.2 `delete-entity-recognizer`

Deletes an entity recognizer. Only recognizers in `TRAINED`, `TRAINED_WITH_WARNING`, `STOPPED`, or `IN_ERROR` state can be deleted.

**Synopsis:**
```bash
aws comprehend delete-entity-recognizer \
    --entity-recognizer-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--entity-recognizer-arn` | **Yes** | string | -- | ARN of the entity recognizer to delete |

**Output:** None (HTTP 200 on success)

---

### 7.3 `describe-entity-recognizer`

Gets the properties of an entity recognizer, including training metrics.

**Synopsis:**
```bash
aws comprehend describe-entity-recognizer \
    --entity-recognizer-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--entity-recognizer-arn` | **Yes** | string | -- | ARN of the entity recognizer |

**Output Schema:**
```json
{
    "EntityRecognizerProperties": {
        "EntityRecognizerArn": "string",
        "LanguageCode": "string",
        "Status": "SUBMITTED|TRAINING|DELETING|STOP_REQUESTED|STOPPED|IN_ERROR|TRAINED|TRAINED_WITH_WARNING",
        "Message": "string",
        "SubmitTime": "timestamp",
        "EndTime": "timestamp",
        "TrainingStartTime": "timestamp",
        "TrainingEndTime": "timestamp",
        "InputDataConfig": {},
        "RecognizerMetadata": {
            "NumberOfTrainedDocuments": "integer",
            "NumberOfTestDocuments": "integer",
            "EvaluationMetrics": {
                "Precision": "double",
                "Recall": "double",
                "F1Score": "double"
            },
            "EntityTypes": [
                {
                    "Type": "string",
                    "EvaluationMetrics": {
                        "Precision": "double",
                        "Recall": "double",
                        "F1Score": "double"
                    },
                    "NumberOfTrainMentions": "integer"
                }
            ]
        },
        "DataAccessRoleArn": "string",
        "VolumeKmsKeyId": "string",
        "VpcConfig": {},
        "ModelKmsKeyId": "string",
        "VersionName": "string",
        "SourceModelArn": "string",
        "FlywheelArn": "string",
        "OutputDataConfig": {
            "FlywheelStatsS3Prefix": "string"
        }
    }
}
```

---

### 7.4 `list-entity-recognizers`

Gets a list of entity recognizers. **Paginated operation.**

**Synopsis:**
```bash
aws comprehend list-entity-recognizers \
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
| `--filter` | No | structure | -- | Filter by Status, RecognizerName, SubmitTimeBefore, SubmitTimeAfter |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "EntityRecognizerPropertiesList": [
        {
            "EntityRecognizerArn": "string",
            "LanguageCode": "string",
            "Status": "string",
            "SubmitTime": "timestamp",
            "EndTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 7.5 `list-entity-recognizer-summaries`

Gets a list of summaries for entity recognizers. **Paginated operation.**

**Synopsis:**
```bash
aws comprehend list-entity-recognizer-summaries \
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
    "EntityRecognizerSummariesList": [
        {
            "RecognizerName": "string",
            "NumberOfVersions": "integer",
            "LatestVersionCreatedAt": "timestamp",
            "LatestVersionName": "string",
            "LatestVersionStatus": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 7.6 `stop-training-entity-recognizer`

Stops an entity recognizer training job while in progress.

**Synopsis:**
```bash
aws comprehend stop-training-entity-recognizer \
    --entity-recognizer-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--entity-recognizer-arn` | **Yes** | string | -- | ARN of the entity recognizer being trained |

**Output:** None (HTTP 200 on success)
