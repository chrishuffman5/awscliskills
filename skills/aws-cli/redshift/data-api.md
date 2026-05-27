# Data API (`aws redshift-data`)

### 13.1 `execute-statement`

Runs a SQL statement against a Redshift cluster or serverless workgroup. Returns a statement ID for async tracking.

**Synopsis:**
```bash
aws redshift-data execute-statement \
    --sql <value> \
    --database <value> \
    [--cluster-identifier <value>] \
    [--workgroup-name <value>] \
    [--db-user <value>] \
    [--secret-arn <value>] \
    [--statement-name <value>] \
    [--with-event | --no-with-event] \
    [--client-token <value>] \
    [--session-id <value>] \
    [--session-keep-alive-seconds <value>] \
    [--result-format <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--sql` | **Yes** | string | -- | SQL statement to execute |
| `--database` | **Yes** | string | -- | Database name |
| `--cluster-identifier` | No | string | -- | Provisioned cluster identifier (mutually exclusive with `--workgroup-name`) |
| `--workgroup-name` | No | string | -- | Serverless workgroup name |
| `--db-user` | No | string | -- | Database user (temporary credentials, for provisioned clusters) |
| `--secret-arn` | No | string | -- | Secrets Manager secret ARN for credentials |
| `--statement-name` | No | string | -- | Name for the statement (for filtering in list-statements) |
| `--with-event` | No | boolean | false | Send an EventBridge event when the statement completes |
| `--client-token` | No | string | -- | Idempotency token |
| `--session-id` | No | string | -- | Session ID for multi-statement sessions |
| `--session-keep-alive-seconds` | No | integer | -- | Seconds to keep session alive |
| `--result-format` | No | string | -- | Result format: `JSON`, `CSV` |

**Output Schema:**
```json
{
    "Id": "string",
    "CreatedAt": "timestamp",
    "ClusterIdentifier": "string",
    "DbUser": "string",
    "Database": "string",
    "SecretArn": "string",
    "WorkgroupName": "string",
    "SessionId": "string"
}
```

---

### 13.2 `batch-execute-statement`

Runs one or more SQL statements in a batch.

**Synopsis:**
```bash
aws redshift-data batch-execute-statement \
    --sqls <value> \
    --database <value> \
    [--cluster-identifier <value>] \
    [--workgroup-name <value>] \
    [--db-user <value>] \
    [--secret-arn <value>] \
    [--statement-name <value>] \
    [--with-event | --no-with-event] \
    [--client-token <value>] \
    [--session-id <value>] \
    [--session-keep-alive-seconds <value>] \
    [--result-format <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--sqls` | **Yes** | list(string) | -- | List of SQL statements to execute |
| `--database` | **Yes** | string | -- | Database name |
| `--cluster-identifier` | No | string | -- | Provisioned cluster identifier |
| `--workgroup-name` | No | string | -- | Serverless workgroup name |
| `--db-user` | No | string | -- | Database user |
| `--secret-arn` | No | string | -- | Secrets Manager secret ARN |
| `--statement-name` | No | string | -- | Statement name |
| `--with-event` | No | boolean | false | Send EventBridge event on completion |
| `--client-token` | No | string | -- | Idempotency token |
| `--session-id` | No | string | -- | Session ID |
| `--session-keep-alive-seconds` | No | integer | -- | Session keep-alive seconds |
| `--result-format` | No | string | -- | Result format: `JSON`, `CSV` |

**Output Schema:**
```json
{
    "Id": "string",
    "CreatedAt": "timestamp",
    "ClusterIdentifier": "string",
    "DbUser": "string",
    "Database": "string",
    "SecretArn": "string",
    "WorkgroupName": "string",
    "SessionId": "string"
}
```

---

### 13.3 `cancel-statement`

Cancels a running SQL statement.

**Synopsis:**
```bash
aws redshift-data cancel-statement \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Statement ID to cancel |

**Output Schema:**
```json
{
    "Status": true|false
}
```

---

### 13.4 `describe-statement`

Describes the details of a specific SQL statement execution.

**Synopsis:**
```bash
aws redshift-data describe-statement \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Statement ID |

