# Transcription Jobs

### 1.1 `start-transcription-job`

Starts a standard asynchronous transcription job. Input audio from S3, output transcript to S3.

**Synopsis:**
```bash
aws transcribe start-transcription-job \
    --transcription-job-name <value> \
    --media <value> \
    [--language-code <value>] \
    [--identify-language | --no-identify-language] \
    [--identify-multiple-languages | --no-identify-multiple-languages] \
    [--language-options <value>] \
    [--media-format <value>] \
    [--media-sample-rate-hertz <value>] \
    [--output-bucket-name <value>] \
    [--output-key <value>] \
    [--output-encryption-kms-key-id <value>] \
    [--settings <value>] \
    [--model-settings <value>] \
    [--job-execution-settings <value>] \
    [--content-redaction <value>] \
    [--subtitles <value>] \
    [--tags <value>] \
    [--language-id-settings <value>] \
    [--toxicity-detection <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--transcription-job-name` | **Yes** | string | -- | Unique job name (1-200 chars, pattern: `^[0-9a-zA-Z._-]+`) |
| `--media` | **Yes** | structure | -- | S3 location. Shorthand: `MediaFileUri=s3://bucket/file.mp3` |
| `--language-code` | No* | string | -- | Language code (e.g., `en-US`). Required unless using language identification |
| `--identify-language` | No* | boolean | false | Enable auto language identification |
| `--identify-multiple-languages` | No* | boolean | false | Enable multi-language identification |
| `--language-options` | No | list(string) | -- | Restrict language identification to these codes |
| `--media-format` | No | string | auto | Format: `mp3`, `mp4`, `wav`, `flac`, `ogg`, `amr`, `webm`, `m4a` |
| `--media-sample-rate-hertz` | No | integer | auto | Sample rate (8000-48000 Hz) |
| `--output-bucket-name` | No | string | -- | S3 bucket for output (max 64 chars) |
| `--output-key` | No | string | -- | S3 key for output (1-1024 chars) |
| `--output-encryption-kms-key-id` | No | string | -- | KMS key for output encryption |
| `--settings` | No | structure | -- | Speaker labels, channel ID, vocabulary, alternatives |
| `--model-settings` | No | structure | -- | Custom language model. Shorthand: `LanguageModelName=string` |
| `--job-execution-settings` | No | structure | -- | Deferred execution and data access role |
| `--content-redaction` | No | structure | -- | PII redaction settings |
| `--subtitles` | No | structure | -- | Subtitle generation: `Formats=vtt\|srt,OutputStartIndex=0\|1` |
| `--tags` | No | list | -- | Tags. Shorthand: `Key=string,Value=string ...` |
| `--language-id-settings` | No | map | -- | Per-language custom models/vocabularies |
| `--toxicity-detection` | No | list | -- | Toxic speech detection |

*One of `--language-code`, `--identify-language`, or `--identify-multiple-languages` is required.

**Settings Structure:**
```json
{
    "VocabularyName": "string",
    "ShowSpeakerLabels": true,
    "MaxSpeakerLabels": "integer (2-30)",
    "ChannelIdentification": true,
    "ShowAlternatives": true,
    "MaxAlternatives": "integer (2-10)",
    "VocabularyFilterName": "string",
    "VocabularyFilterMethod": "remove|mask|tag"
}
```

**Content Redaction Structure:**
```json
{
    "RedactionType": "PII",
    "RedactionOutput": "redacted|redacted_and_unredacted",
    "PiiEntityTypes": ["BANK_ACCOUNT_NUMBER", "BANK_ROUTING", "CREDIT_DEBIT_NUMBER", "CREDIT_DEBIT_CVV", "CREDIT_DEBIT_EXPIRY", "PIN", "EMAIL", "ADDRESS", "NAME", "PHONE", "SSN", "ALL"]
}
```

**Output Schema:**
```json
{
    "TranscriptionJob": {
        "TranscriptionJobName": "string",
        "TranscriptionJobStatus": "QUEUED|IN_PROGRESS|FAILED|COMPLETED",
        "LanguageCode": "string",
        "MediaSampleRateHertz": "integer",
        "MediaFormat": "string",
        "Media": {
            "MediaFileUri": "string"
        },
        "Transcript": {
            "TranscriptFileUri": "string",
            "RedactedTranscriptFileUri": "string"
        },
        "StartTime": "timestamp",
        "CreationTime": "timestamp",
        "CompletionTime": "timestamp",
        "FailureReason": "string",
        "Settings": {},
        "ModelSettings": {},
        "JobExecutionSettings": {},
        "ContentRedaction": {},
        "IdentifyLanguage": "boolean",
        "IdentifyMultipleLanguages": "boolean",
        "LanguageOptions": ["string"],
        "IdentifiedLanguageScore": "float",
        "LanguageCodes": [
            {
                "LanguageCode": "string",
                "DurationInSeconds": "float"
            }
        ],
        "Subtitles": {
            "Formats": ["vtt", "srt"],
            "SubtitleFileUris": ["string"],
            "OutputStartIndex": "integer"
        },
        "Tags": [],
        "LanguageIdSettings": {},
        "ToxicityDetection": []
    }
}
```

---

### 1.2 `get-transcription-job`

Gets details of a transcription job.

**Synopsis:**
```bash
aws transcribe get-transcription-job \
    --transcription-job-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--transcription-job-name` | **Yes** | string | -- | Name of the job |

**Output Schema:** Same as `start-transcription-job` output.

---

### 1.3 `list-transcription-jobs`

Lists transcription jobs. **Paginated operation.**

**Synopsis:**
```bash
aws transcribe list-transcription-jobs \
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
    "TranscriptionJobSummaries": [
        {
            "TranscriptionJobName": "string",
            "CreationTime": "timestamp",
            "StartTime": "timestamp",
            "CompletionTime": "timestamp",
            "LanguageCode": "string",
            "TranscriptionJobStatus": "string",
            "FailureReason": "string",
            "OutputLocationType": "CUSTOMER_BUCKET|SERVICE_BUCKET",
            "ContentRedaction": {},
            "ModelSettings": {},
            "IdentifyLanguage": "boolean",
            "IdentifyMultipleLanguages": "boolean",
            "IdentifiedLanguageScore": "float",
            "LanguageCodes": [],
            "ToxicityDetection": []
        }
    ]
}
```

---

### 1.4 `delete-transcription-job`

Deletes a transcription job and its output.

**Synopsis:**
```bash
aws transcribe delete-transcription-job \
    --transcription-job-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--transcription-job-name` | **Yes** | string | -- | Name of the job to delete |

**Output:** None (HTTP 200 on success)
