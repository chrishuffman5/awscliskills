# Tasks & Tags

## Task Runner Operations

These commands are used by task runners (the agents that execute pipeline activities). In most cases, AWS Data Pipeline manages task runners automatically via EC2 instances or EMR clusters. Manual use is uncommon.

### 4.1 `poll-for-task`

Task runners call this to receive a task to perform from AWS Data Pipeline. The task runner specifies which tasks it can perform by setting a value for the `workerGroup` parameter.

**Synopsis:**
```bash
aws datapipeline poll-for-task \
    --worker-group <value> \
    [--hostname <value>] \
    [--instance-identity <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--worker-group` | **Yes** | string | -- | Worker group name that identifies available tasks |
| `--hostname` | No | string | None | Hostname of the task runner (for tracking) |
| `--instance-identity` | No | structure | None | EC2 instance identity document for verification |

**Instance Identity Structure:**
```json
{
    "document": "string",
    "signature": "string"
}
```

**Output Schema:**
```json
{
    "taskObject": {
        "taskId": "string",
        "pipelineId": "string",
        "attemptId": "string",
        "objects": {
            "string": {
                "id": "string",
                "name": "string",
                "fields": [
                    {
                        "key": "string",
                        "stringValue": "string",
                        "refValue": "string"
                    }
                ]
            }
        }
    }
}
```

---

### 4.2 `report-task-progress`

Task runners call this when assigned a task to acknowledge that it has the task. If the task runner does not report progress within the timeout period, the task can be reassigned to another task runner. Also used to indicate that the task is still being processed.

**Synopsis:**
```bash
aws datapipeline report-task-progress \
    --task-id <value> \
    [--fields <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--task-id` | **Yes** | string | -- | ID of the task (from `poll-for-task`) |
| `--fields` | No | list | None | Key-value pairs for progress reporting. Shorthand: `key=string,stringValue=string ...` |

**Output Schema:**
```json
{
    "canceled": true|false
}
```

---

### 4.3 `report-task-runner-heartbeat`

Task runners call this to indicate that they are operational. If a task runner fails to send a heartbeat, it can be marked as inactive and its tasks may be reassigned.

**Synopsis:**
```bash
aws datapipeline report-task-runner-heartbeat \
    --taskrunner-id <value> \
    [--worker-group <value>] \
    [--hostname <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--taskrunner-id` | **Yes** | string | -- | ID of the task runner |
| `--worker-group` | No | string | None | Worker group the task runner belongs to |
| `--hostname` | No | string | None | Hostname of the task runner |

**Output Schema:**
```json
{
    "terminate": true|false
}
```

---

### 4.4 `set-task-status`

Task runners call this to notify AWS Data Pipeline that a task is completed and provide information about the final status.

**Synopsis:**
```bash
aws datapipeline set-task-status \
    --task-id <value> \
    --task-status <value> \
    [--error-id <value>] \
    [--error-message <value>] \
    [--error-stack-trace <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--task-id` | **Yes** | string | -- | ID of the task |
| `--task-status` | **Yes** | string | -- | Final status: `FINISHED`, `FAILED`, `FALSE` |
| `--error-id` | No | string | None | Error identifier (for `FAILED` status) |
| `--error-message` | No | string | None | Error message (for `FAILED` status) |
| `--error-stack-trace` | No | string | None | Error stack trace (for `FAILED` status) |

**Output:** None (HTTP 200 on success)

---

## Tags

### 4.5 `add-tags`

Adds or modifies tags for the specified pipeline.

**Synopsis:**
```bash
aws datapipeline add-tags \
    --pipeline-id <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pipeline-id` | **Yes** | string | -- | Pipeline ID |
| `--tags` | **Yes** | list | -- | Tags. Shorthand: `key=string,value=string ...` |

**Output:** None (HTTP 200 on success)

---

### 4.6 `remove-tags`

Removes existing tags from the specified pipeline.

**Synopsis:**
```bash
aws datapipeline remove-tags \
    --pipeline-id <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pipeline-id` | **Yes** | string | -- | Pipeline ID |
| `--tag-keys` | **Yes** | list(string) | -- | List of tag keys to remove |

**Output:** None (HTTP 200 on success)
