# Named Queries

### 2.1 `create-named-query`

Creates a named query (saved query) in Athena.

**Synopsis:**
```bash
aws athena create-named-query \
    --name <value> \
    --database <value> \
    --query-string <value> \
    [--description <value>] \
    [--client-request-token <value>] \
    [--work-group <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Named query name |
| `--database` | **Yes** | string | -- | Database for the query |
| `--query-string` | **Yes** | string | -- | SQL query string |
| `--description` | No | string | -- | Description |
| `--client-request-token` | No | string | -- | Idempotency token |
| `--work-group` | No | string | `primary` | Workgroup |

**Output Schema:**
```json
{
    "NamedQueryId": "string"
}
```

---

### 2.2 `delete-named-query`

Deletes a named query.

**Synopsis:**
```bash
aws athena delete-named-query \
    --named-query-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--named-query-id` | **Yes** | string | -- | Named query ID to delete |

No output on success.

---

### 2.3 `get-named-query`

Returns information about a named query.

**Synopsis:**
```bash
aws athena get-named-query \
    --named-query-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--named-query-id` | **Yes** | string | -- | Named query ID |

**Output Schema:**
```json
{
    "NamedQuery": {
        "Name": "string",
        "Description": "string",
        "Database": "string",
        "QueryString": "string",
        "NamedQueryId": "string",
        "WorkGroup": "string"
    }
}
```

---

### 2.4 `batch-get-named-query`

Returns information about multiple named queries (up to 50).

**Synopsis:**
```bash
aws athena batch-get-named-query \
    --named-query-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--named-query-ids` | **Yes** | list(string) | -- | Up to 50 named query IDs |

**Output Schema:**
```json
{
    "NamedQueries": [
        {
            "Name": "string",
            "Description": "string",
            "Database": "string",
            "QueryString": "string",
            "NamedQueryId": "string",
            "WorkGroup": "string"
        }
    ],
    "UnprocessedNamedQueryIds": [
        {
            "NamedQueryId": "string",
            "ErrorCode": "string",
            "ErrorMessage": "string"
        }
    ]
}
```

---

### 2.5 `list-named-queries`

Lists named query IDs for the specified workgroup. **Paginated operation.**

**Synopsis:**
```bash
aws athena list-named-queries \
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
    "NamedQueryIds": ["string"],
    "NextToken": "string"
}
```
