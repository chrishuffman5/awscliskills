# Datasets

### 2.1 `create-dataset`

Creates a dataset in a dataset group. Each dataset group can contain up to 5 datasets (Interactions, Items, Users, Actions, Action_Interactions).

**Synopsis:**
```bash
aws personalize create-dataset \
    --name <value> \
    --schema-arn <value> \
    --dataset-group-arn <value> \
    --dataset-type <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Dataset name (1-63 chars) |
| `--schema-arn` | **Yes** | string | -- | ARN of the schema for the dataset |
| `--dataset-group-arn` | **Yes** | string | -- | ARN of the dataset group |
| `--dataset-type` | **Yes** | string | -- | Type: `Interactions`, `Items`, `Users`, `Actions`, `Action_Interactions` |
| `--tags` | No | list | None | Tags (max 200) |

**Output Schema:**
```json
{
    "datasetArn": "string"
}
```

---

### 2.2 `describe-dataset`

Describes a dataset.

**Synopsis:**
```bash
aws personalize describe-dataset \
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
    "dataset": {
        "name": "string",
        "datasetArn": "string",
        "datasetGroupArn": "string",
        "datasetType": "string",
        "schemaArn": "string",
        "status": "string",
        "creationDateTime": "timestamp",
        "lastUpdatedDateTime": "timestamp",
        "latestDatasetUpdate": {
            "schemaArn": "string",
            "status": "string",
            "failureReason": "string",
            "creationDateTime": "timestamp",
            "lastUpdatedDateTime": "timestamp"
        }
    }
}
```

---

### 2.3 `list-datasets`

Lists datasets in a dataset group. **Paginated operation.**

**Synopsis:**
```bash
aws personalize list-datasets \
    [--dataset-group-arn <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--dataset-group-arn` | No | string | None | ARN of dataset group to filter by |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call (max 100) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "datasets": [
        {
            "name": "string",
            "datasetArn": "string",
            "datasetType": "string",
            "status": "string",
            "creationDateTime": "timestamp",
            "lastUpdatedDateTime": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 2.4 `update-dataset`

Updates a dataset schema.

**Synopsis:**
```bash
aws personalize update-dataset \
    --dataset-arn <value> \
    --schema-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--dataset-arn` | **Yes** | string | -- | ARN of the dataset |
| `--schema-arn` | **Yes** | string | -- | ARN of the new schema |

**Output Schema:**
```json
{
    "datasetArn": "string"
}
```

---

### 2.5 `delete-dataset`

Deletes a dataset. Cannot be undone.

**Synopsis:**
```bash
aws personalize delete-dataset \
    --dataset-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--dataset-arn` | **Yes** | string | -- | ARN of the dataset to delete |

**Output:** None

---

### 2.6 `create-dataset-import-job`

Creates a job to import training data from S3 into a dataset.

**Synopsis:**
```bash
aws personalize create-dataset-import-job \
    --job-name <value> \
    --dataset-arn <value> \
    --data-source <value> \
    [--role-arn <value>] \
    [--import-mode <value>] \
    [--publish-attribution-metrics-to-s3 | --no-publish-attribution-metrics-to-s3] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-name` | **Yes** | string | -- | Job name (1-63 chars) |
| `--dataset-arn` | **Yes** | string | -- | ARN of the destination dataset |
| `--data-source` | **Yes** | structure | -- | S3 data location. Shorthand: `dataLocation=s3://bucket/path` |
| `--role-arn` | No | string | None | IAM role ARN with S3 read access |
| `--import-mode` | No | string | `FULL` | Import mode: `FULL` (replace all) or `INCREMENTAL` (append) |
| `--publish-attribution-metrics-to-s3` | No | boolean | false | Publish metrics to S3 |
| `--tags` | No | list | None | Tags (max 200) |

**Output Schema:**
```json
{
    "datasetImportJobArn": "string"
}
```

---

### 2.7 `describe-dataset-import-job`

Describes a dataset import job.

**Synopsis:**
```bash
aws personalize describe-dataset-import-job \
    --dataset-import-job-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--dataset-import-job-arn` | **Yes** | string | -- | ARN of the dataset import job |

**Output Schema:**
```json
{
    "datasetImportJob": {
        "jobName": "string",
        "datasetImportJobArn": "string",
        "datasetArn": "string",
        "dataSource": {"dataLocation": "string"},
        "roleArn": "string",
        "status": "string",
        "importMode": "FULL|INCREMENTAL",
        "creationDateTime": "timestamp",
        "lastUpdatedDateTime": "timestamp",
        "failureReason": "string",
        "publishAttributionMetricsToS3": true|false
    }
}
```

---

### 2.8 `list-dataset-import-jobs`

Lists dataset import jobs. **Paginated operation.**

**Synopsis:**
```bash
aws personalize list-dataset-import-jobs \
    [--dataset-arn <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--dataset-arn` | No | string | None | Filter by dataset ARN |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call (max 100) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "datasetImportJobs": [
        {
            "datasetImportJobArn": "string",
            "jobName": "string",
            "status": "string",
            "creationDateTime": "timestamp",
            "lastUpdatedDateTime": "timestamp",
            "failureReason": "string",
            "importMode": "FULL|INCREMENTAL"
        }
    ],
    "nextToken": "string"
}
```

---

### 2.9 `create-dataset-export-job`

Creates a job to export data from a dataset to S3.

**Synopsis:**
```bash
aws personalize create-dataset-export-job \
    --job-name <value> \
    --dataset-arn <value> \
    --role-arn <value> \
    --job-output <value> \
    [--ingestion-mode <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-name` | **Yes** | string | -- | Job name (1-63 chars) |
| `--dataset-arn` | **Yes** | string | -- | ARN of the dataset to export |
| `--role-arn` | **Yes** | string | -- | IAM role ARN with S3 write access |
| `--job-output` | **Yes** | structure | -- | S3 output location |
| `--ingestion-mode` | No | string | `ALL` | Data to export: `BULK`, `PUT`, `ALL` |
| `--tags` | No | list | None | Tags (max 200) |

**Output Schema:**
```json
{
    "datasetExportJobArn": "string"
}
```

---

### 2.10 `describe-dataset-export-job`

Describes a dataset export job.

**Synopsis:**
```bash
aws personalize describe-dataset-export-job \
    --dataset-export-job-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--dataset-export-job-arn` | **Yes** | string | -- | ARN of the dataset export job |

**Output Schema:**
```json
{
    "datasetExportJob": {
        "jobName": "string",
        "datasetExportJobArn": "string",
        "datasetArn": "string",
        "ingestionMode": "BULK|PUT|ALL",
        "roleArn": "string",
        "status": "string",
        "jobOutput": {
            "s3DataDestination": {
                "path": "string",
                "kmsKeyArn": "string"
            }
        },
        "creationDateTime": "timestamp",
        "lastUpdatedDateTime": "timestamp",
        "failureReason": "string"
    }
}
```

---

### 2.11 `list-dataset-export-jobs`

Lists dataset export jobs. **Paginated operation.**

**Synopsis:**
```bash
aws personalize list-dataset-export-jobs \
    [--dataset-arn <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--dataset-arn` | No | string | None | Filter by dataset ARN |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "datasetExportJobs": [
        {
            "datasetExportJobArn": "string",
            "jobName": "string",
            "status": "string",
            "creationDateTime": "timestamp",
            "lastUpdatedDateTime": "timestamp",
            "failureReason": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 2.12 `create-data-deletion-job`

Creates a job to delete user data from a dataset group.

**Synopsis:**
```bash
aws personalize create-data-deletion-job \
    --job-name <value> \
    --dataset-group-arn <value> \
    --data-source <value> \
    --role-arn <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-name` | **Yes** | string | -- | Job name (1-63 chars) |
| `--dataset-group-arn` | **Yes** | string | -- | ARN of the dataset group |
| `--data-source` | **Yes** | structure | -- | S3 location of user IDs to delete |
| `--role-arn` | **Yes** | string | -- | IAM role ARN |
| `--tags` | No | list | None | Tags (max 200) |

**Output Schema:**
```json
{
    "dataDeletionJobArn": "string"
}
```

---

### 2.13 `describe-data-deletion-job`

Describes a data deletion job.

**Synopsis:**
```bash
aws personalize describe-data-deletion-job \
    --data-deletion-job-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--data-deletion-job-arn` | **Yes** | string | -- | ARN of the data deletion job |

**Output Schema:**
```json
{
    "dataDeletionJob": {
        "jobName": "string",
        "dataDeletionJobArn": "string",
        "datasetGroupArn": "string",
        "dataSource": {"dataLocation": "string"},
        "roleArn": "string",
        "status": "string",
        "numDeleted": "integer",
        "creationDateTime": "timestamp",
        "lastUpdatedDateTime": "timestamp",
        "failureReason": "string"
    }
}
```

---

### 2.14 `list-data-deletion-jobs`

Lists data deletion jobs. **Paginated operation.**

**Synopsis:**
```bash
aws personalize list-data-deletion-jobs \
    [--dataset-group-arn <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--dataset-group-arn` | No | string | None | Filter by dataset group ARN |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "dataDeletionJobs": [
        {
            "dataDeletionJobArn": "string",
            "datasetGroupArn": "string",
            "jobName": "string",
            "status": "string",
            "creationDateTime": "timestamp",
            "lastUpdatedDateTime": "timestamp",
            "failureReason": "string"
        }
    ],
    "nextToken": "string"
}
```
