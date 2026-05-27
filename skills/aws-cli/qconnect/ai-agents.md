# AI Agents

### 5.1 `create-ai-agent`

Creates an AI agent for an assistant.

**Synopsis:**
```bash
aws qconnect create-ai-agent \
    --assistant-id <value> \
    --name <value> \
    --type <value> \
    --configuration <value> \
    --visibility-status <value> \
    [--description <value>] \
    [--client-token <value>] \
    [--tags <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--assistant-id` | **Yes** | string | -- | Assistant ID or ARN |
| `--name` | **Yes** | string | -- | Agent name (1-255 chars) |
| `--type` | **Yes** | string | -- | Agent type (see AI Agent Types) |
| `--configuration` | **Yes** | document | -- | Agent config (JSON, type-specific) |
| `--visibility-status` | **Yes** | string | -- | `SAVED` or `PUBLISHED` |
| `--description` | No | string | None | Description (1-255 chars) |
| `--client-token` | No | string | None | Idempotency token |
| `--tags` | No | map | None | Tags |

**Configuration varies by type. Example for MANUAL_SEARCH:**
```json
{
    "manualSearchAIAgentConfiguration": {
        "answerGenerationAIPromptId": "string",
        "answerGenerationAIGuardrailId": "string",
        "associationConfigurations": [
            {
                "associationId": "string",
                "associationType": "KNOWLEDGE_BASE",
                "associationConfigurationData": {
                    "knowledgeBaseAssociationConfigurationData": {
                        "maxResults": 5,
                        "overrideKnowledgeBaseSearchType": "HYBRID|SEMANTIC"
                    }
                }
            }
        ],
        "locale": "en_US"
    }
}
```

**Output Schema:**
```json
{
    "aiAgent": {
        "assistantId": "string",
        "assistantArn": "string",
        "aiAgentId": "string",
        "aiAgentArn": "string",
        "name": "string",
        "type": "string",
        "configuration": {},
        "visibilityStatus": "string",
        "description": "string",
        "tags": {},
        "status": "CREATE_IN_PROGRESS|CREATE_FAILED|ACTIVE|DELETE_IN_PROGRESS|DELETE_FAILED|DELETED",
        "modifiedTime": "timestamp",
        "origin": "SYSTEM|CUSTOMER"
    }
}
```

---

### 5.2 `create-ai-agent-version`

Creates an immutable version of an AI agent.

**Synopsis:**
```bash
aws qconnect create-ai-agent-version \
    --assistant-id <value> \
    --ai-agent-id <value> \
    [--client-token <value>] \
    [--modified-time <value>]
```

---

### 5.3 `get-ai-agent`

Gets an AI agent.

**Synopsis:**
```bash
aws qconnect get-ai-agent \
    --assistant-id <value> \
    --ai-agent-id <value>
```

---

### 5.4 `list-ai-agents`

Lists AI agents. **Paginated operation.**

**Synopsis:**
```bash
aws qconnect list-ai-agents \
    --assistant-id <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--origin <value>]
```

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--origin` | No | string | None | Filter by origin: `SYSTEM` or `CUSTOMER` |

---

### 5.5 `list-ai-agent-versions`

Lists versions of an AI agent. **Paginated operation.**

**Synopsis:**
```bash
aws qconnect list-ai-agent-versions \
    --assistant-id <value> \
    --ai-agent-id <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--origin <value>]
```

---

### 5.6 `update-ai-agent`

Updates an AI agent.

**Synopsis:**
```bash
aws qconnect update-ai-agent \
    --assistant-id <value> \
    --ai-agent-id <value> \
    --visibility-status <value> \
    [--configuration <value>] \
    [--description <value>] \
    [--client-token <value>]
```

---

### 5.7 `delete-ai-agent`

Deletes an AI agent.

**Synopsis:**
```bash
aws qconnect delete-ai-agent \
    --assistant-id <value> \
    --ai-agent-id <value>
```

**Output:** None

---

### 5.8 `delete-ai-agent-version`

Deletes a specific version of an AI agent.

**Synopsis:**
```bash
aws qconnect delete-ai-agent-version \
    --assistant-id <value> \
    --ai-agent-id <value> \
    --version-number <value>
```

**Output:** None
