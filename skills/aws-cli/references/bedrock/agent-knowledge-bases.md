# Agent Knowledge Bases & Collaborators

### `associate-agent-knowledge-base`

Associates a knowledge base with an agent so the agent can query it during orchestration.

**Synopsis:**
```bash
aws bedrock-agent associate-agent-knowledge-base \
    --agent-id <value> \
    --agent-version <value> \
    --knowledge-base-id <value> \
    --description <value> \
    [--knowledge-base-state <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--agent-id` | **Yes** | string | -- | Agent ID |
| `--agent-version` | **Yes** | string | -- | Agent version (typically `DRAFT`) |
| `--knowledge-base-id` | **Yes** | string | -- | Knowledge base ID |
| `--description` | **Yes** | string | -- | Description of how the agent uses this KB (1-200 chars) |
| `--knowledge-base-state` | No | string | None | `ENABLED` or `DISABLED` |

**Output Schema:**
```json
{
    "agentKnowledgeBase": {
        "agentId": "string",
        "agentVersion": "string",
        "knowledgeBaseId": "string",
        "description": "string",
        "knowledgeBaseState": "ENABLED|DISABLED",
        "createdAt": "timestamp",
        "updatedAt": "timestamp"
    }
}
```

---

### `get-agent-knowledge-base`

Gets details of an agent-knowledge base association.

**Synopsis:**
```bash
aws bedrock-agent get-agent-knowledge-base \
    --agent-id <value> \
    --agent-version <value> \
    --knowledge-base-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--agent-id` | **Yes** | string | -- | Agent ID |
| `--agent-version` | **Yes** | string | -- | Agent version |
| `--knowledge-base-id` | **Yes** | string | -- | Knowledge base ID |

**Output Schema:** Same as `associate-agent-knowledge-base` output.

---

### `list-agent-knowledge-bases`

Lists knowledge bases associated with an agent. **Paginated operation.**

**Synopsis:**
```bash
aws bedrock-agent list-agent-knowledge-bases \
    --agent-id <value> \
    --agent-version <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--agent-id` | **Yes** | string | -- | Agent ID |
| `--agent-version` | **Yes** | string | -- | Agent version |

**Output Schema:**
```json
{
    "agentKnowledgeBaseSummaries": [
        {
            "knowledgeBaseId": "string",
            "description": "string",
            "knowledgeBaseState": "ENABLED|DISABLED",
            "updatedAt": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### `update-agent-knowledge-base`

Updates an agent-knowledge base association.

**Synopsis:**
```bash
aws bedrock-agent update-agent-knowledge-base \
    --agent-id <value> \
    --agent-version <value> \
    --knowledge-base-id <value> \
    --description <value> \
    [--knowledge-base-state <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--agent-id` | **Yes** | string | -- | Agent ID |
| `--agent-version` | **Yes** | string | -- | Agent version |
| `--knowledge-base-id` | **Yes** | string | -- | Knowledge base ID |
| `--description` | **Yes** | string | -- | Updated description |
| `--knowledge-base-state` | No | string | None | `ENABLED` or `DISABLED` |

**Output Schema:** Same as `associate-agent-knowledge-base` output.

---

### `disassociate-agent-knowledge-base`

Removes a knowledge base association from an agent.

**Synopsis:**
```bash
aws bedrock-agent disassociate-agent-knowledge-base \
    --agent-id <value> \
    --agent-version <value> \
    --knowledge-base-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--agent-id` | **Yes** | string | -- | Agent ID |
| `--agent-version` | **Yes** | string | -- | Agent version |
| `--knowledge-base-id` | **Yes** | string | -- | Knowledge base ID |

**Output:** None (HTTP 200 on success)

---

### `associate-agent-collaborator`

Associates a collaborator agent with a supervisor agent for multi-agent collaboration.

**Synopsis:**
```bash
aws bedrock-agent associate-agent-collaborator \
    --agent-id <value> \
    --agent-version <value> \
    --agent-descriptor <value> \
    --collaboration-instruction <value> \
    --collaborator-name <value> \
    [--relay-conversation-history <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--agent-id` | **Yes** | string | -- | Supervisor agent ID |
| `--agent-version` | **Yes** | string | -- | Agent version (typically `DRAFT`) |
| `--agent-descriptor` | **Yes** | structure | -- | Collaborator agent: `aliasArn=<ARN>` |
| `--collaboration-instruction` | **Yes** | string | -- | Instructions for how to collaborate (1-4000 chars) |
| `--collaborator-name` | **Yes** | string | -- | Collaborator name. Pattern: `([0-9a-zA-Z][_-]?){1,100}` |
| `--relay-conversation-history` | No | string | None | `TO_COLLABORATOR` or `DISABLED` |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "agentCollaborator": {
        "agentId": "string",
        "agentVersion": "string",
        "collaboratorId": "string",
        "collaboratorName": "string",
        "agentDescriptor": {
            "aliasArn": "string"
        },
        "collaborationInstruction": "string",
        "relayConversationHistory": "TO_COLLABORATOR|DISABLED",
        "createdAt": "timestamp",
        "lastUpdatedAt": "timestamp"
    }
}
```

---

### `get-agent-collaborator`

Gets details of an agent collaborator.

**Synopsis:**
```bash
aws bedrock-agent get-agent-collaborator \
    --agent-id <value> \
    --agent-version <value> \
    --collaborator-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--agent-id` | **Yes** | string | -- | Agent ID |
| `--agent-version` | **Yes** | string | -- | Agent version |
| `--collaborator-id` | **Yes** | string | -- | Collaborator ID |

**Output Schema:** Same as `associate-agent-collaborator` output.

---

### `list-agent-collaborators`

Lists collaborators for an agent. **Paginated operation.**

**Synopsis:**
```bash
aws bedrock-agent list-agent-collaborators \
    --agent-id <value> \
    --agent-version <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--agent-id` | **Yes** | string | -- | Agent ID |
| `--agent-version` | **Yes** | string | -- | Agent version |

**Output Schema:**
```json
{
    "agentCollaboratorSummaries": [
        {
            "collaboratorId": "string",
            "collaboratorName": "string",
            "agentDescriptor": {"aliasArn": "string"},
            "collaborationInstruction": "string",
            "relayConversationHistory": "TO_COLLABORATOR|DISABLED",
            "createdAt": "timestamp",
            "lastUpdatedAt": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### `update-agent-collaborator`

Updates an agent collaborator.

**Synopsis:**
```bash
aws bedrock-agent update-agent-collaborator \
    --agent-id <value> \
    --agent-version <value> \
    --collaborator-id <value> \
    --agent-descriptor <value> \
    --collaboration-instruction <value> \
    --collaborator-name <value> \
    [--relay-conversation-history <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Output Schema:** Same as `associate-agent-collaborator` output.

---

### `disassociate-agent-collaborator`

Removes a collaborator from an agent.

**Synopsis:**
```bash
aws bedrock-agent disassociate-agent-collaborator \
    --agent-id <value> \
    --agent-version <value> \
    --collaborator-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--agent-id` | **Yes** | string | -- | Agent ID |
| `--agent-version` | **Yes** | string | -- | Agent version |
| `--collaborator-id` | **Yes** | string | -- | Collaborator ID |

**Output:** None (HTTP 200 on success)
