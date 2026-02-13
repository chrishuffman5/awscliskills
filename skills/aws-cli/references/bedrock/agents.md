# Agents

### `create-agent`

Creates an Amazon Bedrock agent that orchestrates interactions between foundation models, knowledge bases, action groups, and user conversations.

**Synopsis:**
```bash
aws bedrock-agent create-agent \
    --agent-name <value> \
    [--agent-resource-role-arn <value>] \
    [--foundation-model <value>] \
    [--instruction <value>] \
    [--description <value>] \
    [--orchestration-type <value>] \
    [--custom-orchestration <value>] \
    [--idle-session-ttl-in-seconds <value>] \
    [--customer-encryption-key-arn <value>] \
    [--tags <value>] \
    [--prompt-override-configuration <value>] \
    [--guardrail-configuration <value>] \
    [--memory-configuration <value>] \
    [--agent-collaboration <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--agent-name` | **Yes** | string | -- | Agent name. Pattern: `([0-9a-zA-Z][_-]?){1,100}` |
| `--agent-resource-role-arn` | No | string | None | IAM role ARN for the agent |
| `--foundation-model` | No | string | None | Model identifier for orchestration (1-2048 chars) |
| `--instruction` | No | string | None | Instructions for the agent (40-4000 chars) |
| `--description` | No | string | None | Description (1-200 chars) |
| `--orchestration-type` | No | string | None | `DEFAULT` or `CUSTOM_ORCHESTRATION` |
| `--custom-orchestration` | No | structure | None | Custom orchestration Lambda config |
| `--idle-session-ttl-in-seconds` | No | integer | None | Session TTL (60-5400 seconds) |
| `--customer-encryption-key-arn` | No | string | None | KMS key ARN for encryption |
| `--tags` | No | map | None | Key-value tags |
| `--prompt-override-configuration` | No | structure | None | Override default prompts |
| `--guardrail-configuration` | No | structure | None | Guardrail config: `guardrailIdentifier`, `guardrailVersion` |
| `--memory-configuration` | No | structure | None | Memory configuration for session retention |
| `--agent-collaboration` | No | string | None | Collaboration role: `SUPERVISOR`, `SUPERVISOR_ROUTER`, `DISABLED` |
| `--client-token` | No | string | None | Idempotency token (33-256 chars) |

**Memory Configuration Structure:**
```json
{
    "enabledMemoryTypes": ["SESSION_SUMMARY"],
    "storageDays": 30,
    "sessionSummaryConfiguration": {
        "maxRecentSessions": 20
    }
}
```

**Output Schema:**
```json
{
    "agent": {
        "agentId": "string",
        "agentName": "string",
        "agentArn": "string",
        "agentVersion": "DRAFT",
        "agentStatus": "CREATING|PREPARING|PREPARED|NOT_PREPARED|FAILED|UPDATING|DELETING|VERSIONING",
        "foundationModel": "string",
        "instruction": "string",
        "description": "string",
        "orchestrationType": "DEFAULT|CUSTOM_ORCHESTRATION",
        "idleSessionTTLInSeconds": "integer",
        "agentResourceRoleArn": "string",
        "customerEncryptionKeyArn": "string",
        "createdAt": "timestamp",
        "updatedAt": "timestamp",
        "failureReasons": ["string"],
        "recommendedActions": ["string"],
        "guardrailConfiguration": {
            "guardrailIdentifier": "string",
            "guardrailVersion": "string"
        },
        "memoryConfiguration": {...},
        "agentCollaboration": "string"
    }
}
```

---

### `get-agent`

Gets details of an agent.

**Synopsis:**
```bash
aws bedrock-agent get-agent \
    --agent-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--agent-id` | **Yes** | string | -- | Agent ID (10 alphanumeric chars) |

**Output Schema:** Same as `create-agent` output.

---

### `list-agents`

Lists agents in the account. **Paginated operation.**