**Output Schema:**
```json
{
    "Id": "string",
    "Status": "SUBMITTED|PICKED|STARTED|FINISHED|ABORTED|FAILED",
    "CreatedAt": "timestamp",
    "UpdatedAt": "timestamp",
    "ClusterIdentifier": "string",
    "WorkgroupName": "string",
    "Database": "string",
    "DbUser": "string",
    "SecretArn": "string",
    "QueryString": "string",
    "QueryParameters": [
        {
            "name": "string",
            "value": "string"
        }
    ],
    "Duration": "long",
    "ResultRows": "long",
    "ResultSize": "long",
    "RedshiftPid": "long",
    "RedshiftQueryId": "long",
    "HasResultSet": "boolean",
    "Error": "string",
    "SubStatements": [
        {
            "Id": "string",
            "Status": "SUBMITTED|PICKED|STARTED|FINISHED|ABORTED|FAILED",
            "CreatedAt": "timestamp",
            "UpdatedAt": "timestamp",
            "QueryString": "string",
            "Duration": "long",
            "ResultRows": "long",
            "ResultSize": "long",
            "RedshiftQueryId": "long",
            "HasResultSet": "boolean",
            "Error": "string"
        }
    ],
    "SessionId": "string",
    "ResultFormat": "JSON|CSV"
}
```

---

### 13.5 `get-statement-result`

Fetches the result of a completed SQL statement. **Paginated operation.**

