# Datasets

## Datasets

### 1.1 `create-dataset`

Creates a dataset for storing time-series data.

**Synopsis:**
```bash
aws forecast create-dataset \
    --dataset-name <value> \
    --domain <value> \
    --dataset-type <value> \
    --schema <value> \
    [--data-frequency <value>] \
    [--encryption-config <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--dataset-name` | **Yes** | string | -- | Dataset name (1-63 chars, `^[a-zA-Z][a-zA-Z0-9_]*`) |
| `--domain` | **Yes** | string | -- | Domain: `RETAIL`, `CUSTOM`, `INVENTORY_PLANNING`, `EC2_CAPACITY`, `WORK_FORCE`, `WEB_TRAFFIC`, `METRICS` |
| `--dataset-type` | **Yes** | string | -- | Type: `TARGET_TIME_SERIES`, `RELATED_TIME_SERIES`, `ITEM_METADATA` |
| `--schema` | **Yes** | structure | -- | Schema: `Attributes=[{AttributeName=string,AttributeType=string}]` |
| `--data-frequency` | No | string | None | Data frequency (e.g., `1D`, `1H`, `15min`). Required for RELATED_TIME_SERIES |
| `--encryption-config` | No | structure | None | KMS config: `RoleArn=string,KMSKeyArn=string` |
| `--tags` | No | list | None | Tags: `Key=string,Value=string ...` |

**Schema AttributeType Values:** `string`, `integer`, `float`, `timestamp`, `geolocation`

**Output Schema:**
```json
{
    "DatasetArn": "string"
}
```

---

### 1.2 `describe-dataset`

Gets properties of a dataset.

**Synopsis:**
```bash
aws forecast describe-dataset \
    --dataset-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--dataset-arn` | **Yes** | string | -- | Dataset ARN (max 256 chars) |

**Output Schema:**
```json
{
    "DatasetArn": "string",
    "DatasetName": "string",
    "Domain": "string",
    "DatasetType": "string",
    "DataFrequency": "string",
    "Schema": {
        "Attributes": [{"AttributeName": "string", "AttributeType": "string"}]
    },
    "EncryptionConfig": {"RoleArn": "string", "KMSKeyArn": "string"},
    "Status": "string",
    "CreationTime": "timestamp",
    "LastModificationTime": "timestamp"
}
```

---

### 1.3 `list-datasets`

Lists datasets. **Paginated operation.**

