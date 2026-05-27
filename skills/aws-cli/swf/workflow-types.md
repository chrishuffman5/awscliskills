# Workflow Types

### 2.1 `register-workflow-type`

Registers a new workflow type and its configuration in the specified domain.

**Synopsis:**
```bash
aws swf register-workflow-type \
    --domain <value> \
    --name <value> \
    --workflow-version <value> \
    [--description <value>] \
    [--default-task-start-to-close-timeout <value>] \
    [--default-execution-start-to-close-timeout <value>] \
    [--default-task-list <value>] \
    [--default-task-priority <value>] \
    [--default-child-policy <value>] \
    [--default-lambda-role <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Domain name (1-256 chars) |
| `--name` | **Yes** | string | -- | Workflow type name (1-256 chars) |
| `--workflow-version` | **Yes** | string | -- | Version string (1-64 chars). Name+version must be unique |
| `--description` | No | string | None | Description (max 1024 chars) |
| `--default-task-start-to-close-timeout` | No | string | None | Default max decision task duration in seconds, or `NONE` |
| `--default-execution-start-to-close-timeout` | No | string | None | Default max workflow execution duration in seconds (max 1 year) |
| `--default-task-list` | No | structure | None | Default task list. Shorthand: `name=string` |
| `--default-task-priority` | No | string | `0` | Default task priority (integer) |
| `--default-child-policy` | No | string | None | `TERMINATE`, `REQUEST_CANCEL`, or `ABANDON` |
| `--default-lambda-role` | No | string | None | IAM role ARN for Lambda invocation (1-1600 chars) |

**Output:** None

---

### 2.2 `describe-workflow-type`

Describes a workflow type including its configuration settings.

**Synopsis:**
```bash
aws swf describe-workflow-type \
    --domain <value> \
    --workflow-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Domain name (1-256 chars) |
| `--workflow-type` | **Yes** | structure | -- | Workflow type. Shorthand: `name=string,version=string` |

**Output Schema:**
```json
{
    "typeInfo": {
        "workflowType": {
            "name": "string",
            "version": "string"
        },
        "status": "REGISTERED|DEPRECATED",
        "description": "string",
        "creationDate": "timestamp",
        "deprecationDate": "timestamp"
    },
    "configuration": {
        "defaultTaskStartToCloseTimeout": "string",
        "defaultExecutionStartToCloseTimeout": "string",
        "defaultTaskList": {
            "name": "string"
        },
        "defaultTaskPriority": "string",
        "defaultChildPolicy": "TERMINATE|REQUEST_CANCEL|ABANDON",
        "defaultLambdaRole": "string"
    }
}
```

---

### 2.3 `list-workflow-types`

Lists workflow types in a domain. **Paginated operation.**

**Synopsis:**
```bash
aws swf list-workflow-types \
    --domain <value> \
    --registration-status <value> \
    [--name <value>] \
    [--reverse-order | --no-reverse-order] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Domain name (1-256 chars) |
| `--registration-status` | **Yes** | string | -- | `REGISTERED` or `DEPRECATED` |
| `--name` | No | string | None | Filter by workflow type name |
| `--reverse-order` | No | boolean | false | Return results in reverse order |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "typeInfos": [
        {
            "workflowType": {
                "name": "string",
                "version": "string"
            },
            "status": "REGISTERED|DEPRECATED",
            "description": "string",
            "creationDate": "timestamp",
            "deprecationDate": "timestamp"
        }
    ],
    "nextPageToken": "string"
}
```

---

### 2.4 `deprecate-workflow-type`

Deprecates a workflow type. No new executions of this type can be started, but existing ones continue.

**Synopsis:**
```bash
aws swf deprecate-workflow-type \
    --domain <value> \
    --workflow-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Domain name (1-256 chars) |
| `--workflow-type` | **Yes** | structure | -- | Workflow type. Shorthand: `name=string,version=string` |

**Output:** None

---

### 2.5 `undeprecate-workflow-type`

Undeprecates a previously deprecated workflow type.

**Synopsis:**
```bash
aws swf undeprecate-workflow-type \
    --domain <value> \
    --workflow-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Domain name (1-256 chars) |
| `--workflow-type` | **Yes** | structure | -- | Workflow type. Shorthand: `name=string,version=string` |

**Output:** None

---

### 2.6 `delete-workflow-type`

Deletes a workflow type. The type must be deprecated first and have no running executions.

**Synopsis:**
```bash
aws swf delete-workflow-type \
    --domain <value> \
    --workflow-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Domain name (1-256 chars) |
| `--workflow-type` | **Yes** | structure | -- | Workflow type. Shorthand: `name=string,version=string` |

**Output:** None
