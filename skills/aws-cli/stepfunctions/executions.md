# Executions

### 2.1 `start-execution`

Starts a new execution of a state machine.

**Synopsis:**
```bash
aws stepfunctions start-execution \
    --state-machine-arn <value> \
    [--name <value>] \
    [--input <value>] \
    [--trace-header <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--state-machine-arn` | **Yes** | string | -- | ARN of the state machine (or version/alias ARN) |
| `--name` | No | string | Auto-generated | Execution name (1-80 chars). Must be unique for standard workflows within 90 days |
| `--input` | No | string | `{}` | JSON input for the execution (max 262144 chars) |
| `--trace-header` | No | string | None | X-Ray trace header |

**Output Schema:**
```json
{
    "executionArn": "string",
    "startDate": "timestamp"
}
```

---

### 2.2 `start-sync-execution`

Starts a synchronous Express execution. Blocks until the execution completes and returns the result. Only works with Express state machines.

**Synopsis:**
```bash
aws stepfunctions start-sync-execution \
    --state-machine-arn <value> \
    [--name <value>] \
    [--input <value>] \
    [--trace-header <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--state-machine-arn` | **Yes** | string | -- | ARN of the Express state machine |
| `--name` | No | string | Auto-generated | Execution name |
| `--input` | No | string | `{}` | JSON input for the execution |
| `--trace-header` | No | string | None | X-Ray trace header |

**Output Schema:**
```json
{
    "executionArn": "string",
    "stateMachineArn": "string",
    "name": "string",
    "startDate": "timestamp",
    "stopDate": "timestamp",
    "status": "SUCCEEDED|FAILED|TIMED_OUT",
    "error": "string",
    "cause": "string",
    "input": "string",
    "inputDetails": {
        "included": "boolean"
    },
    "output": "string",
    "outputDetails": {
        "included": "boolean"
    },
    "traceHeader": "string",
    "billingDetails": {
        "billedMemoryUsedInMB": "long",
        "billedDurationInMilliseconds": "long"
    }
}
```

---

### 2.3 `stop-execution`

Stops a running execution.

**Synopsis:**
```bash
aws stepfunctions stop-execution \
    --execution-arn <value> \
    [--error <value>] \
    [--cause <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--execution-arn` | **Yes** | string | -- | ARN of the execution to stop |
| `--error` | No | string | None | Error code |
| `--cause` | No | string | None | Human-readable description of why the execution was stopped |

**Output Schema:**
```json
{
    "stopDate": "timestamp"
}
```

---

### 2.4 `describe-execution`

Gets information about an execution, including status, input, output, and timestamps.

**Synopsis:**
```bash
aws stepfunctions describe-execution \
    --execution-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--execution-arn` | **Yes** | string | -- | ARN of the execution |

**Output Schema:**
```json
{
    "executionArn": "string",
    "stateMachineArn": "string",
    "name": "string",
    "status": "RUNNING|SUCCEEDED|FAILED|TIMED_OUT|ABORTED|PENDING_REDRIVE",
    "startDate": "timestamp",
    "stopDate": "timestamp",
    "input": "string",
    "inputDetails": {
        "included": "boolean"
    },
    "output": "string",
    "outputDetails": {
        "included": "boolean"
    },
    "error": "string",
    "cause": "string",
    "stateMachineVersionArn": "string",
    "stateMachineAliasArn": "string",
    "redriveCount": "integer",
    "redriveDate": "timestamp",
    "redriveStatus": "REDRIVABLE|NOT_REDRIVABLE|REDRIVABLE_BY_MAP_RUN",
    "redriveStatusReason": "string",
    "mapRunArn": "string",
    "traceHeader": "string"
}
```

---

### 2.5 `list-executions`

Lists executions for a state machine. **Paginated operation.**

**Synopsis:**
```bash
aws stepfunctions list-executions \
    [--state-machine-arn <value>] \
    [--status-filter <value>] \
    [--map-run-arn <value>] \
    [--redrive-filter <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--state-machine-arn` | Cond. | string | None | ARN of the state machine (required unless map-run-arn is specified) |
| `--status-filter` | No | string | None | Filter: `RUNNING`, `SUCCEEDED`, `FAILED`, `TIMED_OUT`, `ABORTED`, `PENDING_REDRIVE` |
| `--map-run-arn` | No | string | None | ARN of a Map Run to list child executions |
| `--redrive-filter` | No | string | `NOT_REDRIVEN` | Filter: `REDRIVEN` or `NOT_REDRIVEN` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call (max 1000) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "executions": [
        {
            "executionArn": "string",
            "stateMachineArn": "string",
            "name": "string",
            "status": "RUNNING|SUCCEEDED|FAILED|TIMED_OUT|ABORTED|PENDING_REDRIVE",
            "startDate": "timestamp",
            "stopDate": "timestamp",
            "mapRunArn": "string",
            "itemCount": "integer",
            "stateMachineVersionArn": "string",
            "stateMachineAliasArn": "string",
            "redriveCount": "integer",
            "redriveDate": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 2.6 `get-execution-history`

Returns the event history for an execution. **Paginated operation.**

**Synopsis:**
```bash
aws stepfunctions get-execution-history \
    --execution-arn <value> \
    [--reverse-order | --no-reverse-order] \
    [--include-execution-data | --no-include-execution-data] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--execution-arn` | **Yes** | string | -- | ARN of the execution |
| `--reverse-order` | No | boolean | false | Return events in reverse chronological order |
| `--include-execution-data` | No | boolean | true | Include input/output data in events |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call (max 1000) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "events": [
        {
            "timestamp": "timestamp",
            "type": "string",
            "id": "long",
            "previousEventId": "long",
            "executionStartedEventDetails": {
                "input": "string",
                "inputDetails": {"included": "boolean"},
                "roleArn": "string"
            },
            "executionSucceededEventDetails": {
                "output": "string",
                "outputDetails": {"included": "boolean"}
            },
            "executionFailedEventDetails": {
                "error": "string",
                "cause": "string"
            },
            "taskScheduledEventDetails": {
                "resourceType": "string",
                "resource": "string",
                "region": "string",
                "parameters": "string",
                "timeoutInSeconds": "long",
                "heartbeatInSeconds": "long",
                "taskCredentials": {"roleArn": "string"}
            },
            "taskStartedEventDetails": {
                "resourceType": "string",
                "resource": "string"
            },
            "taskSucceededEventDetails": {
                "resourceType": "string",
                "resource": "string",
                "output": "string",
                "outputDetails": {"included": "boolean"}
            },
            "taskFailedEventDetails": {
                "resourceType": "string",
                "resource": "string",
                "error": "string",
                "cause": "string"
            },
            "stateEnteredEventDetails": {
                "name": "string",
                "input": "string",
                "inputDetails": {"included": "boolean"}
            },
            "stateExitedEventDetails": {
                "name": "string",
                "output": "string",
                "outputDetails": {"included": "boolean"}
            },
            "mapRunStartedEventDetails": {
                "mapRunArn": "string"
            }
        }
    ],
    "nextToken": "string"
}
```

---

### 2.7 `redrive-execution`

Redrives a failed or timed-out Standard workflow execution from the point of failure.

**Synopsis:**
```bash
aws stepfunctions redrive-execution \
    --execution-arn <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--execution-arn` | **Yes** | string | -- | ARN of the execution to redrive |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "redriveDate": "timestamp"
}
```
