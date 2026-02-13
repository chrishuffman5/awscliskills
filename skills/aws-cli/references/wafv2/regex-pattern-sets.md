# Regex Pattern Sets

### 4.1 `create-regex-pattern-set`

Creates a regex pattern set. Provides a collection of regular expressions that you can reference in rules.

**Synopsis:**
```bash
aws wafv2 create-regex-pattern-set \
    --name <value> \
    --scope <value> \
    --regular-expression-list <value> \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the regex pattern set |
| `--scope` | **Yes** | string | -- | Scope: `REGIONAL` or `CLOUDFRONT` |
| `--regular-expression-list` | **Yes** | list | -- | Regex patterns. Shorthand: `RegexString=string ...` |
| `--description` | No | string | -- | Description |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "Summary": {
        "Name": "string",
        "Id": "string",
        "Description": "string",
        "LockToken": "string",
        "ARN": "string"
    }
}
```

---

### 4.2 `delete-regex-pattern-set`

Deletes a regex pattern set. Must not be referenced by any rule.

**Synopsis:**
```bash
aws wafv2 delete-regex-pattern-set \
    --name <value> \
    --scope <value> \
    --id <value> \
    --lock-token <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the regex pattern set |
| `--scope` | **Yes** | string | -- | Scope: `REGIONAL` or `CLOUDFRONT` |
| `--id` | **Yes** | string | -- | Unique ID |
| `--lock-token` | **Yes** | string | -- | Lock token from get operation |

**Output:** None on success.

---

### 4.3 `get-regex-pattern-set`

Retrieves a regex pattern set with full details.

**Synopsis:**
```bash
aws wafv2 get-regex-pattern-set \
    --name <value> \
    --scope <value> \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the regex pattern set |
| `--scope` | **Yes** | string | -- | Scope: `REGIONAL` or `CLOUDFRONT` |
| `--id` | **Yes** | string | -- | Unique ID |

**Output Schema:**
```json
{
    "RegexPatternSet": {
        "Name": "string",
        "Id": "string",
        "ARN": "string",
        "Description": "string",
        "RegularExpressionList": [
            {
                "RegexString": "string"
            }
        ]
    },
    "LockToken": "string"
}
```

---

### 4.4 `list-regex-pattern-sets`

Returns a list of regex pattern sets. **Paginated operation.**

**Synopsis:**
```bash
aws wafv2 list-regex-pattern-sets \
    --scope <value> \
    [--next-marker <value>] \
    [--limit <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--scope` | **Yes** | string | -- | Scope: `REGIONAL` or `CLOUDFRONT` |
| `--next-marker` | No | string | None | Pagination token |
| `--limit` | No | integer | None | Maximum results (1-100) |

**Output Schema:**
```json
{
    "NextMarker": "string",
    "RegexPatternSets": [
        {
            "Name": "string",
            "Id": "string",
            "Description": "string",
            "LockToken": "string",
            "ARN": "string"
        }
    ]
}
```

---

### 4.5 `update-regex-pattern-set`

Updates a regex pattern set. Replaces the entire set of patterns. Requires the current lock token.

**Synopsis:**
```bash
aws wafv2 update-regex-pattern-set \
    --name <value> \
    --scope <value> \
    --id <value> \
    --lock-token <value> \
    --regular-expression-list <value> \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the regex pattern set |
| `--scope` | **Yes** | string | -- | Scope: `REGIONAL` or `CLOUDFRONT` |
| `--id` | **Yes** | string | -- | Unique ID |
| `--lock-token` | **Yes** | string | -- | Lock token from get operation |
| `--regular-expression-list` | **Yes** | list | -- | New regex patterns (replaces all existing). Shorthand: `RegexString=string ...` |
| `--description` | No | string | -- | New description |

**Output Schema:**
```json
{
    "NextLockToken": "string"
}
```
