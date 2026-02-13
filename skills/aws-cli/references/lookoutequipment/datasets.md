# Datasets

### 1.1 `create-dataset`

Creates a dataset for storing sensor data from industrial equipment.

**Synopsis:**
```bash
aws lookoutequipment create-dataset \
    --dataset-name <value> \
    [--dataset-schema <value>] \
    [--server-side-kms-key-id <value>] \
    [--client-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--dataset-name` | **Yes** | string | -- | Dataset name (1-200 chars, alphanumeric/hyphens/underscores) |
| `--dataset-schema` | No | structure | None | JSON schema describing the time series data |
| `--server-side-kms-key-id` | No | string | None | KMS key ID for encryption |
| `--client-token` | No | string | Auto | Idempotency token |
| `--tags` | No | list | None | Tags (max 200) |

**Schema Structure:**
```json
{
    "InlineDataSchema": "{\"Components\": [{\"ComponentName\": \"pump\", \"Columns\": [{\"Name\": \"timestamp\", \"Type\": \"DATETIME\"}, {\"Name\": \"temperature\", \"Type\": \"DOUBLE\"}]}]}"
}
```

**Output Schema:**
```json
{
    "DatasetName": "string",
    "DatasetArn": "string",
    "Status": "CREATED|INGESTION_IN_PROGRESS|ACTIVE|IMPORT_IN_PROGRESS"
}
```

---

### 1.2 `describe-dataset`

Describes a dataset including data quality summary and ingestion configuration.

**Synopsis:**
```bash
aws lookoutequipment describe-dataset \
    --dataset-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--dataset-name` | **Yes** | string | -- | Name of the dataset |

**Output Schema:**
```json
{
    "DatasetName": "string",
    "DatasetArn": "string",
    "CreatedAt": "timestamp",
    "LastUpdatedAt": "timestamp",
    "Status": "CREATED|INGESTION_IN_PROGRESS|ACTIVE|IMPORT_IN_PROGRESS",
    "Schema": "string",
    "ServerSideKmsKeyId": "string",
    "IngestionInputConfiguration": {
        "S3InputConfiguration": {
            "Bucket": "string",
            "Prefix": "string",
            "KeyPattern": "string"
        }
    },
    "DataQualitySummary": {
        "InsufficientSensorData": {
            "MissingCompleteSensorData": {"AffectedSensorCount": "integer"},
            "SensorsWithShortDateRange": {"AffectedSensorCount": "integer"}
        },
        "MissingSensorData": {
            "AffectedSensorCount": "integer",
            "TotalNumberOfMissingValues": "integer"
        },
        "InvalidSensorData": {
            "AffectedSensorCount": "integer",
            "TotalNumberOfInvalidValues": "integer"
        },
        "UnsupportedTimestamps": {"TotalNumberOfUnsupportedTimestamps": "integer"},
        "DuplicateTimestamps": {"TotalNumberOfDuplicateTimestamps": "integer"}
    },
    "IngestedFilesSummary": {
        "TotalNumberOfFiles": "integer",
        "IngestedNumberOfFiles": "integer",
        "DiscardedFiles": [{"Bucket": "string", "Key": "string"}]
    },
    "RoleArn": "string",
    "DataStartTime": "timestamp",
    "DataEndTime": "timestamp",
    "SourceDatasetArn": "string"
}
```

---

### 1.3 `list-datasets`

Lists datasets. **Paginated operation.**

