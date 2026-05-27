# Dead-Letter Queue Redrive

### 3.1 `list-dead-letter-source-queues`

Returns the queues that have a `RedrivePolicy` configured to use the specified queue as their dead-letter queue. **Paginated operation.**

**Synopsis:**
```bash
aws sqs list-dead-letter-source-queues \
    --queue-url <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--queue-url` | **Yes** | string | -- | URL of the dead-letter queue. Case-sensitive. |
| `--starting-token` | No | string | -- | Pagination token from previous response |
| `--page-size` | No | integer | -- | Number of items per service call |
| `--max-items` | No | integer | 1000 | Maximum total items to return |

**Output Schema:**
```json
{
    "queueUrls": [
        "string"
    ],
    "NextToken": "string"
}
```

---

### 3.2 `start-message-move-task`

Starts an asynchronous task to move messages from a dead-letter queue back to source queues or to a specified destination. Only one active task per queue at a time. Max rate: 500 messages/second.

**Synopsis:**
```bash
aws sqs start-message-move-task \
    --source-arn <value> \
    [--destination-arn <value>] \
    [--max-number-of-messages-per-second <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-arn` | **Yes** | string | -- | ARN of the DLQ containing messages to move |
| `--destination-arn` | No | string | original source queues | ARN of the destination queue. If omitted, messages redrive to their original source queues. |
| `--max-number-of-messages-per-second` | No | integer | auto-optimized | Movement rate (max 500). If omitted, system optimizes based on backlog. |

**Output Schema:**
```json
{
    "TaskHandle": "string"
}
```

| Field | Description |
|-------|-------------|
| `TaskHandle` | Identifier for the move task. Use with `cancel-message-move-task`. |

---

### 3.3 `cancel-message-move-task`

Cancels a message move task. Can only cancel tasks with `RUNNING` status. Already-moved messages are not reverted.

**Synopsis:**
```bash
aws sqs cancel-message-move-task \
    --task-handle <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--task-handle` | **Yes** | string | -- | Task handle from `start-message-move-task` |

**Output Schema:**
```json
{
    "ApproximateNumberOfMessagesMoved": long
}
```

---

### 3.4 `list-message-move-tasks`

Lists message move tasks for a specified source queue. Returns up to 10 most recent tasks.

**Synopsis:**
```bash
aws sqs list-message-move-tasks \
    --source-arn <value> \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-arn` | **Yes** | string | -- | ARN of the source queue |
| `--max-results` | No | integer | 1 | Max results to return (1-10) |

**Output Schema:**
```json
{
    "Results": [
        {
            "TaskHandle": "string",
            "Status": "RUNNING|COMPLETED|CANCELLING|CANCELLED|FAILED",
            "SourceArn": "string",
            "DestinationArn": "string",
            "MaxNumberOfMessagesPerSecond": integer,
            "ApproximateNumberOfMessagesMoved": long,
            "ApproximateNumberOfMessagesToMove": long,
            "FailureReason": "string",
            "StartedTimestamp": long
        }
    ]
}
```

| Field | Description |
|-------|-------------|
| `TaskHandle` | Task identifier (populated only for `RUNNING` tasks) |
| `Status` | `RUNNING`, `COMPLETED`, `CANCELLING`, `CANCELLED`, or `FAILED` |
| `SourceArn` | ARN of the source DLQ |
| `DestinationArn` | ARN of the destination queue (null if not specified) |
| `MaxNumberOfMessagesPerSecond` | Configured movement rate |
| `ApproximateNumberOfMessagesMoved` | Count of messages already moved |
| `ApproximateNumberOfMessagesToMove` | Total messages to move |
| `FailureReason` | Reason for failure (only if `FAILED`) |
| `StartedTimestamp` | Unix timestamp when task started |
