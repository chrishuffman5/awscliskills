# Language Models

### 5.1 `create-language-model`

Creates a custom language model using training data to improve transcription accuracy for domain-specific content.

**Synopsis:**
```bash
aws transcribe create-language-model \
    --language-code <value> \
    --base-model-name <value> \
    --model-name <value> \
    --input-data-config <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--language-code` | **Yes** | string | -- | Language code: `en-US`, `en-GB`, `en-AU`, `hi-IN`, `es-US`, `de-DE`, `ja-JP` |
| `--base-model-name` | **Yes** | string | -- | `NarrowBand` (audio < 16 kHz) or `WideBand` (audio >= 16 kHz) |
| `--model-name` | **Yes** | string | -- | Unique model name (1-200 chars, pattern: `^[0-9a-zA-Z._-]+`) |
| `--input-data-config` | **Yes** | structure | -- | Training data config. Shorthand: `S3Uri=s3://bucket/training/,DataAccessRoleArn=arn:aws:iam::123456789012:role/Role` |
| `--tags` | No | list | -- | Tags. Shorthand: `Key=string,Value=string ...` |

**Input Data Config Structure:**
```json
{
    "S3Uri": "string",
    "TuningDataS3Uri": "string",
    "DataAccessRoleArn": "string"
}
```

| Field | Required | Description |
|-------|----------|-------------|
| `S3Uri` | **Yes** | S3 path to training text files |
| `DataAccessRoleArn` | **Yes** | IAM role ARN with S3 access permissions |
| `TuningDataS3Uri` | No | S3 path to tuning text files |

**Output Schema:**
```json
{
    "LanguageCode": "string",
    "BaseModelName": "NarrowBand|WideBand",
    "ModelName": "string",
    "InputDataConfig": {
        "S3Uri": "string",
        "TuningDataS3Uri": "string",
        "DataAccessRoleArn": "string"
    },
    "ModelStatus": "IN_PROGRESS|FAILED|COMPLETED"
}
```

---

### 5.2 `describe-language-model`

Gets details of a custom language model.

**Synopsis:**
```bash
aws transcribe describe-language-model \
    --model-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--model-name` | **Yes** | string | -- | Name of the language model (1-200 chars) |

**Output Schema:**
```json
{
    "LanguageModel": {
        "ModelName": "string",
        "CreateTime": "timestamp",
        "LastModifiedTime": "timestamp",
        "LanguageCode": "string",
        "BaseModelName": "NarrowBand|WideBand",
        "ModelStatus": "IN_PROGRESS|FAILED|COMPLETED",
        "UpgradeAvailability": "boolean",
        "FailureReason": "string",
        "InputDataConfig": {
            "S3Uri": "string",
            "TuningDataS3Uri": "string",
            "DataAccessRoleArn": "string"
        }
    }
}
```

---

### 5.3 `list-language-models`

Lists custom language models. **Paginated operation.**

**Synopsis:**
```bash
aws transcribe list-language-models \
    [--status-equals <value>] \
    [--name-contains <value>] \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--status-equals` | No | string | -- | Filter by status: `IN_PROGRESS`, `FAILED`, `COMPLETED` |
| `--name-contains` | No | string | -- | Filter by name substring |
| `--next-token` | No | string | -- | Pagination token |
| `--max-results` | No | integer | 5 | Max items per page (1-100) |

**Output Schema:**
```json
{
    "NextToken": "string",
    "Models": [
        {
            "ModelName": "string",
            "CreateTime": "timestamp",
            "LastModifiedTime": "timestamp",
            "LanguageCode": "string",
            "BaseModelName": "NarrowBand|WideBand",
            "ModelStatus": "IN_PROGRESS|FAILED|COMPLETED",
            "UpgradeAvailability": "boolean",
            "FailureReason": "string",
            "InputDataConfig": {
                "S3Uri": "string",
                "TuningDataS3Uri": "string",
                "DataAccessRoleArn": "string"
            }
        }
    ]
}
```

---

### 5.4 `delete-language-model`

Deletes a custom language model.

**Synopsis:**
```bash
aws transcribe delete-language-model \
    --model-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--model-name` | **Yes** | string | -- | Name of the language model to delete |

**Output:** None (HTTP 200 on success)
