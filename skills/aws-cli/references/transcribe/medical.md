# Medical

### 3.1 `start-medical-transcription-job`

Starts an asynchronous medical transcription job. Supports primary care dictation and conversation audio.

**Synopsis:**
```bash
aws transcribe start-medical-transcription-job \
    --medical-transcription-job-name <value> \
    --language-code <value> \
    --media <value> \
    --output-bucket-name <value> \
    --specialty <value> \
    --type <value> \
    [--media-sample-rate-hertz <value>] \
    [--media-format <value>] \
    [--output-key <value>] \
    [--output-encryption-kms-key-id <value>] \
    [--kms-encryption-context <value>] \
    [--settings <value>] \
    [--content-identification-type <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--medical-transcription-job-name` | **Yes** | string | -- | Unique job name (1-200 chars, pattern: `^[0-9a-zA-Z._-]+`) |
| `--language-code` | **Yes** | string | -- | Only `en-US` supported for medical transcription |
| `--media` | **Yes** | structure | -- | S3 location. Shorthand: `MediaFileUri=s3://bucket/audio.wav` |
| `--output-bucket-name` | **Yes** | string | -- | S3 bucket for output (max 64 chars, no `s3://` prefix) |
| `--specialty` | **Yes** | string | -- | Only `PRIMARYCARE` supported |
| `--type` | **Yes** | string | -- | `CONVERSATION` or `DICTATION` |
| `--media-sample-rate-hertz` | No | integer | auto | Sample rate (16000-48000 Hz) |
| `--media-format` | No | string | auto | Format: `mp3`, `mp4`, `wav`, `flac`, `ogg`, `amr`, `webm`, `m4a` |
| `--output-key` | No | string | job name | S3 key for output (1-1024 chars) |
| `--output-encryption-kms-key-id` | No | string | SSE-S3 | KMS key for output encryption |
| `--kms-encryption-context` | No | map | -- | Encryption context key:value pairs (1-10 pairs) |
| `--settings` | No | structure | -- | Speaker labels, channel ID, vocabulary, alternatives |
| `--content-identification-type` | No | string | -- | Only `PHI` (identifies personal health information) |
| `--tags` | No | list | -- | Tags. Shorthand: `Key=string,Value=string ...` |

**Settings Structure:**
```json
{
    "ShowSpeakerLabels": true,
    "MaxSpeakerLabels": "integer (2-30)",
    "ChannelIdentification": true,
    "ShowAlternatives": true,
    "MaxAlternatives": "integer (2-10)",
    "VocabularyName": "string"
}
```

**Output Schema:**
```json
{
    "MedicalTranscriptionJob": {
        "MedicalTranscriptionJobName": "string",
        "TranscriptionJobStatus": "QUEUED|IN_PROGRESS|FAILED|COMPLETED",
        "LanguageCode": "string",
        "MediaSampleRateHertz": "integer",
        "MediaFormat": "string",
        "Media": {
            "MediaFileUri": "string"
        },
        "Transcript": {
            "TranscriptFileUri": "string"
        },
        "StartTime": "timestamp",
        "CreationTime": "timestamp",
        "CompletionTime": "timestamp",
        "FailureReason": "string",
        "Settings": {},
        "ContentIdentificationType": "PHI",
        "Specialty": "PRIMARYCARE",
        "Type": "CONVERSATION|DICTATION",
        "Tags": []
    }
}
```

---

### 3.2 `get-medical-transcription-job`

Gets details of a medical transcription job.

**Synopsis:**
```bash
aws transcribe get-medical-transcription-job \
    --medical-transcription-job-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--medical-transcription-job-name` | **Yes** | string | -- | Name of the job (1-200 chars) |

**Output Schema:** Same as `start-medical-transcription-job` output.

---

### 3.3 `list-medical-transcription-jobs`

Lists medical transcription jobs. **Paginated operation.**

**Synopsis:**
```bash
aws transcribe list-medical-transcription-jobs \
    [--status <value>] \
    [--job-name-contains <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--status` | No | string | -- | Filter by status: `QUEUED`, `IN_PROGRESS`, `COMPLETED`, `FAILED` |
