# Stages (Real-Time)

### 6.1 `create-stage`

Creates a real-time stage for interactive video experiences.

**Synopsis:**
```bash
aws ivs-realtime create-stage \
    [--name <value>] \
    [--participant-token-configurations <value>] \
    [--auto-participant-recording-configuration <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | No | string | None | Stage name (0-128 chars) |
| `--participant-token-configurations` | No | list | None | Participant tokens to create (max 12) |
| `--auto-participant-recording-configuration` | No | structure | None | Auto-recording config |
| `--tags` | No | map | None | Key-value tag pairs |

**ParticipantTokenConfiguration:**
```json
[
    {
        "duration": 720,
        "userId": "string",
        "attributes": {"string": "string"},
        "capabilities": ["PUBLISH", "SUBSCRIBE"]
    }
]
```

**AutoParticipantRecordingConfiguration:**
```json
{
    "storageConfigurationArn": "string",
    "mediaTypes": ["AUDIO_VIDEO", "AUDIO_ONLY", "NONE"],
    "thumbnailConfiguration": {
        "recordingMode": "INTERVAL|DISABLED",
        "targetIntervalSeconds": 60,
        "storage": ["SEQUENTIAL", "LATEST"]
    },
    "recordingReconnectWindowSeconds": 0,
    "hlsConfiguration": {"targetSegmentDurationSeconds": 6}
}
```

**Output Schema:**
```json
{
    "stage": {
        "arn": "string",
        "name": "string",
        "activeSessionId": "string",
        "tags": {"string": "string"},
        "autoParticipantRecordingConfiguration": {},
        "endpoints": {
            "events": "string",
            "whip": "string",
            "rtmp": "string",
            "rtmps": "string"
        }
    },
    "participantTokens": [
        {
            "participantId": "string",
            "token": "string",
            "userId": "string",
            "attributes": {"string": "string"},
            "duration": "integer",
            "capabilities": ["PUBLISH|SUBSCRIBE"],
            "expirationTime": "timestamp"
        }
    ]
}
```

---

### 6.2 `get-stage`

Gets details for a stage.

**Synopsis:**
```bash
aws ivs-realtime get-stage \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the stage |

**Output Schema:** `stage` object.

---

### 6.3 `list-stages`

Lists all stages. **Paginated operation.**

**Synopsis:**
```bash
aws ivs-realtime list-stages \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results per page |

---

### 6.4 `update-stage`

Updates a stage's configuration.

**Synopsis:**
```bash
aws ivs-realtime update-stage \
    --arn <value> \
    [--name <value>] \
    [--auto-participant-recording-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the stage |
| `--name` | No | string | None | Updated name |
| `--auto-participant-recording-configuration` | No | structure | None | Updated recording config |

---

### 6.5 `delete-stage`

Deletes a stage.

**Synopsis:**
```bash
aws ivs-realtime delete-stage \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

---

### 6.6 `get-stage-session`

Gets details for a stage session.

**Synopsis:**
```bash
aws ivs-realtime get-stage-session \
    --stage-arn <value> \
    --session-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stage-arn` | **Yes** | string | -- | ARN of the stage |
| `--session-id` | **Yes** | string | -- | Session ID |

---

### 6.7 `list-stage-sessions`

Lists stage sessions. **Paginated operation.**

**Synopsis:**
```bash
aws ivs-realtime list-stage-sessions \
    --stage-arn <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stage-arn` | **Yes** | string | -- | ARN of the stage |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results per page |
