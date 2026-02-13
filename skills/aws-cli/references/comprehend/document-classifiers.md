# Document Classifiers

### 6.1 `create-document-classifier`

Creates a document classifier to categorize documents.

**Synopsis:**
```bash
aws comprehend create-document-classifier \
    --document-classifier-name <value> \
    --data-access-role-arn <value> \
    --input-data-config <value> \
    --language-code <value> \
    [--version-name <value>] \
    [--tags <value>] \
    [--output-data-config <value>] \
    [--client-request-token <value>] \
    [--volume-kms-key-id <value>] \
    [--vpc-config <value>] \
    [--mode <value>] \
    [--model-kms-key-id <value>] \
    [--model-policy <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--document-classifier-name` | **Yes** | string | -- | Name of the classifier (max 63 chars, alphanumeric with hyphens) |
| `--data-access-role-arn` | **Yes** | string | -- | IAM role ARN granting Comprehend read access to input data |
| `--input-data-config` | **Yes** | structure | -- | Training data config (see structure below) |
| `--language-code` | **Yes** | string | -- | Language code: `en`, `es`, `fr`, `de`, `it`, `pt`, `ar`, `hi`, `ja`, `ko`, `zh`, `zh-TW` |
| `--version-name` | No | string | -- | Version name (max 63 chars) |
| `--tags` | No | list | -- | Tags. Shorthand: `Key=string,Value=string ...` |
| `--output-data-config` | No | structure | -- | Output config. Shorthand: `S3Uri=string,KmsKeyId=string` |
| `--client-request-token` | No | string | auto | Idempotency token (1-64 chars) |
| `--volume-kms-key-id` | No | string | -- | KMS key for encrypting storage volume |
| `--vpc-config` | No | structure | -- | VPC configuration |
| `--mode` | No | string | `MULTI_CLASS` | Training mode: `MULTI_CLASS` or `MULTI_LABEL` |
| `--model-kms-key-id` | No | string | -- | KMS key for encrypting trained models |
| `--model-policy` | No | string | -- | Resource-based policy JSON (max 20000 chars) |

**Input Data Config Structure:**
```json
{
    "DataFormat": "COMPREHEND_CSV|AUGMENTED_MANIFEST",
    "S3Uri": "string",
    "TestS3Uri": "string",
    "LabelDelimiter": "string",
    "AugmentedManifests": [
        {
            "S3Uri": "string",
            "Split": "TRAIN|TEST",
            "AttributeNames": ["string"],
            "AnnotationDataS3Uri": "string",
            "SourceDocumentsS3Uri": "string",
            "DocumentType": "PLAIN_TEXT_DOCUMENT|SEMI_STRUCTURED_DOCUMENT"
        }
    ],
    "DocumentType": "PLAIN_TEXT_DOCUMENT|SEMI_STRUCTURED_DOCUMENT",
    "Documents": {
        "S3Uri": "string",
        "TestS3Uri": "string"
    },
    "DocumentReaderConfig": {
        "DocumentReadAction": "TEXTRACT_DETECT_DOCUMENT_TEXT|TEXTRACT_ANALYZE_DOCUMENT",
        "DocumentReadMode": "SERVICE_DEFAULT|FORCE_DOCUMENT_READ_ACTION",
        "FeatureTypes": ["TABLES", "FORMS"]
    }
}
```

**Output Schema:**
```json
{
    "DocumentClassifierArn": "string"
}
```

---

### 6.2 `delete-document-classifier`

Deletes a previously created document classifier. Only classifiers in `TRAINED`, `TRAINED_WITH_WARNING`, `STOPPED`, or `IN_ERROR` state can be deleted.

**Synopsis:**
```bash
aws comprehend delete-document-classifier \
    --document-classifier-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--document-classifier-arn` | **Yes** | string | -- | ARN of the document classifier to delete |

**Output:** None (HTTP 200 on success)

---

### 6.3 `describe-document-classifier`

Gets properties of a document classifier, including training metrics.

**Synopsis:**
```bash
aws comprehend describe-document-classifier \
    --document-classifier-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--document-classifier-arn` | **Yes** | string | -- | ARN of the document classifier |

**Output Schema:**
```json
{
    "DocumentClassifierProperties": {
        "DocumentClassifierArn": "string",
        "LanguageCode": "string",
        "Status": "SUBMITTED|TRAINING|DELETING|STOP_REQUESTED|STOPPED|IN_ERROR|TRAINED|TRAINED_WITH_WARNING",
        "Message": "string",
        "SubmitTime": "timestamp",
        "EndTime": "timestamp",
        "TrainingStartTime": "timestamp",
        "TrainingEndTime": "timestamp",
        "InputDataConfig": {},
        "OutputDataConfig": {
            "S3Uri": "string",
            "KmsKeyId": "string",
            "FlywheelStatsS3Prefix": "string"
        },
        "ClassifierMetadata": {
            "NumberOfLabels": "integer",
            "NumberOfTrainedDocuments": "integer",
            "NumberOfTestDocuments": "integer",
            "EvaluationMetrics": {
                "Accuracy": "double",
                "Precision": "double",
                "Recall": "double",
                "F1Score": "double",
                "MicroPrecision": "double",
                "MicroRecall": "double",
                "MicroF1Score": "double",
                "HammingLoss": "double"
            }
        },
        "DataAccessRoleArn": "string",
        "VolumeKmsKeyId": "string",
        "VpcConfig": {},
        "Mode": "MULTI_CLASS|MULTI_LABEL",
        "ModelKmsKeyId": "string",
        "VersionName": "string",
        "SourceModelArn": "string",
        "FlywheelArn": "string"
    }
}
```

---

### 6.4 `list-document-classifiers`

Gets a list of document classifiers. **Paginated operation.**

**Synopsis:**
```bash
aws comprehend list-document-classifiers \
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
| `--filter` | No | structure | -- | Filter by Status, DocumentClassifierName, SubmitTimeBefore, SubmitTimeAfter |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "DocumentClassifierPropertiesList": [
        {
            "DocumentClassifierArn": "string",
            "LanguageCode": "string",
            "Status": "string",
            "SubmitTime": "timestamp",
            "EndTime": "timestamp",
            "Mode": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 6.5 `list-document-classifier-summaries`

Gets a list of summaries of document classifiers. **Paginated operation.**

**Synopsis:**
```bash
aws comprehend list-document-classifier-summaries \
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
    "DocumentClassifierSummariesList": [
        {
            "DocumentClassifierName": "string",
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

### 6.6 `stop-training-document-classifier`

Stops a document classifier training job while in progress.

**Synopsis:**
```bash
aws comprehend stop-training-document-classifier \
    --document-classifier-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--document-classifier-arn` | **Yes** | string | -- | ARN of the document classifier being trained |

**Output:** None (HTTP 200 on success)
