# Prompts & Vocabularies

### 13.1 `create-prompt`

Creates a prompt (audio file) for the specified instance.

**Synopsis:**
```bash
aws connect create-prompt \
    --instance-id <value> \
    --name <value> \
    --s3-uri <value> \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--name` | **Yes** | string | -- | Prompt name (1-127 chars) |
| `--s3-uri` | **Yes** | string | -- | S3 URI for the audio file (1-2000 chars) |
| `--description` | No | string | None | Description (1-250 chars) |
| `--tags` | No | map | None | Tags (max 50) |

**Output Schema:**
```json
{
    "PromptARN": "string",
    "PromptId": "string"
}
```

---

### 13.2 `describe-prompt`

Describes a prompt.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--prompt-id` | **Yes** | string | -- | Prompt ID |

**Output Schema:**
```json
{
    "Prompt": {
        "PromptARN": "string",
        "PromptId": "string",
        "Name": "string",
        "Description": "string",
        "Tags": { "key": "value" },
        "LastModifiedTime": "timestamp",
        "LastModifiedRegion": "string"
    }
}
```

---

### 13.3 `list-prompts`

Lists prompts. **Paginated operation.**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-1000) |

**Output Schema:**
```json
{
    "PromptSummaryList": [ { "Id": "string", "Arn": "string", "Name": "string", "LastModifiedTime": "timestamp", "LastModifiedRegion": "string" } ],
    "NextToken": "string"
}
```

---

### 13.4 `update-prompt`

Updates a prompt's name, description, or S3 URI.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--prompt-id` | **Yes** | string | -- | Prompt ID |
| `--name` | No | string | None | Updated name |
| `--description` | No | string | None | Updated description |
| `--s3-uri` | No | string | None | Updated S3 URI |

**Output Schema:**
```json
{
    "PromptARN": "string",
    "PromptId": "string"
}
```

---

### 13.5 `delete-prompt`

Deletes a prompt.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--prompt-id` | **Yes** | string | -- | Prompt ID |

**Output:** None

---

### 13.6 `get-prompt-file`

Gets a URL for a prompt audio file.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--prompt-id` | **Yes** | string | -- | Prompt ID |

**Output Schema:**
```json
{
    "PromptPresignedUrl": "string",
    "LastModifiedTime": "timestamp",
    "LastModifiedRegion": "string"
}
```

---

### 13.7 `search-prompts`

Searches prompts. **Paginated operation.**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-100) |
| `--search-filter` | No | structure | None | Tag filter |
| `--search-criteria` | No | structure | None | Search criteria |

**Output Schema:**
```json
{
    "Prompts": [ { "PromptARN": "string", "PromptId": "string", "Name": "string", "Description": "string", "Tags": {} } ],
    "NextToken": "string",
    "ApproximateTotalCount": "long"
}
```

---

### 13.8 `create-vocabulary`

Creates a custom vocabulary for Contact Lens.

**Synopsis:**
```bash
aws connect create-vocabulary \
    --instance-id <value> \
    --vocabulary-name <value> \
    --language-code <value> \
    --content <value> \
    [--client-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--vocabulary-name` | **Yes** | string | -- | Vocabulary name |
| `--language-code` | **Yes** | string | -- | Language code (e.g., `en-US`, `es-ES`) |
| `--content` | **Yes** | string | -- | Vocabulary content (phrases/words) |
| `--client-token` | No | string | Auto | Idempotency token |
| `--tags` | No | map | None | Tags |

**Output Schema:**
```json
{
    "VocabularyArn": "string",
    "VocabularyId": "string",
    "State": "CREATION_IN_PROGRESS|ACTIVE|CREATION_FAILED|DELETE_IN_PROGRESS"
}
```

---

### 13.9 `describe-vocabulary`

Describes a vocabulary.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--vocabulary-id` | **Yes** | string | -- | Vocabulary ID |

**Output Schema:**
```json
{
    "Vocabulary": {
        "Name": "string",
        "Id": "string",
        "Arn": "string",
        "LanguageCode": "string",
        "State": "CREATION_IN_PROGRESS|ACTIVE|CREATION_FAILED|DELETE_IN_PROGRESS",
        "LastModifiedTime": "timestamp",
        "FailureReason": "string",
        "Content": "string",
        "Tags": { "key": "value" }
    }
}
```

---

### 13.10 `list-default-vocabularies`

Lists default vocabularies. **Paginated operation.**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--language-code` | No | string | None | Filter by language |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results |

---

### 13.11 `delete-vocabulary`

Deletes a vocabulary.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--vocabulary-id` | **Yes** | string | -- | Vocabulary ID |

**Output Schema:**
```json
{
    "VocabularyArn": "string",
    "VocabularyId": "string",
    "State": "DELETE_IN_PROGRESS"
}
```

---

### 13.12 `search-vocabularies`

Searches vocabularies. **Paginated operation.**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-100) |
| `--state` | No | string | None | Filter by state |
| `--name-starts-with` | No | string | None | Filter by name prefix |
| `--language-code` | No | string | None | Filter by language |

---

### 13.13 `associate-default-vocabulary`

Associates a default vocabulary with an instance for a language.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--language-code` | **Yes** | string | -- | Language code |
| `--vocabulary-id` | No | string | None | Vocabulary ID (omit to remove default) |

**Output:** None
