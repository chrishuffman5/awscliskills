# Data Ingestion

### 2.1 `write-records`

Writes time-series data into a Timestream table. Accepts 1-100 records per request.

**Synopsis:**
```bash
aws timestream-write write-records \
    --database-name <value> \
    --table-name <value> \
    --records <value> \
    [--common-attributes <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database-name` | **Yes** | string | -- | Target database name |
| `--table-name` | **Yes** | string | -- | Target table name |
| `--records` | **Yes** | list | -- | Array of records to write (1-100 per request) |
| `--common-attributes` | No | structure | None | Shared attributes applied to all records in the request |

**Record Structure:**
```json
[
    {
        "Dimensions": [
            {
                "Name": "string",
                "Value": "string",
                "DimensionValueType": "VARCHAR"
            }
        ],
        "MeasureName": "string",
        "MeasureValue": "string",
        "MeasureValueType": "DOUBLE|BIGINT|VARCHAR|BOOLEAN|TIMESTAMP|MULTI",
        "Time": "string",
        "TimeUnit": "MILLISECONDS|SECONDS|MICROSECONDS|NANOSECONDS",
        "Version": "long",
        "MeasureValues": [
            {
                "Name": "string",
                "Value": "string",
                "Type": "DOUBLE|BIGINT|VARCHAR|BOOLEAN|TIMESTAMP|MULTI"
            }
        ]
    }
]
```

**Common Attributes Structure:** Same structure as a single record. Fields set in common attributes apply to all records unless overridden per-record.

**Output Schema:**
```json
{
    "RecordsIngested": {
        "Total": "integer",
        "MemoryStore": "integer",
        "MagneticStore": "integer"
    }
}
```

**Key Notes:**
- Max 100 records per request
- Max 128 dimensions per record
- MeasureValue max: 2048 chars
- Use `Version` for upserts (must be greater than existing version)
- Query results may not immediately reflect the latest writes (eventual consistency)

---

### 2.2 `create-batch-load-task`

Creates a batch load task to ingest data from an S3 CSV file into a Timestream table.

**Synopsis:**
```bash
aws timestream-write create-batch-load-task \
    --target-database-name <value> \
    --target-table-name <value> \
    --data-source-configuration <value> \
    --report-configuration <value> \
    [--client-token <value>] \
    [--data-model-configuration <value>] \
    [--record-version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--target-database-name` | **Yes** | string | -- | Target database name |
| `--target-table-name` | **Yes** | string | -- | Target table name |
| `--data-source-configuration` | **Yes** | structure | -- | S3 data source and CSV format configuration |
| `--report-configuration` | **Yes** | structure | -- | S3 location for error/progress reports |
| `--client-token` | No | string | None | Idempotency token (1-64 chars) |
| `--data-model-configuration` | No | structure | None | Column-to-Timestream mapping (time, dimensions, measures) |
| `--record-version` | No | long | None | Record version for upserts |

**Data Source Configuration:**
```json
{
    "DataSourceS3Configuration": {
        "BucketName": "string",
        "ObjectKeyPrefix": "string"
    },
    "CsvConfiguration": {
        "ColumnSeparator": "string",
        "EscapeChar": "string",
        "QuoteChar": "string",
        "NullValue": "string",
        "TrimWhiteSpace": true
    },
    "DataFormat": "CSV"
}
```

**Report Configuration:**
```json
{
    "ReportS3Configuration": {
        "BucketName": "string",
        "ObjectKeyPrefix": "string",
        "EncryptionOption": "SSE_S3|SSE_KMS",
        "KmsKeyId": "string"
    }
}
```

**Data Model Configuration:**
```json
{
    "DataModel": {
        "TimeColumn": "string",
        "TimeUnit": "MILLISECONDS|SECONDS|MICROSECONDS|NANOSECONDS",
        "DimensionMappings": [
            {
                "SourceColumn": "string",
                "DestinationColumn": "string"
            }
        ],
        "MultiMeasureMappings": {
            "TargetMultiMeasureName": "string",
            "MultiMeasureAttributeMappings": [
                {
                    "SourceColumn": "string",
                    "TargetMultiMeasureAttributeName": "string",
                    "MeasureValueType": "DOUBLE|BIGINT|BOOLEAN|VARCHAR|TIMESTAMP"
                }
            ]
        },
        "MixedMeasureMappings": [
            {
                "MeasureName": "string",
                "SourceColumn": "string",
                "TargetMeasureName": "string",
                "MeasureValueType": "DOUBLE|BIGINT|VARCHAR|BOOLEAN|TIMESTAMP|MULTI",
                "MultiMeasureAttributeMappings": []
            }
        ],
        "MeasureNameColumn": "string"
    },
    "DataModelS3Configuration": {
        "BucketName": "string",
        "ObjectKey": "string"
    }
}
```

**Output Schema:**
```json
{
    "TaskId": "string"
}
```

---

### 2.3 `describe-batch-load-task`

Describes a batch load task, including its progress, configuration, and status.

**Synopsis:**
```bash
aws timestream-write describe-batch-load-task \
    --task-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--task-id` | **Yes** | string | -- | Batch load task ID (3-32 chars, pattern: `[A-Z0-9]+`) |

**Output Schema:**
```json
{
    "BatchLoadTaskDescription": {
        "TaskId": "string",
        "ErrorMessage": "string",
        "DataSourceConfiguration": {
            "DataSourceS3Configuration": {
                "BucketName": "string",
                "ObjectKeyPrefix": "string"
            },
            "CsvConfiguration": {
                "ColumnSeparator": "string",
                "EscapeChar": "string",
                "QuoteChar": "string",
                "NullValue": "string",
                "TrimWhiteSpace": "boolean"
            },
            "DataFormat": "CSV"
        },
        "ProgressReport": {
            "RecordsProcessed": "long",
            "RecordsIngested": "long",
            "ParseFailures": "long",
            "RecordIngestionFailures": "long",
            "FileFailures": "long",
            "BytesMetered": "long"
        },
        "ReportConfiguration": {
            "ReportS3Configuration": {
                "BucketName": "string",
                "ObjectKeyPrefix": "string",
                "EncryptionOption": "SSE_S3|SSE_KMS",
                "KmsKeyId": "string"
            }
        },
        "DataModelConfiguration": {
            "DataModel": {},
            "DataModelS3Configuration": {}
        },
        "TargetDatabaseName": "string",
        "TargetTableName": "string",
        "TaskStatus": "CREATED|IN_PROGRESS|FAILED|SUCCEEDED|PROGRESS_STOPPED|PENDING_RESUME",
        "RecordVersion": "long",
        "CreationTime": "timestamp",
        "LastUpdatedTime": "timestamp",
        "ResumableUntil": "timestamp"
    }
}
```

---

### 2.4 `list-batch-load-tasks`

Lists batch load tasks. **Paginated operation.**

**Synopsis:**
```bash
aws timestream-write list-batch-load-tasks \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "BatchLoadTasks": [
        {
            "TaskId": "string",
            "TaskStatus": "CREATED|IN_PROGRESS|FAILED|SUCCEEDED|PROGRESS_STOPPED|PENDING_RESUME",
            "DatabaseName": "string",
            "TableName": "string",
            "CreationTime": "timestamp",
            "LastUpdatedTime": "timestamp",
            "ResumableUntil": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.5 `resume-batch-load-task`

Resumes a batch load task that was previously stopped.

**Synopsis:**
```bash
aws timestream-write resume-batch-load-task \
    --task-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--task-id` | **Yes** | string | -- | Batch load task ID to resume |

**Output:** None