**Synopsis:**
```bash
aws forecast list-datasets \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-100) |

**Output Schema:**
```json
{
    "Datasets": [
        {
            "DatasetArn": "string",
            "DatasetName": "string",
            "DatasetType": "string",
            "Domain": "string",
            "CreationTime": "timestamp",
            "LastModificationTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.4 `delete-dataset`

Deletes a dataset. You can only delete datasets that have a status of `ACTIVE` or `CREATE_FAILED`.

**Synopsis:**
```bash
aws forecast delete-dataset \
    --dataset-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--dataset-arn` | **Yes** | string | -- | Dataset ARN |

**Output:** None

---

## Dataset Groups

### 1.5 `create-dataset-group`

Creates a dataset group that links one or more datasets.

**Synopsis:**
```bash
aws forecast create-dataset-group \
    --dataset-group-name <value> \
    --domain <value> \
    [--dataset-arns <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--dataset-group-name` | **Yes** | string | -- | Group name (1-63 chars) |
| `--domain` | **Yes** | string | -- | Domain (must match datasets) |
| `--dataset-arns` | No | list | None | Dataset ARNs to include |
| `--tags` | No | list | None | Tags: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "DatasetGroupArn": "string"
}
```

---

### 1.6 `describe-dataset-group`

Gets properties of a dataset group.

**Synopsis:**
```bash
aws forecast describe-dataset-group \
    --dataset-group-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--dataset-group-arn` | **Yes** | string | -- | Dataset group ARN |

**Output Schema:**
```json
{
    "DatasetGroupName": "string",
    "DatasetGroupArn": "string",
    "DatasetArns": ["string"],
    "Domain": "string",
    "Status": "string",
    "CreationTime": "timestamp",
    "LastModificationTime": "timestamp"
}
```

---

### 1.7 `list-dataset-groups`

Lists dataset groups. **Paginated operation.**

**Synopsis:**
```bash
aws forecast list-dataset-groups \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-100) |

**Output Schema:**
```json
{
    "DatasetGroups": [
        {
            "DatasetGroupArn": "string",
            "DatasetGroupName": "string",
            "CreationTime": "timestamp",
            "LastModificationTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.8 `update-dataset-group`

Updates the datasets in a dataset group.

**Synopsis:**
```bash
aws forecast update-dataset-group \
    --dataset-group-arn <value> \
    --dataset-arns <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--dataset-group-arn` | **Yes** | string | -- | Dataset group ARN |
| `--dataset-arns` | **Yes** | list | -- | Complete list of dataset ARNs (replaces existing) |

**Output:** None

---

### 1.9 `delete-dataset-group`

Deletes a dataset group.

**Synopsis:**
```bash
aws forecast delete-dataset-group \
    --dataset-group-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--dataset-group-arn` | **Yes** | string | -- | Dataset group ARN |

**Output:** None

---

## Dataset Import Jobs

### 1.10 `create-dataset-import-job`

Imports data from S3 into a dataset.

**Synopsis:**
```bash
aws forecast create-dataset-import-job \
    --dataset-import-job-name <value> \
    --dataset-arn <value> \
    --data-source <value> \
    [--timestamp-format <value>] \
    [--time-zone <value>] \
    [--use-geolocation-for-time-zone | --no-use-geolocation-for-time-zone] \
    [--geolocation-format <value>] \
    [--tags <value>] \
    [--format <value>] \
    [--import-mode <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--dataset-import-job-name` | **Yes** | string | -- | Job name (1-63 chars). Include timestamp to avoid duplicates |
| `--dataset-arn` | **Yes** | string | -- | Target dataset ARN |
| `--data-source` | **Yes** | structure | -- | S3 config: `S3Config={Path=string,RoleArn=string,KMSKeyArn=string}` |
| `--timestamp-format` | No | string | `yyyy-MM-dd HH:mm:ss` | Timestamp format |
| `--time-zone` | No | string | None | Single time zone (Joda-Time name) |
| `--use-geolocation-for-time-zone` | No | boolean | false | Derive time zone from geolocation |
| `--geolocation-format` | No | string | None | `LAT_LONG` or `CC_POSTALCODE` |
| `--tags` | No | list | None | Tags |
| `--format` | No | string | `CSV` | Data format: `CSV` or `PARQUET` |
| `--import-mode` | No | string | None | `FULL` (replace all) or `INCREMENTAL` (append) |

**Output Schema:**
```json
{
    "DatasetImportJobArn": "string"
}
```

---

### 1.11 `describe-dataset-import-job`

Gets properties of a dataset import job.

**Synopsis:**
```bash
aws forecast describe-dataset-import-job \
    --dataset-import-job-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--dataset-import-job-arn` | **Yes** | string | -- | Import job ARN |

**Output Schema:**
```json
{
    "DatasetImportJobName": "string",
    "DatasetImportJobArn": "string",
    "DatasetArn": "string",
    "TimestampFormat": "string",
    "TimeZone": "string",
    "UseGeolocationForTimeZone": "boolean",
    "GeolocationFormat": "string",
    "DataSource": {"S3Config": {}},
    "EstimatedTimeRemainingInMinutes": "long",
    "FieldStatistics": {},
    "DataSize": "double",
    "Status": "string",
    "Message": "string",
    "CreationTime": "timestamp",
    "LastModificationTime": "timestamp",
    "Format": "string",
    "ImportMode": "string"
}
```

---

### 1.12 `list-dataset-import-jobs`

Lists dataset import jobs. **Paginated operation.**

**Synopsis:**
```bash
aws forecast list-dataset-import-jobs \
    [--next-token <value>] \
    [--max-results <value>] \
    [--filters <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-100) |
| `--filters` | No | list | None | Filters: `Key=string,Value=string,Condition=string` |

**Output Schema:**
```json
{
    "DatasetImportJobs": [
        {
            "DatasetImportJobArn": "string",
            "DatasetImportJobName": "string",
            "DataSource": {},
            "Status": "string",
            "Message": "string",
            "CreationTime": "timestamp",
            "LastModificationTime": "timestamp",
            "ImportMode": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.13 `delete-dataset-import-job`

Deletes a dataset import job.

**Synopsis:**
```bash
aws forecast delete-dataset-import-job \
    --dataset-import-job-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--dataset-import-job-arn` | **Yes** | string | -- | Import job ARN |

**Output:** None
