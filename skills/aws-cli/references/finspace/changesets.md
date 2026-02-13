# Changesets

### 5.1 `create-kx-changeset`

Creates a changeset for a KX database. A changeset allows you to add and delete existing data in a database by loading data from an S3 bucket.

**Synopsis:**
```bash
aws finspace create-kx-changeset \
    --environment-id <value> \
    --database-name <value> \
    --change-requests <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | **Yes** | string | -- | Environment ID |
| `--database-name` | **Yes** | string | -- | Database name |
| `--change-requests` | **Yes** | list | -- | List of change requests (PUT or DELETE operations) |
| `--client-token` | No | string | Auto | Idempotency token |

**Change Request Structure:**
```json
[
    {
        "changeType": "PUT|DELETE",
        "s3Path": "string",
        "dbPath": "string"
    }
]
```

| Field | Description |
|-------|-------------|
| `changeType` | `PUT` to add/update data, `DELETE` to remove data |
| `s3Path` | S3 URI of the source data (for PUT) or empty (for DELETE) |
| `dbPath` | Database path where data is stored |

**Output Schema:**
```json
{
    "changesetId": "string",
    "databaseName": "string",
    "environmentId": "string",
    "changeRequests": [
        {
            "changeType": "PUT|DELETE",
            "s3Path": "string",
            "dbPath": "string"
        }
    ],
    "createdTimestamp": "timestamp",
    "lastModifiedTimestamp": "timestamp",
    "status": "PENDING|PROCESSING|FAILED|COMPLETED",
    "errorInfo": {
        "errorMessage": "string",
        "errorType": "string"
    }
}
```

---

### 5.2 `get-kx-changeset`

Returns information about a specific changeset for a database.

**Synopsis:**
```bash
aws finspace get-kx-changeset \
    --environment-id <value> \
    --database-name <value> \
    --changeset-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | **Yes** | string | -- | Environment ID |
| `--database-name` | **Yes** | string | -- | Database name |
| `--changeset-id` | **Yes** | string | -- | Changeset ID |

**Output Schema:**
```json
{
    "changesetId": "string",
    "databaseName": "string",
    "environmentId": "string",
    "changeRequests": [
        {
            "changeType": "PUT|DELETE",
            "s3Path": "string",
            "dbPath": "string"
        }
    ],
    "createdTimestamp": "timestamp",
    "activeFromTimestamp": "timestamp",
    "lastModifiedTimestamp": "timestamp",
    "status": "PENDING|PROCESSING|FAILED|COMPLETED",
    "errorInfo": {
        "errorMessage": "string",
        "errorType": "string"
    }
}
```

---

### 5.3 `list-kx-changesets`

Returns a list of all changesets for a specified database. **Paginated operation.**

**Synopsis:**
```bash
aws finspace list-kx-changesets \
    --environment-id <value> \
    --database-name <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-id` | **Yes** | string | -- | Environment ID |
| `--database-name` | **Yes** | string | -- | Database name |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Maximum results per page |

**Output Schema:**
```json
{
    "kxChangesets": [
        {
            "changesetId": "string",
            "createdTimestamp": "timestamp",
            "activeFromTimestamp": "timestamp",
            "lastModifiedTimestamp": "timestamp",
            "status": "PENDING|PROCESSING|FAILED|COMPLETED"
        }
    ],
    "nextToken": "string"
}
```
