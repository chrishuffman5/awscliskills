# AI Prompts

### 7.1 `create-ai-prompt`

Creates a prompt template for AI agents.

**Synopsis:**
```bash
aws qconnect create-ai-prompt \
    --assistant-id <value> \
    --name <value> \
    --type <value> \
    --template-configuration <value> \
    --visibility-status <value> \
    --template-type <value> \
    --model-id <value> \
    --api-format <value> \
    [--description <value>] \
    [--inference-configuration <value>] \
    [--client-token <value>] \
    [--tags <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--assistant-id` | **Yes** | string | -- | Assistant ID or ARN |
| `--name` | **Yes** | string | -- | Prompt name (1-255 chars) |
| `--type` | **Yes** | string | -- | Prompt type (see AI Prompt Types) |
| `--template-configuration` | **Yes** | structure | -- | Template config (see below) |
| `--visibility-status` | **Yes** | string | -- | `SAVED` or `PUBLISHED` |
| `--template-type` | **Yes** | string | -- | Must be `TEXT` |
| `--model-id` | **Yes** | string | -- | Model ID (1-2048 chars) |
| `--api-format` | **Yes** | string | -- | `MESSAGES`, `TEXT_COMPLETIONS`, `ANTHROPIC_CLAUDE_MESSAGES`, `ANTHROPIC_CLAUDE_TEXT_COMPLETIONS` |
| `--description` | No | string | None | Description (1-255 chars) |
| `--inference-configuration` | No | structure | None | Inference params |
| `--client-token` | No | string | None | Idempotency token |
| `--tags` | No | map | None | Tags |

**Template Configuration:**
```json
{
    "textFullAIPromptEditTemplateConfiguration": {
        "text": "string (1-1,000,000 chars)"
    }
}
```

**Inference Configuration:**
```json
{
    "temperature": 0.7,
    "topP": 0.9,
    "topK": 50,
    "maxTokensToSample": 1024
}
```

**Output Schema:**
```json
{
    "aiPrompt": {
        "assistantId": "string",
        "assistantArn": "string",
        "aiPromptId": "string",
        "aiPromptArn": "string",
        "name": "string",
        "type": "string",
        "templateType": "TEXT",
        "modelId": "string",
        "apiFormat": "string",
        "templateConfiguration": {},
        "inferenceConfiguration": {},
        "visibilityStatus": "string",
        "description": "string",
        "tags": {},
        "origin": "SYSTEM|CUSTOMER",
        "status": "string",
        "modifiedTime": "timestamp"
    }
}
```

---

### 7.2 `create-ai-prompt-version`

Creates an immutable version of an AI prompt.

**Synopsis:**
```bash
aws qconnect create-ai-prompt-version \
    --assistant-id <value> \
    --ai-prompt-id <value> \
    [--client-token <value>] \
    [--modified-time <value>]
```

---

### 7.3 `get-ai-prompt`

Gets an AI prompt.

**Synopsis:**
```bash
aws qconnect get-ai-prompt \
    --assistant-id <value> \
    --ai-prompt-id <value>
```

---

### 7.4 `list-ai-prompts`

Lists AI prompts. **Paginated operation.**

**Synopsis:**
```bash
aws qconnect list-ai-prompts \
    --assistant-id <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--origin <value>]
```

---

### 7.5 `list-ai-prompt-versions`

Lists versions of an AI prompt. **Paginated operation.**

---

### 7.6 `update-ai-prompt`

Updates an AI prompt.

**Synopsis:**
```bash
aws qconnect update-ai-prompt \
    --assistant-id <value> \
    --ai-prompt-id <value> \
    --visibility-status <value> \
    [--template-configuration <value>] \
    [--description <value>] \
    [--client-token <value>]
```

---

### 7.7 `delete-ai-prompt`

Deletes an AI prompt.

**Synopsis:**
```bash
aws qconnect delete-ai-prompt \
    --assistant-id <value> \
    --ai-prompt-id <value>
```

**Output:** None

---

### 7.8 `delete-ai-prompt-version`

Deletes a specific version of an AI prompt.

**Synopsis:**
```bash
aws qconnect delete-ai-prompt-version \
    --assistant-id <value> \
    --ai-prompt-id <value> \
    --version-number <value>
```

**Output:** None
