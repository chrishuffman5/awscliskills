# Channel Messages

CLI namespace: `aws chime-sdk-messaging`

All commands require `--chime-bearer`.

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
    [--target <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-arn` | **Yes** | string | -- | Channel ARN |
| `--content` | **Yes** | string | -- | Message content (1 char min) |
| `--type` | **Yes** | string | -- | `STANDARD` or `CONTROL` |
| `--persistence` | **Yes** | string | -- | `PERSISTENT` or `NON_PERSISTENT` |
| `--chime-bearer` | **Yes** | string | -- | Bearer ARN |
| `--metadata` | No | string | None | Message metadata (0-1024 chars) |
| `--client-request-token` | No | string | Auto | Idempotency token |
| `--push-notification` | No | structure | None | Push notification config |
| `--message-attributes` | No | map | None | Custom attributes |
| `--sub-channel-id` | No | string | None | Sub-channel ID |
| `--content-type` | No | string | None | Content type (0-45 chars) |
| `--target` | No | list | None | Target members for the message |

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

Gets a channel message by ID.

**Synopsis:**
```bash
aws chime-sdk-messaging get-channel-message \
    --channel-arn <value> \
    --message-id <value> \
    --chime-bearer <value> \
    [--sub-channel-id <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-arn` | **Yes** | string | -- | Channel ARN |
| `--message-id` | **Yes** | string | -- | Message ID |
| `--chime-bearer` | **Yes** | string | -- | Bearer ARN |
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
        "Sender": {"Arn": "string", "Name": "string"},
        "Redacted": "boolean",
        "Persistence": "PERSISTENT|NON_PERSISTENT",
        "Status": {"Value": "string", "Detail": "string"},
        "MessageAttributes": {},
        "SubChannelId": "string",
        "ContentType": "string",
        "Target": []
    }
}
```

---

### 8.3 `list-channel-messages`

Lists channel messages. **Paginated operation.**

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
    [--sub-channel-id <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-arn` | **Yes** | string | -- | Channel ARN |
| `--chime-bearer` | **Yes** | string | -- | Bearer ARN |
| `--sort-order` | No | string | None | `ASCENDING` or `DESCENDING` |
| `--not-before` | No | timestamp | None | Start time filter |
| `--not-after` | No | timestamp | None | End time filter |
| `--max-results` | No | integer | None | Max results (1-50) |
| `--next-token` | No | string | None | Pagination token |
| `--sub-channel-id` | No | string | None | Sub-channel ID |

**Output Schema:**
```json
{
    "ChannelArn": "string",
    "ChannelMessages": [],
    "NextToken": "string",
    "SubChannelId": "string"
}
```

---

### 8.4 `update-channel-message`

Edits a channel message.

**Synopsis:**
```bash
aws chime-sdk-messaging update-channel-message \
    --channel-arn <value> --message-id <value> --chime-bearer <value> \
    [--content <value>] [--metadata <value>] [--sub-channel-id <value>] [--content-type <value>]
```

**Output Schema:**
```json
{
    "ChannelArn": "string",
    "MessageId": "string",
    "Status": {"Value": "string", "Detail": "string"},
    "SubChannelId": "string"
}
```

---

### 8.5 `delete-channel-message`

Deletes a channel message.

**Synopsis:**
```bash
aws chime-sdk-messaging delete-channel-message \
    --channel-arn <value> --message-id <value> --chime-bearer <value> [--sub-channel-id <value>]
```

**Output:** None

---

### 8.6 `redact-channel-message`

Redacts (hides content of) a channel message.

**Synopsis:**
```bash
aws chime-sdk-messaging redact-channel-message \
    --channel-arn <value> --message-id <value> --chime-bearer <value> [--sub-channel-id <value>]
```

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

Gets the message delivery status.

**Synopsis:**
```bash
aws chime-sdk-messaging get-channel-message-status \
    --channel-arn <value> --message-id <value> --chime-bearer <value> [--sub-channel-id <value>]
```

**Output Schema:**
```json
{
    "Status": {"Value": "SENT|PENDING|FAILED|DENIED", "Detail": "string"}
}
```

---

### 8.8 `update-channel-read-marker`

Updates the read marker position for a channel member.

**Synopsis:**
```bash
aws chime-sdk-messaging update-channel-read-marker \
    --channel-arn <value> --chime-bearer <value>
```

**Output Schema:**
```json
{
    "ChannelArn": "string"
}
```
