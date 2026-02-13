# Real-Time Analysis

### 1.1 `detect-dominant-language`

Detects the dominant language of the input text. Returns a list of languages with confidence scores.

**Synopsis:**
```bash
aws comprehend detect-dominant-language \
    --text <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--text` | **Yes** | string | -- | UTF-8 text string (max 100 KB). Must contain at least 20 characters |

**Output Schema:**
```json
{
    "Languages": [
        {
            "LanguageCode": "string",
            "Score": "float"
        }
    ]
}
```

---

### 1.2 `detect-entities`

Detects named entities in text. Supports text input directly or via base64-encoded documents (PDF, Word, images).

**Synopsis:**
```bash
aws comprehend detect-entities \
    [--text <value>] \
    [--language-code <value>] \
    [--endpoint-arn <value>] \
    [--bytes <value>] \
    [--document-reader-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--text` | No* | string | -- | UTF-8 text string (max 100 KB). Do not use with `--bytes` |
| `--language-code` | No | string | -- | Language code: `en`, `es`, `fr`, `de`, `it`, `pt`, `ar`, `hi`, `ja`, `ko`, `zh`, `zh-TW` |
| `--endpoint-arn` | No | string | -- | ARN of custom entity recognition model endpoint |
| `--bytes` | No* | blob | -- | Base64-encoded document (text, PDF, Word, image). Do not use with `--text` |
| `--document-reader-config` | No | structure | -- | Configuration for text extraction from PDFs and images |

*Either `--text` or `--bytes` must be provided.

**Document Reader Config Structure:**
```json
{
    "DocumentReadAction": "TEXTRACT_DETECT_DOCUMENT_TEXT|TEXTRACT_ANALYZE_DOCUMENT",
    "DocumentReadMode": "SERVICE_DEFAULT|FORCE_DOCUMENT_READ_ACTION",
    "FeatureTypes": ["TABLES", "FORMS"]
}
```

**Output Schema:**
```json
{
    "Entities": [
        {
            "Score": "float",
            "Type": "PERSON|LOCATION|ORGANIZATION|COMMERCIAL_ITEM|EVENT|DATE|QUANTITY|TITLE|OTHER",
            "Text": "string",
            "BeginOffset": "integer",
            "EndOffset": "integer",
            "BlockReferences": [
                {
                    "BlockId": "string",
                    "BeginOffset": "integer",
                    "EndOffset": "integer",
                    "ChildBlocks": [
                        {
                            "ChildBlockId": "string",
                            "BeginOffset": "integer",
                            "EndOffset": "integer"
                        }
                    ]
                }
            ]
        }
    ],
    "DocumentMetadata": {
        "Pages": "integer",
        "ExtractedCharacters": [
            {
                "Page": "integer",
                "Count": "integer"
            }
        ]
    },
    "DocumentType": [
        {
            "Page": "integer",
            "Type": "NATIVE_PDF|SCANNED_PDF|MS_WORD|IMAGE|PLAIN_TEXT|TEXTRACT_DETECT_DOCUMENT_TEXT_JSON|TEXTRACT_ANALYZE_DOCUMENT_JSON"
        }
    ],
    "Errors": [
        {
            "Page": "integer",
            "ErrorCode": "TEXTRACT_BAD_PAGE|TEXTRACT_PROVISIONED_THROUGHPUT_EXCEEDED|PAGE_CHARACTERS_EXCEEDED|PAGE_SIZE_EXCEEDED|INTERNAL_SERVER_ERROR",
            "ErrorMessage": "string"
        }
    ]
}
```

---

### 1.3 `detect-key-phrases`

Detects key noun phrases in text.

**Synopsis:**
```bash
aws comprehend detect-key-phrases \
    --text <value> \
    --language-code <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--text` | **Yes** | string | -- | UTF-8 text string (max 100 KB) |
| `--language-code` | **Yes** | string | -- | Language code: `en`, `es`, `fr`, `de`, `it`, `pt`, `ar`, `hi`, `ja`, `ko`, `zh`, `zh-TW` |

**Output Schema:**
```json
{
    "KeyPhrases": [
        {
            "Score": "float",
            "Text": "string",
            "BeginOffset": "integer",
            "EndOffset": "integer"
        }
    ]
}
```

---

### 1.4 `detect-pii-entities`

Detects personally identifiable information (PII) in text. Returns entity offsets and types.

