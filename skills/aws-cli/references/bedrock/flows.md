# Flows

### `create-flow`

Creates a flow that defines a directed acyclic graph (DAG) of nodes. Nodes can include prompts, knowledge bases, Lambda functions, conditions, and more.

**Synopsis:**
```bash
aws bedrock-agent create-flow \
    --name <value> \
    --execution-role-arn <value> \
    [--description <value>] \
    [--customer-encryption-key-arn <value>] \
    [--definition <value>] \
    [--client-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Flow name. Pattern: `([0-9a-zA-Z][_-]?){1,100}` |
| `--execution-role-arn` | **Yes** | string | -- | IAM role ARN for flow execution |
| `--description` | No | string | None | Description (1-200 chars) |
| `--customer-encryption-key-arn` | No | string | None | KMS key ARN for encryption |
| `--definition` | No | structure | None | Flow definition with nodes and connections |
| `--client-token` | No | string | None | Idempotency token |
| `--tags` | No | map | None | Key-value tags |

**Flow Definition Structure:**
```json
{
    "nodes": [
        {
            "name": "InputNode",
            "type": "Input",
            "configuration": {
                "input": {
                    "type": "String"
                }
            },
            "outputs": [
                {
                    "name": "document",
                    "type": "String"
                }
            ]
        },
        {
            "name": "PromptNode",
            "type": "Prompt",
            "configuration": {
                "prompt": {
                    "sourceConfiguration": {
                        "inline": {
                            "modelId": "anthropic.claude-3-sonnet-20240229-v1:0",
                            "templateType": "TEXT",
                            "templateConfiguration": {
                                "text": {
                                    "text": "Summarize: {{input}}"
                                }
                            },
                            "inferenceConfiguration": {
                                "text": {
                                    "maxTokens": 500,
                                    "temperature": 0.7
                                }
                            }
                        }
                    }
                }
            }
        },
        {
            "name": "OutputNode",
            "type": "Output"
        }
    ],
    "connections": [
        {
            "name": "InputToPrompt",
            "source": "InputNode",
            "target": "PromptNode",
            "type": "Data",
            "configuration": {
                "data": {
                    "sourceOutput": "document",
                    "targetInput": "input"
                }
            }
        },
        {
            "name": "PromptToOutput",
            "source": "PromptNode",
            "target": "OutputNode",
            "type": "Data",
            "configuration": {
                "data": {
                    "sourceOutput": "modelCompletion",
                    "targetInput": "document"
                }
            }
        }
    ]
}
```

**Node Types:** `Input`, `Output`, `KnowledgeBase`, `Condition`, `Lex`, `Prompt`, `LambdaFunction`, `Storage`, `Agent`, `Retrieval`, `Iterator`, `Collector`, `InlineCode`, `Loop`, `LoopInput`, `LoopController`

**Connection Types:** `Data` (data flow between nodes), `Conditional` (conditional branching)

**Output Schema:**
```json
{
    "name": "string",
    "description": "string",
    "executionRoleArn": "string",
    "id": "string",
    "arn": "string",
    "status": "NotPrepared|Preparing|Prepared|Failed",
    "createdAt": "timestamp",
    "updatedAt": "timestamp",
    "version": "DRAFT",
    "definition": {...},
    "customerEncryptionKeyArn": "string"
}
```

---

### `get-flow`

Gets details of a flow.

**Synopsis:**
```bash
aws bedrock-agent get-flow \
    --flow-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--flow-identifier` | **Yes** | string | -- | Flow ID or ARN |

**Output Schema:** Same as `create-flow` output.

---

### `list-flows`

Lists flows. **Paginated operation.**

**Synopsis:**
```bash
aws bedrock-agent list-flows \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Output Schema:**
```json
{
    "flowSummaries": [
        {
            "name": "string",
            "description": "string",
            "id": "string",
            "arn": "string",
            "status": "NotPrepared|Preparing|Prepared|Failed",
            "version": "string",
            "createdAt": "timestamp",
            "updatedAt": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### `update-flow`

Updates a flow definition and configuration.

**Synopsis:**
```bash
aws bedrock-agent update-flow \
    --flow-identifier <value> \
    --name <value> \
    --execution-role-arn <value> \
    [--description <value>] \
    [--customer-encryption-key-arn <value>] \
    [--definition <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Output Schema:** Same as `create-flow` output.

---

### `delete-flow`

Deletes a flow.

**Synopsis:**
```bash
aws bedrock-agent delete-flow \
    --flow-identifier <value> \
    [--skip-resource-in-use-check | --no-skip-resource-in-use-check] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--flow-identifier` | **Yes** | string | -- | Flow ID or ARN |
| `--skip-resource-in-use-check` | No | boolean | false | Skip resource in use check |

**Output Schema:**
```json
{
    "id": "string"
}
```

---

### `prepare-flow`

Prepares a flow for execution. Must be called after creating or updating a flow.

**Synopsis:**
```bash
aws bedrock-agent prepare-flow \
    --flow-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--flow-identifier` | **Yes** | string | -- | Flow ID or ARN |

**Output Schema:**
```json
{
    "id": "string",
    "status": "Preparing|Prepared|Failed"
}
```

---

### `validate-flow-definition`

Validates a flow definition without creating or updating the flow.

**Synopsis:**
```bash
aws bedrock-agent validate-flow-definition \
    --definition <value> \
    --execution-role-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--definition` | **Yes** | structure | -- | Flow definition to validate |
| `--execution-role-arn` | **Yes** | string | -- | IAM role ARN |

**Output Schema:**
```json
{
    "validations": [
        {
            "message": "string",
            "severity": "Warning|Error",
            "type": "string",
            "details": {...}
        }
    ]
}
```

---

### `create-flow-alias`

Creates an alias for a flow that points to a specific version.

**Synopsis:**
```bash
aws bedrock-agent create-flow-alias \
    --flow-identifier <value> \
    --name <value> \
    --routing-configuration <value> \
    [--description <value>] \
    [--client-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--flow-identifier` | **Yes** | string | -- | Flow ID or ARN |
| `--name` | **Yes** | string | -- | Alias name. Pattern: `([0-9a-zA-Z][_-]?){1,100}` |
| `--routing-configuration` | **Yes** | list | -- | Version routing config |
| `--description` | No | string | None | Description (1-200 chars) |
| `--client-token` | No | string | None | Idempotency token |
| `--tags` | No | map | None | Tags |

**Routing Configuration:**
```json
[
    {
        "flowVersion": "1"
    }
]
```

**Output Schema:**
```json
{
    "flowId": "string",
    "id": "string",
    "arn": "string",
    "name": "string",
    "description": "string",
    "routingConfiguration": [
        {
            "flowVersion": "string"
        }
    ],
    "createdAt": "timestamp",
    "updatedAt": "timestamp"
}
```

---

### `get-flow-alias`

Gets details of a flow alias.

**Synopsis:**
```bash
aws bedrock-agent get-flow-alias \
    --flow-identifier <value> \
    --alias-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

---

### `list-flow-aliases`

Lists flow aliases. **Paginated operation.**

**Synopsis:**
```bash
aws bedrock-agent list-flow-aliases \
    --flow-identifier <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

---

### `update-flow-alias`

Updates a flow alias.

**Synopsis:**
```bash
aws bedrock-agent update-flow-alias \
    --flow-identifier <value> \
    --alias-identifier <value> \
    --name <value> \
    --routing-configuration <value> \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

---

### `delete-flow-alias`

Deletes a flow alias.

**Synopsis:**
```bash
aws bedrock-agent delete-flow-alias \
    --flow-identifier <value> \
    --alias-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

---

### `create-flow-version`

Creates a versioned snapshot of a flow.

**Synopsis:**
```bash
aws bedrock-agent create-flow-version \
    --flow-identifier <value> \
    [--description <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--flow-identifier` | **Yes** | string | -- | Flow ID or ARN |
| `--description` | No | string | None | Version description |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:** Same as `create-flow` output, with incremented version.

---

### `get-flow-version`

Gets details of a specific flow version.

**Synopsis:**
```bash
aws bedrock-agent get-flow-version \
    --flow-identifier <value> \
    --flow-version <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

---

### `list-flow-versions`

Lists flow versions. **Paginated operation.**

**Synopsis:**
```bash
aws bedrock-agent list-flow-versions \
    --flow-identifier <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

---

### `delete-flow-version`

Deletes a specific flow version.

**Synopsis:**
```bash
aws bedrock-agent delete-flow-version \
    --flow-identifier <value> \
    --flow-version <value> \
    [--skip-resource-in-use-check | --no-skip-resource-in-use-check] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```
