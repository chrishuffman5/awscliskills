# Chat Rooms

### 11.1 `create-room`

Creates a chat room.

**Synopsis:**
```bash
aws ivschat create-room \
    [--name <value>] \
    [--maximum-message-rate-per-second <value>] \
    [--maximum-message-length <value>] \
    [--message-review-handler <value>] \
    [--logging-configuration-identifiers <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | No | string | None | Room name (0-128 chars, `[a-zA-Z0-9-_]*`) |
| `--maximum-message-rate-per-second` | No | integer | 10 | Max messages per second (1-100) |
| `--maximum-message-length` | No | integer | 500 | Max chars per message (1-500) |
| `--message-review-handler` | No | structure | None | Lambda function for message review |
| `--logging-configuration-identifiers` | No | list | None | Logging config ARNs (max 3) |
| `--tags` | No | map | None | Key-value tag pairs (max 50) |

**MessageReviewHandler:**
```json
{
    "uri": "arn:aws:lambda:us-east-1:123456789012:function:ReviewMessages",
    "fallbackResult": "ALLOW|DENY"
}
```

**Output Schema:**
```json
{
    "arn": "string",
    "id": "string",
    "name": "string",
    "createTime": "timestamp",
    "updateTime": "timestamp",
    "maximumMessageRatePerSecond": "integer",
    "maximumMessageLength": "integer",
    "messageReviewHandler": {
        "uri": "string",
        "fallbackResult": "ALLOW|DENY"
    },
    "loggingConfigurationIdentifiers": ["string"],
    "tags": {"string": "string"}
}
```

---

### 11.2 `get-room`

Gets details for a chat room.

**Synopsis:**
```bash
aws ivschat get-room \
    --identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identifier` | **Yes** | string | -- | Room ARN or ID |

**Output Schema:** Same as `create-room` output.

---

### 11.3 `list-rooms`

Lists chat rooms. **Paginated operation.**

**Synopsis:**
```bash
aws ivschat list-rooms \
    [--name <value>] \
    [--logging-configuration-identifier <value>] \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | No | string | None | Filter by room name |
| `--logging-configuration-identifier` | No | string | None | Filter by logging config ARN |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results per page |

---

### 11.4 `update-room`

Updates a chat room's configuration.

**Synopsis:**
```bash
aws ivschat update-room \
    --identifier <value> \
    [--name <value>] \
    [--maximum-message-rate-per-second <value>] \
    [--maximum-message-length <value>] \
    [--message-review-handler <value>] \
    [--logging-configuration-identifiers <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identifier` | **Yes** | string | -- | Room ARN or ID |
| All other params | No | -- | -- | Same as `create-room` (except `--tags`) |

---

### 11.5 `delete-room`

Deletes a chat room.

**Synopsis:**
```bash
aws ivschat delete-room \
    --identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Output:** None

---

### 11.6 `create-chat-token`

Creates a chat token for a user to connect to a room.

**Synopsis:**
```bash
aws ivschat create-chat-token \
    --room-identifier <value> \
    --user-id <value> \
    [--capabilities <value>] \
    [--session-duration-in-minutes <value>] \
    [--attributes <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--room-identifier` | **Yes** | string | -- | Room ARN or ID |
| `--user-id` | **Yes** | string | -- | User identifier (1-128 chars) |
| `--capabilities` | No | list | `[SEND_MESSAGE]` | `SEND_MESSAGE`, `DISCONNECT_USER`, `DELETE_MESSAGE` |
| `--session-duration-in-minutes` | No | integer | 60 | Token duration (1-180 minutes) |
| `--attributes` | No | map | None | Custom attributes |

**Output Schema:**
```json
{
    "token": "string",
    "tokenExpirationTime": "timestamp",
    "sessionExpirationTime": "timestamp"
}
```

---

### 11.7 `send-event`

Sends an event to a chat room.

**Synopsis:**
```bash
aws ivschat send-event \
    --room-identifier <value> \
    --event-name <value> \
    [--attributes <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--room-identifier` | **Yes** | string | -- | Room ARN or ID |
| `--event-name` | **Yes** | string | -- | Event name (1-100 chars) |
| `--attributes` | No | map | None | Event attributes |

**Output Schema:**
```json
{
    "id": "string"
}
```

---

### 11.8 `delete-message`

Deletes a message from a chat room.

**Synopsis:**
```bash
aws ivschat delete-message \
    --room-identifier <value> \
    --id <value> \
    [--reason <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--room-identifier` | **Yes** | string | -- | Room ARN or ID |
| `--id` | **Yes** | string | -- | Message ID to delete |
| `--reason` | No | string | None | Reason for deletion |

**Output Schema:**
```json
{
    "id": "string"
}
```

---

### 11.9 `disconnect-user`

Disconnects a user from a chat room.

**Synopsis:**
```bash
aws ivschat disconnect-user \
    --room-identifier <value> \
    --user-id <value> \
    [--reason <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--room-identifier` | **Yes** | string | -- | Room ARN or ID |
| `--user-id` | **Yes** | string | -- | User ID to disconnect |
| `--reason` | No | string | None | Reason for disconnection |

**Output:** None
