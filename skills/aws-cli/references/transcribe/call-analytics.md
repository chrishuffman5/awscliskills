# Call Analytics

### 2.1 `start-call-analytics-job`

Starts a call analytics transcription job with features like speaker role assignment, summarization, and sentiment analysis.

**Synopsis:**
```bash
aws transcribe start-call-analytics-job \
    --call-analytics-job-name <value> \
    --media <value> \
    [--output-location <value>] \
    [--output-encryption-kms-key-id <value>] \
    [--data-access-role-arn <value>] \
    [--settings <value>] \
    [--channel-definitions <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--call-analytics-job-name` | **Yes** | string | -- | Unique job name (1-200 chars) |
| `--media` | **Yes** | structure | -- | S3 location. Shorthand: `MediaFileUri=s3://bucket/call.mp3` |
| `--output-location` | No | string | -- | S3 output location (e.g., `s3://bucket/folder/`) |
| `--output-encryption-kms-key-id` | No | string | -- | KMS key for output encryption |
| `--data-access-role-arn` | No | string | -- | IAM role ARN with S3 access |
| `--settings` | No | structure | -- | Vocabulary, redaction, summarization settings |
| `--channel-definitions` | No | list | -- | Channel-to-speaker mapping. Shorthand: `ChannelId=0,ParticipantRole=AGENT ChannelId=1,ParticipantRole=CUSTOMER` |
| `--tags` | No | list | -- | Tags. Shorthand: `Key=string,Value=string ...` |

**Settings Structure:**
```json
{
    "VocabularyName": "string",
    "VocabularyFilterName": "string",
    "VocabularyFilterMethod": "remove|mask|tag",
    "LanguageModelName": "string",
    "ContentRedaction": {
        "RedactionType": "PII",
        "RedactionOutput": "redacted|redacted_and_unredacted",
        "PiiEntityTypes": ["string"]
    },
    "LanguageOptions": ["string"],
    "LanguageIdSettings": {},
    "Summarization": {
        "GenerateAbstractiveSummary": "boolean"
    }
}
```

**Output Schema:**
```json
{
    "CallAnalyticsJob": {
        "CallAnalyticsJobName": "string",
        "CallAnalyticsJobStatus": "QUEUED|IN_PROGRESS|FAILED|COMPLETED",
        "CallAnalyticsJobDetails": {
            "Skipped": [
                {
                    "Feature": "GENERATIVE_SUMMARIZATION",
                    "ReasonCode": "INSUFFICIENT_CONVERSATION_CONTENT|FAILED_SAFETY_GUIDELINES",
                    "Message": "string"
                }
            ]
        },
        "LanguageCode": "string",
        "Media": {},
        "Transcript": {
            "TranscriptFileUri": "string",
            "RedactedTranscriptFileUri": "string"
        },
        "StartTime": "timestamp",
        "CreationTime": "timestamp",
        "CompletionTime": "timestamp",
        "FailureReason": "string",
        "DataAccessRoleArn": "string",
        "Settings": {},
        "ChannelDefinitions": [],
        "Tags": []
    }
}
```

---

### 2.2 `get-call-analytics-job`

Gets details of a call analytics job.

**Synopsis:**
```bash
aws transcribe get-call-analytics-job \
    --call-analytics-job-name <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--call-analytics-job-name` | **Yes** | string | -- | Name of the job |

---

### 2.3 `list-call-analytics-jobs`

Lists call analytics jobs. **Paginated operation.**

**Synopsis:**
```bash
aws transcribe list-call-analytics-jobs \
    [--status <value>] \
    [--job-name-contains <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

---

### 2.4 `delete-call-analytics-job`

Deletes a call analytics job.

**Synopsis:**
```bash
aws transcribe delete-call-analytics-job \
    --call-analytics-job-name <value>
```

---

### 2.5 `create-call-analytics-category`

Creates a category for call analytics with rules for matching specific conditions (sentiments, keywords, interruptions, silence).

**Synopsis:**
```bash
aws transcribe create-call-analytics-category \
    --category-name <value> \
    --rules <value> \
    [--input-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--category-name` | **Yes** | string | -- | Category name (1-200 chars) |
| `--rules` | **Yes** | list | -- | Rules defining the category (1-20 rules) |
| `--input-type` | No | string | `POST_CALL` | Input type: `REAL_TIME` or `POST_CALL` |

**Rules Structure (JSON):**
```json
[
    {
        "NonTalkTimeFilter": {
            "Threshold": "long",
            "AbsoluteTimeRange": {"StartTime": "long", "EndTime": "long", "First": "long", "Last": "long"},
            "RelativeTimeRange": {"StartPercentage": "integer", "EndPercentage": "integer", "First": "integer", "Last": "integer"},
            "Negate": "boolean"
        },
        "InterruptionFilter": {
            "Threshold": "long",
            "ParticipantRole": "AGENT|CUSTOMER",
            "AbsoluteTimeRange": {},
            "RelativeTimeRange": {},
            "Negate": "boolean"
        },
        "TranscriptFilter": {
            "TranscriptFilterType": "EXACT",
            "AbsoluteTimeRange": {},
            "RelativeTimeRange": {},
            "ParticipantRole": "AGENT|CUSTOMER",
            "Negate": "boolean",
            "Targets": ["string"]
        },
        "SentimentFilter": {
            "Sentiments": ["POSITIVE|NEGATIVE|NEUTRAL|MIXED"],
            "AbsoluteTimeRange": {},
            "RelativeTimeRange": {},
            "ParticipantRole": "AGENT|CUSTOMER",
            "Negate": "boolean"
        }
    }
]
```

**Output Schema:**
```json
{
    "CategoryProperties": {
        "CategoryName": "string",
        "Rules": [],
        "CreateTime": "timestamp",
        "LastUpdateTime": "timestamp",
        "InputType": "REAL_TIME|POST_CALL"
    }
}
```

---

### 2.6 `get-call-analytics-category`

Gets details of a call analytics category.

**Synopsis:**
```bash
aws transcribe get-call-analytics-category \
    --category-name <value>
```

---

### 2.7 `list-call-analytics-categories`

Lists call analytics categories. **Paginated operation.**

**Synopsis:**
```bash
aws transcribe list-call-analytics-categories \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

---

### 2.8 `update-call-analytics-category`

Updates a call analytics category.

**Synopsis:**
```bash
aws transcribe update-call-analytics-category \
    --category-name <value> \
    --rules <value> \
    [--input-type <value>]
```

---

### 2.9 `delete-call-analytics-category`

Deletes a call analytics category.

**Synopsis:**
```bash
aws transcribe delete-call-analytics-category \
    --category-name <value>
```

**Output:** None (HTTP 200 on success)
