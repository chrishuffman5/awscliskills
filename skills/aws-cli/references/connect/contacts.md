# Contacts

### 3.1 `create-contact`

Creates a new contact.

**Synopsis:**
```bash
aws connect create-contact \
    --instance-id <value> \
    --channel <value> \
    --initiation-method <value> \
    [--client-token <value>] \
    [--related-contact-id <value>] \
    [--attributes <value>] \
    [--references <value>] \
    [--name <value>] \
    [--description <value>] \
    [--segment-attributes <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--channel` | **Yes** | string | -- | `VOICE`, `CHAT`, `TASK`, `EMAIL` |
| `--initiation-method` | **Yes** | string | -- | `INBOUND`, `OUTBOUND`, `TRANSFER`, `API`, etc. |
| `--client-token` | No | string | Auto | Idempotency token |
| `--related-contact-id` | No | string | None | Related contact ID |
| `--attributes` | No | map | None | Contact attributes |
| `--references` | No | map | None | Contact references |
| `--name` | No | string | None | Contact name (max 1024) |
| `--description` | No | string | None | Contact description (max 4096) |
| `--segment-attributes` | No | map | None | Segment attributes |

**Output Schema:**
```json
{
    "ContactId": "string",
    "ContactArn": "string"
}
```

---

### 3.2 `describe-contact`

Describes a contact with full detail.

**Synopsis:**
```bash
aws connect describe-contact \
    --instance-id <value> \
    --contact-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--contact-id` | **Yes** | string | -- | Contact ID (1-256 chars) |

**Output Schema:**
```json
{
    "Contact": {
        "Arn": "string",
        "Id": "string",
        "InitialContactId": "string",
        "PreviousContactId": "string",
        "InitiationMethod": "INBOUND|OUTBOUND|TRANSFER|QUEUE_TRANSFER|CALLBACK|API|DISCONNECT|MONITOR|EXTERNAL_OUTBOUND|WEBRTC_API|AGENT_REPLY|FLOW",
        "Channel": "VOICE|CHAT|TASK|EMAIL",
        "Name": "string",
        "Description": "string",
        "QueueInfo": { "Id": "string", "EnqueueTimestamp": "timestamp" },
        "AgentInfo": {
            "Id": "string",
            "ConnectedToAgentTimestamp": "timestamp",
            "AgentPauseDurationInSeconds": "integer",
            "DeviceInfo": { "PlatformName": "string", "PlatformVersion": "string", "OperatingSystem": "string" }
        },
        "InitiationTimestamp": "timestamp",
        "DisconnectTimestamp": "timestamp",
        "LastUpdateTimestamp": "timestamp",
        "ScheduledTimestamp": "timestamp",
        "RelatedContactId": "string",
        "Tags": { "key": "value" },
        "Recordings": [
            { "StorageType": "string", "Location": "string", "MediaStreamType": "string", "ParticipantType": "string", "Status": "AVAILABLE|DELETED" }
        ],
        "CustomerEndpoint": { "Type": "string", "Address": "string" },
        "SystemEndpoint": { "Type": "string", "Address": "string" },
        "QualityMetrics": {},
        "DisconnectReason": "string",
        "Attributes": { "key": "value" }
    }
}
```

---

### 3.3 `list-associated-contacts`

Lists contacts associated with a given contact.

**Synopsis:**
```bash
aws connect list-associated-contacts \
    --instance-id <value> \
    --contact-id <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--contact-id` | **Yes** | string | -- | Contact ID |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results |

**Output Schema:**
```json
{
    "ContactSummaryList": [
        { "ContactId": "string", "ContactArn": "string", "InitiationTimestamp": "timestamp", "DisconnectTimestamp": "timestamp", "Channel": "string", "InitiationMethod": "string" }
    ],
    "NextToken": "string"
}
```

---

### 3.4 `update-contact`

Updates contact details.

**Synopsis:**
```bash
aws connect update-contact \
    --instance-id <value> \
    --contact-id <value> \
    [--name <value>] \
    [--description <value>] \
    [--references <value>] \
    [--segment-attributes <value>] \
    [--queue-info <value>] \
    [--customer-endpoint <value>] \
    [--system-endpoint <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--contact-id` | **Yes** | string | -- | Contact ID |
| `--name` | No | string | None | Updated name |
| `--description` | No | string | None | Updated description |
| `--references` | No | map | None | Updated references |
| `--segment-attributes` | No | map | None | Updated segment attributes |
| `--queue-info` | No | structure | None | Queue info update |
| `--customer-endpoint` | No | structure | None | Customer endpoint |
| `--system-endpoint` | No | structure | None | System endpoint |

