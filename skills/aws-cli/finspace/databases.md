# Databases

### 2.1 `create-kx-database`

Creates a new KX database in the specified environment.

**Synopsis:**
```bash
aws finspace create-kx-database \
    --environment-id <value> \
    --database-name <value> \
    [--description <value>] \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | **Yes** | string | -- | Environment ID |
| `--database-name` | **Yes** | string | -- | Database name (3-63 chars: lowercase letters, numbers, hyphens) |
| `--description` | No | string | None | Description (1-1000 chars) |
| `--tags` | No | map | None | Tags |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "databaseName": "string",
    "databaseArn": "string",
    "environmentId": "string",
    "description": "string",
    "createdTimestamp": "timestamp",
    "lastModifiedTimestamp": "timestamp"
}
```

---

### 2.2 `delete-kx-database`

Deletes a KX database. All changesets and dataviews associated with the database are also deleted.

**Synopsis:**
```bash
aws finspace delete-kx-database \
    --environment-id <value> \
    --database-name <value> \
    --client-token <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | **Yes** | string | -- | Environment ID |
| `--database-name` | **Yes** | string | -- | Database name to delete |
| `--client-token` | **Yes** | string | -- | Idempotency token |

**Output:** None (HTTP 200 on success)

---

### 2.3 `get-kx-database`

Returns database information for the specified environment and database.

**Synopsis:**
```bash
aws finspace get-kx-database \
    --environment-id <value> \
    --database-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | **Yes** | string | -- | Environment ID |
| `--database-name` | **Yes** | string | -- | Database name |

**Output Schema:**
```json
{
    "databaseName": "string",
    "databaseArn": "string",
    "environmentId": "string",
    "description": "string",
    "createdTimestamp": "timestamp",
    "lastModifiedTimestamp": "timestamp",
    "lastCompletedChangesetId": "string",
    "numBytes": "long",
    "numChangesets": "integer",
    "numFiles": "integer"
}
```

---

### 2.4 `list-kx-databases`

Returns a list of all KX databases in the specified environment. **Paginated operation.**

**Synopsis:**
```bash
aws finspace list-kx-databases \
    --environment-id <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | **Yes** | string | -- | Environment ID |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Maximum results per page |

**Output Schema:**
```json
{
    "kxDatabases": [
        {
            "databaseName": "string",
            "createdTimestamp": "timestamp",
            "lastModifiedTimestamp": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 2.5 `update-kx-database`

Updates the configuration of a KX database.

**Synopsis:**
```bash
aws finspace update-kx-database \
    --environment-id <value> \
    --database-name <value> \
    --client-token <value> \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | **Yes** | string | -- | Environment ID |
| `--database-name` | **Yes** | string | -- | Database name |
| `--client-token` | **Yes** | string | -- | Idempotency token |
| `--description` | No | string | -- | New description |

**Output Schema:**
```json
{
    "databaseName": "string",
    "environmentId": "string",
    "description": "string",
    "lastModifiedTimestamp": "timestamp"
}
```
