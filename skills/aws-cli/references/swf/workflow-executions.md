# Workflow Executions

### 4.1 `start-workflow-execution`

Starts a new workflow execution of the specified type in the specified domain.

**Synopsis:**
```bash
aws swf start-workflow-execution \
    --domain <value> \
    --workflow-id <value> \
    --workflow-type <value> \
    [--task-list <value>] \
    [--task-priority <value>] \
    [--input <value>] \
    [--execution-start-to-close-timeout <value>] \
    [--tag-list <value>] \
    [--task-start-to-close-timeout <value>] \
    [--child-policy <value>] \
    [--lambda-role <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Domain name (1-256 chars) |
| `--workflow-id` | **Yes** | string | -- | User-defined execution identifier (1-256 chars) |
| `--workflow-type` | **Yes** | structure | -- | Workflow type. Shorthand: `name=string,version=string` |
| `--task-list` | No | structure | from type default | Task list for decisions. Shorthand: `name=string` |
| `--task-priority` | No | string | from type default | Task priority (integer) |
| `--input` | No | string | None | Input data for the workflow (max 32768 chars) |
| `--execution-start-to-close-timeout` | No | string | from type default | Max execution duration in seconds (max 1 year) |
| `--tag-list` | No | list | None | Tags for the execution (max 5). Space-separated strings |
| `--task-start-to-close-timeout` | No | string | from type default | Max decision task duration in seconds, or `NONE` |
| `--child-policy` | No | string | from type default | `TERMINATE`, `REQUEST_CANCEL`, or `ABANDON` |
| `--lambda-role` | No | string | from type default | IAM role ARN for Lambda invocation |

**Output Schema:**
```json
{
    "runId": "string"
}
```

---

### 4.2 `describe-workflow-execution`

Describes a workflow execution including its status, configuration, and open task counts.

**Synopsis:**
```bash
aws swf describe-workflow-execution \
    --domain <value> \
    --execution <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Domain name (1-256 chars) |
| `--execution` | **Yes** | structure | -- | Workflow execution. Shorthand: `workflowId=string,runId=string` |

**Output Schema:**
```json
{
    "executionInfo": {
        "execution": {
            "workflowId": "string",
            "runId": "string"
        },
        "workflowType": {
            "name": "string",
            "version": "string"
        },
        "startTimestamp": "timestamp",
        "closeTimestamp": "timestamp",
        "executionStatus": "OPEN|CLOSED",
        "closeStatus": "COMPLETED|FAILED|CANCELED|TERMINATED|CONTINUED_AS_NEW|TIMED_OUT",
        "parent": {
            "workflowId": "string",
            "runId": "string"
        },
        "tagList": ["string"],
        "cancelRequested": "boolean"
    },
    "executionConfiguration": {
        "taskStartToCloseTimeout": "string",
        "executionStartToCloseTimeout": "string",
        "taskList": {
            "name": "string"
        },
        "taskPriority": "string",
        "childPolicy": "TERMINATE|REQUEST_CANCEL|ABANDON",
        "lambdaRole": "string"
    },
    "openCounts": {
        "openActivityTasks": "integer",
        "openDecisionTasks": "integer",
        "openTimers": "integer",
        "openChildWorkflowExecutions": "integer",
        "openLambdaFunctions": "integer"
    },
    "latestActivityTaskTimestamp": "timestamp",
    "latestExecutionContext": "string"
}
```

---

### 4.3 `get-workflow-execution-history`

Returns the history of the specified workflow execution. **Paginated operation.**

**Synopsis:**
```bash
aws swf get-workflow-execution-history \
    --domain <value> \
    --execution <value> \
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
| `--execution` | **Yes** | structure | -- | Workflow execution. Shorthand: `workflowId=string,runId=string` |
| `--reverse-order` | No | boolean | false | Return events in reverse chronological order |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "events": [
        {
            "eventTimestamp": "timestamp",
            "eventType": "string",
            "eventId": "long",
            "workflowExecutionStartedEventAttributes": {},
            "workflowExecutionCompletedEventAttributes": {},
            "activityTaskScheduledEventAttributes": {},
            "activityTaskStartedEventAttributes": {},
            "activityTaskCompletedEventAttributes": {},
            "decisionTaskScheduledEventAttributes": {},
            "decisionTaskStartedEventAttributes": {},
            "decisionTaskCompletedEventAttributes": {}
        }
    ],
    "nextPageToken": "string"
}
```

---

### 4.4 `list-open-workflow-executions`

Lists open workflow executions in a domain matching specified criteria. **Paginated operation.**

