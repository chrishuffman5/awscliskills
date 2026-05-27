# Miscellaneous

### 28.1 `start-outbound-voice-contact`

Initiates an outbound voice contact.

**Synopsis:**
```bash
aws connect start-outbound-voice-contact \
    --destination-phone-number <value> \
    --contact-flow-id <value> \
    --instance-id <value> \
    [--source-phone-number <value>] \
    [--queue-id <value>] \
    [--attributes <value>] \
    [--client-token <value>] \
    [--name <value>] \
    [--description <value>] \
    [--references <value>] \
    [--related-contact-id <value>] \
    [--campaign-id <value>] \
    [--traffic-type <value>] \
    [--answer-machine-detection-config <value>] \
    [--ring-timeout-in-seconds <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--destination-phone-number` | **Yes** | string | -- | Customer phone (E.164 format) |
| `--contact-flow-id` | **Yes** | string | -- | Contact flow ID (max 500 chars) |
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--source-phone-number` | No | string | None | Caller ID number (E.164) |
| `--queue-id` | No | string | None | Queue for the call |
| `--attributes` | No | map | None | Contact attributes |
| `--client-token` | No | string | Auto | Idempotency token |
| `--name` | No | string | None | Contact name (max 1024) |
| `--description` | No | string | None | Description (max 4096) |
| `--references` | No | map | None | References |
| `--related-contact-id` | No | string | None | Related contact ID |
| `--campaign-id` | No | string | None | Campaign ID |
| `--traffic-type` | No | string | `GENERAL` | `GENERAL` or `CAMPAIGN` |
| `--answer-machine-detection-config` | No | structure | None | AMD config |
| `--ring-timeout-in-seconds` | No | integer | 60 | Ring timeout (15-60) |

**Output Schema:**
```json
{
    "ContactId": "string"
}
```

---

### 28.2 `start-chat-contact`

Initiates a chat contact.

**Synopsis:**
```bash
aws connect start-chat-contact \
    --instance-id <value> \
    --contact-flow-id <value> \
    --participant-details <value> \
    [--attributes <value>] \
    [--initial-message <value>] \
    [--client-token <value>] \
    [--chat-duration-in-minutes <value>] \
    [--supported-messaging-content-types <value>] \
    [--persistent-chat <value>] \
    [--related-contact-id <value>] \
    [--segment-attributes <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--contact-flow-id` | **Yes** | string | -- | Contact flow ID |
| `--participant-details` | **Yes** | structure | -- | `DisplayName` for the customer |
| `--attributes` | No | map | None | Contact attributes |
| `--initial-message` | No | structure | None | First message with `ContentType` and `Content` |
| `--client-token` | No | string | Auto | Idempotency token |
| `--chat-duration-in-minutes` | No | integer | None | Chat TTL (60-10080 minutes) |
| `--supported-messaging-content-types` | No | list | None | Supported content types |
| `--persistent-chat` | No | structure | None | Persistent chat config |
| `--related-contact-id` | No | string | None | Related contact ID |
| `--segment-attributes` | No | map | None | Segment attributes |

**Output Schema:**
```json
{
    "ContactId": "string",
    "ParticipantId": "string",
    "ParticipantToken": "string",
    "ContinuedFromContactId": "string"
}
```

---

### 28.3 `start-task-contact`

Initiates a task contact.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--name` | **Yes** | string | -- | Task name (max 512) |
| `--previous-contact-id` | No | string | None | Previous contact ID |
| `--contact-flow-id` | No | string | None | Contact flow ID |
| `--attributes` | No | map | None | Contact attributes |
| `--references` | No | map | None | References |
| `--description` | No | string | None | Description |
| `--client-token` | No | string | Auto | Idempotency token |
| `--scheduled-time` | No | timestamp | None | Scheduled time |
| `--task-template-id` | No | string | None | Task template ID |
| `--quick-connect-id` | No | string | None | Quick connect ID |
| `--related-contact-id` | No | string | None | Related contact ID |
| `--segment-attributes` | No | map | None | Segment attributes |

**Output Schema:**
```json
{
    "ContactId": "string"
}
```

---

### 28.4 `start-web-rtc-contact`

Initiates a WebRTC contact for video/voice.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--contact-flow-id` | **Yes** | string | -- | Contact flow ID |
| `--participant-details` | **Yes** | structure | -- | Participant display name |
| `--attributes` | No | map | None | Contact attributes |
| `--client-token` | No | string | Auto | Idempotency token |
| `--allowed-capabilities` | No | structure | None | Allowed capabilities |
| `--related-contact-id` | No | string | None | Related contact ID |
| `--references` | No | map | None | References |
| `--description` | No | string | None | Description |

**Output Schema:**
```json
{
    "ConnectionData": {
        "Attendee": { "AttendeeId": "string", "JoinToken": "string" },
        "Meeting": { "MeetingId": "string", "MediaPlacement": {}, "MeetingFeatures": {} }
    },
    "ContactId": "string",
    "ParticipantId": "string",
    "ParticipantToken": "string"
}
```

---

### 28.5 `start-outbound-chat-contact`

Starts an outbound chat contact.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--contact-flow-id` | **Yes** | string | -- | Contact flow ID |
| `--source-endpoint` | **Yes** | structure | -- | Source endpoint |
| `--destination-endpoint` | **Yes** | structure | -- | Destination endpoint |
| `--segment-attributes` | **Yes** | map | -- | Segment attributes |
| `--attributes` | No | map | None | Contact attributes |
| `--chat-duration-in-minutes` | No | integer | None | Chat duration (60-10080) |
| `--participant-details` | No | structure | None | Participant details |
| `--initial-system-message` | No | structure | None | Initial system message |
| `--related-contact-id` | No | string | None | Related contact ID |
| `--supported-messaging-content-types` | No | list | None | Supported content types |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "ContactId": "string"
}
```

---

### 28.6-28.12 Notification Commands

`create-notification`, `describe-notification`, `list-notifications`, `update-notification-content`, `delete-notification`, `search-notifications`, `list-user-notifications`, `update-user-notification-status`, `create-push-notification-registration`, `delete-push-notification-registration` manage in-app notifications for Connect users. All require `--instance-id`.

---

### 28.13 `search-resource-tags`

Searches resource tags. **Paginated operation.**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--resource-types` | No | list | None | Resource types to search |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-100) |
| `--search-criteria` | No | structure | None | Tag search criteria |

---

### 28.14 `update-participant-role-config`

Updates participant role configuration for a contact.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--contact-id` | **Yes** | string | -- | Contact ID |
| `--channel-configuration` | **Yes** | tagged union | -- | Channel-specific config |

**Output:** None
