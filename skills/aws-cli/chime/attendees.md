# Attendees

CLI namespace: `aws chime-sdk-meetings`

### 5.1 `create-attendee`

Creates a new attendee for a meeting.

**Synopsis:**
```bash
aws chime-sdk-meetings create-attendee \
    --meeting-id <value> \
    --external-user-id <value> \
    [--capabilities <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--meeting-id` | **Yes** | string | -- | Meeting ID (UUID) |
| `--external-user-id` | **Yes** | string | -- | External user ID (2-64 chars) |
| `--capabilities` | No | structure | None | Audio/video/content capabilities |

**Capabilities structure:**
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

Creates multiple attendees for a meeting.

**Synopsis:**
```bash
aws chime-sdk-meetings batch-create-attendee \
    --meeting-id <value> \
    --attendees <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--meeting-id` | **Yes** | string | -- | Meeting ID (UUID) |
| `--attendees` | **Yes** | list | -- | Attendees to create (1-100) |

**Output Schema:**
```json
{
    "Attendees": [
        {
            "ExternalUserId": "string",
            "AttendeeId": "string",
            "JoinToken": "string",
            "Capabilities": {}
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
    --attendee-id <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--meeting-id` | **Yes** | string | -- | Meeting ID |
| `--attendee-id` | **Yes** | string | -- | Attendee ID (UUID) |

**Output Schema:**
```json
{
    "Attendee": {
        "ExternalUserId": "string",
        "AttendeeId": "string",
        "JoinToken": "string",
        "Capabilities": {}
    }
}
```

---

### 5.4 `list-attendees`

Lists attendees in a meeting. **Paginated operation.**

**Synopsis:**
```bash
aws chime-sdk-meetings list-attendees \
    --meeting-id <value> \
    [--next-token <value>] \
    [--max-results <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--meeting-id` | **Yes** | string | -- | Meeting ID |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-100) |

**Output Schema:**
```json
{
    "Attendees": [
        {
            "ExternalUserId": "string",
            "AttendeeId": "string",
            "JoinToken": "string",
            "Capabilities": {}
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
    --attendee-id <value>
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
    --capabilities <value>
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
        "Capabilities": {}
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
    --capabilities <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--meeting-id` | **Yes** | string | -- | Meeting ID |
| `--excluded-attendee-ids` | **Yes** | list | -- | Attendee IDs to exclude (1-250) |
| `--capabilities` | **Yes** | structure | -- | Capabilities to apply |

**Output:** None