**Synopsis:**
```bash
aws swf list-open-workflow-executions \
    --domain <value> \
    --start-time-filter <value> \
    [--type-filter <value>] \
    [--tag-filter <value>] \
    [--execution-filter <value>] \
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
| `--start-time-filter` | **Yes** | structure | -- | Start time range. Shorthand: `oldestDate=timestamp,latestDate=timestamp` |
| `--type-filter` | No | structure | None | Filter by workflow type. Shorthand: `name=string,version=string`. Mutually exclusive with `--tag-filter` and `--execution-filter` |
| `--tag-filter` | No | structure | None | Filter by tag. Shorthand: `tag=string`. Mutually exclusive with others |
| `--execution-filter` | No | structure | None | Filter by workflow ID. Shorthand: `workflowId=string`. Mutually exclusive with others |
| `--reverse-order` | No | boolean | false | Return results in reverse order |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "executionInfos": [
        {
            "execution": {
                "workflowId": "string",
                "runId": "string"
            },
            "workflowType": {
                "name": "string",
                "version": "string"
            },
            "startTimestamp": "timestamp",
            "closeTimestamp": "timestamp",
            "executionStatus": "OPEN|CLOSED",
            "closeStatus": "string",
            "parent": {
                "workflowId": "string",
                "runId": "string"
            },
            "tagList": ["string"],
            "cancelRequested": "boolean"
        }
    ],
    "nextPageToken": "string"
}
```

---

### 4.5 `list-closed-workflow-executions`

Lists closed workflow executions in a domain matching specified criteria. **Paginated operation.**

**Synopsis:**
```bash
aws swf list-closed-workflow-executions \
    --domain <value> \
    [--start-time-filter <value>] \
    [--close-time-filter <value>] \
    [--type-filter <value>] \
    [--tag-filter <value>] \
    [--execution-filter <value>] \
    [--close-status-filter <value>] \
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
| `--start-time-filter` | No | structure | None | Filter by start time. Mutually exclusive with `--close-time-filter` |
| `--close-time-filter` | No | structure | None | Filter by close time. Mutually exclusive with `--start-time-filter` |
| `--type-filter` | No | structure | None | Filter by workflow type. Mutually exclusive with `--tag-filter`, `--execution-filter`, `--close-status-filter` |
| `--tag-filter` | No | structure | None | Filter by tag. Mutually exclusive with others |
| `--execution-filter` | No | structure | None | Filter by workflow ID. Mutually exclusive with others |
| `--close-status-filter` | No | structure | None | Filter by close status: `COMPLETED`, `FAILED`, `CANCELED`, `TERMINATED`, `CONTINUED_AS_NEW`, `TIMED_OUT` |
| `--reverse-order` | No | boolean | false | Return results in reverse order |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "executionInfos": [
        {
            "execution": {
                "workflowId": "string",
                "runId": "string"
            },
            "workflowType": {
                "name": "string",
                "version": "string"
            },
            "startTimestamp": "timestamp",
            "closeTimestamp": "timestamp",
            "executionStatus": "OPEN|CLOSED",
            "closeStatus": "COMPLETED|FAILED|CANCELED|TERMINATED|CONTINUED_AS_NEW|TIMED_OUT",
            "parent": {},
            "tagList": ["string"],
            "cancelRequested": "boolean"
        }
    ],
    "nextPageToken": "string"
}
```

---

### 4.6 `request-cancel-workflow-execution`

Records a cancellation request for a workflow execution. The execution may or may not honor the request.

**Synopsis:**
```bash
aws swf request-cancel-workflow-execution \
    --domain <value> \
    --workflow-id <value> \
    [--run-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Domain name (1-256 chars) |
| `--workflow-id` | **Yes** | string | -- | Workflow execution ID (1-256 chars) |
| `--run-id` | No | string | None | Run ID of the execution (max 64 chars) |

**Output:** None

---

### 4.7 `signal-workflow-execution`

Sends a signal to a running workflow execution, which can be used to trigger decision logic.

**Synopsis:**
```bash
aws swf signal-workflow-execution \
    --domain <value> \
    --workflow-id <value> \
    --signal-name <value> \
    [--run-id <value>] \
    [--input <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Domain name (1-256 chars) |
| `--workflow-id` | **Yes** | string | -- | Workflow execution ID (1-256 chars) |
| `--signal-name` | **Yes** | string | -- | Signal name (1-256 chars) |
| `--run-id` | No | string | None | Run ID (max 64 chars) |
| `--input` | No | string | None | Signal data (max 32768 chars) |

**Output:** None

---

### 4.8 `terminate-workflow-execution`

Terminates a workflow execution immediately.

**Synopsis:**
```bash
aws swf terminate-workflow-execution \
    --domain <value> \
    --workflow-id <value> \
    [--run-id <value>] \
    [--reason <value>] \
    [--details <value>] \
    [--child-policy <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Domain name (1-256 chars) |
| `--workflow-id` | **Yes** | string | -- | Workflow execution ID (1-256 chars) |
| `--run-id` | No | string | None | Run ID (max 64 chars). If omitted, terminates the latest run |
| `--reason` | No | string | None | Reason for termination (max 256 chars) |
| `--details` | No | string | None | Details (max 32768 chars) |
| `--child-policy` | No | string | from type default | `TERMINATE`, `REQUEST_CANCEL`, or `ABANDON` |

**Output:** None
