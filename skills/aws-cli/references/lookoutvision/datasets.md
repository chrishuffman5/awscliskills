# Datasets

### 3.1 `create-dataset`

Creates a new dataset in a project. A dataset can be a training dataset (`train`) or a test dataset (`test`). You can provide a manifest file as the dataset source, or create an empty dataset to populate later with `update-dataset-entries`.

**Synopsis:**
```bash
aws lookoutvision create-dataset \
    --project-name <value> \
    --dataset-type <value> \
    [--dataset-source <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project-name` | **Yes** | string | -- | Project to create the dataset in |
| `--dataset-type` | **Yes** | string | -- | Dataset type: `train` or `test` |
| `--dataset-source` | No | structure | None | Location of manifest file; omit to create empty dataset |
| `--client-token` | No | string | Auto | Idempotency token (active for 8 hours) |

**DatasetSource Structure:**
```json
{
    "GroundTruthManifest": {
        "S3Object": {
            "Bucket": "string",
            "Key": "string",
            "VersionId": "string"
        }
    }
}
```

**Output Schema:**
```json
{
    "DatasetMetadata": {
        "DatasetType": "string",
        "CreationTimestamp": "timestamp",
        "Status": "CREATE_IN_PROGRESS|CREATE_COMPLETE|CREATE_FAILED|UPDATE_IN_PROGRESS|UPDATE_COMPLETE|UPDATE_FAILED_ROLLBACK_IN_PROGRESS|UPDATE_FAILED_ROLLBACK_COMPLETE|DELETE_IN_PROGRESS|DELETE_COMPLETE|DELETE_FAILED",
        "StatusMessage": "string"
    }
}
```

---

### 3.2 `delete-dataset`

Deletes a dataset from a project. If the project has a single dataset, you must create a new dataset before training another model. If you delete the test dataset, the project reverts to single-dataset mode.

**Synopsis:**
```bash
aws lookoutvision delete-dataset \
    --project-name <value> \
    --dataset-type <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project-name` | **Yes** | string | -- | Project containing the dataset |
| `--dataset-type` | **Yes** | string | -- | Dataset type: `train` or `test` |
| `--client-token` | No | string | Auto | Idempotency token (active for 8 hours) |

**Output:** None

---

### 3.3 `describe-dataset`

Describes a dataset including image statistics (total, labeled, normal, and anomaly counts).

**Synopsis:**
```bash
aws lookoutvision describe-dataset \
    --project-name <value> \
    --dataset-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project-name` | **Yes** | string | -- | Project containing the dataset |
| `--dataset-type` | **Yes** | string | -- | Dataset type: `train` or `test` |

**Output Schema:**
```json
{
    "DatasetDescription": {
        "ProjectName": "string",
        "DatasetType": "string",
        "CreationTimestamp": "timestamp",
        "LastUpdatedTimestamp": "timestamp",
        "Status": "CREATE_IN_PROGRESS|CREATE_COMPLETE|CREATE_FAILED|UPDATE_IN_PROGRESS|UPDATE_COMPLETE|UPDATE_FAILED_ROLLBACK_IN_PROGRESS|UPDATE_FAILED_ROLLBACK_COMPLETE|DELETE_IN_PROGRESS|DELETE_COMPLETE|DELETE_FAILED",
        "StatusMessage": "string",
        "ImageStats": {
            "Total": "integer",
            "Labeled": "integer",
            "Normal": "integer",
            "Anomaly": "integer"
        }
    }
}
```

---

### 3.4 `list-dataset-entries`

Lists JSON Line entries in a dataset. Each entry contains anomaly information for a single image, including the image location and assigned label. **Paginated operation.**

**Synopsis:**
```bash
aws lookoutvision list-dataset-entries \
    --project-name <value> \
    --dataset-type <value> \
    [--labeled | --no-labeled] \
    [--anomaly-class <value>] \
    [--before-creation-date <value>] \
    [--after-creation-date <value>] \
    [--source-ref-contains <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project-name` | **Yes** | string | -- | Project containing the dataset |
| `--dataset-type` | **Yes** | string | -- | Dataset type: `train` or `test` |
| `--labeled` / `--no-labeled` | No | boolean | None | Filter labeled/unlabeled entries |
| `--anomaly-class` | No | string | None | Filter by class: `normal` or `anomaly` |
| `--before-creation-date` | No | timestamp | None | Only entries created before this date |
| `--after-creation-date` | No | timestamp | None | Only entries created after this date |
| `--source-ref-contains` | No | string | None | Filter by substring match in `source-ref` field |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Maximum total items to return |

**Output Schema:**
```json
{
    "DatasetEntries": [
        "string"
    ],
    "NextToken": "string"
}
```

---

### 3.5 `update-dataset-entries`

Adds or updates JSON Line entries in a dataset. If an entry with the same `source-ref` already exists, it is replaced. Referenced images must reside in the same S3 bucket as existing dataset images. Use `describe-dataset` to verify completion.

**Synopsis:**
```bash
aws lookoutvision update-dataset-entries \
    --project-name <value> \
    --dataset-type <value> \
    --changes <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project-name` | **Yes** | string | -- | Project containing the dataset |
| `--dataset-type` | **Yes** | string | -- | Dataset type: `train` or `test` |
| `--changes` | **Yes** | blob | -- | JSON Lines entries to add or update |
| `--client-token` | No | string | Auto | Idempotency token (active for 8 hours) |

**Output Schema:**
```json
{
    "Status": "CREATE_IN_PROGRESS|CREATE_COMPLETE|CREATE_FAILED|UPDATE_IN_PROGRESS|UPDATE_COMPLETE|UPDATE_FAILED_ROLLBACK_IN_PROGRESS|UPDATE_FAILED_ROLLBACK_COMPLETE|DELETE_IN_PROGRESS|DELETE_COMPLETE|DELETE_FAILED"
}
```
