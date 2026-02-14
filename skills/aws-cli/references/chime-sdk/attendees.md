# Attendees

Commands from the `aws chime-sdk-meetings` service.

### 5.1 `create-attendee`

Creates an attendee for a meeting.

**Synopsis:**
```bash
aws chime-sdk-meetings create-attendee \
    --meeting-id <value> \
    --external-user-id <value> \
    [--capabilities <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--meeting-id` | **Yes** | string | -- | Meeting ID (UUID format) |
| `--external-user-id` | **Yes** | string | -- | External user ID (2-64 chars) |
| `--capabilities` | No | structure | All SendReceive | Audio/video/content capabilities |

**Capabilities:**
```json
{
    "Audio": "SendReceive|Send|Receive|None",
    "Video": "SendReceive|Send|Receive|None",
    "Content": "SendReceive|Send|Receive|None"
}
```

**Output Schema:**
```json
{
    "Attendee": {
        "ExternalUserId": "string",
        "AttendeeId": "string",
        "JoinToken": "string",
        "Capabilities": {
            "Audio": "SendReceive|Send|Receive|None",
            "Video": "SendReceive|Send|Receive|None",
            "Content": "SendReceive|Send|Receive|None"
        }
    }
}
```

---

### 5.2 `batch-create-attendee`

Creates multiple attendees in a single call.

**Synopsis:**
```bash
aws chime-sdk-meetings batch-create-attendee \
    --meeting-id <value> \
    --attendees <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--meeting-id` | **Yes** | string | -- | Meeting ID |
| `--attendees` | **Yes** | list | -- | Attendee list (1-100 items) |

**Attendees:**
```json
[
    {
        "ExternalUserId": "string (2-64 chars, required)",
        "Capabilities": {
            "Audio": "SendReceive|Send|Receive|None",
            "Video": "SendReceive|Send|Receive|None",
            "Content": "SendReceive|Send|Receive|None"
        }
    }
]
```

**Output Schema:**
```json
{
    "Attendees": [
        {
            "ExternalUserId": "string",
            "AttendeeId": "string",
            "JoinToken": "string",
            "Capabilities": { "..." }
        }
    ],
    "Errors": [
        {
            "ExternalUserId": "string",
            "ErrorCode": "string",
            "ErrorMessage": "string"
        }
    ]
}
```

---

### 5.3 `get-attendee`

Gets attendee details.

**Synopsis:**
```bash
aws chime-sdk-meetings get-attendee \
    --meeting-id <value> \
    --attendee-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--meeting-id` | **Yes** | string | -- | Meeting ID |
| `--attendee-id` | **Yes** | string | -- | Attendee ID (UUID format) |

**Output Schema:**
```json
{
    "Attendee": {
        "ExternalUserId": "string",
        "AttendeeId": "string",
        "JoinToken": "string",
        "Capabilities": {
            "Audio": "SendReceive|Send|Receive|None",
            "Video": "SendReceive|Send|Receive|None",
            "Content": "SendReceive|Send|Receive|None"
        }
    }
}
```

---

### 5.4 `list-attendees`

Lists attendees for a meeting. **Paginated operation.**

**Synopsis:**
```bash
aws chime-sdk-meetings list-attendees \
    --meeting-id <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--meeting-id` | **Yes** | string | -- | Meeting ID |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results per page (1-100) |

**Output Schema:**
```json
{
    "Attendees": [
        {
            "ExternalUserId": "string",
            "AttendeeId": "string",
            "JoinToken": "string",
            "Capabilities": { "..." }
        }
    ],
    "NextToken": "string"
}
```

---

### 5.5 `delete-attendee`

Deletes an attendee from a meeting.

**Synopsis:**
```bash
aws chime-sdk-meetings delete-attendee \
    --meeting-id <value> \
    --attendee-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--meeting-id` | **Yes** | string | -- | Meeting ID |
| `--attendee-id` | **Yes** | string | -- | Attendee ID |

**Output:** None

---

### 5.6 `update-attendee-capabilities`

Updates an attendee's audio/video/content capabilities.

**Synopsis:**
```bash
aws chime-sdk-meetings update-attendee-capabilities \
    --meeting-id <value> \
    --attendee-id <value> \
    --capabilities <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--meeting-id` | **Yes** | string | -- | Meeting ID |
| `--attendee-id` | **Yes** | string | -- | Attendee ID |
| `--capabilities` | **Yes** | structure | -- | Updated capabilities |

**Output Schema:**
```json
{
    "Attendee": {
        "ExternalUserId": "string",
        "AttendeeId": "string",
        "JoinToken": "string",
        "Capabilities": {
            "Audio": "SendReceive|Send|Receive|None",
            "Video": "SendReceive|Send|Receive|None",
            "Content": "SendReceive|Send|Receive|None"
        }
    }
}
```

---

### 5.7 `batch-update-attendee-capabilities-except`

Updates capabilities for all attendees except specified ones.

**Synopsis:**
```bash
aws chime-sdk-meetings batch-update-attendee-capabilities-except \
    --meeting-id <value> \
    --excluded-attendee-ids <value> \
    --capabilities <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--meeting-id` | **Yes** | string | -- | Meeting ID |
| `--excluded-attendee-ids` | **Yes** | list | -- | Attendee IDs to exclude (1-250) |
| `--capabilities` | **Yes** | structure | -- | Capabilities to apply |

**ExcludedAttendeeIds:**
```json
[
    { "AttendeeId": "string" }
]
```

**Output:** None
