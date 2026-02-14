# Meetings

Commands from the `aws chime-sdk-meetings` service.

### 4.1 `create-meeting`

Creates a new meeting with the specified configuration.

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
    [--media-placement-network-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--media-region` | **Yes** | string | -- | Media region (e.g., `us-east-1`, `eu-west-1`) |
| `--external-meeting-id` | **Yes** | string | -- | External meeting ID (2-64 chars) |
| `--client-request-token` | No | string | Auto | Idempotency token (2-64 chars) |
| `--meeting-host-id` | No | string | None | Reserved (2-64 chars) |
| `--notifications-configuration` | No | structure | None | Notification targets (Lambda, SNS, SQS) |
| `--meeting-features` | No | structure | None | Audio/video feature configuration |
| `--primary-meeting-id` | No | string | None | Primary meeting ID for media replication |
| `--tenant-ids` | No | list | None | Tenant IDs (1-5 items, 2-256 chars each) |
| `--tags` | No | list | None | Tags (max 50) |
| `--media-placement-network-type` | No | string | None | `Ipv4Only` or `DualStack` |

**MeetingFeatures:**
```json
{
    "Audio": { "EchoReduction": "AVAILABLE|UNAVAILABLE" },
    "Video": { "MaxResolution": "None|HD|FHD" },
    "Content": { "MaxResolution": "None|FHD|UHD" },
    "Attendee": { "MaxCount": "integer (1-250)" }
}
```

**NotificationsConfiguration:**
```json
{
    "LambdaFunctionArn": "string",
    "SnsTopicArn": "string",
    "SqsQueueArn": "string"
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
            "TurnControlUrl": "string",
            "EventIngestionUrl": "string"
        },
        "MeetingFeatures": {
            "Audio": { "EchoReduction": "AVAILABLE|UNAVAILABLE" },
            "Video": { "MaxResolution": "None|HD|FHD" },
            "Content": { "MaxResolution": "None|FHD|UHD" },
            "Attendee": { "MaxCount": "integer" }
        },
        "PrimaryMeetingId": "string",
        "TenantIds": ["string"],
        "MeetingArn": "string"
    }
}
```

---

### 4.2 `create-meeting-with-attendees`

Creates a meeting and attendees in a single call.

**Synopsis:**
```bash
aws chime-sdk-meetings create-meeting-with-attendees \
    --media-region <value> \
    --external-meeting-id <value> \
    --attendees <value> \
    [--client-request-token <value>] \
    [--meeting-host-id <value>] \
    [--notifications-configuration <value>] \
    [--meeting-features <value>] \
    [--primary-meeting-id <value>] \
    [--tenant-ids <value>] \
    [--tags <value>] \
    [--media-placement-network-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--media-region` | **Yes** | string | -- | Media region |
| `--external-meeting-id` | **Yes** | string | -- | External meeting ID (2-64 chars) |
| `--attendees` | **Yes** | list | -- | Attendee list (1-20 items) |
| `--client-request-token` | No | string | Auto | Idempotency token |
| `--meeting-host-id` | No | string | None | Reserved |
| `--notifications-configuration` | No | structure | None | Notification targets |
| `--meeting-features` | No | structure | None | Audio/video features |
| `--primary-meeting-id` | No | string | None | Primary meeting ID |
| `--tenant-ids` | No | list | None | Tenant IDs |
| `--tags` | No | list | None | Tags (max 50) |
| `--media-placement-network-type` | No | string | None | `Ipv4Only` or `DualStack` |

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
    "Meeting": { "...same as create-meeting..." },
    "Attendees": [
        {
            "ExternalUserId": "string",
            "AttendeeId": "string",
            "JoinToken": "string",
            "Capabilities": {
                "Audio": "SendReceive|Send|Receive|None",
                "Video": "SendReceive|Send|Receive|None",
                "Content": "SendReceive|Send|Receive|None"
            }
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
    --meeting-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--meeting-id` | **Yes** | string | -- | Meeting ID (UUID format) |

**Output Schema:**
```json
{
    "Meeting": {
        "MeetingId": "string",
        "MeetingHostId": "string",
        "ExternalMeetingId": "string",
        "MediaRegion": "string",
        "MediaPlacement": { "..." },
        "MeetingFeatures": { "..." },
        "PrimaryMeetingId": "string",
        "TenantIds": ["string"],
        "MeetingArn": "string"
    }
}
```

---

### 4.4 `delete-meeting`

Deletes a meeting.

**Synopsis:**
```bash
aws chime-sdk-meetings delete-meeting \
    --meeting-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--meeting-id` | **Yes** | string | -- | Meeting ID |

**Output:** None

---

### 4.5 `start-meeting-transcription`

Starts transcription for a meeting.

**Synopsis:**
```bash
aws chime-sdk-meetings start-meeting-transcription \
    --meeting-id <value> \
    --transcription-configuration <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--meeting-id` | **Yes** | string | -- | Meeting ID |
| `--transcription-configuration` | **Yes** | structure | -- | Transcription config |

**TranscriptionConfiguration:**
```json
{
    "EngineTranscribeSettings": {
        "LanguageCode": "en-US|en-GB|es-US|fr-CA|fr-FR|en-AU|it-IT|de-DE|pt-BR|ja-JP|ko-KR|zh-CN|th-TH|hi-IN",
        "VocabularyFilterMethod": "remove|mask|tag",
        "VocabularyFilterName": "string",
        "VocabularyName": "string",
        "Region": "string",
        "EnablePartialResultsStabilization": "boolean",
        "PartialResultsStability": "low|medium|high",
        "ContentIdentificationType": "PII",
        "ContentRedactionType": "PII",
        "PiiEntityTypes": "string",
        "LanguageModelName": "string",
        "IdentifyLanguage": "boolean",
        "LanguageOptions": "string",
        "PreferredLanguage": "string",
        "VocabularyNames": "string",
        "VocabularyFilterNames": "string"
    },
    "EngineTranscribeMedicalSettings": {
        "LanguageCode": "en-US",
        "Specialty": "PRIMARYCARE|CARDIOLOGY|NEUROLOGY|ONCOLOGY|RADIOLOGY|UROLOGY",
        "Type": "CONVERSATION|DICTATION",
        "VocabularyName": "string",
        "Region": "string",
        "ContentIdentificationType": "PHI"
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
    --meeting-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--meeting-id` | **Yes** | string | -- | Meeting ID |

**Output:** None
