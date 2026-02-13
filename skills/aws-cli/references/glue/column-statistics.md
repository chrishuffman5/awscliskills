# Column Statistics

### 17.1 `get-column-statistics-for-table`

Retrieves column statistics for a table.

**Synopsis:**
```bash
aws glue get-column-statistics-for-table \
    --database-name <value> \
    --table-name <value> \
    --column-names <value> \
    [--catalog-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database-name` | **Yes** | string | -- | Database name |
| `--table-name` | **Yes** | string | -- | Table name |
| `--column-names` | **Yes** | list(string) | -- | Column names |
| `--catalog-id` | No | string | -- | Catalog ID |

**Output Schema:**
```json
{
    "ColumnStatisticsList": [
        {
            "ColumnName": "string",
            "ColumnType": "string",
            "AnalyzedTime": "timestamp",
            "StatisticsData": {
                "Type": "BOOLEAN|DATE|DECIMAL|DOUBLE|LONG|STRING|BINARY",
                "BooleanColumnStatisticsData": {
                    "NumberOfTrues": "long",
                    "NumberOfFalses": "long",
                    "NumberOfNulls": "long"
                },
                "DateColumnStatisticsData": {
                    "MinimumValue": "timestamp",
                    "MaximumValue": "timestamp",
                    "NumberOfNulls": "long",
                    "NumberOfDistinctValues": "long"
                },
                "DecimalColumnStatisticsData": {},
                "DoubleColumnStatisticsData": {},
                "LongColumnStatisticsData": {},
                "StringColumnStatisticsData": {
                    "MaximumLength": "long",
                    "AverageLength": "double",
                    "NumberOfNulls": "long",
                    "NumberOfDistinctValues": "long"
                },
                "BinaryColumnStatisticsData": {}
            }
        }
    ],
    "Errors": [
        {
            "ColumnName": "string",
            "Error": {
                "ErrorCode": "string",
                "ErrorMessage": "string"
            }
        }
    ]
}
```

---

### 17.2 `update-column-statistics-for-table`

Updates column statistics for a table.

**Synopsis:**
```bash
aws glue update-column-statistics-for-table \
    --database-name <value> \
    --table-name <value> \
    --column-statistics-list <value> \
    [--catalog-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database-name` | **Yes** | string | -- | Database name |
| `--table-name` | **Yes** | string | -- | Table name |
| `--column-statistics-list` | **Yes** | list | -- | Column statistics entries (JSON) |
| `--catalog-id` | No | string | -- | Catalog ID |

**Output Schema:**
```json
{
    "Errors": [
        {
            "ColumnStatistics": {},
            "Error": {
                "ErrorCode": "string",
                "ErrorMessage": "string"
            }
        }
    ]
}
```

---

### 17.3 `delete-column-statistics-for-table`

Deletes column statistics for a table.

**Synopsis:**
```bash
aws glue delete-column-statistics-for-table \
    --database-name <value> \
    --table-name <value> \
    --column-name <value> \
    [--catalog-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database-name` | **Yes** | string | -- | Database name |
| `--table-name` | **Yes** | string | -- | Table name |
| `--column-name` | **Yes** | string | -- | Column name |
| `--catalog-id` | No | string | -- | Catalog ID |

No output on success.

---

### 17.4 `get-column-statistics-for-partition`

Retrieves column statistics for a partition.

**Synopsis:**
```bash
aws glue get-column-statistics-for-partition \
    --database-name <value> \
    --table-name <value> \
    --partition-values <value> \
    --column-names <value> \
    [--catalog-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database-name` | **Yes** | string | -- | Database name |
| `--table-name` | **Yes** | string | -- | Table name |
| `--partition-values` | **Yes** | list(string) | -- | Partition values |
| `--column-names` | **Yes** | list(string) | -- | Column names |
| `--catalog-id` | No | string | -- | Catalog ID |

**Output Schema:**
```json
{
    "ColumnStatisticsList": ["<ColumnStatistics structure>"],
    "Errors": []
}
```

---

### 17.5 `update-column-statistics-for-partition`

Updates column statistics for a partition.

**Synopsis:**
```bash
aws glue update-column-statistics-for-partition \
    --database-name <value> \
    --table-name <value> \
    --partition-values <value> \
    --column-statistics-list <value> \
    [--catalog-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database-name` | **Yes** | string | -- | Database name |
