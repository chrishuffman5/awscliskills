# Stack Refactors

### 5.1 `create-stack-refactor`

Creates a stack refactor operation, which allows you to move resources between stacks.

**Synopsis:**
```bash
aws cloudformation create-stack-refactor \
    --description <value> \
    --resource-mappings <value> \
    [--enable-stack-creation | --no-enable-stack-creation] \
    [--stack-definitions <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--description` | **Yes** | string | -- | Description of the refactor operation |
| `--resource-mappings` | **Yes** | list | -- | Resource mappings. JSON: `[{"Source":{"StackName":"string","LogicalResourceId":"string"},"Destination":{"StackName":"string","LogicalResourceId":"string"}}]` |
| `--enable-stack-creation` | No | boolean | false | Allow creation of new stacks during refactor |
| `--stack-definitions` | No | list | None | Definitions for new stacks. JSON: `[{"StackName":"string","TemplateBody":"string","TemplateURL":"string"}]` |

**Output Schema:**
```json
{
    "StackRefactorId": "string"
}
```

---

### 5.2 `describe-stack-refactor`

Returns information about a stack refactor operation.

**Synopsis:**
```bash
aws cloudformation describe-stack-refactor \
    --stack-refactor-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stack-refactor-id` | **Yes** | string | -- | Stack refactor ID |

**Output Schema:**
```json
{
    "StackRefactorId": "string",
    "Description": "string",
    "Status": "CREATE_IN_PROGRESS|CREATE_COMPLETE|CREATE_FAILED|EXECUTE_IN_PROGRESS|EXECUTE_COMPLETE|EXECUTE_FAILED|ROLLBACK_IN_PROGRESS|ROLLBACK_COMPLETE|ROLLBACK_FAILED",
    "StatusReason": "string",
    "ExecutionStatus": "UNAVAILABLE|AVAILABLE|EXECUTE_IN_PROGRESS|EXECUTE_COMPLETE|EXECUTE_FAILED|OBSOLETE|ROLLBACK_COMPLETE|ROLLBACK_FAILED",
    "ExecutionStatusReason": "string",
    "StackIds": ["string"],
    "CreationTime": "timestamp"
}
```

---

### 5.3 `execute-stack-refactor`

Executes a previously created stack refactor operation, moving resources between stacks.

**Synopsis:**
```bash
aws cloudformation execute-stack-refactor \
    --stack-refactor-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stack-refactor-id` | **Yes** | string | -- | Stack refactor ID |

**Output:** No output on success (empty JSON `{}`).

---

### 5.4 `list-stack-refactors`

Lists stack refactor operations. **Paginated operation.**

**Synopsis:**
```bash
aws cloudformation list-stack-refactors \
    [--execution-status-filter <value>] \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--execution-status-filter` | No | list(string) | None | Filter by execution status |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "StackRefactorSummaries": [
        {
            "StackRefactorId": "string",
            "Description": "string",
            "Status": "string",
            "StatusReason": "string",
            "ExecutionStatus": "string",
            "ExecutionStatusReason": "string",
            "CreationTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 5.5 `list-stack-refactor-actions`

Lists the resource-level actions for a stack refactor operation. **Paginated operation.**

**Synopsis:**
```bash
aws cloudformation list-stack-refactor-actions \
    --stack-refactor-id <value> \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stack-refactor-id` | **Yes** | string | -- | Stack refactor ID |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "StackRefactorActions": [
        {
            "Action": "MOVE",
            "Entity": "RESOURCE",
            "PhysicalResourceId": "string",
            "ResourceType": "string",
            "Description": "string",
            "Detection": "AUTO|MANUAL",
            "Source": {
                "StackName": "string",
                "LogicalResourceId": "string"
            },
            "Destination": {
                "StackName": "string",
                "LogicalResourceId": "string"
            },
            "ResourceMapping": {
                "Source": {
                    "StackName": "string",
                    "LogicalResourceId": "string"
                },
                "Destination": {
                    "StackName": "string",
                    "LogicalResourceId": "string"
                }
            },
            "TagResources": [
                {
                    "Key": "string",
                    "Value": "string"
                }
            ]
        }
    ],
    "NextToken": "string"
}
```
