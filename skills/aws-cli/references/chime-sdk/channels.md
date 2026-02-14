# Channels

Commands from the `aws chime-sdk-messaging` service.

### 6.1 `create-channel`

Creates a channel for messaging.

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
    [--expiration-settings <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-instance-arn` | **Yes** | string | -- | App instance ARN |
| `--name` | **Yes** | string | -- | Channel name (1-256 chars) |
| `--chime-bearer` | **Yes** | string | -- | ARN of the user/bot making the call |
| `--mode` | No | string | None | `UNRESTRICTED` or `RESTRICTED` |
| `--privacy` | No | string | None | `PUBLIC` or `PRIVATE` |
| `--metadata` | No | string | None | Metadata (max 1024 chars) |
| `--client-request-token` | No | string | Auto | Idempotency token (2-64 chars) |
| `--tags` | No | list | None | Tags (max 50) |
| `--channel-id` | No | string | Auto UUID | Custom channel ID (1-64 chars) |
| `--member-arns` | No | list | None | Initial member ARNs (1-10) |
| `--moderator-arns` | No | list | None | Initial moderator ARNs (1-10) |
| `--elastic-channel-configuration` | No | structure | None | Elastic channel config |
| `--expiration-settings` | No | structure | None | Automatic deletion settings |

**ElasticChannelConfiguration:**
```json
{
    "MaximumSubChannels": "integer (min 2, required)",
    "TargetMembershipsPerSubChannel": "integer (min 2, required)",
    "MinimumMembershipPercentage": "integer (1-40, required)"
}
```

**ExpirationSettings:**
```json
{
    "ExpirationDays": "integer (1-5475, required)",
    "ExpirationCriterion": "CREATED_TIMESTAMP|LAST_MESSAGE_TIMESTAMP (required)"
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
    --chime-bearer <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-arn` | **Yes** | string | -- | Channel ARN |
| `--chime-bearer` | **Yes** | string | -- | ARN of the user/bot making the call |

**Output Schema:**
```json
{
    "Channel": {
        "Name": "string",
        "ChannelArn": "string",
        "Mode": "UNRESTRICTED|RESTRICTED",
        "Privacy": "PUBLIC|PRIVATE",
        "Metadata": "string",
        "CreatedBy": { "Arn": "string", "Name": "string" },
        "CreatedTimestamp": "timestamp",
        "LastMessageTimestamp": "timestamp",
        "LastUpdatedTimestamp": "timestamp",
        "ChannelFlowArn": "string",
        "ElasticChannelConfiguration": {
            "MaximumSubChannels": "integer",
            "TargetMembershipsPerSubChannel": "integer",
            "MinimumMembershipPercentage": "integer"
        },
        "ExpirationSettings": {
            "ExpirationDays": "integer",
            "ExpirationCriterion": "string"
        }
    }
}
```

---

### 6.3 `list-channels`

Lists channels in an AppInstance. **Paginated operation.**

**Synopsis:**
```bash
aws chime-sdk-messaging list-channels \
    --app-instance-arn <value> \
    --chime-bearer <value> \
    [--privacy <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-instance-arn` | **Yes** | string | -- | App instance ARN |
| `--chime-bearer` | **Yes** | string | -- | ARN of the user/bot making the call |
| `--privacy` | No | string | None | `PUBLIC` or `PRIVATE` |
| `--max-results` | No | integer | None | Max results per page (1-50) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "Channels": [
        {
            "Name": "string",
            "ChannelArn": "string",
            "Mode": "UNRESTRICTED|RESTRICTED",
            "Privacy": "PUBLIC|PRIVATE",
            "Metadata": "string",
            "LastMessageTimestamp": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 6.4 `update-channel`

Updates a channel's name, mode, and metadata.

**Synopsis:**
```bash
aws chime-sdk-messaging update-channel \
    --channel-arn <value> \
    --chime-bearer <value> \
    [--name <value>] \
    [--mode <value>] \
    [--metadata <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-arn` | **Yes** | string | -- | Channel ARN |
| `--chime-bearer` | **Yes** | string | -- | ARN of the user/bot making the call |
| `--name` | No | string | None | Updated name (1-256 chars) |
| `--mode` | No | string | None | `UNRESTRICTED` or `RESTRICTED` |
| `--metadata` | No | string | None | Updated metadata (max 1024 chars) |

**Output Schema:**
```json
{
    "ChannelArn": "string"
}
```

---

### 6.5 `delete-channel`

Deletes a channel.

**Synopsis:**
```bash
aws chime-sdk-messaging delete-channel \
    --channel-arn <value> \
    --chime-bearer <value> \
    [--sub-channel-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-arn` | **Yes** | string | -- | Channel ARN |
| `--chime-bearer` | **Yes** | string | -- | ARN of the user/bot making the call |
| `--sub-channel-id` | No | string | None | Sub-channel ID for elastic channels |

**Output:** None

---

### 6.6 `search-channels`

Searches channels by name or members. **Paginated operation.**

**Synopsis:**
```bash
aws chime-sdk-messaging search-channels \
    --fields <value> \
    [--chime-bearer <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fields` | **Yes** | list | -- | Search fields (1-20) |
| `--chime-bearer` | No | string | None | ARN of the user/bot making the call |
| `--max-results` | No | integer | None | Max results per page (1-50) |
| `--next-token` | No | string | None | Pagination token |

**Fields:**
```json
[
    {
        "Key": "MEMBERS",
        "Values": ["string"],
        "Operator": "EQUALS|INCLUDES"
    }
]
```

**Output Schema:**
```json
{
    "Channels": [
        {
            "Name": "string",
            "ChannelArn": "string",
            "Mode": "UNRESTRICTED|RESTRICTED",
            "Privacy": "PUBLIC|PRIVATE",
            "Metadata": "string",
            "LastMessageTimestamp": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 6.7 `describe-channel-moderated-by-app-instance-user`

Describes a channel that a user moderates.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-arn` | **Yes** | string | -- | Channel ARN |
| `--app-instance-user-arn` | **Yes** | string | -- | User ARN |
| `--chime-bearer` | **Yes** | string | -- | ARN of the user/bot making the call |

---

### 6.8 `list-channels-moderated-by-app-instance-user`

Lists channels moderated by a user. **Paginated operation.**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-instance-user-arn` | No | string | None | User ARN (defaults to chime-bearer) |
| `--chime-bearer` | **Yes** | string | -- | ARN of the user/bot making the call |
| `--max-results` | No | integer | None | Max results per page (1-50) |
| `--next-token` | No | string | None | Pagination token |

---

### 6.9 `list-sub-channels`

Lists sub-channels of an elastic channel. **Paginated operation.**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-arn` | **Yes** | string | -- | Channel ARN |
| `--chime-bearer` | **Yes** | string | -- | ARN of the user/bot making the call |
| `--max-results` | No | integer | None | Max results per page (1-50) |
| `--next-token` | No | string | None | Pagination token |

---

### 6.10 `put-channel-expiration-settings`

Sets expiration settings for a channel.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-arn` | **Yes** | string | -- | Channel ARN |
| `--chime-bearer` | No | string | None | ARN of the user/bot making the call |
| `--expiration-settings` | No | structure | None | Expiration settings (omit to remove) |

**Output Schema:**
```json
{
    "ChannelArn": "string",
    "ExpirationSettings": {
        "ExpirationDays": "integer",
        "ExpirationCriterion": "CREATED_TIMESTAMP|LAST_MESSAGE_TIMESTAMP"
    }
}
```
