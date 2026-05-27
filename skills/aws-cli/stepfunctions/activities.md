# Activities

### 3.1 `create-activity`

Creates an activity. Activities enable you to have a task in your state machine that is performed by a worker running outside of Step Functions.

**Synopsis:**
```bash
aws stepfunctions create-activity \
    --name <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the activity (1-80 chars) |
| `--tags` | No | list | None | Tags. Shorthand: `key=string,value=string` |

**Output Schema:**
```json
{
    "activityArn": "string",
    "creationDate": "timestamp"
}
```

---

### 3.2 `delete-activity`

Deletes an activity.

**Synopsis:**
```bash
aws stepfunctions delete-activity \
    --activity-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--activity-arn` | **Yes** | string | -- | ARN of the activity to delete |

**Output:** None

---

### 3.3 `describe-activity`

Gets information about an activity.

**Synopsis:**
```bash
aws stepfunctions describe-activity \
    --activity-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--activity-arn` | **Yes** | string | -- | ARN of the activity |

**Output Schema:**
```json
{
    "activityArn": "string",
    "name": "string",
    "creationDate": "timestamp"
}
```

---

### 3.4 `list-activities`

Lists activities. **Paginated operation.**

**Synopsis:**
```bash
aws stepfunctions list-activities \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call (max 1000) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "activities": [
        {
            "activityArn": "string",
            "name": "string",
            "creationDate": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 3.5 `get-activity-task`

Gets a task token and input for an activity worker. This is a long-poll operation that blocks for up to 60 seconds waiting for work.

**Synopsis:**
```bash
aws stepfunctions get-activity-task \
    --activity-arn <value> \
    [--worker-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--activity-arn` | **Yes** | string | -- | ARN of the activity |
| `--worker-name` | No | string | None | Name of the worker requesting the task |

**Output Schema:**
```json
{
    "taskToken": "string",
    "input": "string"
}
```

---

### 3.6 `send-task-success`

Reports that the identified activity task completed successfully with the provided output.

**Synopsis:**
```bash
aws stepfunctions send-task-success \
    --task-token <value> \
    --output <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--task-token` | **Yes** | string | -- | Task token from `get-activity-task` |
| `--output` | **Yes** | string | -- | JSON output of the task (max 262144 chars) |

**Output:** None

---

### 3.7 `send-task-failure`

Reports that the identified activity task failed.

**Synopsis:**
```bash
aws stepfunctions send-task-failure \
    --task-token <value> \
    [--error <value>] \
    [--cause <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--task-token` | **Yes** | string | -- | Task token from `get-activity-task` |
| `--error` | No | string | None | Error code |
| `--cause` | No | string | None | Human-readable error description |

**Output:** None

---

### 3.8 `send-task-heartbeat`

Sends a heartbeat for an activity task to prevent it from timing out.

**Synopsis:**
```bash
aws stepfunctions send-task-heartbeat \
    --task-token <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--task-token` | **Yes** | string | -- | Task token from `get-activity-task` |

**Output:** None
