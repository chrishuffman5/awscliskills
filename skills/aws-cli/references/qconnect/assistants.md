# Assistants

### 1.1 `create-assistant`

Creates an Amazon Q in Connect assistant.

**Synopsis:**
```bash
aws qconnect create-assistant \
    --name <value> \
    --type <value> \
    [--description <value>] \
    [--server-side-encryption-configuration <value>] \
    [--client-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Assistant name (1-255 chars) |
| `--type` | **Yes** | string | -- | Must be `AGENT` |
| `--description` | No | string | None | Description (1-255 chars) |
| `--server-side-encryption-configuration` | No | structure | None | KMS config: `kmsKeyId=string` |
| `--client-token` | No | string | None | Idempotency token (1-4096 chars) |
| `--tags` | No | map | None | Tags |

**Output Schema:**
```json
{
    "assistant": {
        "assistantId": "string",
        "assistantArn": "string",
        "name": "string",
        "type": "AGENT",
        "status": "CREATE_IN_PROGRESS|CREATE_FAILED|ACTIVE|DELETE_IN_PROGRESS|DELETE_FAILED|DELETED",
        "description": "string",
        "tags": {},
        "serverSideEncryptionConfiguration": {},
        "capabilityConfiguration": {"type": "V1|V2"},
        "aiAgentConfiguration": {}
    }
}
```

---

### 1.2 `get-assistant`

Gets an assistant.

**Synopsis:**
```bash
aws qconnect get-assistant \
    --assistant-id <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--assistant-id` | **Yes** | string | -- | Assistant ID or ARN |

**Output Schema:** Same as `create-assistant`.

---

### 1.3 `list-assistants`

Lists assistants. **Paginated operation.**

**Synopsis:**
```bash
aws qconnect list-assistants \
    [--next-token <value>] \
    [--max-results <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-100) |

**Output Schema:**
```json
{
    "assistantSummaries": [
        {
            "assistantId": "string",
            "assistantArn": "string",
            "name": "string",
            "type": "string",
            "status": "string",
            "description": "string",
            "tags": {},
            "serverSideEncryptionConfiguration": {},
            "capabilityConfiguration": {},
            "aiAgentConfiguration": {}
        }
    ],
    "nextToken": "string"
}
```

---

### 1.4 `delete-assistant`

Deletes an assistant.

**Synopsis:**
```bash
aws qconnect delete-assistant \
    --assistant-id <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--assistant-id` | **Yes** | string | -- | Assistant ID or ARN |

**Output:** None

---

### 1.5 `update-assistant-ai-agent`

Updates the AI agent configuration on an assistant.

**Synopsis:**
```bash
aws qconnect update-assistant-ai-agent \
    --assistant-id <value> \
    --ai-agent-type <value> \
    --configuration <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--assistant-id` | **Yes** | string | -- | Assistant ID or ARN |
| `--ai-agent-type` | **Yes** | string | -- | Agent type (see AI Agent Types in index) |
| `--configuration` | **Yes** | structure | -- | Config: `aiAgentId=string` |

**Output Schema:**
```json
{
    "assistant": { ... }
}
```

---

### 1.6 `remove-assistant-ai-agent`

Removes an AI agent from an assistant.

**Synopsis:**
```bash
aws qconnect remove-assistant-ai-agent \
    --assistant-id <value> \
    --ai-agent-type <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--assistant-id` | **Yes** | string | -- | Assistant ID or ARN |
| `--ai-agent-type` | **Yes** | string | -- | Agent type to remove |

**Output:** None

---

## Assistant Associations

### 1.7 `create-assistant-association`

Associates a resource (e.g., knowledge base) with an assistant.

**Synopsis:**
```bash
aws qconnect create-assistant-association \
    --assistant-id <value> \
    --association-type <value> \
    --association <value> \
    [--client-token <value>] \
    [--tags <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--assistant-id` | **Yes** | string | -- | Assistant ID or ARN |
| `--association-type` | **Yes** | string | -- | Must be `KNOWLEDGE_BASE` |
| `--association` | **Yes** | structure | -- | Association data: `knowledgeBaseId=string` |
| `--client-token` | No | string | None | Idempotency token |
| `--tags` | No | map | None | Tags |

**Output Schema:**
```json
{
    "assistantAssociation": {
        "assistantAssociationId": "string",
        "assistantAssociationArn": "string",
        "assistantId": "string",
        "assistantArn": "string",
        "associationType": "KNOWLEDGE_BASE",
        "associationData": {
            "knowledgeBaseAssociation": {
                "knowledgeBaseId": "string",
                "knowledgeBaseArn": "string"
            }
        },
        "tags": {}
    }
}
```

---

### 1.8 `get-assistant-association`

Gets an assistant association.

**Synopsis:**
```bash
aws qconnect get-assistant-association \
    --assistant-id <value> \
    --assistant-association-id <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--assistant-id` | **Yes** | string | -- | Assistant ID or ARN |
| `--assistant-association-id` | **Yes** | string | -- | Association ID or ARN |

**Output Schema:** Same as `create-assistant-association`.

---

### 1.9 `list-assistant-associations`

Lists assistant associations. **Paginated operation.**

**Synopsis:**
```bash
aws qconnect list-assistant-associations \
    --assistant-id <value> \
    [--next-token <value>] \
    [--max-results <value>]
```

**Output Schema:**
```json
{
    "assistantAssociationSummaries": [...],
    "nextToken": "string"
}
```

---

### 1.10 `delete-assistant-association`

Deletes an assistant association.

**Synopsis:**
```bash
aws qconnect delete-assistant-association \
    --assistant-id <value> \
    --assistant-association-id <value>
```

**Output:** None