**Synopsis:**
```bash
aws redshift-data get-statement-result \
    --id <value> \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Statement ID (or sub-statement ID for batch) |
| `--next-token` | No | string | -- | Pagination token |

**Output Schema:**
```json
{
    "ColumnMetadata": [
        {
            "columnDefault": "string",
            "isCaseSensitive": "boolean",
            "isCurrency": "boolean",
            "isSigned": "boolean",
            "label": "string",
            "length": "integer",
            "name": "string",
            "nullable": "integer",
            "precision": "integer",
            "scale": "integer",
            "schemaName": "string",
            "tableName": "string",
            "typeName": "string"
        }
    ],
    "Records": [
        [
            {
                "isNull": "boolean",
                "booleanValue": "boolean",
                "longValue": "long",
                "doubleValue": "double",
                "stringValue": "string",
                "blobValue": "blob"
            }
        ]
    ],
    "TotalNumRows": "long",
    "NextToken": "string"
}
```

---

### 13.6 `list-statements`

Lists SQL statement executions. **Paginated operation.**

**Synopsis:**
```bash
aws redshift-data list-statements \
    [--status <value>] \
    [--statement-name <value>] \
    [--role-level | --no-role-level] \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--status` | No | string | -- | Filter: `SUBMITTED`, `PICKED`, `STARTED`, `FINISHED`, `ABORTED`, `FAILED`, `ALL` |
| `--statement-name` | No | string | -- | Filter by statement name |
| `--role-level` | No | boolean | false | List statements submitted by all users (requires IAM permission) |
| `--next-token` | No | string | -- | Pagination token |
| `--max-results` | No | integer | -- | Maximum results (1-100) |

**Output Schema:**
```json
{
    "Statements": [
        {
            "Id": "string",
            "Status": "SUBMITTED|PICKED|STARTED|FINISHED|ABORTED|FAILED",
            "CreatedAt": "timestamp",
            "UpdatedAt": "timestamp",
            "QueryString": "string",
            "QueryStrings": ["string"],
            "StatementName": "string",
            "SecretArn": "string",
            "IsBatchStatement": "boolean",
            "SessionId": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 13.7 `list-databases`

Lists databases in a cluster or serverless workgroup. **Paginated operation.**

**Synopsis:**
```bash
aws redshift-data list-databases \
    --database <value> \
    [--cluster-identifier <value>] \
    [--workgroup-name <value>] \
    [--db-user <value>] \
    [--secret-arn <value>] \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database` | **Yes** | string | -- | Database to connect to |
| `--cluster-identifier` | No | string | -- | Cluster identifier |
| `--workgroup-name` | No | string | -- | Workgroup name |
| `--db-user` | No | string | -- | Database user |
| `--secret-arn` | No | string | -- | Secrets Manager secret ARN |
| `--next-token` | No | string | -- | Pagination token |
| `--max-results` | No | integer | -- | Maximum results |

**Output Schema:**
```json
{
    "Databases": ["string"],
    "NextToken": "string"
}
```

---

### 13.8 `list-schemas`

Lists schemas in a database. **Paginated operation.**

**Synopsis:**
```bash
aws redshift-data list-schemas \
    --database <value> \
    [--cluster-identifier <value>] \
    [--workgroup-name <value>] \
    [--db-user <value>] \
    [--secret-arn <value>] \
    [--schema-pattern <value>] \
    [--connected-database <value>] \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database` | **Yes** | string | -- | Database name |
| `--cluster-identifier` | No | string | -- | Cluster identifier |
| `--workgroup-name` | No | string | -- | Workgroup name |
| `--db-user` | No | string | -- | Database user |
| `--secret-arn` | No | string | -- | Secrets Manager secret ARN |
| `--schema-pattern` | No | string | -- | Schema name pattern (SQL LIKE syntax) |
| `--connected-database` | No | string | -- | Connected database for cross-database queries |
| `--next-token` | No | string | -- | Pagination token |
| `--max-results` | No | integer | -- | Maximum results |

**Output Schema:**
```json
{
    "Schemas": ["string"],
    "NextToken": "string"
}
```

---

### 13.9 `list-tables`

Lists tables in a schema. **Paginated operation.**

**Synopsis:**
```bash
aws redshift-data list-tables \
    --database <value> \
    [--cluster-identifier <value>] \
    [--workgroup-name <value>] \
    [--db-user <value>] \
    [--secret-arn <value>] \
    [--schema-pattern <value>] \
    [--table-pattern <value>] \
    [--connected-database <value>] \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database` | **Yes** | string | -- | Database name |
| `--cluster-identifier` | No | string | -- | Cluster identifier |
| `--workgroup-name` | No | string | -- | Workgroup name |
| `--db-user` | No | string | -- | Database user |
| `--secret-arn` | No | string | -- | Secrets Manager secret ARN |
| `--schema-pattern` | No | string | -- | Schema name pattern |
| `--table-pattern` | No | string | -- | Table name pattern |
| `--connected-database` | No | string | -- | Connected database |
| `--next-token` | No | string | -- | Pagination token |
| `--max-results` | No | integer | -- | Maximum results |

**Output Schema:**
```json
{
    "Tables": [
        {
            "name": "string",
            "type": "TABLE|VIEW|SYSTEM TABLE|GLOBAL TEMPORARY|LOCAL TEMPORARY|ALIAS|SYNONYM",
            "schema": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 13.10 `describe-table`

Describes the columns of a table. **Paginated operation.**

**Synopsis:**
```bash
aws redshift-data describe-table \
    --database <value> \
    [--cluster-identifier <value>] \
    [--workgroup-name <value>] \
    [--db-user <value>] \
    [--secret-arn <value>] \
    [--schema <value>] \
    [--table <value>] \
    [--connected-database <value>] \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database` | **Yes** | string | -- | Database name |
| `--cluster-identifier` | No | string | -- | Cluster identifier |
| `--workgroup-name` | No | string | -- | Workgroup name |
| `--db-user` | No | string | -- | Database user |
| `--secret-arn` | No | string | -- | Secrets Manager secret ARN |
| `--schema` | No | string | -- | Schema name |
| `--table` | No | string | -- | Table name |
| `--connected-database` | No | string | -- | Connected database |
| `--next-token` | No | string | -- | Pagination token |
| `--max-results` | No | integer | -- | Maximum results |

**Output Schema:**
```json
{
    "TableName": "string",
    "ColumnList": [
        {
            "columnDefault": "string",
            "isCaseSensitive": "boolean",
            "isCurrency": "boolean",
            "isSigned": "boolean",
            "label": "string",
            "length": "integer",
            "name": "string",
            "nullable": "integer",
            "precision": "integer",
            "scale": "integer",
            "schemaName": "string",
            "tableName": "string",
            "typeName": "string"
        }
    ],
    "NextToken": "string"
}
```
