# Actions & Resources

### 3.1 `get-action`

Returns details of a specific FIS action.

**Synopsis:**
```bash
aws fis get-action \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | ID of the action (e.g., `aws:ec2:stop-instances`) |

**Output Schema:**
```json
{
    "action": {
        "id": "string",
        "description": "string",
        "parameters": {
            "string": {
                "description": "string",
                "required": "boolean"
            }
        },
        "targets": {
            "string": {
                "resourceType": "string"
            }
        },
        "tags": {}
    }
}
```

---

### 3.2 `list-actions`

Lists all available FIS actions. **Paginated operation.**

**Synopsis:**
```bash
aws fis list-actions \
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
    "actions": [
        {
            "id": "string",
            "description": "string",
            "targets": {
                "string": {
                    "resourceType": "string"
                }
            },
            "tags": {}
        }
    ],
    "nextToken": "string"
}
```

---

### 3.3 `get-target-resource-type`

Returns details of a target resource type supported by FIS.

**Synopsis:**
```bash
aws fis get-target-resource-type \
    --resource-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-type` | **Yes** | string | -- | Resource type (e.g., `aws:ec2:instance`, `aws:ecs:task`, `aws:rds:db`) |

**Output Schema:**
```json
{
    "targetResourceType": {
        "resourceType": "string",
        "description": "string",
        "parameters": {
            "string": {
                "description": "string",
                "required": "boolean"
            }
        }
    }
}
```

---

### 3.4 `list-target-resource-types`

Lists all target resource types supported by FIS. **Paginated operation.**

**Synopsis:**
```bash
aws fis list-target-resource-types \
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
    "targetResourceTypes": [
        {
            "resourceType": "string",
            "description": "string"
        }
    ],
    "nextToken": "string"
}
```