**Synopsis:**
```bash
aws comprehend detect-pii-entities \
    --text <value> \
    --language-code <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--text` | **Yes** | string | -- | UTF-8 text string (max 100 KB) |
| `--language-code` | **Yes** | string | -- | Language code: `en`, `es`, `fr`, `de`, `it`, `pt`, `ar`, `hi`, `ja`, `ko`, `zh`, `zh-TW` |

**Output Schema:**
```json
{
    "Entities": [
        {
            "Score": "float",
            "Type": "BANK_ACCOUNT_NUMBER|BANK_ROUTING|CREDIT_DEBIT_NUMBER|CREDIT_DEBIT_CVV|CREDIT_DEBIT_EXPIRY|PIN|EMAIL|ADDRESS|NAME|PHONE|SSN|DATE_TIME|PASSPORT_NUMBER|DRIVER_ID|URL|AGE|USERNAME|PASSWORD|AWS_ACCESS_KEY|AWS_SECRET_KEY|IP_ADDRESS|MAC_ADDRESS|LICENSE_PLATE|VEHICLE_IDENTIFICATION_NUMBER|UK_NATIONAL_INSURANCE_NUMBER|CA_SOCIAL_INSURANCE_NUMBER|US_INDIVIDUAL_TAX_IDENTIFICATION_NUMBER|UK_UNIQUE_TAXPAYER_REFERENCE_NUMBER|IN_PERMANENT_ACCOUNT_NUMBER|IN_NREGA|INTERNATIONAL_BANK_ACCOUNT_NUMBER|SWIFT_CODE|UK_NATIONAL_HEALTH_SERVICE_NUMBER|CA_HEALTH_NUMBER|IN_AADHAAR|IN_VOTER_NUMBER|ALL",
            "BeginOffset": "integer",
            "EndOffset": "integer"
        }
    ]
}
```

---

### 1.5 `detect-sentiment`

Detects the prevailing sentiment (positive, negative, neutral, or mixed) in text.

**Synopsis:**
```bash
aws comprehend detect-sentiment \
    --text <value> \
    --language-code <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--text` | **Yes** | string | -- | UTF-8 text string (max 5 KB) |
| `--language-code` | **Yes** | string | -- | Language code: `en`, `es`, `fr`, `de`, `it`, `pt`, `ar`, `hi`, `ja`, `ko`, `zh`, `zh-TW` |

**Output Schema:**
```json
{
    "Sentiment": "POSITIVE|NEGATIVE|NEUTRAL|MIXED",
    "SentimentScore": {
        "Positive": "float",
        "Negative": "float",
        "Neutral": "float",
        "Mixed": "float"
    }
}
```

---

### 1.6 `detect-syntax`

Detects syntax tokens and parts of speech in text.

**Synopsis:**
```bash
aws comprehend detect-syntax \
    --text <value> \
    --language-code <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--text` | **Yes** | string | -- | UTF-8 text string (max 5 KB) |
| `--language-code` | **Yes** | string | -- | Language code: `en`, `es`, `fr`, `de`, `it`, `pt` |

**Output Schema:**
```json
{
    "SyntaxTokens": [
        {
            "TokenId": "integer",
            "Text": "string",
            "BeginOffset": "integer",
            "EndOffset": "integer",
            "PartOfSpeech": {
                "Tag": "ADJ|ADP|ADV|AUX|CONJ|CCONJ|DET|INTJ|NOUN|NUM|O|PART|PRON|PROPN|PUNCT|SCONJ|SYM|VERB",
                "Score": "float"
            }
        }
    ]
}
```

---

### 1.7 `detect-targeted-sentiment`

Detects sentiment associated with specific entities mentioned in text.

**Synopsis:**
```bash
aws comprehend detect-targeted-sentiment \
    --text <value> \
    --language-code <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--text` | **Yes** | string | -- | UTF-8 text string (max 5 KB) |
| `--language-code` | **Yes** | string | -- | Language code: `en`, `es`, `fr`, `de`, `it`, `pt`, `ar`, `hi`, `ja`, `ko`, `zh`, `zh-TW` |

