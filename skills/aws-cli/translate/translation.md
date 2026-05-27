# Translation

### 1.1 `translate-text`

Translates input text from the source language to the target language. Supports real-time translation with optional custom terminology and translation settings.

**Synopsis:**
```bash
aws translate translate-text \
    --text <value> \
    --source-language-code <value> \
    --target-language-code <value> \
    [--terminology-names <value>] \
    [--settings <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--text` | **Yes** | string | -- | Text to translate (max 10,000 bytes) |
| `--source-language-code` | **Yes** | string | -- | Language code of the source text (2-5 chars). Use `auto` for auto-detection |
| `--target-language-code` | **Yes** | string | -- | Language code for the target translation (2-5 chars) |
| `--terminology-names` | No | list(string) | None | Custom terminology names to apply (max 256 terms per list) |
| `--settings` | No | structure | None | Translation output settings (Formality, Profanity, Brevity) |

**Settings Structure:**
```json
{
    "Formality": "FORMAL|INFORMAL",
    "Profanity": "MASK",
    "Brevity": "ON"
}
```

**Output Schema:**
```json
{
    "TranslatedText": "string",
    "SourceLanguageCode": "string",
    "TargetLanguageCode": "string",
    "AppliedTerminologies": [
        {
            "Name": "string",
            "Terms": [
                {
                    "SourceText": "string",
                    "TargetText": "string"
                }
            ]
        }
    ],
    "AppliedSettings": {
        "Formality": "FORMAL|INFORMAL",
        "Profanity": "MASK",
        "Brevity": "ON"
    }
}
```

---

### 1.2 `translate-document`

Translates a document from the source language to the target language. Supports plain text, HTML, and Word document formats.

**Synopsis:**
```bash
aws translate translate-document \
    --document <value> \
    --document-content <value> \
    --source-language-code <value> \
    --target-language-code <value> \
    [--terminology-names <value>] \
    [--settings <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--document` | **Yes** | structure | -- | Document content type. Shorthand: `ContentType=text/plain` |
| `--document-content` | **Yes** | blob | -- | Path to document file: `fileb://data.txt` (max 100 KB) |
| `--source-language-code` | **Yes** | string | -- | Language code of source document (2-5 chars). Use `auto` for auto-detection |
| `--target-language-code` | **Yes** | string | -- | Language code for translated document (2-5 chars) |
| `--terminology-names` | No | list(string) | None | Custom terminology names to apply (max one per request) |
| `--settings` | No | structure | None | Translation output settings (Formality, Profanity, Brevity) |

**Supported ContentType values:**
- `text/html`
- `text/plain`
- `application/vnd.openxmlformats-officedocument.wordprocessingml.document`

**Output Schema:**
```json
{
    "TranslatedDocument": {
        "Content": "blob"
    },
    "SourceLanguageCode": "string",
    "TargetLanguageCode": "string",
    "AppliedTerminologies": [
        {
            "Name": "string",
            "Terms": [
                {
                    "SourceText": "string",
                    "TargetText": "string"
                }
            ]
        }
    ],
    "AppliedSettings": {
        "Formality": "FORMAL|INFORMAL",
        "Profanity": "MASK",
        "Brevity": "ON"
    }
}
```

---

### 1.3 `start-text-translation-job`

Starts an asynchronous batch translation job. Batch translation jobs can translate large volumes of text across multiple files and to multiple target languages.

**Synopsis:**
```bash
aws translate start-text-translation-job \
    --input-data-config <value> \
    --output-data-config <value> \
    --data-access-role-arn <value> \
    --source-language-code <value> \
    --target-language-codes <value> \
    [--job-name <value>] \
    [--terminology-names <value>] \
    [--parallel-data-names <value>] \
    [--client-token <value>] \
    [--settings <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--input-data-config` | **Yes** | structure | -- | S3 location and content type of input documents |
| `--output-data-config` | **Yes** | structure | -- | S3 location for translated output |
| `--data-access-role-arn` | **Yes** | string | -- | IAM role ARN granting Translate read access to input data |
| `--source-language-code` | **Yes** | string | -- | Source language code (2-5 chars) or `auto` |
| `--target-language-codes` | **Yes** | list(string) | -- | Target language codes (1-10, each 2-5 chars) |
| `--job-name` | No | string | None | Name for the batch translation job (1-256 chars) |
| `--terminology-names` | No | list(string) | None | Custom terminology resource names |
| `--parallel-data-names` | No | list(string) | None | Parallel data resource names for Active Custom Translation |
| `--client-token` | No | string | None | Unique identifier for idempotency (1-64 chars) |
| `--settings` | No | structure | None | Translation output settings (Formality, Profanity, Brevity) |

**InputDataConfig Structure:**
```json
{
    "S3Uri": "s3://bucket-name/input/",
    "ContentType": "text/plain|text/html|application/vnd.openxmlformats-officedocument.wordprocessingml.document|application/vnd.openxmlformats-officedocument.presentationml.presentation|application/vnd.openxmlformats-officedocument.spreadsheetml.sheet|application/x-xliff+xml"
}
```

