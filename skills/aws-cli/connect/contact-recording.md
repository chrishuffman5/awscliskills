# Contact Recording

### 4.1 `start-contact-recording`

Starts recording the specified contact.

**Synopsis:**
```bash
aws connect start-contact-recording \
    --instance-id <value> \
    --contact-id <value> \
    --initial-contact-id <value> \
    --voice-recording-configuration <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--contact-id` | **Yes** | string | -- | Contact ID |
| `--initial-contact-id` | **Yes** | string | -- | Initial contact ID |
| `--voice-recording-configuration` | **Yes** | structure | -- | `VoiceRecordingTrack`: `FROM_AGENT`, `TO_AGENT`, `ALL` |

**Output:** None

---

### 4.2 `stop-contact-recording`

Stops recording a contact.

**Synopsis:**
```bash
aws connect stop-contact-recording \
    --instance-id <value> \
    --contact-id <value> \
    --initial-contact-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--contact-id` | **Yes** | string | -- | Contact ID |
| `--initial-contact-id` | **Yes** | string | -- | Initial contact ID |

**Output:** None

---

### 4.3 `suspend-contact-recording`

Suspends recording of a contact (can be resumed later).

**Synopsis:**
```bash
aws connect suspend-contact-recording \
    --instance-id <value> \
    --contact-id <value> \
    --initial-contact-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--contact-id` | **Yes** | string | -- | Contact ID |
| `--initial-contact-id` | **Yes** | string | -- | Initial contact ID |

**Output:** None

---

### 4.4 `resume-contact-recording`

Resumes recording after suspension.

**Synopsis:**
```bash
aws connect resume-contact-recording \
    --instance-id <value> \
    --contact-id <value> \
    --initial-contact-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--contact-id` | **Yes** | string | -- | Contact ID |
| `--initial-contact-id` | **Yes** | string | -- | Initial contact ID |

**Output:** None

---

### 4.5 `start-contact-streaming`

Starts streaming contact events to a Kinesis stream.

**Synopsis:**
```bash
aws connect start-contact-streaming \
    --instance-id <value> \
    --contact-id <value> \
    --chat-streaming-configuration <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--contact-id` | **Yes** | string | -- | Contact ID |
| `--chat-streaming-configuration` | **Yes** | structure | -- | Streaming endpoint ARN |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "StreamingId": "string"
}
```

---

### 4.6 `stop-contact-streaming`

Stops streaming contact events.

**Synopsis:**
```bash
aws connect stop-contact-streaming \
    --instance-id <value> \
    --contact-id <value> \
    --streaming-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--contact-id` | **Yes** | string | -- | Contact ID |
| `--streaming-id` | **Yes** | string | -- | Streaming ID from start command |

**Output:** None

---

### 4.7 `start-contact-media-processing`

Starts media processing for a contact (e.g., real-time audio).

**Synopsis:**
```bash
aws connect start-contact-media-processing \
    --instance-id <value> \
    --contact-id <value> \
    --media-processing-configuration <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--contact-id` | **Yes** | string | -- | Contact ID |
| `--media-processing-configuration` | **Yes** | structure | -- | Media processing config |

**Output Schema:**
```json
{
    "MediaProcessingId": "string"
}
```

---

### 4.8 `stop-contact-media-processing`

Stops media processing for a contact.

**Synopsis:**
```bash
aws connect stop-contact-media-processing \
    --instance-id <value> \
    --contact-id <value> \
    --media-processing-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--contact-id` | **Yes** | string | -- | Contact ID |
| `--media-processing-id` | **Yes** | string | -- | Media processing ID |

**Output:** None

---

### 4.9 `start-screen-sharing`

Starts screen sharing for a contact.

**Synopsis:**
```bash
aws connect start-screen-sharing \
    --instance-id <value> \
    --contact-id <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--contact-id` | **Yes** | string | -- | Contact ID |
| `--client-token` | No | string | Auto | Idempotency token |

**Output:** None

---

### 4.10 `list-realtime-contact-analysis-segments-v2`

Lists real-time contact analysis segments. **Paginated operation.**

**Synopsis:**
```bash
aws connect list-realtime-contact-analysis-segments-v2 \
    --instance-id <value> \
    --contact-id <value> \
    --output-type <value> \
    --segment-types <value> \
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
| `--output-type` | **Yes** | string | -- | `Raw` or `Redacted` |
| `--segment-types` | **Yes** | list | -- | `Transcript`, `Categories`, `Issues`, `Event`, `Attachments`, `PostContactSummary` |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-100) |

**Output Schema:**
```json
{
    "Channel": "VOICE|CHAT",
    "Status": "IN_PROGRESS|FAILED|COMPLETED",
    "Segments": [
        {
            "Transcript": { "Id": "string", "ParticipantId": "string", "ParticipantRole": "string", "DisplayName": "string", "Content": "string", "ContentType": "string", "Time": {} },
            "Categories": {},
            "Issues": {},
            "Event": {},
            "Attachments": {},
            "PostContactSummary": {}
        }
    ],
    "NextToken": "string"
}
```

---

### 4.11 `list-contact-references`

Lists contact references. **Paginated operation.**

**Synopsis:**
```bash
aws connect list-contact-references \
    --instance-id <value> \
    --contact-id <value> \
    --reference-types <value> \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--contact-id` | **Yes** | string | -- | Contact ID |
| `--reference-types` | **Yes** | list | -- | `URL`, `ATTACHMENT`, `NUMBER`, `STRING`, `DATE`, `EMAIL`, `CONTACT_ANALYSIS`, `EMAIL_MESSAGE` |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "ReferenceSummaryList": [
        { "Url": { "Name": "string", "Value": "string" }, "Attachment": { "Name": "string", "Value": "string", "Status": "string" } }
    ],
    "NextToken": "string"
}
```
