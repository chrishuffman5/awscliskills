# Archive Rules

### 3.1 `create-archive-rule`

Creates an archive rule that automatically archives findings matching defined criteria.

**Synopsis:**
```bash
aws accessanalyzer create-archive-rule \
    --analyzer-name <value> \
    --rule-name <value> \
    --filter <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--analyzer-name` | **Yes** | string | -- | The name of the analyzer (1-255 chars, pattern: `[A-Za-z][A-Za-z0-9_.-]*`) |
| `--rule-name` | **Yes** | string | -- | The name of the archive rule (1-255 chars, pattern: `[A-Za-z][A-Za-z0-9_.-]*`) |
| `--filter` | **Yes** | map | -- | Filter criteria with `eq`, `neq`, `contains`, `exists` operators |
| `--client-token` | No | string | None | Client token for idempotency |

**Filter Structure:**
```json
{
    "string": {
        "eq": ["string"],
        "neq": ["string"],
        "contains": ["string"],
        "exists": true|false
    }
}
```

**Output:** None

---

### 3.2 `get-archive-rule`

Retrieves information about an archive rule.

**Synopsis:**
```bash
aws accessanalyzer get-archive-rule \
    --analyzer-name <value> \
    --rule-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--analyzer-name` | **Yes** | string | -- | The name of the analyzer |
| `--rule-name` | **Yes** | string | -- | The name of the archive rule |

**Output Schema:**
```json
{
    "archiveRule": {
        "ruleName": "string",
        "filter": {
            "string": {
                "eq": ["string"],
                "neq": ["string"],
                "contains": ["string"],
                "exists": "boolean"
            }
        },
        "createdAt": "timestamp",
        "updatedAt": "timestamp"
    }
}
```

---

### 3.3 `list-archive-rules`

Lists all archive rules for the specified analyzer. **Paginated operation.**

**Synopsis:**
```bash
aws accessanalyzer list-archive-rules \
    --analyzer-name <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--analyzer-name` | **Yes** | string | -- | The name of the analyzer |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "archiveRules": [
        {
            "ruleName": "string",
            "filter": {
                "string": {
                    "eq": ["string"],
                    "neq": ["string"],
                    "contains": ["string"],
                    "exists": "boolean"
                }
            },
            "createdAt": "timestamp",
            "updatedAt": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 3.4 `update-archive-rule`

Updates the criteria and values for the specified archive rule.

**Synopsis:**
```bash
aws accessanalyzer update-archive-rule \
    --analyzer-name <value> \
    --rule-name <value> \
    --filter <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--analyzer-name` | **Yes** | string | -- | The name of the analyzer |
| `--rule-name` | **Yes** | string | -- | The name of the archive rule to update |
| `--filter` | **Yes** | map | -- | Updated filter criteria |
| `--client-token` | No | string | None | Client token for idempotency |

**Output:** None

---

### 3.5 `delete-archive-rule`

Deletes an archive rule.

**Synopsis:**
```bash
aws accessanalyzer delete-archive-rule \
    --analyzer-name <value> \
    --rule-name <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--analyzer-name` | **Yes** | string | -- | The name of the analyzer |
| `--rule-name` | **Yes** | string | -- | The name of the archive rule to delete |
| `--client-token` | No | string | None | Client token for idempotency |

**Output:** None

---

### 3.6 `apply-archive-rule`

Retroactively applies the archive rule to existing findings that match the rule criteria.

**Synopsis:**
```bash
aws accessanalyzer apply-archive-rule \
    --analyzer-arn <value> \
    --rule-name <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--analyzer-arn` | **Yes** | string | -- | The ARN of the analyzer |
| `--rule-name` | **Yes** | string | -- | The name of the archive rule to apply |
| `--client-token` | No | string | None | Client token for idempotency |

**Output:** None
