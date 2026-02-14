# Participant

Commands from the `aws connectparticipant` service.

### 31.1 `create-participant-connection`

Creates a participant connection (websocket and/or credentials).

**Synopsis:**
```bash
aws connectparticipant create-participant-connection \
    --participant-token <value> \
    [--type <value>] \
    [--connect-participant | --no-connect-participant] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--participant-token` | **Yes** | string | -- | Participant token from StartChatContact (1-1000 chars) |
| `--type` | No | list | None | `WEBSOCKET`, `CONNECTION_CREDENTIALS`, `WEBRTC_CONNECTION` |
| `--connect-participant` | No | boolean | None | Mark participant as connected |

**Output Schema:**
```json
{
    "Websocket": {
        "Url": "string",
        "ConnectionExpiry": "string"
    },
    "ConnectionCredentials": {
        "ConnectionToken": "string",
        "Expiry": "string"
    },
    "WebRTCConnection": {
        "Attendee": { "AttendeeId": "string", "JoinToken": "string" },
        "Meeting": {
            "MeetingId": "string",
            "MediaPlacement": { "AudioHostUrl": "string", "AudioFallbackUrl": "string", "SignalingUrl": "string", "EventIngestionUrl": "string" },
            "MeetingFeatures": { "Audio": { "EchoReduction": "AVAILABLE|UNAVAILABLE" } }
        }
    }
}
```

---

### 31.2 `send-message`

Sends a message from a participant.

**Synopsis:**
```bash
aws connectparticipant send-message \
    --content-type <value> \
    --content <value> \
    --connection-token <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--content-type` | **Yes** | string | -- | `text/plain`, `text/markdown`, `application/json`, `application/vnd.amazonaws.connect.message.interactive.response` |
| `--content` | **Yes** | string | -- | Message content (max 16384 chars) |
| `--connection-token` | **Yes** | string | -- | Connection token (1-1000 chars) |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "Id": "string",
    "AbsoluteTime": "string",
    "MessageMetadata": {
        "MessageProcessingStatus": "PROCESSING|FAILED|REJECTED"
    }
}
```

---

### 31.3 `send-event`

Sends an event (typing indicator, read receipt, etc.).

**Synopsis:**
```bash
aws connectparticipant send-event \
    --content-type <value> \
    --connection-token <value> \
    [--content <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--content-type` | **Yes** | string | -- | Event type (e.g., `application/vnd.amazonaws.connect.event.typing`, `application/vnd.amazonaws.connect.event.connection.acknowledged`) |
| `--connection-token` | **Yes** | string | -- | Connection token |
| `--content` | No | string | None | Event content |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "Id": "string",
    "AbsoluteTime": "string"
}
```

---

### 31.4 `get-transcript`

Gets a chat transcript. **Paginated operation.**

**Synopsis:**
```bash
aws connectparticipant get-transcript \
    --connection-token <value> \
    [--contact-id <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--scan-direction <value>] \
    [--sort-order <value>] \
    [--start-position <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connection-token` | **Yes** | string | -- | Connection token |
| `--contact-id` | No | string | None | Contact ID (for multi-party) |
| `--max-results` | No | integer | None | Max results (0-100) |
| `--next-token` | No | string | None | Pagination token |
| `--scan-direction` | No | string | None | `FORWARD` or `BACKWARD` |
| `--sort-order` | No | string | None | `DESCENDING` or `ASCENDING` |
| `--start-position` | No | structure | None | Start position (`Id`, `AbsoluteTime`, `MostRecent`) |

**Output Schema:**
```json
{
    "InitialContactId": "string",
    "Transcript": [
        {
            "AbsoluteTime": "string",
            "Content": "string",
            "ContentType": "string",
            "Id": "string",
            "Type": "TYPING|PARTICIPANT_JOINED|PARTICIPANT_LEFT|CHAT_ENDED|TRANSFER_SUCCEEDED|TRANSFER_FAILED|MESSAGE|EVENT|ATTACHMENT|CONNECTION_ACK|MESSAGE_DELIVERED|MESSAGE_READ",
            "ParticipantId": "string",
            "DisplayName": "string",
            "ParticipantRole": "AGENT|CUSTOMER|SYSTEM|CUSTOM_BOT|SUPERVISOR",
            "Attachments": [],
            "MessageMetadata": { "MessageProcessingStatus": "string" },
            "RelatedContactId": "string",
            "ContactId": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 31.5 `get-attachment`

Gets a pre-signed URL for an attachment.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--attachment-id` | **Yes** | string | -- | Attachment ID (1-256 chars) |
| `--connection-token` | **Yes** | string | -- | Connection token |
| `--url-expiry-in-seconds` | No | integer | None | URL expiry (5-300 seconds, default 300) |

**Output Schema:**
```json
{
    "Url": "string",
    "UrlExpiry": "string"
}
```

---

### 31.6 `start-attachment-upload`

Starts uploading an attachment.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--content-type` | **Yes** | string | -- | MIME type (1-255 chars) |
| `--attachment-size-in-bytes` | **Yes** | long | -- | File size |
| `--attachment-name` | **Yes** | string | -- | File name (1-256 chars) |
| `--connection-token` | **Yes** | string | -- | Connection token |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "AttachmentId": "string",
    "UploadMetadata": {
        "Url": "string",
        "UrlExpiry": "string",
        "HeadersToInclude": { "key": "value" }
    }
}
```

---

### 31.7 `complete-attachment-upload`

Completes an attachment upload.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--attachment-ids` | **Yes** | list | -- | Attachment IDs (1 item) |
| `--connection-token` | **Yes** | string | -- | Connection token |
| `--client-token` | No | string | Auto | Idempotency token |

**Output:** None

---

### 31.8 `disconnect-participant`

Disconnects a participant from a contact.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connection-token` | **Yes** | string | -- | Connection token |
| `--client-token` | No | string | Auto | Idempotency token |

**Output:** None

---

### 31.9 `describe-view`

Describes a view available to the participant.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--view-token` | **Yes** | string | -- | View token |
| `--connection-token` | **Yes** | string | -- | Connection token |

**Output Schema:**
```json
{
    "View": {
        "Id": "string",
        "Arn": "string",
        "Name": "string",
        "Version": "integer",
        "Content": { "InputSchema": "string", "Template": "string", "Actions": [] }
    }
}
```

---

### 31.10 `get-authentication-url`

Gets an authentication URL for a participant.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--session-id` | **Yes** | string | -- | Session ID |
| `--redirect-uri` | **Yes** | string | -- | Redirect URI |
| `--connection-token` | **Yes** | string | -- | Connection token |

**Output Schema:**
```json
{
    "AuthenticationUrl": "string"
}
```

---

### 31.11 `cancel-participant-authentication`

Cancels participant authentication.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--session-id` | **Yes** | string | -- | Session ID |
| `--connection-token` | **Yes** | string | -- | Connection token |

**Output:** None