**Synopsis:**
```bash
aws lookoutequipment list-datasets \
    [--next-token <value>] \
    [--max-results <value>] \
    [--dataset-name-begins-with <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results per page (1-500) |
| `--dataset-name-begins-with` | No | string | None | Filter by name prefix |

**Output Schema:**
```json
{
    "NextToken": "string",
    "DatasetSummaries": [
        {
            "DatasetName": "string",
            "DatasetArn": "string",
            "Status": "CREATED|INGESTION_IN_PROGRESS|ACTIVE|IMPORT_IN_PROGRESS",
            "CreatedAt": "timestamp"
        }
    ]
}
```

---

### 1.4 `delete-dataset`

Deletes a dataset.

**Synopsis:**
```bash
aws lookoutequipment delete-dataset \
    --dataset-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--dataset-name` | **Yes** | string | -- | Name of the dataset to delete |

**Output:** None

---

### 1.5 `import-dataset`

Imports a dataset from another AWS account or region.

**Synopsis:**
```bash
aws lookoutequipment import-dataset \
    --source-dataset-arn <value> \
    [--dataset-name <value>] \
    [--client-token <value>] \
    [--server-side-kms-key-id <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-dataset-arn` | **Yes** | string | -- | ARN of the source dataset to import |
| `--dataset-name` | No | string | Source name | Name for the imported dataset |
| `--client-token` | No | string | Auto | Idempotency token |
| `--server-side-kms-key-id` | No | string | None | KMS key for encryption |
| `--tags` | No | list | None | Tags (max 200) |

**Output Schema:**
```json
{
    "DatasetName": "string",
    "DatasetArn": "string",
    "Status": "CREATED|INGESTION_IN_PROGRESS|ACTIVE|IMPORT_IN_PROGRESS",
    "JobId": "string"
}
```

---

### 1.6 `start-data-ingestion-job`

Starts ingesting sensor data from S3 into a dataset.

**Synopsis:**
```bash
aws lookoutequipment start-data-ingestion-job \
    --dataset-name <value> \
    --ingestion-input-configuration <value> \
    --role-arn <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--dataset-name` | **Yes** | string | -- | Name of the dataset |
| `--ingestion-input-configuration` | **Yes** | structure | -- | S3 input configuration |
| `--role-arn` | **Yes** | string | -- | IAM role with S3 access |
| `--client-token` | No | string | Auto | Idempotency token |

**IngestionInputConfiguration Structure:**
```json
{
    "S3InputConfiguration": {
        "Bucket": "my-bucket",
        "Prefix": "sensor-data/",
        "KeyPattern": "{prefix}/{component_name}_*"
    }
}
```

**Output Schema:**
```json
{
    "JobId": "string",
    "Status": "IN_PROGRESS|SUCCESS|FAILED|IMPORT_IN_PROGRESS"
}
```

---

### 1.7 `describe-data-ingestion-job`

Describes a data ingestion job.

**Synopsis:**
```bash
aws lookoutequipment describe-data-ingestion-job \
    --job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | The job ID |

**Output Schema:**
```json
{
    "JobId": "string",
    "DatasetArn": "string",
    "IngestionInputConfiguration": {
        "S3InputConfiguration": {
            "Bucket": "string",
            "Prefix": "string",
            "KeyPattern": "string"
        }
    },
    "RoleArn": "string",
    "CreatedAt": "timestamp",
    "Status": "IN_PROGRESS|SUCCESS|FAILED|IMPORT_IN_PROGRESS",
    "FailedReason": "string",
    "DataQualitySummary": {
        "InsufficientSensorData": {},
        "MissingSensorData": {},
        "InvalidSensorData": {},
        "UnsupportedTimestamps": {},
        "DuplicateTimestamps": {}
    },
    "IngestedFilesSummary": {
        "TotalNumberOfFiles": "integer",
        "IngestedNumberOfFiles": "integer",
        "DiscardedFiles": [{"Bucket": "string", "Key": "string"}]
    },
    "StatusDetail": "string",
    "IngestedDataSize": "long",
    "DataStartTime": "timestamp",
    "DataEndTime": "timestamp",
    "SourceDatasetArn": "string"
}
```

---

### 1.8 `list-data-ingestion-jobs`

Lists data ingestion jobs. **Paginated operation.**

**Synopsis:**
```bash
aws lookoutequipment list-data-ingestion-jobs \
    [--dataset-name <value>] \
    [--next-token <value>] \
    [--max-results <value>] \
    [--status <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--dataset-name` | No | string | None | Filter by dataset name |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results per page (1-500) |
| `--status` | No | string | None | Filter by status: `IN_PROGRESS`, `SUCCESS`, `FAILED`, `IMPORT_IN_PROGRESS` |

**Output Schema:**
```json
{
    "NextToken": "string",
    "DataIngestionJobSummaries": [
        {
            "JobId": "string",
            "DatasetName": "string",
            "DatasetArn": "string",
            "IngestionInputConfiguration": {
                "S3InputConfiguration": {
                    "Bucket": "string",
                    "Prefix": "string",
                    "KeyPattern": "string"
                }
            },
            "Status": "IN_PROGRESS|SUCCESS|FAILED|IMPORT_IN_PROGRESS"
        }
    ]
}
```