| `--table-name` | **Yes** | string | -- | Table name |
| `--partition-values` | **Yes** | list(string) | -- | Partition values |
| `--column-statistics-list` | **Yes** | list | -- | Column statistics entries (JSON) |
| `--catalog-id` | No | string | -- | Catalog ID |

**Output Schema:**
```json
{
    "Errors": []
}
```

---

### 17.6 `delete-column-statistics-for-partition`

Deletes column statistics for a partition.

**Synopsis:**
```bash
aws glue delete-column-statistics-for-partition \
    --database-name <value> \
    --table-name <value> \
    --partition-values <value> \
    --column-name <value> \
    [--catalog-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database-name` | **Yes** | string | -- | Database name |
| `--table-name` | **Yes** | string | -- | Table name |
| `--partition-values` | **Yes** | list(string) | -- | Partition values |
| `--column-name` | **Yes** | string | -- | Column name |
| `--catalog-id` | No | string | -- | Catalog ID |

No output on success.

---

### 17.7 `get-column-statistics-task-run`

Retrieves a column statistics task run.

**Synopsis:**
```bash
aws glue get-column-statistics-task-run \
    --database-name <value> \
    --table-name <value> \
    --column-statistics-task-run-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database-name` | **Yes** | string | -- | Database name |
| `--table-name` | **Yes** | string | -- | Table name |
| `--column-statistics-task-run-id` | **Yes** | string | -- | Task run ID |

**Output Schema:**
```json
{
    "ColumnStatisticsTaskRun": {
        "CustomerId": "string",
        "ColumnStatisticsTaskRunId": "string",
        "DatabaseName": "string",
        "TableName": "string",
        "ColumnNameList": ["string"],
        "CatalogID": "string",
        "Role": "string",
        "SampleSize": "double",
        "SecurityConfiguration": "string",
        "NumberOfWorkers": "integer",
        "WorkerType": "string",
        "Status": "STARTING|RUNNING|SUCCEEDED|FAILED|STOPPED",
        "CreationTime": "timestamp",
        "LastUpdated": "timestamp",
        "StartTime": "timestamp",
        "EndTime": "timestamp",
        "ErrorMessage": "string",
        "DPUSeconds": "double"
    }
}
```

---

### 17.8 `get-column-statistics-task-runs`

Lists column statistics task runs. **Paginated operation.**

**Synopsis:**
```bash
aws glue get-column-statistics-task-runs \
    --database-name <value> \
    --table-name <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database-name` | **Yes** | string | -- | Database name |
| `--table-name` | **Yes** | string | -- | Table name |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "ColumnStatisticsTaskRuns": ["<ColumnStatisticsTaskRun structure>"],
    "NextToken": "string"
}
```

---

### 17.9 `start-column-statistics-task-run`

Starts a column statistics generation task.

**Synopsis:**
```bash
aws glue start-column-statistics-task-run \
    --database-name <value> \
    --table-name <value> \
    --role <value> \
    [--column-name-list <value>] \
    [--catalog-id <value>] \
    [--sample-size <value>] \
    [--security-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database-name` | **Yes** | string | -- | Database name |
| `--table-name` | **Yes** | string | -- | Table name |
| `--role` | **Yes** | string | -- | IAM role ARN |
| `--column-name-list` | No | list(string) | -- | Specific columns (all if omitted) |
| `--catalog-id` | No | string | -- | Catalog ID |
| `--sample-size` | No | double | -- | Sample size percentage (0-100) |
| `--security-configuration` | No | string | -- | Security configuration name |

**Output Schema:**
```json
{
    "ColumnStatisticsTaskRunId": "string"
}
```

---

### 17.10 `stop-column-statistics-task-run`

Stops a running column statistics task.

**Synopsis:**
```bash
aws glue stop-column-statistics-task-run \
    --database-name <value> \
    --table-name <value> \
    --column-statistics-task-run-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database-name` | **Yes** | string | -- | Database name |
| `--table-name` | **Yes** | string | -- | Table name |
| `--column-statistics-task-run-id` | **Yes** | string | -- | Task run ID to stop |

No output on success.