**Output:** None

---

### 3.5 `update-contact-attributes`

Creates or updates user-defined contact attributes.

**Synopsis:**
```bash
aws connect update-contact-attributes \
    --initial-contact-id <value> \
    --instance-id <value> \
    --attributes <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--initial-contact-id` | **Yes** | string | -- | Initial contact ID |
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--attributes` | **Yes** | map | -- | Key-value attributes |

**Output:** None (empty object on success)

---

### 3.6 `get-contact-attributes`

Gets contact attributes for a contact.

**Synopsis:**
```bash
aws connect get-contact-attributes \
    --instance-id <value> \
    --initial-contact-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--initial-contact-id` | **Yes** | string | -- | Initial contact ID |

**Output Schema:**
```json
{
    "Attributes": { "key": "value" }
}
```

---

### 3.7 `update-contact-routing-data`

Updates routing priority and age for a contact in queue.

**Synopsis:**
```bash
aws connect update-contact-routing-data \
    --instance-id <value> \
    --contact-id <value> \
    [--queue-time-adjustment-seconds <value>] \
    [--queue-priority <value>] \
    [--routing-criteria <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--contact-id` | **Yes** | string | -- | Contact ID |
| `--queue-time-adjustment-seconds` | No | integer | None | Seconds to adjust queue time |
| `--queue-priority` | No | long | None | Priority (lower = higher priority) |
| `--routing-criteria` | No | structure | None | Routing criteria with steps |

**Output:** None

---

### 3.8 `update-contact-schedule`

Updates scheduling info for a scheduled contact.

**Synopsis:**
```bash
aws connect update-contact-schedule \
    --instance-id <value> \
    --contact-id <value> \
    --scheduled-time <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--contact-id` | **Yes** | string | -- | Contact ID |
| `--scheduled-time` | **Yes** | timestamp | -- | New scheduled time |

**Output:** None

---

### 3.9 `stop-contact`

Ends the specified contact.

**Synopsis:**
```bash
aws connect stop-contact \
    --contact-id <value> \
    --instance-id <value> \
    [--disconnect-reason <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--contact-id` | **Yes** | string | -- | Contact ID |
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--disconnect-reason` | No | structure | None | Disconnect reason code |

**Output:** None

---

### 3.10 `transfer-contact`

Transfers contacts from one agent/queue to another.

**Synopsis:**
```bash
aws connect transfer-contact \
    --instance-id <value> \
    --contact-id <value> \
    --contact-flow-id <value> \
    [--queue-id <value>] \
    [--user-id <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--contact-id` | **Yes** | string | -- | Contact ID |
| `--contact-flow-id` | **Yes** | string | -- | Flow for the transfer |
| `--queue-id` | No | string | None | Target queue ID |
| `--user-id` | No | string | None | Target user ID |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "ContactId": "string",
    "ContactArn": "string"
}
```

---

### 3.11 `monitor-contact`

Initiates silent monitoring of a contact.

**Synopsis:**
```bash
aws connect monitor-contact \
    --instance-id <value> \
    --contact-id <value> \
    --user-id <value> \
    [--allowed-monitor-capabilities <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--contact-id` | **Yes** | string | -- | Contact ID to monitor |
| `--user-id` | **Yes** | string | -- | User ID of the monitor |
| `--allowed-monitor-capabilities` | No | list | None | `SILENT_MONITOR`, `BARGE` |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "ContactId": "string",
    "ContactArn": "string"
}
```

---

### 3.12 `pause-contact`

Pauses an active contact.

**Synopsis:**
```bash
aws connect pause-contact \
    --instance-id <value> \
    --contact-id <value> \
    [--contact-flow-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--contact-id` | **Yes** | string | -- | Contact ID |
| `--contact-flow-id` | No | string | None | Flow for hold experience |

**Output:** None

---

### 3.13 `resume-contact`

Resumes a paused contact.

**Synopsis:**
```bash
aws connect resume-contact \
    --instance-id <value> \
    --contact-id <value> \
    [--contact-flow-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--contact-id` | **Yes** | string | -- | Contact ID |
| `--contact-flow-id` | No | string | None | Flow for resume experience |

**Output:** None

---

### 3.14 `tag-contact` / `untag-contact`

Add or remove tags from a contact.

**Synopsis:**
```bash
aws connect tag-contact \
    --contact-id <value> \
    --instance-id <value> \
    --tags <value>

aws connect untag-contact \
    --contact-id <value> \
    --instance-id <value> \
    --tag-keys <value>
```

**Output:** None

---

### 3.15 `search-contacts`

Searches contacts using filters. **Paginated operation.**

**Synopsis:**
```bash
aws connect search-contacts \
    --instance-id <value> \
    --time-range <value> \
    [--search-criteria <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--sort <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--time-range` | **Yes** | structure | -- | Time range with Type, StartTime, EndTime |
| `--search-criteria` | No | structure | None | Search criteria (agent, channel, queue, etc.) |
| `--max-results` | No | integer | None | Max results (1-100) |
| `--next-token` | No | string | None | Pagination token |
| `--sort` | No | structure | None | Sort by field and order |

**Output Schema:**
```json
{
    "Contacts": [
        {
            "Arn": "string",
            "Id": "string",
            "InitialContactId": "string",
            "Channel": "string",
            "InitiationMethod": "string",
            "AgentInfo": { "Id": "string", "ConnectedToAgentTimestamp": "timestamp" },
            "InitiationTimestamp": "timestamp",
            "DisconnectTimestamp": "timestamp",
            "QueueInfo": { "Id": "string", "EnqueueTimestamp": "timestamp" },
            "ScheduledTimestamp": "timestamp"
        }
    ],
    "NextToken": "string",
    "TotalCount": "long"
}
```

---

### 3.16 `batch-put-contact`

Batch creates or updates contacts with attributes.

**Synopsis:**
```bash
aws connect batch-put-contact \
    --instance-id <value> \
    --contact-data-request-list <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--contact-data-request-list` | **Yes** | list | -- | List of contact data requests |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "SuccessfulRequestList": [ { "RequestIdentifier": "string", "ContactId": "string" } ],
    "FailedRequestList": [ { "RequestIdentifier": "string", "FailureReasonCode": "string", "FailureReasonMessage": "string" } ]
}
```

---

### 3.17 `send-chat-integration-event`

Sends a chat integration event (e.g., typing, read receipt).

**Synopsis:**
```bash
aws connect send-chat-integration-event \
    --source-id <value> \
    --destination-id <value> \
    --event <value> \
    [--subtype <value>] \
    [--new-session-details <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-id` | **Yes** | string | -- | Source ID of the integration |
| `--destination-id` | **Yes** | string | -- | Destination ID |
| `--event` | **Yes** | structure | -- | Event type and content |
| `--subtype` | No | string | None | Event subtype |
| `--new-session-details` | No | structure | None | New session details for new chats |

**Output Schema:**
```json
{
    "InitialContactId": "string",
    "NewChatCreated": "boolean"
}
```

---

### 3.18 `dismiss-user-contact`

Dismisses contacts from agent CCP.

**Synopsis:**
```bash
aws connect dismiss-user-contact \
    --user-id <value> \
    --instance-id <value> \
    --contact-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-id` | **Yes** | string | -- | User ID |
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--contact-id` | **Yes** | string | -- | Contact ID |

**Output:** None

---

### 3.19 `create-persistent-contact-association`

Creates a persistent contact association.

**Synopsis:**
```bash
aws connect create-persistent-contact-association \
    --instance-id <value> \
    --initial-contact-id <value> \
    --rehydration-type <value> \
    --source-contact-id <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--initial-contact-id` | **Yes** | string | -- | Initial contact ID |
| `--rehydration-type` | **Yes** | string | -- | `ENTIRE_PAST_SESSION` or `FROM_SEGMENT` |
| `--source-contact-id` | **Yes** | string | -- | Source contact ID for rehydration |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "ContinuedFromContactId": "string"
}
```

---

### 3.20 `create-participant`

Adds a participant to a chat contact.

**Synopsis:**
```bash
aws connect create-participant \
    --instance-id <value> \
    --contact-id <value> \
    --participant-details <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--contact-id` | **Yes** | string | -- | Contact ID |
| `--participant-details` | **Yes** | structure | -- | Participant details with DisplayName and ParticipantRole |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "ParticipantCredentials": { "ParticipantToken": "string", "Expiry": "string" },
    "ParticipantId": "string"
}
```

---

### 3.21 `get-contact-metrics`

Gets contact-level metrics for a specific contact.

**Synopsis:**
```bash
aws connect get-contact-metrics \
    --instance-id <value> \
    --contact-id <value> \
    --metrics <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--contact-id` | **Yes** | string | -- | Contact ID |
| `--metrics` | **Yes** | list | -- | List of metric names to retrieve |

**Output Schema:**
```json
{
    "ContactMetrics": [
        { "Name": "string", "Value": "double", "Unit": "string" }
    ]
}
```
