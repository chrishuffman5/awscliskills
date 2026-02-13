# Findings Filters

### 4.1 `create-findings-filter`

Creates and defines the criteria for a findings filter.

**Synopsis:**
```bash
aws macie2 create-findings-filter \
    --action <value> \
    --finding-criteria <value> \
    --name <value> \
    [--client-token <value>] \
    [--description <value>] \
    [--position <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--action` | **Yes** | string | -- | Action: `ARCHIVE` or `NOOP` |
| `--finding-criteria` | **Yes** | structure | -- | Criteria for the filter |
| `--name` | **Yes** | string | -- | Filter name |
| `--client-token` | No | string | None | Idempotency token |
| `--description` | No | string | None | Filter description |
| `--position` | No | integer | None | Filter position in the list |
| `--tags` | No | map | None | Tags to add |

**Output Schema:**
```json
{
    "arn": "string",
    "id": "string"
}
```

---

### 4.2 `delete-findings-filter`

Deletes a findings filter.

**Synopsis:**
```bash
aws macie2 delete-findings-filter \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Filter ID to delete |

**Output:** None (HTTP 200 on success)

---

### 4.3 `get-findings-filter`

Retrieves the criteria and other settings for a findings filter.

**Synopsis:**
```bash
aws macie2 get-findings-filter \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Filter ID to retrieve |

**Output Schema:**
```json
{
    "action": "ARCHIVE|NOOP",
    "arn": "string",
    "description": "string",
    "findingCriteria": {
        "criterion": {
            "string": {
                "eq": ["string"],
                "neq": ["string"],
                "gt": "long",
                "gte": "long",
                "lt": "long",
                "lte": "long"
            }
        }
    },
    "id": "string",
    "name": "string",
    "position": "integer",
    "tags": {"string": "string"}
}
```

---

### 4.4 `list-findings-filters`

Retrieves a subset of information about all findings filters. **Paginated operation.**

**Synopsis:**
```bash
aws macie2 list-findings-filters \
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
    "findingsFilterListItems": [
        {
            "action": "ARCHIVE|NOOP",
            "arn": "string",
            "id": "string",
            "name": "string",
            "tags": {"string": "string"}
        }
    ],
    "nextToken": "string"
}
```

---

### 4.5 `update-findings-filter`

Updates the criteria and other settings for a findings filter.

**Synopsis:**
```bash
aws macie2 update-findings-filter \
    --id <value> \
    [--action <value>] \
    [--description <value>] \
    [--finding-criteria <value>] \
    [--name <value>] \
    [--position <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Filter ID to update |
| `--action` | No | string | None | New action |
| `--description` | No | string | None | New description |
| `--finding-criteria` | No | structure | None | New criteria |
| `--name` | No | string | None | New name |
| `--position` | No | integer | None | New position |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "arn": "string",
    "id": "string"
}
```

---

### 4.6 `get-findings-publication-configuration`

Retrieves the configuration settings for publishing findings to Security Hub.

**Synopsis:**
```bash
aws macie2 get-findings-publication-configuration \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output Schema:**
```json
{
    "securityHubConfiguration": {
        "publishClassificationFindings": "boolean",
        "publishPolicyFindings": "boolean"
    }
}
```

---

### 4.7 `put-findings-publication-configuration`

Updates the configuration settings for publishing findings to Security Hub.

**Synopsis:**
```bash
aws macie2 put-findings-publication-configuration \
    [--client-token <value>] \
    [--security-hub-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--client-token` | No | string | None | Idempotency token |
| `--security-hub-configuration` | No | structure | None | Security Hub publication settings |

**Security Hub Configuration Structure:**
```json
{
    "publishClassificationFindings": "boolean",
    "publishPolicyFindings": "boolean"
}
```

**Output:** None (HTTP 200 on success)
