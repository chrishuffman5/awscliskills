# Agent Action Groups

### `create-agent-action-group`

Creates an action group for an agent. Action groups define the tasks the agent can perform by invoking Lambda functions or API operations.

**Synopsis:**
```bash
aws bedrock-agent create-agent-action-group \
    --agent-id <value> \
    --agent-version <value> \
    --action-group-name <value> \
    [--description <value>] \
    [--parent-action-group-signature <value>] \
    [--action-group-executor <value>] \
    [--api-schema <value>] \
    [--function-schema <value>] \
    [--action-group-state <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--agent-id` | **Yes** | string | -- | Agent ID |
| `--agent-version` | **Yes** | string | -- | Agent version (typically `DRAFT`) |
| `--action-group-name` | **Yes** | string | -- | Action group name. Pattern: `([0-9a-zA-Z][_-]?){1,100}` |
| `--description` | No | string | None | Description (1-200 chars) |
| `--parent-action-group-signature` | No | string | None | Built-in action: `AMAZON.UserInput`, `AMAZON.CodeInterpreter` |
| `--action-group-executor` | No | structure | None | Lambda function ARN or return-control config |
| `--api-schema` | No | structure | None | OpenAPI schema (inline or S3) |
| `--function-schema` | No | structure | None | Function definitions for the action group |
| `--action-group-state` | No | string | None | `ENABLED` or `DISABLED` |
| `--client-token` | No | string | None | Idempotency token |

**Action Group Executor Structure:**
```json
{
    "lambda": "arn:aws:lambda:us-east-1:123456789012:function:my-function"
}
```
or
```json
{
    "customControl": "RETURN_CONTROL"
}
```

**API Schema Structure (S3):**
```json
{
    "s3": {
        "s3BucketName": "my-bucket",
        "s3ObjectKey": "openapi-schema.json"
    }
}
```

**API Schema Structure (inline):**
```json
{
    "payload": "{ openapi spec as string }"
}
```

**Function Schema Structure:**
```json
{
    "functions": [
        {
            "name": "string",
            "description": "string",
            "parameters": {
                "paramName": {
                    "description": "string",
                    "type": "string|number|integer|boolean|array",
                    "required": true|false
                }
            },
            "requireConfirmation": "ENABLED|DISABLED"
        }
    ]
}
```

**Output Schema:**
```json
{
    "agentActionGroup": {
        "agentId": "string",
        "agentVersion": "string",
        "actionGroupId": "string",
        "actionGroupName": "string",
        "description": "string",
        "actionGroupState": "ENABLED|DISABLED",
        "actionGroupExecutor": {...},
        "apiSchema": {...},
        "functionSchema": {...},
        "parentActionSignature": "string",
        "createdAt": "timestamp",
        "updatedAt": "timestamp"
    }
}
```

---

### `get-agent-action-group`

Gets details of an action group.

**Synopsis:**
```bash
aws bedrock-agent get-agent-action-group \
    --agent-id <value> \
    --agent-version <value> \
    --action-group-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--agent-id` | **Yes** | string | -- | Agent ID |
| `--agent-version` | **Yes** | string | -- | Agent version |
| `--action-group-id` | **Yes** | string | -- | Action group ID |

**Output Schema:** Same as `create-agent-action-group` output.

---

### `list-agent-action-groups`

Lists action groups for an agent version. **Paginated operation.**

**Synopsis:**
```bash
aws bedrock-agent list-agent-action-groups \
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
    "actionGroupSummaries": [
        {
            "actionGroupId": "string",
            "actionGroupName": "string",
            "actionGroupState": "ENABLED|DISABLED",
            "description": "string",
            "updatedAt": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### `update-agent-action-group`

Updates an action group.

**Synopsis:**
```bash
aws bedrock-agent update-agent-action-group \
    --agent-id <value> \
    --agent-version <value> \
    --action-group-id <value> \
    --action-group-name <value> \
    [--description <value>] \
    [--parent-action-group-signature <value>] \
    [--action-group-executor <value>] \
    [--api-schema <value>] \
    [--function-schema <value>] \
    [--action-group-state <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--agent-id` | **Yes** | string | -- | Agent ID |
| `--agent-version` | **Yes** | string | -- | Agent version |
| `--action-group-id` | **Yes** | string | -- | Action group ID |
| `--action-group-name` | **Yes** | string | -- | Updated action group name |
| (other params same as create) | No | various | None | Same optional params as create |

**Output Schema:** Same as `create-agent-action-group` output.

---

### `delete-agent-action-group`

Deletes an action group.

**Synopsis:**
```bash
aws bedrock-agent delete-agent-action-group \
    --agent-id <value> \
    --agent-version <value> \
    --action-group-id <value> \
    [--skip-resource-in-use-check | --no-skip-resource-in-use-check] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--agent-id` | **Yes** | string | -- | Agent ID |
| `--agent-version` | **Yes** | string | -- | Agent version |
| `--action-group-id` | **Yes** | string | -- | Action group ID |
| `--skip-resource-in-use-check` | No | boolean | false | Skip resource in use check |

**Output:** None (HTTP 200 on success)
