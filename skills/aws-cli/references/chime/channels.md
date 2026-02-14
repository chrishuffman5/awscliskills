# Channels

CLI namespace: `aws chime-sdk-messaging`

All messaging commands require `--chime-bearer` (the ARN of the AppInstanceUser or AppInstanceBot making the call).

### 6.1 `create-channel`

Creates a messaging channel.

**Synopsis:**
```bash
aws chime-sdk-messaging create-channel \
    --app-instance-arn <value> \
    --name <value> \
    --chime-bearer <value> \
    [--mode <value>] \
    [--privacy <value>] \
    [--metadata <value>] \
    [--client-request-token <value>] \
    [--tags <value>] \
    [--channel-id <value>] \
    [--member-arns <value>] \
    [--moderator-arns <value>] \
    [--elastic-channel-configuration <value>] \
    [--expiration-settings <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-instance-arn` | **Yes** | string | -- | App instance ARN |
| `--name` | **Yes** | string | -- | Channel name (1-256 chars) |
| `--chime-bearer` | **Yes** | string | -- | Bearer ARN |
| `--mode` | No | string | None | `UNRESTRICTED` or `RESTRICTED` |
| `--privacy` | No | string | None | `PUBLIC` or `PRIVATE` (cannot change after creation) |
| `--metadata` | No | string | None | Metadata (0-1024 chars) |
| `--client-request-token` | No | string | Auto | Idempotency token |
| `--tags` | No | list | None | Tags (1-50) |
| `--channel-id` | No | string | None | Custom channel ID (1-64 chars) |
| `--member-arns` | No | list | None | Initial members (1-10) |
| `--moderator-arns` | No | list | None | Initial moderators (1-10) |
| `--elastic-channel-configuration` | No | structure | None | Elastic channel settings (up to 1M users) |
| `--expiration-settings` | No | structure | None | Auto-deletion settings |

**ElasticChannelConfiguration:**
```json
{
    "MaximumSubChannels": 2,
    "TargetMembershipsPerSubChannel": 2,
    "MinimumMembershipPercentage": 10
}
```

**Output Schema:**
```json
{
    "ChannelArn": "string"
}
```

---

### 6.2 `describe-channel`

Describes a channel.

**Synopsis:**
```bash
aws chime-sdk-messaging describe-channel \
    --channel-arn <value> \
    --chime-bearer <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-arn` | **Yes** | string | -- | Channel ARN |
| `--chime-bearer` | **Yes** | string | -- | Bearer ARN |

**Output Schema:**
```json
{
    "Channel": {
        "Name": "string",
        "ChannelArn": "string",
        "Mode": "UNRESTRICTED|RESTRICTED",
        "Privacy": "PUBLIC|PRIVATE",
        "Metadata": "string",
        "CreatedBy": {"Arn": "string", "Name": "string"},
        "CreatedTimestamp": "timestamp",
        "LastMessageTimestamp": "timestamp",
        "LastUpdatedTimestamp": "timestamp",
        "ChannelFlowArn": "string",
        "ElasticChannelConfiguration": {},
        "ExpirationSettings": {}
    }
}
```

---

### 6.3 `list-channels`

Lists channels in an app instance. **Paginated operation.**

**Synopsis:**
```bash
aws chime-sdk-messaging list-channels \
    --app-instance-arn <value> \
    --chime-bearer <value> \
    [--privacy <value>] \
    [--max-results <value>] \
    [--next-token <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-instance-arn` | **Yes** | string | -- | App instance ARN |
| `--chime-bearer` | **Yes** | string | -- | Bearer ARN |
| `--privacy` | No | string | None | `PUBLIC` or `PRIVATE` |
| `--max-results` | No | integer | None | Max results (1-50) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "Channels": [
        {
            "Name": "string",
            "ChannelArn": "string",
            "Mode": "string",
            "Privacy": "string",
            "Metadata": "string",
            "LastMessageTimestamp": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 6.4 `update-channel`

Updates a channel name, mode, and metadata.

**Synopsis:**
```bash
aws chime-sdk-messaging update-channel \
    --channel-arn <value> \
    --chime-bearer <value> \
    [--name <value>] \
    [--mode <value>] \
    [--metadata <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-arn` | **Yes** | string | -- | Channel ARN |
| `--chime-bearer` | **Yes** | string | -- | Bearer ARN |
| `--name` | No | string | None | Updated name |
| `--mode` | No | string | None | `UNRESTRICTED` or `RESTRICTED` |
| `--metadata` | No | string | None | Updated metadata |

**Output Schema:**
```json
{
    "ChannelArn": "string"
}
```

---

### 6.5 `delete-channel`

Deletes a channel and all associated messages.

**Synopsis:**
```bash
aws chime-sdk-messaging delete-channel \
    --channel-arn <value> \
    --chime-bearer <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-arn` | **Yes** | string | -- | Channel ARN |
| `--chime-bearer` | **Yes** | string | -- | Bearer ARN |

**Output:** None

---

### 6.6 `search-channels`

Searches for channels by name, members, or other criteria.

**Synopsis:**
```bash
aws chime-sdk-messaging search-channels \
    --fields <value> \
    [--chime-bearer <value>] \
    [--max-results <value>] \
    [--next-token <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fields` | **Yes** | list | -- | Search field criteria |
| `--chime-bearer` | No | string | None | Bearer ARN |
| `--max-results` | No | integer | None | Max results |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "Channels": [],
    "NextToken": "string"
}
```

---

### 6.7 `list-sub-channels`

Lists sub-channels of an elastic channel. **Paginated operation.**

**Synopsis:**
```bash
aws chime-sdk-messaging list-sub-channels \
    --channel-arn <value> \
    --chime-bearer <value> \
    [--max-results <value>] \
    [--next-token <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-arn` | **Yes** | string | -- | Elastic channel ARN |
| `--chime-bearer` | **Yes** | string | -- | Bearer ARN |
| `--max-results` | No | integer | None | Max results |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "ChannelArn": "string",
    "SubChannels": [
        {
            "SubChannelId": "string",
            "MembershipCount": "integer"
        }
    ],
    "NextToken": "string"
}
```

---

### 6.8 `put-channel-expiration-settings`

Sets channel message expiration settings.

**Synopsis:**
```bash
aws chime-sdk-messaging put-channel-expiration-settings \
    --channel-arn <value> \
    --chime-bearer <value> \
    [--expiration-settings <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-arn` | **Yes** | string | -- | Channel ARN |
| `--chime-bearer` | **Yes** | string | -- | Bearer ARN |
| `--expiration-settings` | No | structure | None | Expiration settings (omit to remove) |

**ExpirationSettings:**
```json
{
    "ExpirationDays": 30,
    "ExpirationCriterion": "CREATED_TIMESTAMP|LAST_MESSAGE_TIMESTAMP"
}
```

**Output Schema:**
```json
{
    "ChannelArn": "string",
    "ExpirationSettings": {}
}
```
