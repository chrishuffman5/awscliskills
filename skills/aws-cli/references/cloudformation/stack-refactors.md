# Stack Refactors

### 5.1 `create-stack-refactor`

Creates a stack refactor, which allows you to move resources between stacks. The refactor analyzes the proposed changes and reports any issues.

**Synopsis:**
```bash
aws cloudformation create-stack-refactor \
    --stack-definitions <value> \
    [--description <value>] \
    [--enable-stack-creation | --no-enable-stack-creation] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stack-definitions` | **Yes** | list | -- | Stack definitions describing the source and destination stacks and resources to move. JSON structure: `[{"StackName":"string","TemplateBody":"string","TemplateURL":"string"}]` |
| `--description` | No | string | None | Description of the refactor |
| `--enable-stack-creation` | No | boolean | false | Allow creation of new stacks as part of the refactor |

**Output Schema:**
```json
{
    "StackRefactorId": "string"
}
```

---

### 5.2 `describe-stack-refactor`

Returns the description of a stack refactor, including status and any issues detected.

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
    "ExecutionStatus": "UNAVAILABLE|AVAILABLE|EXECUTE_IN_PROGRESS|EXECUTE_COMPLETE|EXECUTE_FAILED|ROLLBACK_COMPLETE|ROLLBACK_FAILED",
    "ExecutionStatusReason": "string",
    "StackDefinitions": [
        {
            "StackName": "string",
            "TemplateBody": "string",
            "TemplateURL": "string"
        }
    ],
    "ResourceMappings": [
        {
            "Source": {
                "StackName": "string",
                "LogicalResourceId": "string"
            },
            "Destination": {
                "StackName": "string",
                "LogicalResourceId": "string"
            }
        }
    ]
}
```

---

### 5.3 `list-stack-refactors`

Lists all stack refactors. **Paginated operation.**

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
            "ExecutionStatusReason": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 5.4 `execute-stack-refactor`

Executes a stack refactor, moving resources between stacks as planned.

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

**Output:** No output on success.
