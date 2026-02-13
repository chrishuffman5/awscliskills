# Transactions

### 6.1 `start-transaction`

Starts a new governed transaction for use with governed tables.

**Synopsis:**
```bash
aws lakeformation start-transaction \
    [--transaction-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--transaction-type` | No | string | `READ_AND_WRITE` | Transaction type: `READ_AND_WRITE` or `READ_ONLY` |

**Output Schema:**
```json
{
    "TransactionId": "string"
}
```

---

### 6.2 `commit-transaction`

Commits a governed transaction. The transaction must be active.

**Synopsis:**
```bash
aws lakeformation commit-transaction \
    --transaction-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--transaction-id` | **Yes** | string | -- | Transaction ID to commit |

**Output Schema:**
```json
{
    "TransactionStatus": "ACTIVE|COMMITTED|ABORTED|COMMIT_IN_PROGRESS"
}
```

---

### 6.3 `cancel-transaction`

Cancels (aborts) a governed transaction.

**Synopsis:**
```bash
aws lakeformation cancel-transaction \
    --transaction-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--transaction-id` | **Yes** | string | -- | Transaction ID to cancel |

**Output:** None

---

### 6.4 `describe-transaction`

Describes a transaction.

**Synopsis:**
```bash
aws lakeformation describe-transaction \
    --transaction-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--transaction-id` | **Yes** | string | -- | Transaction ID |

**Output Schema:**
```json
{
    "TransactionDescription": {
        "TransactionId": "string",
        "TransactionStatus": "ACTIVE|COMMITTED|ABORTED|COMMIT_IN_PROGRESS",
        "TransactionStartTime": "timestamp",
        "TransactionEndTime": "timestamp"
    }
}
```

---

### 6.5 `extend-transaction`

Extends the heartbeat of a transaction to prevent it from timing out.

**Synopsis:**
```bash
aws lakeformation extend-transaction \
    [--transaction-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--transaction-id` | No | string | None | Transaction ID to extend |

**Output:** None

---

### 6.6 `list-transactions`

Lists transactions. **Paginated operation.**

**Synopsis:**
```bash
aws lakeformation list-transactions \
    [--catalog-id <value>] \
    [--status-filter <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--catalog-id` | No | string | account ID | Data Catalog identifier |
| `--status-filter` | No | string | None | Filter: `ALL`, `ACTIVE`, `COMMITTED`, `ABORTED`, `COMPLETED` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items |

**Output Schema:**
```json
{
    "Transactions": [
        {
            "TransactionId": "string",
            "TransactionStatus": "ACTIVE|COMMITTED|ABORTED|COMMIT_IN_PROGRESS",
            "TransactionStartTime": "timestamp",
            "TransactionEndTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 6.7 `get-table-objects`

Returns the set of S3 objects that make up a governed table. **Paginated operation.**

**Synopsis:**
```bash
aws lakeformation get-table-objects \
    --database-name <value> \
    --table-name <value> \
    [--catalog-id <value>] \
    [--transaction-id <value>] \
    [--query-as-of-time <value>] \
    [--partition-predicate <value>] \
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
| `--catalog-id` | No | string | account ID | Catalog identifier |
| `--transaction-id` | No | string | None | Transaction ID for snapshot isolation |
| `--query-as-of-time` | No | timestamp | None | Point-in-time query |
| `--partition-predicate` | No | string | None | Filter by partition values |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items |

**Output Schema:**
```json
{
    "Objects": [
        {
            "PartitionValues": ["string"],
            "Objects": [
                {
                    "Uri": "string",
                    "ETag": "string",
                    "Size": "long"
                }
            ]
        }
    ],
    "NextToken": "string"
}
```

---

### 6.8 `update-table-objects`

Updates governed table objects by adding or deleting objects within a transaction.

**Synopsis:**
```bash
aws lakeformation update-table-objects \
    --database-name <value> \
    --table-name <value> \
    --write-operations <value> \
    [--catalog-id <value>] \
    [--transaction-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database-name` | **Yes** | string | -- | Database name |
| `--table-name` | **Yes** | string | -- | Table name |
| `--write-operations` | **Yes** | list | -- | List of add/delete operations |
| `--catalog-id` | No | string | account ID | Catalog identifier |
| `--transaction-id` | No | string | None | Transaction ID |

**Write Operations Structure:**
```json
[
    {
        "AddObject": {
            "Uri": "string",
            "ETag": "string",
            "Size": "long",
            "PartitionValues": ["string"]
        },
        "DeleteObject": {
            "Uri": "string",
            "ETag": "string",
            "PartitionValues": ["string"]
        }
    }
]
```

**Output:** None

---

### 6.9 `delete-objects-on-cancel`

Specifies S3 objects to delete if a transaction is cancelled.

**Synopsis:**
```bash
aws lakeformation delete-objects-on-cancel \
    --database-name <value> \
    --table-name <value> \
    --transaction-id <value> \
    --objects <value> \
    [--catalog-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--database-name` | **Yes** | string | -- | Database name |
| `--table-name` | **Yes** | string | -- | Table name |
| `--transaction-id` | **Yes** | string | -- | Transaction ID |
| `--objects` | **Yes** | list | -- | S3 objects to delete on cancel |
| `--catalog-id` | No | string | account ID | Catalog identifier |

**Objects Structure:**
```json
[
    {
        "Uri": "string",
        "ETag": "string"
    }
]
```

**Output:** None
