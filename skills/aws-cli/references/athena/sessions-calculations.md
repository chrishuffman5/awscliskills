# Sessions & Calculations

### 7.1 `start-session`

Starts an interactive session (for notebooks and calculations).

**Synopsis:**
```bash
aws athena start-session \
    --work-group <value> \
    --engine-configuration <value> \
    [--description <value>] \
    [--notebook-version <value>] \
    [--session-idle-timeout-in-minutes <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--work-group` | **Yes** | string | -- | Workgroup |
| `--engine-configuration` | **Yes** | structure | -- | Engine config. Shorthand: `CoordinatorDpuSize=integer,MaxConcurrentDpus=integer,DefaultExecutorDpuSize=integer,AdditionalConfigs={key=value}` |
| `--description` | No | string | -- | Description |
| `--notebook-version` | No | string | -- | Notebook version |
| `--session-idle-timeout-in-minutes` | No | integer | -- | Idle timeout in minutes |
| `--client-request-token` | No | string | -- | Idempotency token |

**Output Schema:**
```json
{
    "SessionId": "string",
    "State": "CREATING|CREATED|IDLE|BUSY|TERMINATING|TERMINATED|DEGRADED|FAILED"
}
```

---

### 7.2 `terminate-session`

Terminates an active session.

**Synopsis:**
```bash
aws athena terminate-session \
    --session-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--session-id` | **Yes** | string | -- | Session ID to terminate |

**Output Schema:**
```json
{
    "State": "TERMINATING"
}
```

---

### 7.3 `get-session`

Returns session details.

**Synopsis:**
```bash
aws athena get-session \
    --session-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--session-id` | **Yes** | string | -- | Session ID |

**Output Schema:**
```json
{
    "SessionId": "string",
    "Description": "string",
    "WorkGroup": "string",
    "EngineVersion": "string",
    "EngineConfiguration": {
        "CoordinatorDpuSize": "integer",
        "MaxConcurrentDpus": "integer",
        "DefaultExecutorDpuSize": "integer",
        "AdditionalConfigs": {}
    },
    "NotebookVersion": "string",
    "SessionConfiguration": {
        "ExecutionRole": "string",
        "WorkingDirectory": "string",
        "IdleTimeoutSeconds": "long",
        "EncryptionConfiguration": {}
    },
    "Status": {
        "StartDateTime": "timestamp",
        "LastModifiedDateTime": "timestamp",
        "EndDateTime": "timestamp",
        "IdleSinceDateTime": "timestamp",
        "State": "CREATING|CREATED|IDLE|BUSY|TERMINATING|TERMINATED|DEGRADED|FAILED",
        "StateChangeReason": "string"
    },
    "Statistics": {
        "DpuExecutionInMillis": "long"
    }
}
```

---

### 7.4 `get-session-status`

Returns the session status.

**Synopsis:**
```bash
aws athena get-session-status \
    --session-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--session-id` | **Yes** | string | -- | Session ID |

**Output Schema:**
```json
{
    "SessionId": "string",
    "Status": {
        "StartDateTime": "timestamp",
        "LastModifiedDateTime": "timestamp",
        "EndDateTime": "timestamp",
        "IdleSinceDateTime": "timestamp",
        "State": "string",
        "StateChangeReason": "string"
    }
}
```

---

### 7.5 `list-sessions`

Lists sessions in a workgroup. **Paginated operation.**

**Synopsis:**
```bash
aws athena list-sessions \
    --work-group <value> \
    [--state-filter <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--work-group` | **Yes** | string | -- | Workgroup |
| `--state-filter` | No | string | -- | Filter: `CREATING`, `CREATED`, `IDLE`, `BUSY`, `TERMINATING`, `TERMINATED`, `DEGRADED`, `FAILED` |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "Sessions": [
        {
            "SessionId": "string",
            "Description": "string",
            "EngineVersion": "string",
            "NotebookVersion": "string",
            "Status": {}
        }
    ],
    "NextToken": "string"
}
```

---

### 7.6 `start-calculation-execution`

Starts a calculation (code execution) in a session.

**Synopsis:**
```bash
aws athena start-calculation-execution \
    --session-id <value> \
    [--description <value>] \
    [--code-block <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--session-id` | **Yes** | string | -- | Session ID |
| `--description` | No | string | -- | Description |
| `--code-block` | No | string | -- | Code to execute (Python/SQL) |
| `--client-request-token` | No | string | -- | Idempotency token |

**Output Schema:**
```json
{
    "CalculationExecutionId": "string",
    "State": "CREATING|CREATED|QUEUED|RUNNING|CANCELING|CANCELED|COMPLETED|FAILED"
}
```

---

### 7.7 `stop-calculation-execution`

Stops a running calculation.

**Synopsis:**
```bash
aws athena stop-calculation-execution \
    --calculation-execution-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--calculation-execution-id` | **Yes** | string | -- | Calculation ID to stop |

**Output Schema:**
```json
{
    "State": "CANCELING"
}
```

---

### 7.8 `get-calculation-execution`

Returns details about a calculation execution.

**Synopsis:**
```bash
aws athena get-calculation-execution \
    --calculation-execution-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--calculation-execution-id` | **Yes** | string | -- | Calculation execution ID |

**Output Schema:**
```json
{
    "CalculationExecutionId": "string",
    "SessionId": "string",
    "Description": "string",
    "WorkingDirectory": "string",
    "Status": {
        "SubmissionDateTime": "timestamp",
        "CompletionDateTime": "timestamp",
        "State": "CREATING|CREATED|QUEUED|RUNNING|CANCELING|CANCELED|COMPLETED|FAILED",
        "StateChangeReason": "string"
    },
    "Statistics": {
        "DpuExecutionInMillis": "long",
        "Progress": "string"
    },
    "Result": {
        "StdOutS3Uri": "string",
        "StdErrorS3Uri": "string",
        "ResultS3Uri": "string",
        "ResultType": "string"
    }
}
```

---

### 7.9 `get-calculation-execution-status`

Returns the status of a calculation execution.

**Synopsis:**
```bash
aws athena get-calculation-execution-status \
    --calculation-execution-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--calculation-execution-id` | **Yes** | string | -- | Calculation execution ID |

**Output Schema:**
```json
{
    "Status": {
        "SubmissionDateTime": "timestamp",
        "CompletionDateTime": "timestamp",
        "State": "string",
        "StateChangeReason": "string"
    },
    "Statistics": {
        "DpuExecutionInMillis": "long",
        "Progress": "string"
    }
}
```

---

### 7.10 `list-calculation-executions`

Lists calculations in a session. **Paginated operation.**

**Synopsis:**
```bash
aws athena list-calculation-executions \
    --session-id <value> \
    [--state-filter <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--session-id` | **Yes** | string | -- | Session ID |
| `--state-filter` | No | string | -- | Filter by state |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "Calculations": [
        {
            "CalculationExecutionId": "string",
            "Description": "string",
            "Status": {}
        }
    ],
    "NextToken": "string"
}
```
