# Quick Connects

### 8.1 `create-quick-connect`

Creates a quick connect for the specified instance.

**Synopsis:**
```bash
aws connect create-quick-connect \
    --instance-id <value> \
    --name <value> \
    --quick-connect-config <value> \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--name` | **Yes** | string | -- | Quick connect name (1-127 chars) |
| `--quick-connect-config` | **Yes** | structure | -- | Configuration with type and type-specific config |
| `--description` | No | string | None | Description (1-250 chars) |
| `--tags` | No | map | None | Tags (max 50) |

**QuickConnectConfig:**
```json
{
    "QuickConnectType": "USER|QUEUE|PHONE_NUMBER|FLOW",
    "UserConfig": { "UserId": "string", "ContactFlowId": "string" },
    "QueueConfig": { "QueueId": "string", "ContactFlowId": "string" },
    "PhoneConfig": { "PhoneNumber": "string" },
    "FlowConfig": { "ContactFlowId": "string" }
}
```

**Output Schema:**
```json
{
    "QuickConnectARN": "string",
    "QuickConnectId": "string"
}
```

---

### 8.2 `describe-quick-connect`

Describes a quick connect.

**Synopsis:**
```bash
aws connect describe-quick-connect \
    --instance-id <value> \
    --quick-connect-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--quick-connect-id` | **Yes** | string | -- | Quick connect ID |

**Output Schema:**
```json
{
    "QuickConnect": {
        "QuickConnectARN": "string",
        "QuickConnectId": "string",
        "Name": "string",
        "Description": "string",
        "QuickConnectConfig": {},
        "Tags": { "key": "value" },
        "LastModifiedTime": "timestamp",
        "LastModifiedRegion": "string"
    }
}
```

---

### 8.3 `list-quick-connects`

Lists quick connects. **Paginated operation.**

**Synopsis:**
```bash
aws connect list-quick-connects \
    --instance-id <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--quick-connect-types <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-1000) |
| `--quick-connect-types` | No | list | None | Filter by types |

**Output Schema:**
```json
{
    "QuickConnectSummaryList": [ { "Id": "string", "Arn": "string", "Name": "string", "QuickConnectType": "USER|QUEUE|PHONE_NUMBER|FLOW", "LastModifiedTime": "timestamp", "LastModifiedRegion": "string" } ],
    "NextToken": "string"
}
```

---

### 8.4 `update-quick-connect-config`

Updates the quick connect configuration.

**Synopsis:**
```bash
aws connect update-quick-connect-config \
    --instance-id <value> \
    --quick-connect-id <value> \
    --quick-connect-config <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--quick-connect-id` | **Yes** | string | -- | Quick connect ID |
| `--quick-connect-config` | **Yes** | structure | -- | Updated config |

**Output:** None

---

### 8.5 `update-quick-connect-name`

Updates quick connect name and description.

**Synopsis:**
```bash
aws connect update-quick-connect-name \
    --instance-id <value> \
    --quick-connect-id <value> \
    [--name <value>] \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--quick-connect-id` | **Yes** | string | -- | Quick connect ID |
| `--name` | No | string | None | Updated name |
| `--description` | No | string | None | Updated description |

**Output:** None

---

### 8.6 `delete-quick-connect`

Deletes a quick connect.

**Synopsis:**
```bash
aws connect delete-quick-connect \
    --instance-id <value> \
    --quick-connect-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--quick-connect-id` | **Yes** | string | -- | Quick connect ID |

**Output:** None

---

### 8.7 `search-quick-connects`

Searches quick connects. **Paginated operation.**

**Synopsis:**
```bash
aws connect search-quick-connects \
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
    "QuickConnects": [ { "QuickConnectARN": "string", "QuickConnectId": "string", "Name": "string", "Description": "string", "QuickConnectConfig": {}, "Tags": {} } ],
    "NextToken": "string",
    "ApproximateTotalCount": "long"
}
```
