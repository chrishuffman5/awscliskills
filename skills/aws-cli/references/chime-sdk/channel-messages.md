# Channel Messages

Commands from the `aws chime-sdk-messaging` service.

### 8.1 `send-channel-message`

Sends a message to a channel.

**Synopsis:**
```bash
aws chime-sdk-messaging send-channel-message \
    --channel-arn <value> \
    --content <value> \
    --type <value> \
    --persistence <value> \
    --chime-bearer <value> \
    [--metadata <value>] \
    [--client-request-token <value>] \
    [--push-notification <value>] \
    [--message-attributes <value>] \
    [--sub-channel-id <value>] \
    [--content-type <value>] \
    [--target <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-arn` | **Yes** | string | -- | Channel ARN |
| `--content` | **Yes** | string | -- | Message content (min 1 char) |
| `--type` | **Yes** | string | -- | `STANDARD` (up to 4KB) or `CONTROL` (up to 30 bytes) |
| `--persistence` | **Yes** | string | -- | `PERSISTENT` or `NON_PERSISTENT` |
| `--chime-bearer` | **Yes** | string | -- | ARN of the user/bot making the call |
| `--metadata` | No | string | None | Metadata (max 1024 chars) |
| `--client-request-token` | No | string | Auto | Idempotency token (2-64 chars) |
| `--push-notification` | No | structure | None | Push notification config |
| `--message-attributes` | No | map | None | Message attributes for filtering |
| `--sub-channel-id` | No | string | None | Sub-channel ID (1-128 chars) |
| `--content-type` | No | string | None | Content type (max 45 chars) |
| `--target` | No | list | None | Target member (max 1) |

**PushNotification:**
```json
{
    "Title": "string",
    "Body": "string",
    "Type": "DEFAULT|VOIP"
}
```

**Output Schema:**
```json
{
    "ChannelArn": "string",
    "MessageId": "string",
    "Status": {
        "Value": "SENT|PENDING|FAILED|DENIED",
        "Detail": "string"
    },
    "SubChannelId": "string"
}
```

---

### 8.2 `get-channel-message`

Gets a message from a channel.

**Synopsis:**
```bash
aws chime-sdk-messaging get-channel-message \
    --channel-arn <value> \
    --message-id <value> \
    --chime-bearer <value> \
    [--sub-channel-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-arn` | **Yes** | string | -- | Channel ARN |
| `--message-id` | **Yes** | string | -- | Message ID |
| `--chime-bearer` | **Yes** | string | -- | ARN of the user/bot making the call |
| `--sub-channel-id` | No | string | None | Sub-channel ID |

**Output Schema:**
```json
{
    "ChannelMessage": {
        "ChannelArn": "string",
        "MessageId": "string",
        "Content": "string",
        "Metadata": "string",
        "Type": "STANDARD|CONTROL",
        "CreatedTimestamp": "timestamp",
        "LastEditedTimestamp": "timestamp",
        "LastUpdatedTimestamp": "timestamp",
        "Sender": { "Arn": "string", "Name": "string" },
        "Redacted": "boolean",
        "Persistence": "PERSISTENT|NON_PERSISTENT",
        "Status": {
            "Value": "SENT|PENDING|FAILED|DENIED",
            "Detail": "string"
        },
        "MessageAttributes": {},
        "SubChannelId": "string",
        "ContentType": "string",
        "Target": [{ "MemberArn": "string" }]
    }
}
```

---

### 8.3 `list-channel-messages`

Lists messages in a channel. **Paginated operation.**

**Synopsis:**
```bash
aws chime-sdk-messaging list-channel-messages \
    --channel-arn <value> \
    --chime-bearer <value> \
    [--sort-order <value>] \
    [--not-before <value>] \
    [--not-after <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--sub-channel-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-arn` | **Yes** | string | -- | Channel ARN |
