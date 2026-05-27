# Vocabularies

### 4.1 `create-vocabulary`

Creates a custom vocabulary to improve transcription accuracy for domain-specific terms.

**Synopsis:**
```bash
aws transcribe create-vocabulary \
    --vocabulary-name <value> \
    --language-code <value> \
    [--phrases <value>] \
    [--vocabulary-file-uri <value>] \
    [--tags <value>] \
    [--data-access-role-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--vocabulary-name` | **Yes** | string | -- | Unique vocabulary name (1-200 chars, pattern: `^[0-9a-zA-Z._-]+`) |
| `--language-code` | **Yes** | string | -- | Language code (e.g., `en-US`, `fr-FR`, `ja-JP`) |
| `--phrases` | No* | list(string) | -- | Terms as inline list. Each phrase max 256 chars |
| `--vocabulary-file-uri` | No* | string | -- | S3 URI of vocabulary text file (e.g., `s3://bucket/vocab.txt`) |
| `--tags` | No | list | -- | Tags. Shorthand: `Key=string,Value=string ...` |
| `--data-access-role-arn` | No | string | -- | IAM role ARN with S3 access permissions |

*One of `--phrases` or `--vocabulary-file-uri` is required. They cannot be used together.

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

### 4.2 `get-vocabulary`

Gets details of a custom vocabulary.

**Synopsis:**
```bash
aws transcribe get-vocabulary \
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

### 4.3 `list-vocabularies`

Lists custom vocabularies. **Paginated operation.**

**Synopsis:**
```bash
aws transcribe list-vocabularies \
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

### 4.4 `update-vocabulary`

Updates a custom vocabulary. Replaces all existing terms.

**Synopsis:**
```bash
aws transcribe update-vocabulary \
    --vocabulary-name <value> \
    --language-code <value> \
    [--phrases <value>] \
    [--vocabulary-file-uri <value>] \
    [--data-access-role-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--vocabulary-name` | **Yes** | string | -- | Name of the vocabulary to update |
| `--language-code` | **Yes** | string | -- | Language code (must match existing) |
| `--phrases` | No* | list(string) | -- | Updated terms as inline list |
| `--vocabulary-file-uri` | No* | string | -- | S3 URI of updated vocabulary text file |
| `--data-access-role-arn` | No | string | -- | IAM role ARN with S3 access permissions |

*One of `--phrases` or `--vocabulary-file-uri` is required. They cannot be used together.

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

### 4.5 `delete-vocabulary`

Deletes a custom vocabulary.

**Synopsis:**
```bash
aws transcribe delete-vocabulary \
    --vocabulary-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--vocabulary-name` | **Yes** | string | -- | Name of the vocabulary to delete |

**Output:** None (HTTP 200 on success)

---

### 4.6 `create-vocabulary-filter`

Creates a vocabulary filter for masking or removing specific words from transcripts.

**Synopsis:**
```bash
aws transcribe create-vocabulary-filter \
    --vocabulary-filter-name <value> \
    --language-code <value> \
    [--words <value>] \
    [--vocabulary-filter-file-uri <value>] \
    [--tags <value>] \
    [--data-access-role-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--vocabulary-filter-name` | **Yes** | string | -- | Unique filter name (1-200 chars, pattern: `^[0-9a-zA-Z._-]+`) |
| `--language-code` | **Yes** | string | -- | Language code (e.g., `en-US`) |
| `--words` | No* | list(string) | -- | Filter terms as inline list. Each word max 256 chars |
| `--vocabulary-filter-file-uri` | No* | string | -- | S3 URI of filter words text file |
| `--tags` | No | list | -- | Tags. Shorthand: `Key=string,Value=string ...` |
| `--data-access-role-arn` | No | string | -- | IAM role ARN with S3 access permissions |

*One of `--words` or `--vocabulary-filter-file-uri` is required. They cannot be used together.

**Output Schema:**
```json
{
    "VocabularyFilterName": "string",
    "LanguageCode": "string",
    "LastModifiedTime": "timestamp"
}
```

---

### 4.7 `get-vocabulary-filter`

Gets details of a vocabulary filter.

**Synopsis:**
```bash
aws transcribe get-vocabulary-filter \
    --vocabulary-filter-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--vocabulary-filter-name` | **Yes** | string | -- | Name of the filter (1-200 chars) |

**Output Schema:**
```json
{
    "VocabularyFilterName": "string",
    "LanguageCode": "string",
    "LastModifiedTime": "timestamp",
    "DownloadUri": "string"
}
```

---

### 4.8 `list-vocabulary-filters`

Lists vocabulary filters. **Paginated operation.**

**Synopsis:**
```bash
aws transcribe list-vocabulary-filters \
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
| `--name-contains` | No | string | -- | Filter by name substring |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "NextToken": "string",
    "VocabularyFilters": [
        {
            "VocabularyFilterName": "string",
            "LanguageCode": "string",
            "LastModifiedTime": "timestamp"
        }
    ]
}
```

---

### 4.9 `update-vocabulary-filter`

Updates a vocabulary filter with new words. Replaces all existing words.

**Synopsis:**
```bash
aws transcribe update-vocabulary-filter \
    --vocabulary-filter-name <value> \
    [--words <value>] \
    [--vocabulary-filter-file-uri <value>] \
    [--data-access-role-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--vocabulary-filter-name` | **Yes** | string | -- | Name of the filter to update |
| `--words` | No* | list(string) | -- | Updated filter terms as inline list |
| `--vocabulary-filter-file-uri` | No* | string | -- | S3 URI of updated filter words text file |
| `--data-access-role-arn` | No | string | -- | IAM role ARN with S3 access permissions |

*One of `--words` or `--vocabulary-filter-file-uri` is required. They cannot be used together.

**Output Schema:**
```json
{
    "VocabularyFilterName": "string",
    "LanguageCode": "string",
    "LastModifiedTime": "timestamp"
}
```

---

### 4.10 `delete-vocabulary-filter`

Deletes a vocabulary filter.

**Synopsis:**
```bash
aws transcribe delete-vocabulary-filter \
    --vocabulary-filter-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--vocabulary-filter-name` | **Yes** | string | -- | Name of the filter to delete |

**Output:** None (HTTP 200 on success)
