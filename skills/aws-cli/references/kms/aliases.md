# Aliases

### 4.1 `create-alias`

Creates a friendly name (alias) for a KMS key.

**Synopsis:**
```bash
aws kms create-alias \
    --alias-name <value> \
    --target-key-id <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--alias-name` | **Yes** | string | -- | Must start with `alias/`. Cannot start with `alias/aws/` (reserved). 1-256 chars, pattern: `^[a-zA-Z0-9:/_-]+$` |
| `--target-key-id` | **Yes** | string | -- | Key ID or key ARN of the target key (1-2048 chars) |

**Output:** None

---

### 4.2 `delete-alias`

Deletes an alias. Does not delete the underlying key.

**Synopsis:**
```bash
aws kms delete-alias --alias-name <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--alias-name` | **Yes** | string | -- | Alias name to delete (1-256 chars) |

**Output:** None

---

### 4.3 `list-aliases`

Lists all aliases in the account. **Paginated.**

**Synopsis:**
```bash
aws kms list-aliases \
    [--key-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-id` | No | string | all aliases | Filter by key ID or key ARN (1-2048 chars) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Aliases": [
        {
            "AliasName": "string",
            "AliasArn": "string",
            "TargetKeyId": "string",
            "CreationDate": "timestamp",
            "LastUpdatedDate": "timestamp"
        }
    ],
    "NextMarker": "string",
    "Truncated": true|false
}
```

---

### 4.4 `update-alias`

Changes the KMS key that an alias points to.

**Synopsis:**
```bash
aws kms update-alias \
    --alias-name <value> \
    --target-key-id <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--alias-name` | **Yes** | string | -- | Alias name to update (1-256 chars) |
| `--target-key-id` | **Yes** | string | -- | New target key ID or key ARN (1-2048 chars) |

**Output:** None

---