| `--job-name-contains` | No | string | -- | Filter by name substring |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "Status": "string",
    "NextToken": "string",
    "MedicalTranscriptionJobSummaries": [
        {
            "MedicalTranscriptionJobName": "string",
            "CreationTime": "timestamp",
            "StartTime": "timestamp",
            "CompletionTime": "timestamp",
            "LanguageCode": "string",
            "TranscriptionJobStatus": "string",
            "FailureReason": "string",
            "OutputLocationType": "CUSTOMER_BUCKET|SERVICE_BUCKET",
            "Specialty": "PRIMARYCARE",
            "ContentIdentificationType": "PHI",
            "Type": "CONVERSATION|DICTATION"
        }
    ]
}
```

---

### 3.4 `delete-medical-transcription-job`

Deletes a medical transcription job.

**Synopsis:**
```bash
aws transcribe delete-medical-transcription-job \
    --medical-transcription-job-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--medical-transcription-job-name` | **Yes** | string | -- | Name of the job to delete |

**Output:** None (HTTP 200 on success)

---

### 3.5 `start-medical-scribe-job`

Starts a Medical Scribe job that transcribes clinician-patient conversations and generates clinical notes.

**Synopsis:**
```bash
aws transcribe start-medical-scribe-job \
    --medical-scribe-job-name <value> \
    --media <value> \
    --output-bucket-name <value> \
    --data-access-role-arn <value> \
    --settings <value> \
    [--output-encryption-kms-key-id <value>] \
    [--kms-encryption-context <value>] \
    [--channel-definitions <value>] \
    [--tags <value>] \
    [--medical-scribe-context <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--medical-scribe-job-name` | **Yes** | string | -- | Unique job name (1-200 chars) |
| `--media` | **Yes** | structure | -- | S3 location. Shorthand: `MediaFileUri=s3://bucket/audio.wav` |
| `--output-bucket-name` | **Yes** | string | -- | S3 bucket for output (max 64 chars) |
| `--data-access-role-arn` | **Yes** | string | -- | IAM role ARN with S3 read/write and KMS permissions |
| `--settings` | **Yes** | structure | -- | Scribe settings (speaker labels or channel ID required) |
| `--output-encryption-kms-key-id` | No | string | SSE-S3 | KMS key for output encryption |
| `--kms-encryption-context` | No | map | -- | Encryption context key:value pairs (1-10 pairs) |
| `--channel-definitions` | No | list | -- | Channel-to-speaker mapping (exactly 2 items). Shorthand: `ChannelId=0,ParticipantRole=CLINICIAN ChannelId=1,ParticipantRole=PATIENT` |
| `--tags` | No | list | -- | Tags. Shorthand: `Key=string,Value=string ...` |
| `--medical-scribe-context` | No | structure | -- | Clinical note context (patient pronouns) |

**Settings Structure (one of `ShowSpeakerLabels` or `ChannelIdentification` required):**
```json
{
    "ShowSpeakerLabels": true,
    "MaxSpeakerLabels": "integer (2-30)",
    "ChannelIdentification": true,
    "VocabularyName": "string",
    "VocabularyFilterName": "string",
    "VocabularyFilterMethod": "remove|mask|tag",
    "ClinicalNoteGenerationSettings": {
        "NoteTemplate": "HISTORY_AND_PHYSICAL|GIRPP|BIRP|SIRP|DAP|BEHAVIORAL_SOAP|PHYSICAL_SOAP"
    }
}
```

**Channel Definitions Structure:**
```json
[
    {"ChannelId": 0, "ParticipantRole": "CLINICIAN"},
    {"ChannelId": 1, "ParticipantRole": "PATIENT"}
]
```

**Medical Scribe Context Structure:**
```json
{
    "PatientContext": {
        "Pronouns": "HE_HIM|SHE_HER|THEY_THEM"
    }
}
```

**Note Template Values:**

| Template | Sections |
|----------|----------|
| `HISTORY_AND_PHYSICAL` | Chief Complaint, History of Present Illness, Review of Systems, Past Medical History, Assessment, Plan |
| `GIRPP` | Goal, Intervention, Response, Progress, Plan |
| `BIRP` | Behavior, Intervention, Response, Plan |
| `SIRP` | Situation, Intervention, Response, Plan |
| `DAP` | Data, Assessment, Plan |
| `BEHAVIORAL_SOAP` | Subjective, Objective, Assessment, Plan (behavioral health) |
| `PHYSICAL_SOAP` | Subjective, Objective, Assessment, Plan (physical health) |

**Output Schema:**
```json
{
    "MedicalScribeJob": {
        "MedicalScribeJobName": "string",
        "MedicalScribeJobStatus": "QUEUED|IN_PROGRESS|FAILED|COMPLETED",
        "LanguageCode": "en-US",
        "Media": {
            "MediaFileUri": "string"
        },
        "MedicalScribeOutput": {
            "TranscriptFileUri": "string",
            "ClinicalDocumentUri": "string"
        },
        "StartTime": "timestamp",
        "CreationTime": "timestamp",
        "CompletionTime": "timestamp",
        "FailureReason": "string",
        "Settings": {},
        "DataAccessRoleArn": "string",
        "ChannelDefinitions": [],
        "MedicalScribeContextProvided": "boolean",
        "Tags": []
    }
}
```

---

### 3.6 `get-medical-scribe-job`

Gets details of a Medical Scribe job.

**Synopsis:**
```bash
aws transcribe get-medical-scribe-job \
    --medical-scribe-job-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--medical-scribe-job-name` | **Yes** | string | -- | Name of the job (1-200 chars) |

**Output Schema:** Same as `start-medical-scribe-job` output.

---

### 3.7 `list-medical-scribe-jobs`

Lists Medical Scribe jobs. **Paginated operation.**

**Synopsis:**
```bash
aws transcribe list-medical-scribe-jobs \
    [--status <value>] \
    [--job-name-contains <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--status` | No | string | -- | Filter by status: `QUEUED`, `IN_PROGRESS`, `COMPLETED`, `FAILED` |
| `--job-name-contains` | No | string | -- | Filter by name substring |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "NextToken": "string",
    "MedicalScribeJobSummaries": [
        {
            "MedicalScribeJobName": "string",
            "CreationTime": "timestamp",
            "StartTime": "timestamp",
            "CompletionTime": "timestamp",
            "LanguageCode": "en-US",
            "MedicalScribeJobStatus": "string",
            "FailureReason": "string"
        }
    ]
}
```

---

### 3.8 `delete-medical-scribe-job`

Deletes a Medical Scribe job.

**Synopsis:**
```bash
aws transcribe delete-medical-scribe-job \
    --medical-scribe-job-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--medical-scribe-job-name` | **Yes** | string | -- | Name of the job to delete |

**Output:** None (HTTP 200 on success)

---

### 3.9 `create-medical-vocabulary`

Creates a custom medical vocabulary for improving transcription accuracy.

**Synopsis:**
```bash
aws transcribe create-medical-vocabulary \
    --vocabulary-name <value> \
    --language-code <value> \
    --vocabulary-file-uri <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--vocabulary-name` | **Yes** | string | -- | Unique vocabulary name (1-200 chars) |
| `--language-code` | **Yes** | string | -- | Only `en-US` supported for medical vocabularies |
| `--vocabulary-file-uri` | **Yes** | string | -- | S3 URI of vocabulary text file (e.g., `s3://bucket/vocab.txt`) |
| `--tags` | No | list | -- | Tags. Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "VocabularyName": "string",
    "LanguageCode": "string",
    "VocabularyState": "PENDING|READY|FAILED",
    "LastModifiedTime": "timestamp",
    "FailureReason": "string"
}
```

---

### 3.10 `get-medical-vocabulary`

Gets details of a medical vocabulary.

**Synopsis:**
```bash
aws transcribe get-medical-vocabulary \
    --vocabulary-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--vocabulary-name` | **Yes** | string | -- | Name of the vocabulary (1-200 chars) |

**Output Schema:**
```json
{
    "VocabularyName": "string",
    "LanguageCode": "string",
    "VocabularyState": "PENDING|READY|FAILED",
    "LastModifiedTime": "timestamp",
    "FailureReason": "string",
    "DownloadUri": "string"
}
```

---

### 3.11 `list-medical-vocabularies`

Lists medical vocabularies. **Paginated operation.**

**Synopsis:**
```bash
aws transcribe list-medical-vocabularies \
    [--state-equals <value>] \
    [--name-contains <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--state-equals` | No | string | -- | Filter by state: `PENDING`, `READY`, `FAILED` |
| `--name-contains` | No | string | -- | Filter by name substring |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "Status": "string",
    "NextToken": "string",
    "Vocabularies": [
        {
            "VocabularyName": "string",
            "LanguageCode": "string",
            "LastModifiedTime": "timestamp",
            "VocabularyState": "PENDING|READY|FAILED"
        }
    ]
}
```

---

### 3.12 `update-medical-vocabulary`

Updates a medical vocabulary with new terms.

**Synopsis:**
```bash
aws transcribe update-medical-vocabulary \
    --vocabulary-name <value> \
    --language-code <value> \
    --vocabulary-file-uri <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--vocabulary-name` | **Yes** | string | -- | Name of the vocabulary to update |
| `--language-code` | **Yes** | string | -- | Language code (must match existing) |
| `--vocabulary-file-uri` | **Yes** | string | -- | S3 URI of updated vocabulary text file |

**Output Schema:**
```json
{
    "VocabularyName": "string",
    "LanguageCode": "string",
    "LastModifiedTime": "timestamp",
    "VocabularyState": "PENDING|READY|FAILED"
}
```

---

### 3.13 `delete-medical-vocabulary`

Deletes a medical vocabulary.

**Synopsis:**
```bash
aws transcribe delete-medical-vocabulary \
    --vocabulary-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--vocabulary-name` | **Yes** | string | -- | Name of the vocabulary to delete |

**Output:** None (HTTP 200 on success)
