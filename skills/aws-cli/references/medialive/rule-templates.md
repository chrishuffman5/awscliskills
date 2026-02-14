# EventBridge Rule Templates

### 13.1 `create-event-bridge-rule-template`

Creates an EventBridge rule template for automated event handling.

**Synopsis:**
```bash
aws medialive create-event-bridge-rule-template \
    --event-type <value> \
    --group-identifier <value> \
    --name <value> \
    [--description <value>] \
    [--event-targets <value>] \
    [--tags <value>] \
    [--request-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--event-type` | **Yes** | string | -- | `MEDIALIVE_MULTIPLEX_ALERT`, `MEDIALIVE_MULTIPLEX_STATE_CHANGE`, `MEDIALIVE_CHANNEL_ALERT`, `MEDIALIVE_CHANNEL_INPUT_CHANGE`, `MEDIALIVE_CHANNEL_STATE_CHANGE`, `MEDIAPACKAGE_INPUT_NOTIFICATION`, `MEDIAPACKAGE_KEY_PROVIDER_NOTIFICATION`, `MEDIAPACKAGE_HARVEST_JOB_NOTIFICATION`, `SIGNAL_MAP_ACTIVE_ALARM`, `MEDIACONNECT_ALERT`, `MEDIACONNECT_SOURCE_HEALTH`, `MEDIACONNECT_OUTPUT_HEALTH`, `MEDIACONNECT_FLOW_STATUS_CHANGE` |
| `--group-identifier` | **Yes** | string | -- | Rule template group ID or name |
| `--name` | **Yes** | string | -- | Template name (unique per region) |
| `--description` | No | string | None | Description |
| `--event-targets` | No | list | None | Event targets (SNS topic ARNs) |
| `--tags` | No | map | None | Key-value tag pairs |
| `--request-id` | No | string | Auto | Idempotency token |

**EventTargets:**
```json
[{"Arn": "arn:aws:sns:us-east-1:123456789012:my-topic"}]
```

**Output Schema:**
```json
{
    "Arn": "string",
    "Id": "string",
    "Name": "string",
    "GroupId": "string",
    "EventType": "string",
    "EventTargets": [{"Arn": "string"}],
    "Description": "string",
    "CreatedAt": "timestamp",
    "ModifiedAt": "timestamp",
    "Tags": {}
}
```

---

### 13.2 `get-event-bridge-rule-template`

Gets an EventBridge rule template.

**Synopsis:**
```bash
aws medialive get-event-bridge-rule-template \
    --identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identifier` | **Yes** | string | -- | Template ID |

**Output Schema:** Same as `create-event-bridge-rule-template` output.

---

### 13.3 `update-event-bridge-rule-template`

Updates an EventBridge rule template.

**Synopsis:**
```bash
aws medialive update-event-bridge-rule-template \
    --identifier <value> \
    [--description <value>] \
    [--event-targets <value>] \
    [--event-type <value>] \
    [--group-identifier <value>] \
    [--name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identifier` | **Yes** | string | -- | Template ID to update |
| `--description` | No | string | None | Updated description |
| `--event-targets` | No | list | None | Updated targets |
| `--event-type` | No | string | None | Updated event type |
| `--group-identifier` | No | string | None | Updated group |
| `--name` | No | string | None | Updated name |

**Output Schema:** Same as `create-event-bridge-rule-template` output.

---

### 13.4 `delete-event-bridge-rule-template`

Deletes an EventBridge rule template.

**Synopsis:**
```bash
aws medialive delete-event-bridge-rule-template \
    --identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identifier` | **Yes** | string | -- | Template ID to delete |

**Output:** None

---

### 13.5 `list-event-bridge-rule-templates`

Lists EventBridge rule templates. **Paginated operation.**

**Synopsis:**
```bash
aws medialive list-event-bridge-rule-templates \
    [--group-identifier <value>] \
    [--signal-map-identifier <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--group-identifier` | No | string | None | Filter by group |
| `--signal-map-identifier` | No | string | None | Filter by signal map |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "NextToken": "string",
    "EventBridgeRuleTemplates": [
        {
            "Arn": "string",
            "Id": "string",
            "Name": "string",
            "GroupId": "string",
            "EventType": "string",
            "Description": "string",
            "CreatedAt": "timestamp",
            "ModifiedAt": "timestamp",
            "Tags": {}
        }
    ]
}
```

---

### 13.6 `create-event-bridge-rule-template-group`

Creates a group for organizing EventBridge rule templates.

**Synopsis:**
```bash
aws medialive create-event-bridge-rule-template-group \
    --name <value> \
    [--description <value>] \
    [--tags <value>] \
    [--request-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Group name (unique per region) |
| `--description` | No | string | None | Description |
| `--tags` | No | map | None | Key-value tag pairs |
| `--request-id` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "Arn": "string",
    "Id": "string",
    "Name": "string",
    "Description": "string",
    "TemplateCount": "integer",
    "CreatedAt": "timestamp",
    "ModifiedAt": "timestamp",
    "Tags": {}
}
```

---

### 13.7 `get-event-bridge-rule-template-group`

Gets an EventBridge rule template group.

**Synopsis:**
```bash
aws medialive get-event-bridge-rule-template-group \
    --identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identifier` | **Yes** | string | -- | Group ID |

**Output Schema:** Same as `create-event-bridge-rule-template-group` output.

---

### 13.8 `update-event-bridge-rule-template-group`

Updates an EventBridge rule template group.

**Synopsis:**
```bash
aws medialive update-event-bridge-rule-template-group \
    --identifier <value> \
    [--description <value>] \
    [--name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identifier` | **Yes** | string | -- | Group ID |
| `--description` | No | string | None | Updated description |
| `--name` | No | string | None | Updated name |

**Output Schema:** Same as `create-event-bridge-rule-template-group` output.

---

### 13.9 `delete-event-bridge-rule-template-group`

Deletes an EventBridge rule template group.

**Synopsis:**
```bash
aws medialive delete-event-bridge-rule-template-group \
    --identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identifier` | **Yes** | string | -- | Group ID to delete |

**Output:** None

---

### 13.10 `list-event-bridge-rule-template-groups`

Lists EventBridge rule template groups. **Paginated operation.**

**Synopsis:**
```bash
aws medialive list-event-bridge-rule-template-groups \
    [--signal-map-identifier <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--signal-map-identifier` | No | string | None | Filter by signal map |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "NextToken": "string",
    "EventBridgeRuleTemplateGroups": [
        {
            "Arn": "string",
            "Id": "string",
            "Name": "string",
            "Description": "string",
            "TemplateCount": "integer",
            "CreatedAt": "timestamp",
            "ModifiedAt": "timestamp",
            "Tags": {}
        }
    ]
}
```
