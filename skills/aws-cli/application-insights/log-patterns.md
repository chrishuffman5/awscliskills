# Log Patterns

### 3.1 `create-log-pattern`

Creates a log pattern for a log pattern set.

**Synopsis:**
```bash
aws application-insights create-log-pattern \
    --resource-group-name <value> \
    --pattern-set-name <value> \
    --pattern-name <value> \
    --pattern <value> \
    --rank <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-group-name` | **Yes** | string | -- | Name of the resource group |
| `--pattern-set-name` | **Yes** | string | -- | Name of the log pattern set |
| `--pattern-name` | **Yes** | string | -- | Name of the log pattern |
| `--pattern` | **Yes** | string | -- | Regular expression pattern to match |
| `--rank` | **Yes** | integer | -- | Rank of the pattern (1=highest priority) |

**Output Schema:**
```json
{
    "LogPattern": {
        "PatternSetName": "string",
        "PatternName": "string",
        "Pattern": "string",
        "Rank": "integer"
    },
    "ResourceGroupName": "string"
}
```

---

### 3.2 `delete-log-pattern`

Removes the specified log pattern from a log pattern set.

**Synopsis:**
```bash
aws application-insights delete-log-pattern \
    --resource-group-name <value> \
    --pattern-set-name <value> \
    --pattern-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-group-name` | **Yes** | string | -- | Name of the resource group |
| `--pattern-set-name` | **Yes** | string | -- | Name of the log pattern set |
| `--pattern-name` | **Yes** | string | -- | Name of the log pattern |

**Output Schema:**
```json
{}
```

---

### 3.3 `describe-log-pattern`

Describes a specific log pattern.

**Synopsis:**
```bash
aws application-insights describe-log-pattern \
    --resource-group-name <value> \
    --pattern-set-name <value> \
    --pattern-name <value> \
    [--account-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-group-name` | **Yes** | string | -- | Name of the resource group |
| `--pattern-set-name` | **Yes** | string | -- | Name of the log pattern set |
| `--pattern-name` | **Yes** | string | -- | Name of the log pattern |
| `--account-id` | No | string | -- | AWS account ID |

**Output Schema:**
```json
{
    "ResourceGroupName": "string",
    "AccountId": "string",
    "LogPattern": {
        "PatternSetName": "string",
        "PatternName": "string",
        "Pattern": "string",
        "Rank": "integer"
    }
}
```

---

### 3.4 `list-log-patterns`

Lists the log patterns in a pattern set. **Paginated operation.**

**Synopsis:**
```bash
aws application-insights list-log-patterns \
    --resource-group-name <value> \
    [--pattern-set-name <value>] \
    [--account-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-group-name` | **Yes** | string | -- | Name of the resource group |
| `--pattern-set-name` | No | string | -- | Name of the log pattern set to filter by |
| `--account-id` | No | string | -- | AWS account ID |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "ResourceGroupName": "string",
    "AccountId": "string",
    "LogPatterns": [
        {
            "PatternSetName": "string",
            "PatternName": "string",
            "Pattern": "string",
            "Rank": "integer"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.5 `update-log-pattern`

Updates a log pattern.

**Synopsis:**
```bash
aws application-insights update-log-pattern \
    --resource-group-name <value> \
    --pattern-set-name <value> \
    --pattern-name <value> \
    [--pattern <value>] \
    [--rank <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-group-name` | **Yes** | string | -- | Name of the resource group |
| `--pattern-set-name` | **Yes** | string | -- | Name of the log pattern set |
| `--pattern-name` | **Yes** | string | -- | Name of the log pattern |
| `--pattern` | No | string | -- | New regular expression pattern |
| `--rank` | No | integer | -- | New rank |

**Output Schema:**
```json
{
    "ResourceGroupName": "string",
    "LogPattern": {
        "PatternSetName": "string",
        "PatternName": "string",
        "Pattern": "string",
        "Rank": "integer"
    }
}
```

---

### 3.6 `list-log-pattern-sets`

Lists the log pattern sets in an application. **Paginated operation.**

**Synopsis:**
```bash
aws application-insights list-log-pattern-sets \
    --resource-group-name <value> \
    [--account-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-group-name` | **Yes** | string | -- | Name of the resource group |
| `--account-id` | No | string | -- | AWS account ID |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "ResourceGroupName": "string",
    "AccountId": "string",
    "LogPatternSets": ["string"],
    "NextToken": "string"
}
```
