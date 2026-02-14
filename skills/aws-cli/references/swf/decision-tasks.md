# Decision Tasks

### 6.1 `poll-for-decision-task`

Polls for a decision task from the specified task list. This is a long-poll operation that holds the connection open for up to 60 seconds. **Paginated operation** (for history events).

**Synopsis:**
```bash
aws swf poll-for-decision-task \
    --domain <value> \
    --task-list <value> \
    [--identity <value>] \
    [--reverse-order | --no-reverse-order] \
    [--start-at-previous-started-event | --no-start-at-previous-started-event] \
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
| `--task-list` | **Yes** | structure | -- | Task list to poll. Shorthand: `name=string` |
| `--identity` | No | string | None | Decider identity for diagnostics (max 256 chars) |
| `--reverse-order` | No | boolean | false | Return events in reverse chronological order |
| `--start-at-previous-started-event` | No | boolean | false | Return events from most recent DecisionTaskStarted only |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "taskToken": "string",
    "startedEventId": "long",
    "workflowExecution": {
        "workflowId": "string",
        "runId": "string"
    },
    "workflowType": {
        "name": "string",
        "version": "string"
    },
    "events": [
        {
            "eventTimestamp": "timestamp",
            "eventType": "string",
            "eventId": "long",
            "workflowExecutionStartedEventAttributes": {},
            "activityTaskScheduledEventAttributes": {},
            "activityTaskCompletedEventAttributes": {},
            "decisionTaskScheduledEventAttributes": {},
            "decisionTaskStartedEventAttributes": {}
        }
    ],
    "nextPageToken": "string",
    "previousStartedEventId": "long"
}
```

> **Note:** Set client-side socket timeout to at least 70 seconds. An empty `taskToken` means no task was available.

---

### 6.2 `respond-decision-task-completed`

Reports that a decision task has completed and provides a list of decisions to be applied.

**Synopsis:**
```bash
aws swf respond-decision-task-completed \
    --task-token <value> \
    [--decisions <value>] \
    [--execution-context <value>] \
    [--task-list <value>] \
    [--task-list-schedule-to-start-timeout <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--task-token` | **Yes** | string | -- | Task token (1-1024 chars) |
| `--decisions` | No | list | None | List of decision structures |
| `--execution-context` | No | string | None | Execution context data (max 32768 chars) |
| `--task-list` | No | structure | None | Override task list for future decisions. Shorthand: `name=string` |
| `--task-list-schedule-to-start-timeout` | No | string | None | Timeout for temporary task list override (seconds) |

**Decision Types:**

| Decision Type | Description |
|---------------|-------------|
| `ScheduleActivityTask` | Schedule an activity task |
| `RequestCancelActivityTask` | Cancel a scheduled activity task |
| `CompleteWorkflowExecution` | Complete the workflow successfully |
| `FailWorkflowExecution` | Fail the workflow |
| `CancelWorkflowExecution` | Cancel the workflow |
| `ContinueAsNewWorkflowExecution` | Close and restart as new execution |
| `RecordMarker` | Record a marker in history |
| `StartTimer` | Start a timer |
| `CancelTimer` | Cancel a timer |
| `SignalExternalWorkflowExecution` | Signal an external workflow |
| `RequestCancelExternalWorkflowExecution` | Request cancellation of external workflow |
| `StartChildWorkflowExecution` | Start a child workflow |
| `ScheduleLambdaFunction` | Schedule a Lambda function |

**Decision Structure Example:**
```json
[
    {
        "decisionType": "ScheduleActivityTask",
        "scheduleActivityTaskDecisionAttributes": {
            "activityType": {"name": "string", "version": "string"},
            "activityId": "string",
            "input": "string",
            "taskList": {"name": "string"},
            "scheduleToCloseTimeout": "string",
            "scheduleToStartTimeout": "string",
            "startToCloseTimeout": "string",
            "heartbeatTimeout": "string"
        }
    }
]
```

**Output:** None
