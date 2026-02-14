# Meetings

CLI namespace: `aws chime-sdk-meetings`

### 4.1 `create-meeting`

Creates a new Amazon Chime SDK meeting in the specified media Region.

**Synopsis:**
```bash
aws chime-sdk-meetings create-meeting \
    --media-region <value> \
    --external-meeting-id <value> \
    [--client-request-token <value>] \
    [--meeting-host-id <value>] \
    [--notifications-configuration <value>] \
    [--meeting-features <value>] \
    [--primary-meeting-id <value>] \
    [--tenant-ids <value>] \
    [--tags <value>] \
    [--media-placement-network-type <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--media-region` | **Yes** | string | -- | Media region (e.g., `us-east-1`, `eu-west-1`) |
| `--external-meeting-id` | **Yes** | string | -- | External meeting ID (2-64 chars) |
| `--client-request-token` | No | string | Auto | Idempotency token (2-64 chars) |
| `--meeting-host-id` | No | string | None | Reserved (2-64 chars) |
| `--notifications-configuration` | No | structure | None | Lambda/SNS/SQS notification targets |
| `--meeting-features` | No | structure | None | Audio, video, content, attendee features |
| `--primary-meeting-id` | No | string | None | Primary meeting ID for replication (2-64 chars) |
| `--tenant-ids` | No | list | None | Tenant IDs (1-5, 2-256 chars each) |
| `--tags` | No | list | None | Tags (max 50) |
| `--media-placement-network-type` | No | string | None | `Ipv4Only` or `DualStack` |

**MeetingFeatures structure:**
```json
{
    "Audio": {"EchoReduction": "AVAILABLE|UNAVAILABLE"},
    "Video": {"MaxResolution": "None|HD|FHD"},
    "Content": {"MaxResolution": "None|FHD|UHD"},
    "Attendee": {"MaxCount": 25}
}
```

**Output Schema:**
```json
{
    "Meeting": {
        "MeetingId": "string",
        "MeetingHostId": "string",
        "ExternalMeetingId": "string",
        "MediaRegion": "string",
        "MediaPlacement": {
            "AudioHostUrl": "string",
            "AudioFallbackUrl": "string",
            "SignalingUrl": "string",
            "EventIngestionUrl": "string"
        },
        "MeetingFeatures": {},
        "PrimaryMeetingId": "string",
        "TenantIds": [],
        "MeetingArn": "string"
    }
}
```

---

### 4.2 `create-meeting-with-attendees`

Creates a meeting and up to 10 attendees in one call.

**Synopsis:**
```bash
aws chime-sdk-meetings create-meeting-with-attendees \
    --media-region <value> \
    --external-meeting-id <value> \
    --attendees <value> \
    [--client-request-token <value>] \
    [--meeting-features <value>] \
    [--notifications-configuration <value>] \
    [--primary-meeting-id <value>] \
    [--tenant-ids <value>] \
    [--tags <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--media-region` | **Yes** | string | -- | Media region |
| `--external-meeting-id` | **Yes** | string | -- | External meeting ID |
| `--attendees` | **Yes** | list | -- | Attendees to create (1-10) |
| `--client-request-token` | No | string | Auto | Idempotency token |
| `--meeting-features` | No | structure | None | Meeting features |
| `--notifications-configuration` | No | structure | None | Notification config |
| `--primary-meeting-id` | No | string | None | For meeting replication |
| `--tenant-ids` | No | list | None | Tenant IDs |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "Meeting": {},
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

### 4.3 `get-meeting`

Gets meeting details.

**Synopsis:**
```bash
aws chime-sdk-meetings get-meeting \
    --meeting-id <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--meeting-id` | **Yes** | string | -- | Meeting ID (UUID) |

**Output Schema:**
```json
{
    "Meeting": {
        "MeetingId": "string",
        "ExternalMeetingId": "string",
        "MediaRegion": "string",
        "MediaPlacement": {},
        "MeetingFeatures": {},
        "MeetingArn": "string"
    }
}
```

---

### 4.4 `delete-meeting`

Deletes a meeting and its attendees. Resources are released upon deletion.

**Synopsis:**
```bash
aws chime-sdk-meetings delete-meeting \
    --meeting-id <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--meeting-id` | **Yes** | string | -- | Meeting ID (UUID) |

**Output:** None

---

### 4.5 `start-meeting-transcription`

Starts transcription for a meeting using Amazon Transcribe or Amazon Transcribe Medical.

**Synopsis:**
```bash
aws chime-sdk-meetings start-meeting-transcription \
    --meeting-id <value> \
    --transcription-configuration <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--meeting-id` | **Yes** | string | -- | Meeting ID (UUID) |
| `--transcription-configuration` | **Yes** | structure | -- | Transcription settings |

**TranscriptionConfiguration structure:**
```json
{
    "EngineTranscribeSettings": {
        "LanguageCode": "en-US|...",
        "VocabularyFilterMethod": "remove|mask|tag",
        "VocabularyFilterName": "string",
        "VocabularyName": "string",
        "Region": "string",
        "EnablePartialResultsStabilization": true,
        "PartialResultsStability": "low|medium|high",
        "ContentIdentificationType": "PII",
        "ContentRedactionType": "PII",
        "PiiEntityTypes": "string",
        "LanguageModelName": "string",
        "IdentifyLanguage": true,
        "LanguageOptions": "string",
        "PreferredLanguage": "string",
        "VocabularyNames": "string",
        "VocabularyFilterNames": "string"
    }
}
```

**Output:** None

---

### 4.6 `stop-meeting-transcription`

Stops transcription for a meeting.

**Synopsis:**
```bash
aws chime-sdk-meetings stop-meeting-transcription \
    --meeting-id <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--meeting-id` | **Yes** | string | -- | Meeting ID (UUID) |

**Output:** None
