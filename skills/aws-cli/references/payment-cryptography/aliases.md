# Aliases

### 3.1 `create-alias`

Creates a friendly alias for a key. Aliases must begin with `alias/`.

**Synopsis:**
```bash
aws payment-cryptography create-alias \
    --alias-name <value> \
    [--key-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--alias-name` | **Yes** | string | -- | Alias name (7-256 chars, pattern: `alias/[a-zA-Z0-9/_-]+`) |
| `--key-arn` | No | string | None | KeyARN to associate with the alias |

**Output Schema:**
```json
{
    "Alias": {
        "AliasName": "string",
        "KeyArn": "string"
    }
}
```

---

### 3.2 `delete-alias`

Deletes a key alias. Does not affect the underlying key.

**Synopsis:**
```bash
aws payment-cryptography delete-alias \
    --alias-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--alias-name` | **Yes** | string | -- | Alias name to delete (pattern: `alias/[a-zA-Z0-9/_-]+`) |

**Output Schema:**

None (no output on success).

---

### 3.3 `get-alias`

Retrieves details about a key alias.

**Synopsis:**
```bash
aws payment-cryptography get-alias \
    --alias-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--alias-name` | **Yes** | string | -- | Alias name to look up (pattern: `alias/[a-zA-Z0-9/_-]+`) |

**Output Schema:**
```json
{
    "Alias": {
        "AliasName": "string",
        "KeyArn": "string"
    }
}
```

---

### 3.4 `list-aliases`

Lists all aliases in the account. **Paginated operation.**

**Synopsis:**
```bash
aws payment-cryptography list-aliases \
    [--key-arn <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-arn` | No | string | None | Filter aliases by key ARN |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Aliases": [
        {
            "AliasName": "string",
            "KeyArn": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.5 `update-alias`

Updates the key associated with an alias, or removes the key association.

**Synopsis:**
```bash
aws payment-cryptography update-alias \
    --alias-name <value> \
    [--key-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--alias-name` | **Yes** | string | -- | Alias name to update |
| `--key-arn` | No | string | None | New KeyARN to associate (omit to remove association) |

**Output Schema:**
```json
{
    "Alias": {
        "AliasName": "string",
        "KeyArn": "string"
    }
}
```
