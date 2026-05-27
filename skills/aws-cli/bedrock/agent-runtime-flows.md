# Agent Runtime Flows

### `start-flow-execution`

Starts the execution of a prepared flow.

**Synopsis:**
```bash
aws bedrock-agent-runtime start-flow-execution \
    --flow-identifier <value> \
    --flow-alias-identifier <value> \
    --inputs <value> \
    [--model-performance-configuration <value>] \
    [--execution-role-override <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--flow-identifier` | **Yes** | string | -- | Flow ID or ARN |
| `--flow-alias-identifier` | **Yes** | string | -- | Flow alias ID or ARN |
| `--inputs` | **Yes** | list | -- | Input values for the flow |
| `--model-performance-configuration` | No | structure | None | Performance settings for models |
| `--execution-role-override` | No | string | None | Override execution role ARN |

**Inputs Structure:**
```json
[
    {
        "nodeName": "InputNode",
        "nodeOutputName": "document",
        "content": {
            "document": {
                "text": "What is Amazon Bedrock?"
            }
        }
    }
]
```

**Output Schema:**
```json
{
    "executionArn": "string"
}
```

---

### `get-flow-execution`

Gets details of a flow execution.

**Synopsis:**
```bash
aws bedrock-agent-runtime get-flow-execution \
    --flow-identifier <value> \
    --flow-alias-identifier <value> \
    --execution-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--flow-identifier` | **Yes** | string | -- | Flow ID or ARN |
| `--flow-alias-identifier` | **Yes** | string | -- | Flow alias ID or ARN |
| `--execution-identifier` | **Yes** | string | -- | Execution ID or ARN |

**Output Schema:**
```json
{
    "executionArn": "string",
    "flowIdentifier": "string",
    "flowAliasIdentifier": "string",
    "flowVersion": "string",
    "status": "Running|Succeeded|Failed|TimedOut|Aborted",
    "statusReason": "string",
    "startedAt": "timestamp",
    "endedAt": "timestamp"
}
```

---

### `list-flow-executions`

Lists flow executions. **Paginated operation.**

**Synopsis:**
```bash
aws bedrock-agent-runtime list-flow-executions \
    --flow-identifier <value> \
    --flow-alias-identifier <value> \
    [--status-equals <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--flow-identifier` | **Yes** | string | -- | Flow ID or ARN |
| `--flow-alias-identifier` | **Yes** | string | -- | Flow alias ID or ARN |
| `--status-equals` | No | string | None | Filter: `Running`, `Succeeded`, `Failed`, `TimedOut`, `Aborted` |

**Output Schema:**
```json
{
    "flowExecutionSummaries": [
        {
            "executionArn": "string",
            "flowIdentifier": "string",
            "flowAliasIdentifier": "string",
            "flowVersion": "string",
            "status": "Running|Succeeded|Failed|TimedOut|Aborted",
            "startedAt": "timestamp",
            "endedAt": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### `list-flow-execution-events`

Lists events for a flow execution. **Paginated operation.**

**Synopsis:**
```bash
aws bedrock-agent-runtime list-flow-execution-events \
    --flow-identifier <value> \
    --flow-alias-identifier <value> \
    --execution-identifier <value> \
    [--event-type <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--flow-identifier` | **Yes** | string | -- | Flow ID or ARN |
| `--flow-alias-identifier` | **Yes** | string | -- | Flow alias ID or ARN |
| `--execution-identifier` | **Yes** | string | -- | Execution ID or ARN |
| `--event-type` | No | string | None | Filter by event type: `Node`, `Flow` |

**Output Schema:**
```json
{
    "flowExecutionEvents": [
        {
            "node": {
                "nodeName": "string",
                "nodeType": "string",
                "timestamp": "timestamp",
                "eventType": "NodeStarted|NodeCompleted|NodeFailed",
                "fields": [...]
            },
            "flow": {
                "timestamp": "timestamp",
                "eventType": "FlowStarted|FlowCompleted|FlowFailed|FlowOutputReceived",
                "fields": [...]
            }
        }
    ],
    "nextToken": "string"
}
```

---

### `stop-flow-execution`

Stops a running flow execution.

**Synopsis:**
```bash
aws bedrock-agent-runtime stop-flow-execution \
    --flow-identifier <value> \
    --flow-alias-identifier <value> \
    --execution-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--flow-identifier` | **Yes** | string | -- | Flow ID or ARN |
| `--flow-alias-identifier` | **Yes** | string | -- | Flow alias ID or ARN |
| `--execution-identifier` | **Yes** | string | -- | Execution ID or ARN |

**Output Schema:**
```json
{
    "executionArn": "string",
    "status": "Aborted"
}
```

---

### `get-execution-flow-snapshot`

Gets the flow definition snapshot used for a specific execution.

**Synopsis:**
```bash
aws bedrock-agent-runtime get-execution-flow-snapshot \
    --flow-identifier <value> \
    --flow-alias-identifier <value> \
    --execution-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--flow-identifier` | **Yes** | string | -- | Flow ID or ARN |
| `--flow-alias-identifier` | **Yes** | string | -- | Flow alias ID or ARN |
| `--execution-identifier` | **Yes** | string | -- | Execution ID or ARN |

**Output Schema:**
```json
{
    "executionArn": "string",
    "flowIdentifier": "string",
    "flowAliasIdentifier": "string",
    "flowVersion": "string",
    "definition": {
        "nodes": [...],
        "connections": [...]
    },
    "executionRoleArn": "string",
    "customerEncryptionKeyArn": "string"
}
```
