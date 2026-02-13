# Groups

### 4.1 `create-group`

Creates a group with a filter expression. Groups organize traces that match a filter expression into a named set.

**Synopsis:**
```bash
aws xray create-group \
    --group-name <value> \
    [--filter-expression <value>] \
    [--insights-configuration <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--group-name` | **Yes** | string | -- | Name of the group (1-32 chars) |
| `--filter-expression` | No | string | None | Filter expression (e.g., `service("my-service")`) |
| `--insights-configuration` | No | structure | None | Insights configuration. Shorthand: `InsightsEnabled=boolean,NotificationsEnabled=boolean` |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "Group": {
        "GroupName": "string",
        "GroupARN": "string",
        "FilterExpression": "string",
        "InsightsConfiguration": {
            "InsightsEnabled": "boolean",
            "NotificationsEnabled": "boolean"
        }
    }
}
```

---

### 4.2 `delete-group`

Deletes a group.

**Synopsis:**
```bash
aws xray delete-group \
    [--group-name <value>] \
    [--group-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--group-name` | No | string | None | Name of the group (specify either name or ARN) |
| `--group-arn` | No | string | None | ARN of the group |

**Output Schema:**
```json
{}
```

---

### 4.3 `get-group`

Returns details of a group.

**Synopsis:**
```bash
aws xray get-group \
    [--group-name <value>] \
    [--group-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--group-name` | No | string | None | Name of the group (specify either name or ARN) |
| `--group-arn` | No | string | None | ARN of the group |

**Output Schema:**
```json
{
    "Group": {
        "GroupName": "string",
        "GroupARN": "string",
        "FilterExpression": "string",
        "InsightsConfiguration": {
            "InsightsEnabled": "boolean",
            "NotificationsEnabled": "boolean"
        }
    }
}
```

---

### 4.4 `get-groups`

Returns a list of all active groups. **Paginated operation.**

**Synopsis:**
```bash
aws xray get-groups \
    [--starting-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "Groups": [
        {
            "GroupName": "string",
            "GroupARN": "string",
            "FilterExpression": "string",
            "InsightsConfiguration": {
                "InsightsEnabled": "boolean",
                "NotificationsEnabled": "boolean"
            }
        }
    ],
    "NextToken": "string"
}
```

---

### 4.5 `update-group`

Updates a group's filter expression or insights configuration.

**Synopsis:**
```bash
aws xray update-group \
    [--group-name <value>] \
    [--group-arn <value>] \
    [--filter-expression <value>] \
    [--insights-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--group-name` | No | string | None | Name of the group (specify either name or ARN) |
| `--group-arn` | No | string | None | ARN of the group |
| `--filter-expression` | No | string | None | Updated filter expression |
| `--insights-configuration` | No | structure | None | Updated insights configuration |

**Output Schema:**
```json
{
    "Group": {
        "GroupName": "string",
        "GroupARN": "string",
        "FilterExpression": "string",
        "InsightsConfiguration": {
            "InsightsEnabled": "boolean",
            "NotificationsEnabled": "boolean"
        }
    }
}
```
