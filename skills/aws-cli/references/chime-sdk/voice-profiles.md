# Voice Profiles

Commands from the `aws chime-sdk-voice` service.

### 16.1 `create-voice-profile-domain`

Creates a voice profile domain for speaker search and voice tone analysis.

**Synopsis:**
```bash
aws chime-sdk-voice create-voice-profile-domain \
    --name <value> \
    --server-side-encryption-configuration <value> \
    [--description <value>] \
    [--client-request-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Domain name (1-256 chars) |
| `--server-side-encryption-configuration` | **Yes** | structure | -- | KMS encryption config |
| `--description` | No | string | None | Description (max 1024 chars) |
| `--client-request-token` | No | string | Auto | Idempotency token (2-64 chars) |
| `--tags` | No | list | None | Tags (max 50) |

**ServerSideEncryptionConfiguration:**
```json
{
    "KmsKeyArn": "string (1-1024 chars, required)"
}
```

**Output Schema:**
```json
{
    "VoiceProfileDomain": {
        "VoiceProfileDomainId": "string",
        "VoiceProfileDomainArn": "string",
        "Name": "string",
        "Description": "string",
        "ServerSideEncryptionConfiguration": {
            "KmsKeyArn": "string"
        },
        "CreatedTimestamp": "timestamp",
        "UpdatedTimestamp": "timestamp"
    }
}
```

---

### 16.2 `get-voice-profile-domain`

Gets voice profile domain details.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-profile-domain-id` | **Yes** | string | -- | Domain ID |

**Output Schema:** Same as `create-voice-profile-domain` VoiceProfileDomain object.

---

### 16.3 `list-voice-profile-domains`

Lists voice profile domains. **Paginated operation.**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-99) |

---

### 16.4 `update-voice-profile-domain`

Updates a voice profile domain.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-profile-domain-id` | **Yes** | string | -- | Domain ID |
| `--name` | No | string | None | Updated name |
| `--description` | No | string | None | Updated description |

---

### 16.5 `delete-voice-profile-domain`

Deletes a voice profile domain.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-profile-domain-id` | **Yes** | string | -- | Domain ID |

**Output:** None

---

### 16.6 `create-voice-profile`

Creates a voice profile from a speaker search task.

**Synopsis:**
```bash
aws chime-sdk-voice create-voice-profile \
    --speaker-search-task-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--speaker-search-task-id` | **Yes** | string | -- | Speaker search task ID |

**Output Schema:**
```json
{
    "VoiceProfile": {
        "VoiceProfileId": "string",
        "VoiceProfileArn": "string",
        "VoiceProfileDomainId": "string",
        "CreatedTimestamp": "timestamp",
        "UpdatedTimestamp": "timestamp",
        "ExpirationTimestamp": "timestamp"
    }
}
```

---

### 16.7 `get-voice-profile`

Gets voice profile details.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-profile-id` | **Yes** | string | -- | Voice profile ID |

**Output Schema:** Same as `create-voice-profile` VoiceProfile object.

---

### 16.8 `list-voice-profiles`

Lists voice profiles in a domain. **Paginated operation.**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-profile-domain-id` | **Yes** | string | -- | Domain ID |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-99) |

---

### 16.9 `update-voice-profile`

Updates a voice profile (re-enrolls the speaker).

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-profile-id` | **Yes** | string | -- | Voice profile ID |
| `--speaker-search-task-id` | **Yes** | string | -- | New speaker search task ID |

---

### 16.10 `delete-voice-profile`

Deletes a voice profile.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-profile-id` | **Yes** | string | -- | Voice profile ID |

**Output:** None

---

### 16.11 `start-speaker-search-task`

Starts a speaker search task.

**Synopsis:**
```bash
aws chime-sdk-voice start-speaker-search-task \
    --voice-connector-id <value> \
    --transaction-id <value> \
    --voice-profile-domain-id <value> \
    [--client-request-token <value>] \
    [--call-leg <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-connector-id` | **Yes** | string | -- | Voice connector ID |
| `--transaction-id` | **Yes** | string | -- | Call transaction ID |
| `--voice-profile-domain-id` | **Yes** | string | -- | Domain ID to search |
| `--client-request-token` | No | string | Auto | Idempotency token |
| `--call-leg` | No | string | None | `Caller` or `Callee` |

**Output Schema:**
```json
{
    "SpeakerSearchTask": {
        "SpeakerSearchTaskId": "string",
        "SpeakerSearchTaskStatus": "NotStarted|InProgress|Failed|Completed",
        "CallDetails": {
            "VoiceConnectorId": "string",
            "TransactionId": "string",
            "IsCaller": "boolean"
        },
        "SpeakerSearchDetails": {
            "Results": [
                {
                    "ConfidenceScore": "float (0.0-1.0)",
                    "VoiceProfileId": "string"
                }
            ],
            "VoipId": "string"
        },
        "CreatedTimestamp": "timestamp",
        "UpdatedTimestamp": "timestamp",
        "StartedTimestamp": "timestamp",
        "StatusMessage": "string"
    }
}
```

---

### 16.12 `get-speaker-search-task`

Gets speaker search task details.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-connector-id` | **Yes** | string | -- | Voice connector ID |
| `--speaker-search-task-id` | **Yes** | string | -- | Task ID |

**Output Schema:** Same as `start-speaker-search-task` SpeakerSearchTask object.

---

### 16.13 `stop-speaker-search-task`

Stops a speaker search task.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-connector-id` | **Yes** | string | -- | Voice connector ID |
| `--speaker-search-task-id` | **Yes** | string | -- | Task ID |

**Output:** None

---

### 16.14 `start-voice-tone-analysis-task`

Starts a voice tone analysis task.

**Synopsis:**
```bash
aws chime-sdk-voice start-voice-tone-analysis-task \
    --voice-connector-id <value> \
    --transaction-id <value> \
    --language-code <value> \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-connector-id` | **Yes** | string | -- | Voice connector ID |
| `--transaction-id` | **Yes** | string | -- | Call transaction ID |
| `--language-code` | **Yes** | string | -- | `en-US` |
| `--client-request-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "VoiceToneAnalysisTask": {
        "VoiceToneAnalysisTaskId": "string",
        "VoiceToneAnalysisTaskStatus": "NotStarted|InProgress|Failed|Completed",
        "CallDetails": {
            "VoiceConnectorId": "string",
            "TransactionId": "string",
            "IsCaller": "boolean"
        },
        "CreatedTimestamp": "timestamp",
        "UpdatedTimestamp": "timestamp",
        "StartedTimestamp": "timestamp",
        "StatusMessage": "string"
    }
}
```

---

### 16.15 `get-voice-tone-analysis-task`

Gets voice tone analysis task details.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-connector-id` | **Yes** | string | -- | Voice connector ID |
| `--voice-tone-analysis-task-id` | **Yes** | string | -- | Task ID |
| `--is-caller` | **Yes** | boolean | -- | Whether to get caller or callee analysis |

**Output Schema:** Same as `start-voice-tone-analysis-task` VoiceToneAnalysisTask object.

---

### 16.16 `stop-voice-tone-analysis-task`

Stops a voice tone analysis task.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-connector-id` | **Yes** | string | -- | Voice connector ID |
| `--voice-tone-analysis-task-id` | **Yes** | string | -- | Task ID |

**Output:** None
