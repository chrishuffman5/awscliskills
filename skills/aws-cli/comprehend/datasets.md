# Datasets

### 10.1 `create-dataset`

Creates a dataset for a flywheel. Used to provide training or test data for model retraining.

**Synopsis:**
```bash
aws comprehend create-dataset \
    --flywheel-arn <value> \
    --dataset-name <value> \
    --input-data-config <value> \
    [--dataset-type <value>] \
    [--description <value>] \
    [--client-request-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--flywheel-arn` | **Yes** | string | -- | ARN of the flywheel to receive the data |
| `--dataset-name` | **Yes** | string | -- | Name of the dataset (max 63 chars, alphanumeric with hyphens) |
| `--input-data-config` | **Yes** | structure | -- | Input data configuration (see structure below) |
| `--dataset-type` | No | string | -- | Type of dataset: `TRAIN` or `TEST` |
| `--description` | No | string | -- | Description (max 2048 chars) |
| `--client-request-token` | No | string | auto | Idempotency token (1-64 chars) |
| `--tags` | No | list | -- | Tags. Shorthand: `Key=string,Value=string ...` |

**Input Data Config Structure:**
```json
{
    "AugmentedManifests": [
        {
            "AttributeNames": ["string"],
            "S3Uri": "string",
            "AnnotationDataS3Uri": "string",
            "SourceDocumentsS3Uri": "string",
            "DocumentType": "PLAIN_TEXT_DOCUMENT|SEMI_STRUCTURED_DOCUMENT"
        }
    ],
    "DataFormat": "COMPREHEND_CSV|AUGMENTED_MANIFEST",
    "DocumentClassifierInputDataConfig": {
        "S3Uri": "string",
        "LabelDelimiter": "string"
    },
    "EntityRecognizerInputDataConfig": {
        "Annotations": {
            "S3Uri": "string"
        },
        "Documents": {
            "S3Uri": "string",
            "InputFormat": "ONE_DOC_PER_FILE|ONE_DOC_PER_LINE"
        },
        "EntityList": {
            "S3Uri": "string"
        }
    }
}
```

**Output Schema:**
```json
{
    "DatasetArn": "string"
}
```

---

### 10.2 `describe-dataset`

Gets the properties of a dataset.

**Synopsis:**
```bash
aws comprehend describe-dataset \
    --dataset-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--dataset-arn` | **Yes** | string | -- | ARN of the dataset |

**Output Schema:**
```json
{
    "DatasetProperties": {
        "DatasetArn": "string",
        "DatasetName": "string",
        "DatasetType": "TRAIN|TEST",
        "DatasetS3Uri": "string",
        "Description": "string",
        "Status": "CREATING|COMPLETED|FAILED",
        "Message": "string",
        "NumberOfDocuments": "long",
        "CreationTime": "timestamp",
        "EndTime": "timestamp"
    }
}
```

---

### 10.3 `list-datasets`

Gets a list of datasets for a flywheel. **Paginated operation.**

**Synopsis:**
```bash
aws comprehend list-datasets \
    [--flywheel-arn <value>] \
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
| `--flywheel-arn` | No | string | -- | ARN of the flywheel |
| `--filter` | No | structure | -- | Filter by Status, DatasetType, CreationTimeAfter, CreationTimeBefore |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "DatasetPropertiesList": [
        {
            "DatasetArn": "string",
            "DatasetName": "string",
            "DatasetType": "TRAIN|TEST",
            "DatasetS3Uri": "string",
            "Status": "CREATING|COMPLETED|FAILED",
            "NumberOfDocuments": "long",
            "CreationTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```
