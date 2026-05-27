# Agent Status

### 10.1 `create-agent-status`

Creates an agent status for the specified instance.

**Synopsis:**
```bash
aws connect create-agent-status \
    --instance-id <value> \
    --name <value> \
    --state <value> \
    [--description <value>] \
    [--display-order <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--name` | **Yes** | string | -- | Status name (1-127 chars) |
| `--state` | **Yes** | string | -- | `ENABLED` or `DISABLED` |
| `--description` | No | string | None | Description (1-250 chars) |
| `--display-order` | No | integer | None | Display order (1-50) |
| `--tags` | No | map | None | Tags |

**Output Schema:**
```json
{
    "AgentStatusARN": "string",
    "AgentStatusId": "string"
}
```

---

### 10.2 `describe-agent-status`

Describes an agent status.

**Synopsis:**
```bash
aws connect describe-agent-status \
    --instance-id <value> \
    --agent-status-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--agent-status-id` | **Yes** | string | -- | Agent status ID |

**Output Schema:**
```json
{
    "AgentStatus": {
        "AgentStatusARN": "string",
        "AgentStatusId": "string",
        "Name": "string",
        "Description": "string",
        "Type": "ROUTABLE|CUSTOM|OFFLINE",
        "DisplayOrder": "integer",
        "State": "ENABLED|DISABLED",
        "Tags": { "key": "value" },
        "LastModifiedTime": "timestamp",
        "LastModifiedRegion": "string"
    }
}
```

---

### 10.3 `list-agent-statuses`

Lists agent statuses. **Paginated operation.**

**Synopsis:**
```bash
aws connect list-agent-statuses \
    --instance-id <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--agent-status-types <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-1000) |
| `--agent-status-types` | No | list | None | Filter: `ROUTABLE`, `CUSTOM`, `OFFLINE` |

**Output Schema:**
```json
{
    "AgentStatusSummaryList": [ { "Id": "string", "Arn": "string", "Name": "string", "Type": "string", "LastModifiedTime": "timestamp", "LastModifiedRegion": "string" } ],
    "NextToken": "string"
}
```

---

### 10.4 `update-agent-status`

Updates an agent status.

**Synopsis:**
```bash
aws connect update-agent-status \
    --instance-id <value> \
    --agent-status-id <value> \
    [--name <value>] \
    [--description <value>] \
    [--state <value>] \
    [--display-order <value>] \
    [--reset-order-number | --no-reset-order-number] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--agent-status-id` | **Yes** | string | -- | Agent status ID |
| `--name` | No | string | None | Updated name |
| `--description` | No | string | None | Updated description |
| `--state` | No | string | None | `ENABLED` or `DISABLED` |
| `--display-order` | No | integer | None | Updated display order |
| `--reset-order-number` | No | boolean | None | Reset display order |

**Output:** None

---

### 10.5 `search-agent-statuses`

Searches agent statuses. **Paginated operation.**

**Synopsis:**
```bash
aws connect search-agent-statuses \
    --instance-id <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--search-filter <value>] \
    [--search-criteria <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-100) |
| `--search-filter` | No | structure | None | Tag filter |
| `--search-criteria` | No | structure | None | Search criteria |

**Output Schema:**
```json
{
    "AgentStatuses": [ { "AgentStatusARN": "string", "AgentStatusId": "string", "Name": "string", "Description": "string", "Type": "string", "DisplayOrder": "integer", "State": "string", "Tags": {} } ],
    "NextToken": "string",
    "ApproximateTotalCount": "long"
}
```
