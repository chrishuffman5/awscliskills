# Sessions

### 15.1 `create-session`

Creates an interactive session.

**Synopsis:**
```bash
aws glue create-session \
    --id <value> \
    --role <value> \
    --command <value> \
    [--description <value>] \
    [--timeout <value>] \
    [--idle-timeout <value>] \
    [--default-arguments <value>] \
    [--connections <value>] \
    [--max-capacity <value>] \
    [--number-of-workers <value>] \
    [--worker-type <value>] \
    [--security-configuration <value>] \
    [--glue-version <value>] \
    [--tags <value>] \
    [--request-origin <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Session ID |
| `--role` | **Yes** | string | -- | IAM role ARN |
| `--command` | **Yes** | structure | -- | Session command. Shorthand: `Name=glueetl|gluestreaming|gluray,PythonVersion=string,Runtime=string` |
| `--description` | No | string | -- | Description |
| `--timeout` | No | integer | -- | Timeout in minutes |
| `--idle-timeout` | No | integer | -- | Idle timeout in minutes |
| `--default-arguments` | No | map | -- | Default arguments as JSON |
| `--connections` | No | structure | -- | Connections. Shorthand: `Connections=string,string` |
| `--max-capacity` | No | double | -- | Max DPUs |
| `--number-of-workers` | No | integer | -- | Number of workers |
| `--worker-type` | No | string | -- | `Standard`, `G.1X`, `G.2X`, `G.025X`, `G.4X`, `G.8X`, `Z.2X` |
| `--security-configuration` | No | string | -- | Security configuration name |
| `--glue-version` | No | string | -- | Glue version |
| `--tags` | No | map | -- | Tags as JSON |
| `--request-origin` | No | string | -- | Request origin |

**Output Schema:**
```json
{
    "Session": {
        "Id": "string",
        "CreatedOn": "timestamp",
        "Status": "PROVISIONING|READY|FAILED|TIMEOUT|STOPPING|STOPPED",
        "ErrorMessage": "string",
        "Description": "string",
        "Role": "string",
        "Command": {},
        "DefaultArguments": {},
        "Connections": {},
        "Progress": "double",
        "MaxCapacity": "double",
        "SecurityConfiguration": "string",
        "GlueVersion": "string",
        "NumberOfWorkers": "integer",
        "WorkerType": "string",
        "CompletedOn": "timestamp",
        "ExecutionTime": "double",
        "DPUSeconds": "double",
        "IdleTimeout": "integer"
    }
}
```

---

### 15.2 `delete-session`

Deletes a session.

**Synopsis:**
```bash
aws glue delete-session \
    --id <value> \
    [--request-origin <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Session ID |
| `--request-origin` | No | string | -- | Request origin |

**Output Schema:**
```json
{
    "Id": "string"
}
```

---

### 15.3 `get-session`

Retrieves session details.

**Synopsis:**
```bash
aws glue get-session \
    --id <value> \
    [--request-origin <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Session ID |
| `--request-origin` | No | string | -- | Request origin |

**Output Schema:**
```json
{
    "Session": "<Session structure>"
}
```

---

### 15.4 `list-sessions`

Lists sessions. **Paginated operation.**

**Synopsis:**
```bash
aws glue list-sessions \
    [--tags <value>] \
    [--request-origin <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--tags` | No | map | -- | Filter by tags |
| `--request-origin` | No | string | -- | Request origin |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "Ids": ["string"],
    "Sessions": ["<Session structure>"],
    "NextToken": "string"
}
```

---

### 15.5 `stop-session`

Stops an interactive session.

**Synopsis:**
```bash
aws glue stop-session \
    --id <value> \
    [--request-origin <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Session ID |
| `--request-origin` | No | string | -- | Request origin |

**Output Schema:**
```json
{
    "Id": "string"
}
```

---

### 15.6 `run-statement`

Runs a statement (code) in a session.

**Synopsis:**
```bash
aws glue run-statement \
    --session-id <value> \
    --code <value> \
    [--request-origin <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--session-id` | **Yes** | string | -- | Session ID |
| `--code` | **Yes** | string | -- | Code to execute |
| `--request-origin` | No | string | -- | Request origin |

**Output Schema:**
```json
{
    "Id": "integer"
}
```

---

### 15.7 `cancel-statement`

Cancels a running statement.

**Synopsis:**
```bash
aws glue cancel-statement \
    --session-id <value> \
    --id <value> \
    [--request-origin <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--session-id` | **Yes** | string | -- | Session ID |
| `--id` | **Yes** | integer | -- | Statement ID |
| `--request-origin` | No | string | -- | Request origin |

No output on success.

---

### 15.8 `get-statement`

Retrieves statement details.

**Synopsis:**
```bash
aws glue get-statement \
    --session-id <value> \
    --id <value> \
    [--request-origin <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--session-id` | **Yes** | string | -- | Session ID |
| `--id` | **Yes** | integer | -- | Statement ID |
| `--request-origin` | No | string | -- | Request origin |

**Output Schema:**
```json
{
    "Statement": {
        "Id": "integer",
        "Code": "string",
        "State": "WAITING|RUNNING|AVAILABLE|CANCELLING|CANCELLED|ERROR",
        "Output": {
            "Data": {
                "TextPlain": "string"
            },
            "ExecutionCount": "integer",
            "Status": "OK|ERROR",
            "ErrorName": "string",
            "ErrorValue": "string",
            "Traceback": ["string"]
        },
        "Progress": "double",
        "StartedOn": "long",
        "CompletedOn": "long"
    }
}
```

---

### 15.9 `list-statements`

Lists statements in a session.

**Synopsis:**
```bash
aws glue list-statements \
    --session-id <value> \
    [--request-origin <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--session-id` | **Yes** | string | -- | Session ID |
| `--request-origin` | No | string | -- | Request origin |
| `--next-token` | No | string | -- | Pagination token |

**Output Schema:**
```json
{
    "Statements": ["<Statement structure>"],
    "NextToken": "string"
}
```
