# Prompts

### `create-prompt`

Creates a managed prompt in Amazon Bedrock Prompt Management. Prompts can include text or chat templates with variables, and can be versioned.

**Synopsis:**
```bash
aws bedrock-agent create-prompt \
    --name <value> \
    [--description <value>] \
    [--customer-encryption-key-arn <value>] \
    [--default-variant <value>] \
    [--variants <value>] \
    [--client-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Prompt name. Pattern: `([0-9a-zA-Z][_-]?){1,100}` |
| `--description` | No | string | None | Description (1-200 chars) |
| `--customer-encryption-key-arn` | No | string | None | KMS key ARN for encryption (1-2048 chars) |
| `--default-variant` | No | string | None | Name of the default variant |
| `--variants` | No | list | None | Prompt variants (max 1) |
| `--client-token` | No | string | None | Idempotency token (33-256 chars) |
| `--tags` | No | map | None | Key-value tags |

**Variant Structure (Text):**
```json
{
    "name": "default",
    "templateType": "TEXT",
    "templateConfiguration": {
        "text": {
            "text": "You are a helpful assistant. {{topic}}",
            "inputVariables": [
                {"name": "topic"}
            ]
        }
    },
    "modelId": "anthropic.claude-3-sonnet-20240229-v1:0",
    "inferenceConfiguration": {
        "text": {
            "temperature": 0.7,
            "topP": 0.9,
            "maxTokens": 1024,
            "stopSequences": []
        }
    }
}
```

**Variant Structure (Chat):**
```json
{
    "name": "chat-variant",
    "templateType": "CHAT",
    "templateConfiguration": {
        "chat": {
            "messages": [
                {
                    "role": "user",
                    "content": [{"text": "{{question}}"}]
                }
            ],
            "system": [
                {"text": "You are a helpful assistant."}
            ],
            "inputVariables": [{"name": "question"}],
            "toolConfiguration": {
                "tools": [...],
                "toolChoice": {"auto": {}}
            }
        }
    },
    "modelId": "anthropic.claude-3-sonnet-20240229-v1:0",
    "inferenceConfiguration": {
        "text": {
            "temperature": 0.5,
            "maxTokens": 512
        }
    }
}
```

**Output Schema:**
```json
{
    "name": "string",
    "description": "string",
    "customerEncryptionKeyArn": "string",
    "defaultVariant": "string",
    "variants": [...],
    "id": "string",
    "arn": "string",
    "version": "DRAFT",
    "createdAt": "timestamp",
    "updatedAt": "timestamp"
}
```

---

### `get-prompt`

Gets details of a managed prompt.

**Synopsis:**
```bash
aws bedrock-agent get-prompt \
    --prompt-identifier <value> \
    [--prompt-version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--prompt-identifier` | **Yes** | string | -- | Prompt ID or ARN |
| `--prompt-version` | No | string | None | Version number or `DRAFT` |

**Output Schema:** Same as `create-prompt` output.

---

### `list-prompts`

Lists managed prompts. **Paginated operation.**

**Synopsis:**
```bash
aws bedrock-agent list-prompts \
    [--prompt-identifier <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--prompt-identifier` | No | string | None | Filter by prompt ID (lists versions) |

**Output Schema:**
```json
{
    "promptSummaries": [
        {
            "name": "string",
            "description": "string",
            "id": "string",
            "arn": "string",
            "version": "string",
            "createdAt": "timestamp",
            "updatedAt": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### `update-prompt`

Updates a managed prompt.

**Synopsis:**
```bash
aws bedrock-agent update-prompt \
    --prompt-identifier <value> \
    --name <value> \
    [--description <value>] \
    [--customer-encryption-key-arn <value>] \
    [--default-variant <value>] \
    [--variants <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--prompt-identifier` | **Yes** | string | -- | Prompt ID or ARN |
| `--name` | **Yes** | string | -- | Updated name |
| (other params same as create) | No | various | None | Same optional params as create |

**Output Schema:** Same as `create-prompt` output.

---

### `delete-prompt`

Deletes a managed prompt.

**Synopsis:**
```bash
aws bedrock-agent delete-prompt \
    --prompt-identifier <value> \
    [--prompt-version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--prompt-identifier` | **Yes** | string | -- | Prompt ID or ARN |
| `--prompt-version` | No | string | None | Version to delete (omit for all) |

**Output Schema:**
```json
{
    "id": "string",
    "version": "string"
}
```

---

### `create-prompt-version`

Creates a versioned snapshot of a managed prompt. Versions are immutable.

**Synopsis:**
```bash
aws bedrock-agent create-prompt-version \
    --prompt-identifier <value> \
    [--description <value>] \
    [--client-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--prompt-identifier` | **Yes** | string | -- | Prompt ID or ARN |
| `--description` | No | string | None | Version description (1-200 chars) |
| `--client-token` | No | string | None | Idempotency token |
| `--tags` | No | map | None | Tags |

**Output Schema:** Same as `create-prompt` output, with incremented version number.
