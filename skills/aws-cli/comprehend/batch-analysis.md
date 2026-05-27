# Batch Analysis

### 2.1 `batch-detect-dominant-language`

Detects the dominant language in a batch of documents.

**Synopsis:**
```bash
aws comprehend batch-detect-dominant-language \
    --text-list <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--text-list` | **Yes** | list(string) | -- | List of UTF-8 text strings (max 25 documents, 5 KB each) |

**Output Schema:**
```json
{
    "ResultList": [
        {
            "Index": "integer",
            "Languages": [
                {
                    "LanguageCode": "string",
                    "Score": "float"
                }
            ]
        }
    ],
    "ErrorList": [
        {
            "Index": "integer",
            "ErrorCode": "string",
            "ErrorMessage": "string"
        }
    ]
}
```

---

### 2.2 `batch-detect-entities`

Detects named entities in a batch of documents.

**Synopsis:**
```bash
aws comprehend batch-detect-entities \
    --text-list <value> \
    --language-code <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--text-list` | **Yes** | list(string) | -- | List of UTF-8 text strings (max 25 documents, 5 KB each) |
| `--language-code` | **Yes** | string | -- | Language code: `en`, `es`, `fr`, `de`, `it`, `pt`, `ar`, `hi`, `ja`, `ko`, `zh`, `zh-TW` |

**Output Schema:**
```json
{
    "ResultList": [
        {
            "Index": "integer",
            "Entities": [
                {
                    "Score": "float",
                    "Type": "PERSON|LOCATION|ORGANIZATION|COMMERCIAL_ITEM|EVENT|DATE|QUANTITY|TITLE|OTHER",
                    "Text": "string",
                    "BeginOffset": "integer",
                    "EndOffset": "integer"
                }
            ]
        }
    ],
    "ErrorList": [
        {
            "Index": "integer",
            "ErrorCode": "string",
            "ErrorMessage": "string"
        }
    ]
}
```

---

### 2.3 `batch-detect-key-phrases`

Detects key noun phrases in a batch of documents.

**Synopsis:**
```bash
aws comprehend batch-detect-key-phrases \
    --text-list <value> \
    --language-code <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--text-list` | **Yes** | list(string) | -- | List of UTF-8 text strings (max 25 documents, 5 KB each) |
| `--language-code` | **Yes** | string | -- | Language code: `en`, `es`, `fr`, `de`, `it`, `pt`, `ar`, `hi`, `ja`, `ko`, `zh`, `zh-TW` |

**Output Schema:**
```json
{
    "ResultList": [
        {
            "Index": "integer",
            "KeyPhrases": [
                {
                    "Score": "float",
                    "Text": "string",
                    "BeginOffset": "integer",
                    "EndOffset": "integer"
                }
            ]
        }
    ],
    "ErrorList": [
        {
            "Index": "integer",
            "ErrorCode": "string",
            "ErrorMessage": "string"
        }
    ]
}
```

---

### 2.4 `batch-detect-sentiment`

Detects sentiment in a batch of documents.

**Synopsis:**
```bash
aws comprehend batch-detect-sentiment \
    --text-list <value> \
    --language-code <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--text-list` | **Yes** | list(string) | -- | List of UTF-8 text strings (max 25 documents, 5 KB each) |
| `--language-code` | **Yes** | string | -- | Language code: `en`, `es`, `fr`, `de`, `it`, `pt`, `ar`, `hi`, `ja`, `ko`, `zh`, `zh-TW` |

**Output Schema:**
```json
{
    "ResultList": [
        {
            "Index": "integer",
            "Sentiment": "POSITIVE|NEGATIVE|NEUTRAL|MIXED",
            "SentimentScore": {
                "Positive": "float",
                "Negative": "float",
                "Neutral": "float",
                "Mixed": "float"
            }
        }
    ],
    "ErrorList": [
        {
            "Index": "integer",
            "ErrorCode": "string",
            "ErrorMessage": "string"
        }
    ]
}
```

---

### 2.5 `batch-detect-syntax`

Detects syntax tokens and parts of speech in a batch of documents.

**Synopsis:**
```bash
aws comprehend batch-detect-syntax \
    --text-list <value> \
    --language-code <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--text-list` | **Yes** | list(string) | -- | List of UTF-8 text strings (max 25 documents, 5 KB each) |
| `--language-code` | **Yes** | string | -- | Language code: `en`, `es`, `fr`, `de`, `it`, `pt` |

**Output Schema:**
```json
{
    "ResultList": [
        {
            "Index": "integer",
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
    ],
    "ErrorList": [
        {
            "Index": "integer",
            "ErrorCode": "string",
            "ErrorMessage": "string"
        }
    ]
}
```

---

### 2.6 `batch-detect-targeted-sentiment`

Detects targeted sentiment in a batch of documents.

**Synopsis:**
```bash
aws comprehend batch-detect-targeted-sentiment \
    --text-list <value> \
    --language-code <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--text-list` | **Yes** | list(string) | -- | List of UTF-8 text strings (max 25 documents, 5 KB each) |
| `--language-code` | **Yes** | string | -- | Language code: `en`, `es`, `fr`, `de`, `it`, `pt`, `ar`, `hi`, `ja`, `ko`, `zh`, `zh-TW` |

**Output Schema:**
```json
{
    "ResultList": [
        {
            "Index": "integer",
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
    ],
    "ErrorList": [
        {
            "Index": "integer",
            "ErrorCode": "string",
            "ErrorMessage": "string"
        }
    ]
}
```
