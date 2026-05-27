# Voice Profiles & Analytics

CLI namespace: `aws chime-sdk-voice`

### 16.1 `create-voice-profile-domain`

Creates a voice profile domain for storing voice prints. Requires KMS encryption.

**Synopsis:**
```bash
aws chime-sdk-voice create-voice-profile-domain \
    --name <value> \
    --server-side-encryption-configuration <value> \
    [--description <value>] \
    [--client-request-token <value>] \
    [--tags <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Domain name (1-256 chars) |
| `--server-side-encryption-configuration` | **Yes** | structure | -- | KMS encryption config |
| `--description` | No | string | None | Description (0-1024 chars) |
| `--client-request-token` | No | string | Auto | Idempotency token |
| `--tags` | No | list | None | Tags (1-50) |

**ServerSideEncryptionConfiguration structure:**
```json
{
    "KmsKeyArn": "arn:aws:kms:us-east-1:123456789012:key/xxx"
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

### 16.2 `get-voice-profile-domain` / `list-voice-profile-domains` / `update-voice-profile-domain` / `delete-voice-profile-domain`

```bash
aws chime-sdk-voice get-voice-profile-domain \
    --voice-profile-domain-id <value>

aws chime-sdk-voice list-voice-profile-domains \
    [--next-token <value>] [--max-results <value>]

aws chime-sdk-voice update-voice-profile-domain \
    --voice-profile-domain-id <value> \
    [--name <value>] [--description <value>]

aws chime-sdk-voice delete-voice-profile-domain \
    --voice-profile-domain-id <value>
```

---

### 16.3 `create-voice-profile`

Creates a voice profile from a completed speaker search task.

**Synopsis:**
```bash
aws chime-sdk-voice create-voice-profile \
    --speaker-search-task-id <value>
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

> **Important:** You must provide all notices and obtain all consents from the speaker as required under applicable privacy and biometrics laws before creating voice profiles.

---

### 16.4 `get-voice-profile` / `update-voice-profile` / `delete-voice-profile`

```bash
aws chime-sdk-voice get-voice-profile --voice-profile-id <value>

aws chime-sdk-voice update-voice-profile \
    --voice-profile-id <value> \
    --speaker-search-task-id <value>

aws chime-sdk-voice delete-voice-profile --voice-profile-id <value>
```

---

### 16.5 `start-speaker-search-task`

Starts a speaker search task to identify a voice profile match.

**Synopsis:**
```bash
aws chime-sdk-voice start-speaker-search-task \
    --voice-connector-id <value> \
    --transaction-id <value> \
    --voice-profile-domain-id <value> \
    [--client-request-token <value>] \
    [--call-leg <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-connector-id` | **Yes** | string | -- | Voice Connector ID |
| `--transaction-id` | **Yes** | string | -- | Transaction ID of the call |
| `--voice-profile-domain-id` | **Yes** | string | -- | Voice profile domain ID |
| `--client-request-token` | No | string | Auto | Idempotency token |
| `--call-leg` | No | string | None | `Caller` or `Callee` |

**Output Schema:**
```json
{
    "SpeakerSearchTask": {
        "SpeakerSearchTaskId": "string",
        "SpeakerSearchTaskStatus": "IN_QUEUE|IN_PROGRESS|PARTIAL_SUCCESS|SUCCEEDED|FAILED|STOPPED",
        "CallDetails": {
            "VoiceConnectorId": "string",
            "TransactionId": "string",
            "IsCaller": "boolean"
        },
        "SpeakerSearchDetails": {
            "Results": [
                {
                    "ConfidenceScore": "float (0-1)",
                    "VoiceProfileId": "string"
                }
            ],
            "VoiceprintGenerationStatus": "VoiceprintGenerationSuccess|VoiceprintGenerationFailure"
        },
        "CreatedTimestamp": "timestamp",
        "UpdatedTimestamp": "timestamp",
        "StartedTimestamp": "timestamp",
        "StatusMessage": "string"
    }
}
```

---

### 16.6 `get-speaker-search-task` / `stop-speaker-search-task`

```bash
aws chime-sdk-voice get-speaker-search-task \
    --voice-connector-id <value> \
    --speaker-search-task-id <value>

aws chime-sdk-voice stop-speaker-search-task \
    --voice-connector-id <value> \
    --speaker-search-task-id <value>
```

---

### 16.7 `start-voice-tone-analysis-task`

Starts a voice tone analysis task to detect sentiment in a call.

**Synopsis:**
```bash
aws chime-sdk-voice start-voice-tone-analysis-task \
    --voice-connector-id <value> \
    --transaction-id <value> \
    --language-code <value> \
    [--client-request-token <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--voice-connector-id` | **Yes** | string | -- | Voice Connector ID |
| `--transaction-id` | **Yes** | string | -- | Transaction ID of the call |
| `--language-code` | **Yes** | string | -- | Language code (`en-US`) |
| `--client-request-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "VoiceToneAnalysisTask": {
        "VoiceToneAnalysisTaskId": "string",
        "VoiceToneAnalysisTaskStatus": "IN_QUEUE|IN_PROGRESS|PARTIAL_SUCCESS|SUCCEEDED|FAILED|STOPPED",
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

### 16.8 `get-voice-tone-analysis-task` / `stop-voice-tone-analysis-task`

```bash
aws chime-sdk-voice get-voice-tone-analysis-task \
    --voice-connector-id <value> \
    --voice-tone-analysis-task-id <value>

aws chime-sdk-voice stop-voice-tone-analysis-task \
    --voice-connector-id <value> \
    --voice-tone-analysis-task-id <value>
```
