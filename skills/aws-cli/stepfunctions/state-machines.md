# State Machines

### 1.1 `create-state-machine`

Creates a state machine. A state machine consists of a collection of states that perform work (Task), determine flow (Choice, Parallel, Map), or pass data (Pass, Wait, Succeed, Fail).

**Synopsis:**
```bash
aws stepfunctions create-state-machine \
    --name <value> \
    --definition <value> \
    --role-arn <value> \
    [--type <value>] \
    [--logging-configuration <value>] \
    [--tags <value>] \
    [--tracing-configuration <value>] \
    [--publish | --no-publish] \
    [--version-description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the state machine (1-80 chars, letters, numbers, hyphens, underscores) |
| `--definition` | **Yes** | string | -- | ASL definition (JSON string or `file://` path) |
| `--role-arn` | **Yes** | string | -- | IAM role ARN for the state machine to assume |
| `--type` | No | string | `STANDARD` | Type: `STANDARD` or `EXPRESS` |
| `--logging-configuration` | No | structure | None | CloudWatch Logs configuration |
| `--tags` | No | list | None | Tags. Shorthand: `key=string,value=string` |
| `--tracing-configuration` | No | structure | None | X-Ray tracing. Shorthand: `enabled=true\|false` |
| `--publish` | No | boolean | false | Publish version 1 on creation |
| `--version-description` | No | string | None | Description for the published version |

**Logging Configuration Structure:**
```json
{
    "level": "ALL|ERROR|FATAL|OFF",
    "includeExecutionData": true|false,
    "destinations": [
        {
            "cloudWatchLogsLogGroup": {
                "logGroupArn": "string"
            }
        }
    ]
}
```

**Output Schema:**
```json
{
    "stateMachineArn": "string",
    "creationDate": "timestamp",
    "stateMachineVersionArn": "string"
}
```

---

### 1.2 `delete-state-machine`

Deletes a state machine. All running executions continue until they complete or are stopped. Deleted state machines are removed after 30 days.

**Synopsis:**
```bash
aws stepfunctions delete-state-machine \
    --state-machine-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--state-machine-arn` | **Yes** | string | -- | ARN of the state machine to delete |

**Output:** None

---

### 1.3 `describe-state-machine`

Gets information about a state machine, including its definition, role, type, and configuration.

**Synopsis:**
```bash
aws stepfunctions describe-state-machine \
    --state-machine-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--state-machine-arn` | **Yes** | string | -- | ARN of the state machine |

**Output Schema:**
```json
{
    "stateMachineArn": "string",
    "name": "string",
    "status": "ACTIVE|DELETING",
    "definition": "string",
    "roleArn": "string",
    "type": "STANDARD|EXPRESS",
    "creationDate": "timestamp",
    "loggingConfiguration": {
        "level": "ALL|ERROR|FATAL|OFF",
        "includeExecutionData": "boolean",
        "destinations": [
            {
                "cloudWatchLogsLogGroup": {
                    "logGroupArn": "string"
                }
            }
        ]
    },
    "tracingConfiguration": {
        "enabled": "boolean"
    },
    "label": "string",
    "revisionId": "string",
    "description": "string"
}
```

---

### 1.4 `list-state-machines`

Lists state machines. **Paginated operation.**

**Synopsis:**
```bash
aws stepfunctions list-state-machines \
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
    "stateMachines": [
        {
            "stateMachineArn": "string",
            "name": "string",
            "type": "STANDARD|EXPRESS",
            "creationDate": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 1.5 `update-state-machine`

Updates a state machine. Can change the definition, role, logging configuration, or tracing configuration.

**Synopsis:**
```bash
aws stepfunctions update-state-machine \
    --state-machine-arn <value> \
    [--definition <value>] \
    [--role-arn <value>] \
    [--logging-configuration <value>] \
    [--tracing-configuration <value>] \
    [--publish | --no-publish] \
    [--version-description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--state-machine-arn` | **Yes** | string | -- | ARN of the state machine |
| `--definition` | No | string | None | New ASL definition |
| `--role-arn` | No | string | None | New IAM role ARN |
| `--logging-configuration` | No | structure | None | New logging configuration |
| `--tracing-configuration` | No | structure | None | New tracing configuration |
| `--publish` | No | boolean | false | Publish a new version after updating |
| `--version-description` | No | string | None | Description for the new version |

**Output Schema:**
```json
{
    "updateDate": "timestamp",
    "revisionId": "string",
    "stateMachineVersionArn": "string"
}
```

---

### 1.6 `describe-state-machine-for-execution`

Returns the state machine definition and configuration that was used to start a specific execution. This is useful to see the exact definition that a running execution is using.

**Synopsis:**
```bash
aws stepfunctions describe-state-machine-for-execution \
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
    "stateMachineArn": "string",
    "name": "string",
    "definition": "string",
    "roleArn": "string",
    "updateDate": "timestamp",
    "loggingConfiguration": {},
    "tracingConfiguration": {},
    "mapRunArn": "string",
    "label": "string",
    "revisionId": "string"
}
```

---

### 1.7 `publish-state-machine-version`

Publishes a version of the current state machine revision. Versions are immutable snapshots.

**Synopsis:**
```bash
aws stepfunctions publish-state-machine-version \
    --state-machine-arn <value> \
    [--revision-id <value>] \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--state-machine-arn` | **Yes** | string | -- | ARN of the state machine |
| `--revision-id` | No | string | None | Expected revision ID for optimistic concurrency |
| `--description` | No | string | None | Description for this version |

**Output Schema:**
```json
{
    "creationDate": "timestamp",
    "stateMachineVersionArn": "string"
}
```

---

### 1.8 `list-state-machine-versions`

Lists published versions of a state machine. **Paginated operation.**

**Synopsis:**
```bash
aws stepfunctions list-state-machine-versions \
    --state-machine-arn <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--state-machine-arn` | **Yes** | string | -- | ARN of the state machine |
| `--max-results` | No | integer | None | Maximum items (1-1000) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "stateMachineVersions": [
        {
            "stateMachineVersionArn": "string",
            "creationDate": "timestamp"
        }
    ],
    "nextToken": "string"
}
```
