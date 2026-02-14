# Commands

## 7.1 `create-command`

Creates a command for remote device execution.

**Synopsis:**
```bash
aws iot create-command \
    --command-id <value> \
    [--namespace <value>] \
    [--display-name <value>] \
    [--description <value>] \
    [--payload <value>] \
    [--payload-template <value>] \
    [--preprocessor <value>] \
    [--mandatory-parameters <value>] \
    [--role-arn <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--command-id` | **Yes** | string | -- | Unique command ID (1-64 chars) |
| `--namespace` | No | string | None | `AWS-IoT` or `AWS-IoT-FleetWise` |
| `--display-name` | No | string | None | Display name (max 64 chars) |
| `--description` | No | string | None | Description (max 2028 chars) |
| `--payload` | No | structure | None | Static payload (content blob, contentType string) |
| `--payload-template` | No | string | None | Dynamic payload template (max 32768 chars) |
| `--preprocessor` | No | structure | None | JSON substitution config |
| `--mandatory-parameters` | No | list | None | Required parameters for execution |
| `--role-arn` | No | string | None | IAM role (for FleetWise namespace) |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "commandId": "string",
    "commandArn": "string"
}
```

---

## 7.2 `get-command`

Gets a command.

**Synopsis:**
```bash
aws iot get-command \
    --command-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--command-id` | **Yes** | string | -- | Command ID |

**Output Schema:**
```json
{
    "commandId": "string",
    "commandArn": "string",
    "namespace": "AWS-IoT|AWS-IoT-FleetWise",
    "displayName": "string",
    "description": "string",
    "mandatoryParameters": [],
    "payload": {"content": "blob", "contentType": "string"},
    "roleArn": "string",
    "createdAt": "timestamp",
    "lastUpdatedAt": "timestamp",
    "deprecated": "boolean",
    "pendingDeletion": "boolean"
}
```

---

## 7.3 `list-commands`

Lists commands. **Paginated operation.**

**Synopsis:**
```bash
aws iot list-commands \
    [--max-results <value>] \
    [--next-token <value>] \
    [--namespace <value>] \
    [--command-parameter-name <value>] \
    [--sort-order <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--max-results` | No | integer | None | Max results |
| `--next-token` | No | string | None | Pagination token |
| `--namespace` | No | string | None | Filter by namespace |
| `--command-parameter-name` | No | string | None | Filter by parameter name |
| `--sort-order` | No | string | None | `ASCENDING` or `DESCENDING` |

**Output Schema:**
```json
{
    "commands": [
        {
            "commandArn": "string",
            "commandId": "string",
            "displayName": "string",
            "deprecated": "boolean",
            "createdAt": "timestamp",
            "lastUpdatedAt": "timestamp",
            "pendingDeletion": "boolean"
        }
    ],
    "nextToken": "string"
}
```

---

## 7.4 `update-command`

Updates a command (deprecate or update description).

**Synopsis:**
```bash
aws iot update-command \
    --command-id <value> \
    [--display-name <value>] \
    [--description <value>] \
    [--deprecated | --no-deprecated] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--command-id` | **Yes** | string | -- | Command ID |
| `--display-name` | No | string | None | Updated display name |
| `--description` | No | string | None | Updated description |
| `--deprecated` | No | boolean | None | Deprecate/undeprecate command |

**Output Schema:**
```json
{
    "commandId": "string",
    "displayName": "string",
    "description": "string",
    "deprecated": "boolean",
    "lastUpdatedAt": "timestamp"
}
```

---

## 7.5 `delete-command`

Deletes a command. Must be deprecated first.

**Synopsis:**
```bash
aws iot delete-command \
    --command-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--command-id` | **Yes** | string | -- | Command ID |

**Output Schema:**
```json
{
    "statusCode": "integer"
}
```

---

## 7.6 `get-command-execution`

Gets a command execution.

**Synopsis:**
```bash
aws iot get-command-execution \
    --execution-id <value> \
    --target-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--execution-id` | **Yes** | string | -- | Execution ID (1-64 chars) |
| `--target-arn` | **Yes** | string | -- | Target thing ARN |

**Output Schema:**
```json
{
    "executionId": "string",
    "commandArn": "string",
    "targetArn": "string",
    "status": "CREATED|IN_PROGRESS|SUCCEEDED|FAILED|REJECTED|TIMED_OUT",
    "statusReason": {"reasonCode": "string", "reasonDescription": "string"},
    "result": {},
    "parameters": {},
    "executionTimeoutSeconds": "long",
    "createdAt": "timestamp",
    "lastUpdatedAt": "timestamp",
    "startedAt": "timestamp",
    "completedAt": "timestamp",
    "timeToLive": "timestamp"
}
```

---

## 7.7 `list-command-executions`

Lists command executions. **Paginated operation.**

**Synopsis:**
```bash
aws iot list-command-executions \
    [--max-results <value>] \
    [--next-token <value>] \
    [--namespace <value>] \
    [--status <value>] \
    [--sort-order <value>] \
    [--started-time-filter <value>] \
    [--completed-time-filter <value>] \
    [--target-arn <value>] \
    [--command-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--max-results` | No | integer | None | Max results |
| `--next-token` | No | string | None | Pagination token |
| `--namespace` | No | string | None | Filter by namespace |
| `--status` | No | string | None | Filter by status |
| `--sort-order` | No | string | None | `ASCENDING` or `DESCENDING` |
| `--started-time-filter` | No | structure | None | Filter by start time (after, before) |
| `--completed-time-filter` | No | structure | None | Filter by completion time |
| `--target-arn` | No | string | None | Filter by target ARN |
| `--command-arn` | No | string | None | Filter by command ARN |

**Output Schema:**
```json
{
    "commandExecutions": [
        {
            "commandArn": "string",
            "executionId": "string",
            "targetArn": "string",
            "status": "string",
            "createdAt": "timestamp",
            "startedAt": "timestamp",
            "completedAt": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

## 7.8 `delete-command-execution`

Deletes a command execution record.

**Synopsis:**
```bash
aws iot delete-command-execution \
    --execution-id <value> \
    --target-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--execution-id` | **Yes** | string | -- | Execution ID |
| `--target-arn` | **Yes** | string | -- | Target thing ARN |

**Output:** None

---

## 7.9 `start-command-execution` (iot-jobs-data)

Starts a command execution on a device. This is from the `aws iot-jobs-data` service.

**Synopsis:**
```bash
aws iot-jobs-data start-command-execution \
    --target-arn <value> \
    --command-arn <value> \
    [--parameters <value>] \
    [--execution-timeout-seconds <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--target-arn` | **Yes** | string | -- | Target thing ARN (max 2048 chars) |
| `--command-arn` | **Yes** | string | -- | Command ARN |
| `--parameters` | No | map | None | Command parameters (key-value with typed values: S, B, I, L, D, BIN, UL) |
| `--execution-timeout-seconds` | No | long | None | Timeout in seconds (min 1) |
| `--client-token` | No | string | None | Idempotency token (1-64 chars) |

**Output Schema:**
```json
{
    "executionId": "string"
}
```
