# Tags

### 5.1 `create-tags`

Creates tags for configuration items (servers, applications).

**Synopsis:**
```bash
aws discovery create-tags \
    --configuration-ids <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configuration-ids` | **Yes** | list(string) | -- | Configuration IDs to tag |
| `--tags` | **Yes** | list | -- | Tags to apply |

**Tags Structure (shorthand):**
```
key=string,value=string ...
```

**Output:** None on success.

---

### 5.2 `delete-tags`

Removes tags from configuration items.

**Synopsis:**
```bash
aws discovery delete-tags \
    --configuration-ids <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configuration-ids` | **Yes** | list(string) | -- | Configuration IDs to untag |
| `--tags` | No | list | None | Specific tags to remove (removes all tags if omitted) |

**Output:** None on success.

---

### 5.3 `describe-tags`

Lists tags for specified configuration items. **Paginated operation.**

**Synopsis:**
```bash
aws discovery describe-tags \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | list | None | Filter by configurationId, key, value, or configurationItemType |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Filter Structure (shorthand):**
```
name=string,values=string,string
```

**Output Schema:**
```json
{
    "tags": [
        {
            "configurationType": "SERVER|PROCESS|CONNECTION|APPLICATION",
            "configurationId": "string",
            "key": "string",
            "value": "string",
            "timeOfCreation": "timestamp"
        }
    ],
    "nextToken": "string"
}
```
