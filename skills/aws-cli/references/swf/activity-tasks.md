# Activity Tasks

### 5.1 `poll-for-activity-task`

Polls for an activity task from the specified task list. This is a long-poll operation that holds the connection open for up to 60 seconds.

**Synopsis:**
```bash
aws swf poll-for-activity-task \
    --domain <value> \
    --task-list <value> \
    [--identity <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Domain name (1-256 chars) |
| `--task-list` | **Yes** | structure | -- | Task list to poll. Shorthand: `name=string` |
| `--identity` | No | string | None | Worker identity for diagnostics (max 256 chars) |

**Output Schema:**
```json
{
    "taskToken": "string",
    "activityId": "string",
    "startedEventId": "long",
    "workflowExecution": {
        "workflowId": "string",
        "runId": "string"
    },
    "activityType": {
        "name": "string",
        "version": "string"
    },
    "input": "string"
}
```

> **Note:** Set client-side socket timeout to at least 70 seconds. An empty `taskToken` means no task was available.

---

### 5.2 `record-activity-task-heartbeat`

Records that a worker is still making progress on an activity task. Used to prevent task timeout.

**Synopsis:**
```bash
aws swf record-activity-task-heartbeat \
    --task-token <value> \
    [--details <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--task-token` | **Yes** | string | -- | Task token from poll-for-activity-task (1-1024 chars) |
| `--details` | No | string | None | Free-form progress details (max 2048 chars) |

**Output Schema:**
```json
{
    "cancelRequested": "boolean"
}
```

---

### 5.3 `respond-activity-task-completed`

Reports that an activity task has completed successfully.

**Synopsis:**
```bash
aws swf respond-activity-task-completed \
    --task-token <value> \
    [--result <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--task-token` | **Yes** | string | -- | Task token (1-1024 chars) |
| `--result` | No | string | None | Result of the activity task (max 32768 chars) |

**Output:** None

---

### 5.4 `respond-activity-task-failed`

Reports that an activity task has failed.

**Synopsis:**
```bash
aws swf respond-activity-task-failed \
    --task-token <value> \
    [--reason <value>] \
    [--details <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--task-token` | **Yes** | string | -- | Task token (1-1024 chars) |
| `--reason` | No | string | None | Reason for failure (max 256 chars) |
| `--details` | No | string | None | Failure details (max 32768 chars) |

**Output:** None

---

### 5.5 `respond-activity-task-canceled`

Reports that an activity task has been canceled.

**Synopsis:**
```bash
aws swf respond-activity-task-canceled \
    --task-token <value> \
    [--details <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--task-token` | **Yes** | string | -- | Task token (1-1024 chars) |
| `--details` | No | string | None | Cancellation details (max 32768 chars) |

**Output:** None