**Synopsis:**
```bash
aws bedrock-agent list-agents \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Output Schema:**
```json
{
    "agentSummaries": [
        {
            "agentId": "string",
            "agentName": "string",
            "agentStatus": "CREATING|PREPARING|PREPARED|NOT_PREPARED|FAILED|UPDATING|DELETING|VERSIONING",
            "description": "string",
            "guardrailConfiguration": {...},
            "latestAgentVersion": "string",
            "updatedAt": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### `update-agent`

Updates an agent configuration. The agent must be re-prepared after updating.

**Synopsis:**
```bash
aws bedrock-agent update-agent \
    --agent-id <value> \
    --agent-name <value> \
    --agent-resource-role-arn <value> \
    [--foundation-model <value>] \
    [--instruction <value>] \
    [--description <value>] \
    [--orchestration-type <value>] \
    [--custom-orchestration <value>] \
    [--idle-session-ttl-in-seconds <value>] \
    [--customer-encryption-key-arn <value>] \
    [--prompt-override-configuration <value>] \
    [--guardrail-configuration <value>] \
    [--memory-configuration <value>] \
    [--agent-collaboration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--agent-id` | **Yes** | string | -- | Agent ID |
| `--agent-name` | **Yes** | string | -- | Agent name |
| `--agent-resource-role-arn` | **Yes** | string | -- | IAM role ARN |
| (other params same as create-agent) | No | various | None | Same optional params as create |

**Output Schema:** Same as `create-agent` output.

---

### `delete-agent`

Deletes an agent.

**Synopsis:**
```bash
aws bedrock-agent delete-agent \
    --agent-id <value> \
    [--skip-resource-in-use-check | --no-skip-resource-in-use-check] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--agent-id` | **Yes** | string | -- | Agent ID |
| `--skip-resource-in-use-check` | No | boolean | false | Skip check for resources in use |

**Output Schema:**
```json
{
    "agentId": "string",
    "agentStatus": "DELETING"
}
```

---

### `prepare-agent`

Prepares an agent for use. Must be called after creating or updating the agent.

**Synopsis:**
```bash
aws bedrock-agent prepare-agent \
    --agent-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--agent-id` | **Yes** | string | -- | Agent ID |

**Output Schema:**
```json
{
    "agentId": "string",
    "agentStatus": "PREPARING|PREPARED|FAILED",
    "agentVersion": "string",
    "preparedAt": "timestamp"
}
```

---

### `create-agent-alias`

Creates an alias that points to a specific agent version.

**Synopsis:**
```bash
aws bedrock-agent create-agent-alias \
    --agent-id <value> \
    --agent-alias-name <value> \
    [--description <value>] \
    [--routing-configuration <value>] \
    [--client-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--agent-id` | **Yes** | string | -- | Agent ID |
| `--agent-alias-name` | **Yes** | string | -- | Alias name. Pattern: `([0-9a-zA-Z][_-]?){1,100}` |
| `--description` | No | string | None | Description (1-200 chars) |
| `--routing-configuration` | No | list | None | Version routing config |
| `--client-token` | No | string | None | Idempotency token |
| `--tags` | No | map | None | Tags |

**Output Schema:**
```json
{
    "agentAlias": {
        "agentAliasId": "string",
        "agentAliasName": "string",
        "agentAliasArn": "string",
        "agentId": "string",
        "description": "string",
        "routingConfiguration": [
            {
                "agentVersion": "string",
                "provisionedThroughput": "string"
            }
        ],
        "agentAliasStatus": "CREATING|PREPARED|FAILED|UPDATING|DELETING",
        "createdAt": "timestamp",
        "updatedAt": "timestamp",
        "agentAliasHistoryEvents": [
            {
                "endDate": "timestamp",
                "startDate": "timestamp",
                "routingConfiguration": [...]
            }
        ]
    }
}
```

---

### `get-agent-alias`

Gets details of an agent alias.

**Synopsis:**
```bash
aws bedrock-agent get-agent-alias \
    --agent-id <value> \
    --agent-alias-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--agent-id` | **Yes** | string | -- | Agent ID |
| `--agent-alias-id` | **Yes** | string | -- | Alias ID |

**Output Schema:** Same as `create-agent-alias` output.

---

### `list-agent-aliases`

Lists aliases for an agent. **Paginated operation.**

**Synopsis:**
```bash
aws bedrock-agent list-agent-aliases \
    --agent-id <value> \
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

**Output Schema:**
```json
{
    "agentAliasSummaries": [
        {
            "agentAliasId": "string",
            "agentAliasName": "string",
            "agentAliasStatus": "CREATING|PREPARED|FAILED|UPDATING|DELETING",
            "description": "string",
            "routingConfiguration": [...],
            "createdAt": "timestamp",
            "updatedAt": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### `update-agent-alias`

Updates an agent alias.

**Synopsis:**
```bash
aws bedrock-agent update-agent-alias \
    --agent-id <value> \
    --agent-alias-id <value> \
    --agent-alias-name <value> \
    [--description <value>] \
    [--routing-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--agent-id` | **Yes** | string | -- | Agent ID |
| `--agent-alias-id` | **Yes** | string | -- | Alias ID |
| `--agent-alias-name` | **Yes** | string | -- | Updated alias name |
| `--description` | No | string | None | Updated description |
| `--routing-configuration` | No | list | None | Updated routing |

**Output Schema:** Same as `create-agent-alias` output.

---

### `delete-agent-alias`

Deletes an agent alias.

**Synopsis:**
```bash
aws bedrock-agent delete-agent-alias \
    --agent-id <value> \
    --agent-alias-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--agent-id` | **Yes** | string | -- | Agent ID |
| `--agent-alias-id` | **Yes** | string | -- | Alias ID |

**Output Schema:**
```json
{
    "agentId": "string",
    "agentAliasId": "string",
    "agentAliasStatus": "DELETING"
}
```

---

### `get-agent-version`

Gets details of a specific agent version.

**Synopsis:**
```bash
aws bedrock-agent get-agent-version \
    --agent-id <value> \
    --agent-version <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--agent-id` | **Yes** | string | -- | Agent ID |
| `--agent-version` | **Yes** | string | -- | Version number |

**Output Schema:**
```json
{
    "agentVersion": {
        "agentId": "string",
        "agentName": "string",
        "agentArn": "string",
        "version": "string",
        "agentStatus": "string",
        "foundationModel": "string",
        "instruction": "string",
        "description": "string",
        "createdAt": "timestamp",
        "updatedAt": "timestamp"
    }
}
```

---

### `list-agent-versions`

Lists versions of an agent. **Paginated operation.**

**Synopsis:**
```bash
aws bedrock-agent list-agent-versions \
    --agent-id <value> \
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

**Output Schema:**
```json
{
    "agentVersionSummaries": [
        {
            "agentName": "string",
            "agentStatus": "string",
            "agentVersion": "string",
            "createdAt": "timestamp",
            "updatedAt": "timestamp",
            "description": "string",
            "guardrailConfiguration": {...}
        }
    ],
    "nextToken": "string"
}
```

---

### `delete-agent-version`

Deletes a specific agent version.

**Synopsis:**
```bash
aws bedrock-agent delete-agent-version \
    --agent-id <value> \
    --agent-version <value> \
    [--skip-resource-in-use-check | --no-skip-resource-in-use-check] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--agent-id` | **Yes** | string | -- | Agent ID |
| `--agent-version` | **Yes** | string | -- | Version number to delete |
| `--skip-resource-in-use-check` | No | boolean | false | Skip resource in use check |

**Output Schema:**
```json
{
    "agentId": "string",
    "agentVersion": "string",
    "agentStatus": "DELETING"
}
```