**OutputDataConfig Structure:**
```json
{
    "S3Uri": "s3://bucket-name/output/",
    "EncryptionKey": {
        "Type": "KMS",
        "Id": "string"
    }
}
```

**Output Schema:**
```json
{
    "JobId": "string",
    "JobStatus": "SUBMITTED|IN_PROGRESS|COMPLETED|COMPLETED_WITH_ERROR|FAILED|STOP_REQUESTED|STOPPED"
}
```

---

### 1.4 `describe-text-translation-job`

Gets the properties of an asynchronous batch translation job including status, creation time, source/target languages, input/output data configuration, and error messages.

**Synopsis:**
```bash
aws translate describe-text-translation-job \
    --job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | Identifier for the translation job (1-32 chars) |

**Output Schema:**
```json
{
    "TextTranslationJobProperties": {
        "JobId": "string",
        "JobName": "string",
        "JobStatus": "SUBMITTED|IN_PROGRESS|COMPLETED|COMPLETED_WITH_ERROR|FAILED|STOP_REQUESTED|STOPPED",
        "JobDetails": {
            "TranslatedDocumentsCount": "integer",
            "DocumentsWithErrorsCount": "integer",
            "InputDocumentsCount": "integer"
        },
        "SourceLanguageCode": "string",
        "TargetLanguageCodes": ["string"],
        "TerminologyNames": ["string"],
        "ParallelDataNames": ["string"],
        "Message": "string",
        "SubmittedTime": "timestamp",
        "EndTime": "timestamp",
        "InputDataConfig": {
            "S3Uri": "string",
            "ContentType": "string"
        },
        "OutputDataConfig": {
            "S3Uri": "string",
            "EncryptionKey": {
                "Type": "KMS",
                "Id": "string"
            }
        },
        "DataAccessRoleArn": "string",
        "Settings": {
            "Formality": "FORMAL|INFORMAL",
            "Profanity": "MASK",
            "Brevity": "ON"
        }
    }
}
```

---

### 1.5 `list-text-translation-jobs`

Gets a list of batch translation jobs with optional filtering by job name, status, or submission time.

**Synopsis:**
```bash
aws translate list-text-translation-jobs \
    [--filter <value>] \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filter` | No | structure | None | Filter criteria for batch translation jobs |
| `--next-token` | No | string | None | Pagination token (max 8192 chars) |
| `--max-results` | No | integer | 100 | Maximum results per page (1-500) |

**Filter Structure:**
```json
{
    "JobName": "string",
    "JobStatus": "SUBMITTED|IN_PROGRESS|COMPLETED|COMPLETED_WITH_ERROR|FAILED|STOP_REQUESTED|STOPPED",
    "SubmittedBeforeTime": "timestamp",
    "SubmittedAfterTime": "timestamp"
}
```

**Output Schema:**
```json
{
    "TextTranslationJobPropertiesList": [
        {
            "JobId": "string",
            "JobName": "string",
            "JobStatus": "string",
            "JobDetails": {
                "TranslatedDocumentsCount": "integer",
                "DocumentsWithErrorsCount": "integer",
                "InputDocumentsCount": "integer"
            },
            "SourceLanguageCode": "string",
            "TargetLanguageCodes": ["string"],
            "TerminologyNames": ["string"],
            "ParallelDataNames": ["string"],
            "Message": "string",
            "SubmittedTime": "timestamp",
            "EndTime": "timestamp",
            "InputDataConfig": {
                "S3Uri": "string",
                "ContentType": "string"
            },
            "OutputDataConfig": {
                "S3Uri": "string",
                "EncryptionKey": {
                    "Type": "KMS",
                    "Id": "string"
                }
            },
            "DataAccessRoleArn": "string",
            "Settings": {
                "Formality": "FORMAL|INFORMAL",
                "Profanity": "MASK",
                "Brevity": "ON"
            }
        }
    ],
    "NextToken": "string"
}
```

---

### 1.6 `stop-text-translation-job`

Stops an asynchronous batch translation job that is in progress. Translated documents already completed are not reverted.

**Synopsis:**
```bash
aws translate stop-text-translation-job \
    --job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | Identifier for the translation job to stop (1-32 chars) |

**Output Schema:**
```json
{
    "JobId": "string",
    "JobStatus": "SUBMITTED|IN_PROGRESS|COMPLETED|COMPLETED_WITH_ERROR|FAILED|STOP_REQUESTED|STOPPED"
}
```

---

### 1.7 `list-languages`

Lists all languages supported by Amazon Translate. Returns language names and codes.

**Synopsis:**
```bash
aws translate list-languages \
    [--display-language-code <value>] \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--display-language-code` | No | string | `en` | Language code for display names: `de`, `en`, `es`, `fr`, `it`, `ja`, `ko`, `pt`, `zh`, `zh-TW` |
| `--next-token` | No | string | None | Pagination token (max 8192 chars) |
| `--max-results` | No | integer | None | Maximum results per response (1-500) |

**Output Schema:**
```json
{
    "Languages": [
        {
            "LanguageName": "string",
            "LanguageCode": "string"
        }
    ],
    "DisplayLanguageCode": "string",
    "NextToken": "string"
}
```
