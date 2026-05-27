# Channels

### 2.1 `create-channel`

Creates a channel within a channel group for live content ingest.

**Synopsis:**
```bash
aws mediapackagev2 create-channel \
    --channel-group-name <value> \
    --channel-name <value> \
    [--client-token <value>] \
    [--input-type <value>] \
    [--description <value>] \
    [--input-switch-configuration <value>] \
    [--output-header-configuration <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-group-name` | **Yes** | string | -- | Name of the channel group (1-256 chars) |
| `--channel-name` | **Yes** | string | -- | Unique channel name (1-256 chars, `[a-zA-Z0-9_-]+`) |
| `--client-token` | No | string | Auto | Idempotency token |
| `--input-type` | No | string | `HLS` | Input format: `HLS` or `CMAF` |
| `--description` | No | string | None | Descriptive text (0-1024 chars) |
| `--input-switch-configuration` | No | structure | None | MQCS input switching config (CMAF only) |
| `--output-header-configuration` | No | structure | None | CMSD headers config (CMAF only) |
| `--tags` | No | map | None | Key-value tag pairs |

**InputSwitchConfiguration:**
```json
{
    "MQCSInputSwitching": true,
    "PreferredInput": 1
}
```

**OutputHeaderConfiguration:**
```json
{
    "PublishMQCS": true
}
```

**Output Schema:**
```json
{
    "Arn": "string",
    "ChannelName": "string",
    "ChannelGroupName": "string",
    "CreatedAt": "timestamp",
    "ModifiedAt": "timestamp",
    "Description": "string",
    "IngestEndpoints": [
        {
            "Id": "string",
            "Url": "string"
        }
    ],
    "InputType": "HLS|CMAF",
    "ETag": "string",
    "Tags": {"string": "string"},
    "InputSwitchConfiguration": {
        "MQCSInputSwitching": "boolean",
        "PreferredInput": "integer"
    },
    "OutputHeaderConfiguration": {
        "PublishMQCS": "boolean"
    }
}
```

---

### 2.2 `get-channel`

Retrieves details for a channel including ingest endpoints.

**Synopsis:**
```bash
aws mediapackagev2 get-channel \
    --channel-group-name <value> \
    --channel-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-group-name` | **Yes** | string | -- | Name of the channel group |
| `--channel-name` | **Yes** | string | -- | Name of the channel |

**Output Schema:**
```json
{
    "Arn": "string",
    "ChannelName": "string",
    "ChannelGroupName": "string",
    "CreatedAt": "timestamp",
    "ModifiedAt": "timestamp",
    "ResetAt": "timestamp",
    "Description": "string",
    "IngestEndpoints": [
        {
            "Id": "string",
            "Url": "string"
        }
    ],
    "InputType": "HLS|CMAF",
    "ETag": "string",
    "Tags": {"string": "string"},
    "InputSwitchConfiguration": {
        "MQCSInputSwitching": "boolean",
        "PreferredInput": "integer"
    },
    "OutputHeaderConfiguration": {
        "PublishMQCS": "boolean"
    }
}
```

---

### 2.3 `list-channels`

Lists all channels in a channel group. **Paginated operation.**

**Synopsis:**
```bash
aws mediapackagev2 list-channels \
    --channel-group-name <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-group-name` | **Yes** | string | -- | Name of the channel group |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Number of items per API call |
| `--max-items` | No | integer | None | Total number of items to return |

**Output Schema:**
```json
{
    "Items": [
        {
            "Arn": "string",
            "ChannelName": "string",
            "ChannelGroupName": "string",
            "CreatedAt": "timestamp",
            "ModifiedAt": "timestamp",
            "Description": "string",
            "InputType": "HLS|CMAF"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.4 `update-channel`

Updates a channel's configuration.

**Synopsis:**
```bash
aws mediapackagev2 update-channel \
    --channel-group-name <value> \
    --channel-name <value> \
    [--e-tag <value>] \
    [--description <value>] \
    [--input-switch-configuration <value>] \
    [--output-header-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-group-name` | **Yes** | string | -- | Name of the channel group |
| `--channel-name` | **Yes** | string | -- | Name of the channel |
| `--e-tag` | No | string | None | Expected ETag for concurrent update safety |
| `--description` | No | string | None | Updated description (0-1024 chars) |
| `--input-switch-configuration` | No | structure | None | Updated input switch config |
| `--output-header-configuration` | No | structure | None | Updated output header config |

**Output Schema:**
```json
{
    "Arn": "string",
    "ChannelName": "string",
    "ChannelGroupName": "string",
    "CreatedAt": "timestamp",
    "ModifiedAt": "timestamp",
    "Description": "string",
    "IngestEndpoints": [
        {"Id": "string", "Url": "string"}
    ],
    "InputType": "HLS|CMAF",
    "ETag": "string",
    "Tags": {"string": "string"},
    "InputSwitchConfiguration": {
        "MQCSInputSwitching": "boolean",
        "PreferredInput": "integer"
    },
    "OutputHeaderConfiguration": {
        "PublishMQCS": "boolean"
    }
}
```

---

### 2.5 `delete-channel`

Deletes a channel. All origin endpoints must be deleted first.

**Synopsis:**
```bash
aws mediapackagev2 delete-channel \
    --channel-group-name <value> \
    --channel-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-group-name` | **Yes** | string | -- | Name of the channel group |
| `--channel-name` | **Yes** | string | -- | Name of the channel to delete |

**Output:** None

---

### 2.6 `put-channel-policy`

Attaches or updates an IAM policy on a channel for cross-account access.

**Synopsis:**
```bash
aws mediapackagev2 put-channel-policy \
    --channel-group-name <value> \
    --channel-name <value> \
    --policy <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-group-name` | **Yes** | string | -- | Name of the channel group |
| `--channel-name` | **Yes** | string | -- | Name of the channel |
| `--policy` | **Yes** | string | -- | JSON policy document |

**Output:** None

---

### 2.7 `get-channel-policy`

Retrieves the IAM policy attached to a channel.

**Synopsis:**
```bash
aws mediapackagev2 get-channel-policy \
    --channel-group-name <value> \
    --channel-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-group-name` | **Yes** | string | -- | Name of the channel group |
| `--channel-name` | **Yes** | string | -- | Name of the channel |

**Output Schema:**
```json
{
    "ChannelGroupName": "string",
    "ChannelName": "string",
    "Policy": "string"
}
```

---

### 2.8 `delete-channel-policy`

Deletes the IAM policy from a channel.

**Synopsis:**
```bash
aws mediapackagev2 delete-channel-policy \
    --channel-group-name <value> \
    --channel-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-group-name` | **Yes** | string | -- | Name of the channel group |
| `--channel-name` | **Yes** | string | -- | Name of the channel |

**Output:** None

---

### 2.9 `reset-channel-state`

Resets a channel's state, clearing any error conditions.

**Synopsis:**
```bash
aws mediapackagev2 reset-channel-state \
    --channel-group-name <value> \
    --channel-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-group-name` | **Yes** | string | -- | Name of the channel group |
| `--channel-name` | **Yes** | string | -- | Name of the channel |

**Output:** None
