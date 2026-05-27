# Query Definitions

### 18.1 `put-query-definition`

Creates or updates a saved Logs Insights query definition.

**Synopsis:**
```bash
aws logs put-query-definition \
    --name <value> \
    --query-string <value> \
    [--query-definition-id <value>] \
    [--log-group-names <value>] \
    [--query-language <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Query definition name (1-255 chars). Use `/` for folders |
| `--query-string` | **Yes** | string | -- | Query string (1-10000 chars) |
| `--query-definition-id` | No | string | -- | ID to update existing definition |
| `--log-group-names` | No | list | -- | Associated log group names |
| `--query-language` | No | string | `CWLI` | `CWLI`, `SQL`, or `PPL` |

**Output Schema:**
```json
{
    "queryDefinitionId": "string"
}
```

---

### 18.2 `describe-query-definitions`

Lists saved query definitions. **Paginated.**

**Synopsis:**
```bash
aws logs describe-query-definitions \
    [--query-definition-name-prefix <value>] \
    [--max-results <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--query-definition-name-prefix` | No | string | -- | Name prefix filter (1-255 chars) |
| `--max-results` | No | integer | -- | Max results per API call (1-1000) |
| `--max-items` | No | integer | -- | Total items to return |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |

**Output Schema:**
```json
{
    "queryDefinitions": [
        {
            "queryDefinitionId": "string",
            "name": "string",
            "queryString": "string",
            "lastModified": long,
            "logGroupNames": ["string"]
        }
    ],
    "nextToken": "string"
}
```

---

### 18.3 `delete-query-definition`

Deletes a saved query definition.

**Synopsis:**
```bash
aws logs delete-query-definition \
    --query-definition-id <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--query-definition-id` | **Yes** | string | -- | Query definition ID |

**Output Schema:**
```json
{
    "success": true|false
}
```

---
