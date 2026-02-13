# Datasets

### 9.1 `create-dataset`

Creates a dataset for a Custom Labels project.

**Synopsis:**
```bash
aws rekognition create-dataset \
    --dataset-source <value> \
    --dataset-type <value> \
    --project-arn <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--dataset-source` | **Yes** | structure | -- | Source of dataset (S3 manifest, existing dataset ARN) |
| `--dataset-type` | **Yes** | string | -- | Type: `TRAIN` or `TEST` |
| `--project-arn` | **Yes** | string | -- | ARN of the project |
| `--tags` | No | map | -- | Key-value tags |

**Output Schema:**
```json
{
    "DatasetArn": "string"
}
```

---

### 9.2 `delete-dataset`

Deletes a dataset. The project must not have a running model.

**Synopsis:**
```bash
aws rekognition delete-dataset \
    --dataset-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--dataset-arn` | **Yes** | string | -- | ARN of the dataset to delete |

**Output:** None (HTTP 200 on success)

---

### 9.3 `describe-dataset`

Gets information about a dataset.

**Synopsis:**
```bash
aws rekognition describe-dataset \
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
    "DatasetDescription": {
        "CreationTimestamp": "timestamp",
        "LastUpdatedTimestamp": "timestamp",
        "Status": "CREATE_IN_PROGRESS|CREATE_COMPLETE|CREATE_FAILED|UPDATE_IN_PROGRESS|UPDATE_COMPLETE|UPDATE_FAILED_ROLLBACK_IN_PROGRESS|UPDATE_FAILED_ROLLBACK_COMPLETE|DELETE_IN_PROGRESS",
        "StatusMessage": "string",
        "StatusMessageCode": "SUCCESS|SERVICE_ERROR|CLIENT_ERROR",
        "DatasetStats": {
            "LabeledEntries": "integer",
            "TotalEntries": "integer",
            "TotalLabels": "integer",
            "ErrorEntries": "integer"
        }
    }
}
```

---

### 9.4 `list-dataset-entries`

Lists dataset entries (images and labels). **Paginated operation.**

**Synopsis:**
```bash
aws rekognition list-dataset-entries \
    --dataset-arn <value> \
    [--contains-labels <value>] \
    [--labeled | --no-labeled] \
    [--source-ref-contains <value>] \
    [--has-errors | --no-has-errors] \
    [--cli-input-json | --cli-input-yaml] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--dataset-arn` | **Yes** | string | -- | ARN of the dataset |
| `--contains-labels` | No | list(string) | -- | Filter by label names |
| `--labeled` / `--no-labeled` | No | boolean | -- | Filter labeled/unlabeled entries |
| `--source-ref-contains` | No | string | -- | Filter by source reference |
| `--has-errors` / `--no-has-errors` | No | boolean | -- | Filter by error status |

**Output Schema:**
```json
{
    "DatasetEntries": ["string"],
    "NextToken": "string"
}
```

---

### 9.5 `list-dataset-labels`

Lists the labels in a dataset. **Paginated operation.**

**Synopsis:**
```bash
aws rekognition list-dataset-labels \
    --dataset-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--dataset-arn` | **Yes** | string | -- | ARN of the dataset |

**Output Schema:**
```json
{
    "DatasetLabelDescriptions": [
        {
            "LabelName": "string",
            "LabelStats": {
                "EntryCount": "integer",
                "BoundingBoxCount": "integer"
            }
        }
    ],
    "NextToken": "string"
}
```

---

### 9.6 `update-dataset-entries`

Adds or updates entries in a dataset.

**Synopsis:**
```bash
aws rekognition update-dataset-entries \
    --dataset-arn <value> \
    --changes <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--dataset-arn` | **Yes** | string | -- | ARN of the dataset |
| `--changes` | **Yes** | structure | -- | Changes to apply. Contains `GroundTruth` (blob, JSON Lines format) |

**Output Schema:**
```json
{
    "Status": "CREATE_IN_PROGRESS|CREATE_COMPLETE|CREATE_FAILED|UPDATE_IN_PROGRESS|UPDATE_COMPLETE|UPDATE_FAILED_ROLLBACK_IN_PROGRESS|UPDATE_FAILED_ROLLBACK_COMPLETE|DELETE_IN_PROGRESS"
}
```

---

### 9.7 `distribute-dataset-entries`

Distributes entries from training dataset to test dataset (or vice versa).

**Synopsis:**
```bash
aws rekognition distribute-dataset-entries \
    --datasets <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--datasets` | **Yes** | list | -- | Source and destination datasets. Each item has `Arn` field. Requires exactly 2 entries |

**Output:** None (HTTP 200 on success)
