# Prepared Statements

### 3.1 `create-prepared-statement`

Creates a prepared statement for use with parameterized queries.

**Synopsis:**
```bash
aws athena create-prepared-statement \
    --statement-name <value> \
    --work-group <value> \
    --query-statement <value> \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--statement-name` | **Yes** | string | -- | Statement name (1-256 chars) |
| `--work-group` | **Yes** | string | -- | Workgroup |
| `--query-statement` | **Yes** | string | -- | SQL with `?` placeholders for parameters |
| `--description` | No | string | -- | Description |

No output on success.

---

### 3.2 `delete-prepared-statement`

Deletes a prepared statement.

**Synopsis:**
```bash
aws athena delete-prepared-statement \
    --statement-name <value> \
    --work-group <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--statement-name` | **Yes** | string | -- | Statement to delete |
| `--work-group` | **Yes** | string | -- | Workgroup |

No output on success.

---

### 3.3 `get-prepared-statement`

Returns information about a prepared statement.

**Synopsis:**
```bash
aws athena get-prepared-statement \
    --statement-name <value> \
    --work-group <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--statement-name` | **Yes** | string | -- | Statement name |
| `--work-group` | **Yes** | string | -- | Workgroup |

**Output Schema:**
```json
{
    "PreparedStatement": {
        "StatementName": "string",
        "QueryStatement": "string",
        "WorkGroupName": "string",
        "Description": "string",
        "LastModifiedTime": "timestamp"
    }
}
```

---

### 3.4 `update-prepared-statement`

Updates a prepared statement.

**Synopsis:**
```bash
aws athena update-prepared-statement \
    --statement-name <value> \
    --work-group <value> \
    --query-statement <value> \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--statement-name` | **Yes** | string | -- | Statement to update |
| `--work-group` | **Yes** | string | -- | Workgroup |
| `--query-statement` | **Yes** | string | -- | New SQL statement |
| `--description` | No | string | -- | New description |

No output on success.

---

### 3.5 `list-prepared-statements`

Lists prepared statements in a workgroup. **Paginated operation.**

**Synopsis:**
```bash
aws athena list-prepared-statements \
    --work-group <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--work-group` | **Yes** | string | -- | Workgroup |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "PreparedStatements": [
        {
            "StatementName": "string",
            "LastModifiedTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```
