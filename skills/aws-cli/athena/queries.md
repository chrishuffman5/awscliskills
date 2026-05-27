# Queries

### 1.1 `start-query-execution`

Starts a SQL query execution in Athena.

**Synopsis:**
```bash
aws athena start-query-execution \
    --query-string <value> \
    [--client-request-token <value>] \
    [--query-execution-context <value>] \
    [--result-configuration <value>] \
    [--work-group <value>] \
    [--execution-parameters <value>] \
    [--result-reuse-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--query-string` | **Yes** | string | -- | SQL query to execute |
| `--client-request-token` | No | string | -- | Idempotency token |
| `--query-execution-context` | No | structure | -- | Database/catalog context. Shorthand: `Database=string,Catalog=string` |
| `--result-configuration` | No | structure | -- | Results location. Shorthand: `OutputLocation=s3://...,EncryptionConfiguration={EncryptionOption=SSE_S3\|SSE_KMS\|CSE_KMS,KmsKey=string},ExpectedBucketOwner=string,AclConfiguration={S3AclOption=BUCKET_OWNER_FULL_CONTROL}` |
| `--work-group` | No | string | `primary` | Workgroup to run in |
| `--execution-parameters` | No | list(string) | -- | Parameters for parameterized queries |
| `--result-reuse-configuration` | No | structure | -- | Reuse config. Shorthand: `ResultReuseByAgeConfiguration={Enabled=boolean,MaxAgeInMinutes=integer}` |

**Output Schema:**
```json
{
    "QueryExecutionId": "string"
}
```

---

### 1.2 `stop-query-execution`

Stops a running query execution.

**Synopsis:**
```bash
aws athena stop-query-execution \
    --query-execution-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--query-execution-id` | **Yes** | string | -- | Query execution ID to stop |

No output on success.

---

### 1.3 `get-query-execution`

Returns information about a single query execution.

**Synopsis:**
```bash
aws athena get-query-execution \
    --query-execution-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--query-execution-id` | **Yes** | string | -- | Query execution ID |

**Output Schema:**
```json
{
    "QueryExecution": {
        "QueryExecutionId": "string",
        "Query": "string",
        "StatementType": "DDL|DML|UTILITY",
        "ResultConfiguration": {
            "OutputLocation": "string",
            "EncryptionConfiguration": {
                "EncryptionOption": "SSE_S3|SSE_KMS|CSE_KMS",
                "KmsKey": "string"
            }
        },
        "ResultReuseConfiguration": {
            "ResultReuseByAgeConfiguration": {
                "Enabled": "boolean",
                "MaxAgeInMinutes": "integer"
            }
        },
        "QueryExecutionContext": {
            "Database": "string",
            "Catalog": "string"
        },
        "Status": {
            "State": "QUEUED|RUNNING|SUCCEEDED|FAILED|CANCELLED",
            "StateChangeReason": "string",
            "SubmissionDateTime": "timestamp",
            "CompletionDateTime": "timestamp",
            "AthenaError": {
                "ErrorCategory": "integer",
                "ErrorType": "integer",
                "Retryable": "boolean",
                "ErrorMessage": "string"
            }
        },
        "Statistics": {
            "EngineExecutionTimeInMillis": "long",
            "DataScannedInBytes": "long",
            "DataManifestLocation": "string",
            "TotalExecutionTimeInMillis": "long",
            "QueryQueueTimeInMillis": "long",
            "ServicePreProcessingTimeInMillis": "long",
            "QueryPlanningTimeInMillis": "long",
            "ServiceProcessingTimeInMillis": "long",
            "ResultReuseInformation": {
                "ReusedPreviousResult": "boolean"
            }
        },
        "WorkGroup": "string",
        "EngineVersion": {
            "SelectedEngineVersion": "string",
            "EffectiveEngineVersion": "string"
        },
        "ExecutionParameters": ["string"],
        "SubstatementType": "string"
    }
}
```

---

### 1.4 `get-query-results`

Returns query result rows. **Paginated operation.**

**Synopsis:**
```bash
aws athena get-query-results \
    --query-execution-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--query-execution-id` | **Yes** | string | -- | Query execution ID |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Rows per page (max 1000) |
| `--max-items` | No | integer | -- | Maximum total rows |

**Output Schema:**
```json
{
    "UpdateCount": "long",
    "ResultSet": {
        "Rows": [
            {
                "Data": [
                    {
                        "VarCharValue": "string"
                    }
                ]
            }
        ],
        "ResultSetMetadata": {
            "ColumnInfo": [
                {
                    "CatalogName": "string",
                    "SchemaName": "string",
                    "TableName": "string",
                    "Name": "string",
                    "Label": "string",
                    "Type": "string",
                    "Precision": "integer",
                    "Scale": "integer",
                    "Nullable": "NOT_NULL|NULLABLE|UNKNOWN",
                    "CaseSensitive": "boolean"
                }
            ]
        }
    },
    "NextToken": "string"
}
```

---

### 1.5 `batch-get-query-execution`

Returns information about multiple query executions (up to 50).

**Synopsis:**
```bash
aws athena batch-get-query-execution \
    --query-execution-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--query-execution-ids` | **Yes** | list(string) | -- | Up to 50 query execution IDs |

**Output Schema:**
```json
{
    "QueryExecutions": [
        {
            "QueryExecutionId": "string",
            "Query": "string",
            "Status": {},
            "Statistics": {},
            "WorkGroup": "string"
        }
    ],
    "UnprocessedQueryExecutionIds": [
        {
            "QueryExecutionId": "string",
            "ErrorCode": "string",
            "ErrorMessage": "string"
        }
    ]
}
```

---

### 1.6 `list-query-executions`

Lists query execution IDs for the specified workgroup. **Paginated operation.**

**Synopsis:**
```bash
aws athena list-query-executions \
    [--work-group <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--work-group` | No | string | `primary` | Workgroup to list for |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page (max 50) |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "QueryExecutionIds": ["string"],
    "NextToken": "string"
}
```

---

### 1.7 `get-query-runtime-statistics`

Returns runtime statistics for a completed query execution.

**Synopsis:**
```bash
aws athena get-query-runtime-statistics \
    --query-execution-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--query-execution-id` | **Yes** | string | -- | Query execution ID |

**Output Schema:**
```json
{
    "QueryRuntimeStatistics": {
        "Timeline": {
            "QueryQueueTimeInMillis": "long",
            "ServiceProcessingTimeInMillis": "long",
            "QueryPlanningTimeInMillis": "long",
            "EngineExecutionTimeInMillis": "long",
            "TotalExecutionTimeInMillis": "long"
        },
        "Rows": {
            "InputRows": "long",
            "InputBytes": "long",
            "OutputRows": "long",
            "OutputBytes": "long"
        },
        "OutputStage": {
            "StageId": "long",
            "State": "string",
            "OutputBytes": "long",
            "OutputRows": "long",
            "InputBytes": "long",
            "InputRows": "long",
            "ExecutionTime": "long",
            "QueryStagePlan": {},
            "SubStages": []
        }
    }
}
```