**Output Schema:**
```json
{
    "Entities": [
        {
            "DescriptiveMentionIndex": ["integer"],
            "Mentions": [
                {
                    "Score": "float",
                    "GroupScore": "float",
                    "Text": "string",
                    "Type": "PERSON|LOCATION|ORGANIZATION|FACILITY|BRAND|COMMERCIAL_ITEM|MOVIE|MUSIC|BOOK|SOFTWARE|GAME|PERSONAL_TITLE|EVENT|DATE|QUANTITY|ATTRIBUTE|OTHER",
                    "MentionSentiment": {
                        "Sentiment": "POSITIVE|NEGATIVE|NEUTRAL|MIXED",
                        "SentimentScore": {
                            "Positive": "float",
                            "Negative": "float",
                            "Neutral": "float",
                            "Mixed": "float"
                        }
                    },
                    "BeginOffset": "integer",
                    "EndOffset": "integer"
                }
            ]
        }
    ]
}
```

---

### 1.8 `detect-toxic-content`

Detects toxic content in text segments (harassment, hate speech, profanity, etc.).

**Synopsis:**
```bash
aws comprehend detect-toxic-content \
    --text-segments <value> \
    --language-code <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--text-segments` | **Yes** | list | -- | Up to 10 text strings (max 1 KB each). Shorthand: `Text=string ...` |
| `--language-code` | **Yes** | string | -- | Language code (currently only `en` fully supported) |

**Output Schema:**
```json
{
    "ResultList": [
        {
            "Labels": [
                {
                    "Name": "GRAPHIC|HARASSMENT_OR_ABUSE|HATE_SPEECH|INSULT|PROFANITY|SEXUAL|VIOLENCE_OR_THREAT",
                    "Score": "float"
                }
            ],
            "Toxicity": "float"
        }
    ]
}
```

---

### 1.9 `contains-pii-entities`

Checks if text contains PII entities and returns labels with confidence scores (without offsets).

**Synopsis:**
```bash
aws comprehend contains-pii-entities \
    --text <value> \
    --language-code <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--text` | **Yes** | string | -- | UTF-8 text string (max 100 KB) |
| `--language-code` | **Yes** | string | -- | Language code: `en`, `es`, `fr`, `de`, `it`, `pt`, `ar`, `hi`, `ja`, `ko`, `zh`, `zh-TW` |

**Output Schema:**
```json
{
    "Labels": [
        {
            "Name": "BANK_ACCOUNT_NUMBER|BANK_ROUTING|CREDIT_DEBIT_NUMBER|...|ALL",
            "Score": "float"
        }
    ]
}
```

---

### 1.10 `classify-document`

Classifies a document using a custom document classifier endpoint.

**Synopsis:**
```bash
aws comprehend classify-document \
    --endpoint-arn <value> \
    [--text <value>] \
    [--bytes <value>] \
    [--document-reader-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-arn` | **Yes** | string | -- | ARN of the document classifier endpoint |
| `--text` | No* | string | -- | Document text to classify. Do not use with `--bytes` |
| `--bytes` | No* | blob | -- | Base64-encoded document (text, PDF, Word, image). Do not use with `--text` |
| `--document-reader-config` | No | structure | -- | Configuration for text extraction from PDFs and images |

*Either `--text` or `--bytes` must be provided.

**Output Schema:**
```json
{
    "Classes": [
        {
            "Name": "string",
            "Score": "float",
            "Page": "integer"
        }
    ],
    "Labels": [
        {
            "Name": "string",
            "Score": "float",
            "Page": "integer"
        }
    ],
    "DocumentMetadata": {
        "Pages": "integer",
        "ExtractedCharacters": [
            {
                "Page": "integer",
                "Count": "integer"
            }
        ]
    },
    "DocumentType": [
        {
            "Page": "integer",
            "Type": "NATIVE_PDF|SCANNED_PDF|MS_WORD|IMAGE|PLAIN_TEXT|TEXTRACT_DETECT_DOCUMENT_TEXT_JSON|TEXTRACT_ANALYZE_DOCUMENT_JSON"
        }
    ],
    "Errors": [
        {
            "Page": "integer",
            "ErrorCode": "string",
            "ErrorMessage": "string"
        }
    ],
    "Warnings": [
        {
            "Page": "integer",
            "WarnCode": "INFERENCING_PLAINTEXT_WITH_NATIVE_TRAINED_MODEL|INFERENCING_NATIVE_DOCUMENT_WITH_PLAINTEXT_TRAINED_MODEL",
            "WarnMessage": "string"
        }
    ]
}
```
