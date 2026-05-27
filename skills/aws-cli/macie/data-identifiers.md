# Data Identifiers

### 6.1 `create-custom-data-identifier`

Creates a custom data identifier using a regular expression.

**Synopsis:**
```bash
aws macie2 create-custom-data-identifier \
    --name <value> \
    --regex <value> \
    [--client-token <value>] \
    [--description <value>] \
    [--ignore-words <value>] \
    [--keywords <value>] \
    [--maximum-match-distance <value>] \
    [--severity-levels <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the data identifier |
| `--regex` | **Yes** | string | -- | Regular expression to match |
| `--client-token` | No | string | None | Idempotency token |
| `--description` | No | string | None | Description |
| `--ignore-words` | No | list(string) | None | Words to ignore in matches |
| `--keywords` | No | list(string) | None | Keywords that must be near the regex match |
| `--maximum-match-distance` | No | integer | None | Max chars between keyword and regex match |
| `--severity-levels` | No | list | None | Severity levels based on occurrence count |
| `--tags` | No | map | None | Tags to add |

**Severity Levels Structure:**
```json
[
    {
        "occurrencesThreshold": "long",
        "severity": "LOW|MEDIUM|HIGH"
    }
]
```

**Output Schema:**
```json
{
    "customDataIdentifierId": "string"
}
```

---

### 6.2 `delete-custom-data-identifier`

Soft-deletes a custom data identifier.

**Synopsis:**
```bash
aws macie2 delete-custom-data-identifier \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Custom data identifier ID to delete |

**Output:** None (HTTP 200 on success)

---

### 6.3 `get-custom-data-identifier`

Retrieves the criteria and settings for a custom data identifier.

**Synopsis:**
```bash
aws macie2 get-custom-data-identifier \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Custom data identifier ID |

**Output Schema:**
```json
{
    "arn": "string",
    "createdAt": "timestamp",
    "deleted": "boolean",
    "description": "string",
    "id": "string",
    "ignoreWords": ["string"],
    "keywords": ["string"],
    "maximumMatchDistance": "integer",
    "name": "string",
    "regex": "string",
    "severityLevels": [
        {
            "occurrencesThreshold": "long",
            "severity": "LOW|MEDIUM|HIGH"
        }
    ],
    "tags": {"string": "string"}
}
```

---

### 6.4 `list-custom-data-identifiers`

Retrieves a subset of information about all custom data identifiers. **Paginated operation.**

**Synopsis:**
```bash
aws macie2 list-custom-data-identifiers \
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
    "items": [
        {
            "arn": "string",
            "createdAt": "timestamp",
            "description": "string",
            "id": "string",
            "name": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 6.5 `batch-get-custom-data-identifiers`

Retrieves information about one or more custom data identifiers.

**Synopsis:**
```bash
aws macie2 batch-get-custom-data-identifiers \
    [--ids <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--ids` | No | list(string) | None | Custom data identifier IDs |

**Output Schema:**
```json
{
    "customDataIdentifiers": [
        {
            "arn": "string",
            "createdAt": "timestamp",
            "deleted": "boolean",
            "description": "string",
            "id": "string",
            "name": "string"
        }
    ],
    "notFoundIdentifierIds": ["string"]
}
```

---

### 6.6 `list-managed-data-identifiers`

Retrieves information about all managed data identifiers. **Paginated operation.**

**Synopsis:**
```bash
aws macie2 list-managed-data-identifiers \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "items": [
        {
            "category": "FINANCIAL_INFORMATION|PERSONAL_INFORMATION|CREDENTIALS|CUSTOM_IDENTIFIER",
            "id": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 6.7 `test-custom-data-identifier`

Tests a custom data identifier against sample text.

**Synopsis:**
```bash
aws macie2 test-custom-data-identifier \
    --regex <value> \
    --sample-text <value> \
    [--ignore-words <value>] \
    [--keywords <value>] \
    [--maximum-match-distance <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--regex` | **Yes** | string | -- | Regular expression to test |
| `--sample-text` | **Yes** | string | -- | Sample text to test against |
| `--ignore-words` | No | list(string) | None | Words to ignore |
| `--keywords` | No | list(string) | None | Keywords that must be near matches |
| `--maximum-match-distance` | No | integer | None | Max distance between keyword and match |

**Output Schema:**
```json
{
    "matchCount": "integer"
}
```