| `--chime-bearer` | **Yes** | string | -- | ARN of the user/bot making the call |
| `--sort-order` | No | string | None | `ASCENDING` or `DESCENDING` |
| `--not-before` | No | timestamp | None | Start time filter |
| `--not-after` | No | timestamp | None | End time filter |
| `--max-results` | No | integer | None | Max results per page (1-50) |
| `--next-token` | No | string | None | Pagination token |
| `--sub-channel-id` | No | string | None | Sub-channel ID |

**Output Schema:**
```json
{
    "ChannelArn": "string",
    "ChannelMessages": [
        {
            "MessageId": "string",
            "Content": "string",
            "Metadata": "string",
            "Type": "STANDARD|CONTROL",
            "CreatedTimestamp": "timestamp",
            "LastUpdatedTimestamp": "timestamp",
            "LastEditedTimestamp": "timestamp",
            "Sender": { "Arn": "string", "Name": "string" },
            "Redacted": "boolean",
            "Status": { "Value": "string", "Detail": "string" },
            "MessageAttributes": {},
            "ContentType": "string",
            "Target": [{ "MemberArn": "string" }]
        }
    ],
    "NextToken": "string",
    "SubChannelId": "string"
}
```

---

### 8.4 `update-channel-message`

Updates a channel message.

**Synopsis:**
```bash
aws chime-sdk-messaging update-channel-message \
    --channel-arn <value> \
    --message-id <value> \
    --content <value> \
    --chime-bearer <value> \
    [--metadata <value>] \
    [--sub-channel-id <value>] \
    [--content-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-arn` | **Yes** | string | -- | Channel ARN |
| `--message-id` | **Yes** | string | -- | Message ID |
| `--content` | **Yes** | string | -- | Updated content |
| `--chime-bearer` | **Yes** | string | -- | ARN of the user/bot making the call |
| `--metadata` | No | string | None | Updated metadata |
| `--sub-channel-id` | No | string | None | Sub-channel ID |
| `--content-type` | No | string | None | Content type |

**Output Schema:**
```json
{
    "ChannelArn": "string",
    "MessageId": "string",
    "Status": {
        "Value": "SENT|PENDING|FAILED|DENIED",
        "Detail": "string"
    },
    "SubChannelId": "string"
}
```

---

### 8.5 `delete-channel-message`

Deletes a channel message.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-arn` | **Yes** | string | -- | Channel ARN |
| `--message-id` | **Yes** | string | -- | Message ID |
| `--chime-bearer` | **Yes** | string | -- | ARN of the user/bot making the call |
| `--sub-channel-id` | No | string | None | Sub-channel ID |

**Output:** None

---

### 8.6 `redact-channel-message`

Redacts a message's content (keeps metadata).

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-arn` | **Yes** | string | -- | Channel ARN |
| `--message-id` | **Yes** | string | -- | Message ID |
| `--chime-bearer` | **Yes** | string | -- | ARN of the user/bot making the call |
| `--sub-channel-id` | No | string | None | Sub-channel ID |

**Output Schema:**
```json
{
    "ChannelArn": "string",
    "MessageId": "string",
    "SubChannelId": "string"
}
```

---

### 8.7 `get-channel-message-status`

Gets the status of a channel message.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-arn` | **Yes** | string | -- | Channel ARN |
| `--message-id` | **Yes** | string | -- | Message ID |
| `--chime-bearer` | **Yes** | string | -- | ARN of the user/bot making the call |
| `--sub-channel-id` | No | string | None | Sub-channel ID |

**Output Schema:**
```json
{
    "Status": {
        "Value": "SENT|PENDING|FAILED|DENIED",
        "Detail": "string"
    }
}
```

---

### 8.8 `update-channel-read-marker`

Updates the read marker for a channel.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-arn` | **Yes** | string | -- | Channel ARN |
| `--chime-bearer` | **Yes** | string | -- | ARN of the user/bot making the call |

**Output Schema:**
```json
{
    "ChannelArn": "string"
}
```
