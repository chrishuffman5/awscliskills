# Logging

### 5.1 `create-logging-configuration`

Creates a logging configuration for the workspace. Logs are sent to the specified CloudWatch Logs log group.

**Synopsis:**
```bash
aws amp create-logging-configuration \
    --workspace-id <value> \
    --log-group-arn <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | ID of the workspace |
| `--log-group-arn` | **Yes** | string | -- | ARN of the CloudWatch Logs log group |
| `--client-token` | No | string | auto-generated | Idempotency token |

**Output Schema:**
```json
{
    "status": {
        "statusCode": "CREATING|ACTIVE|UPDATING|DELETING|CREATION_FAILED|UPDATE_FAILED",
        "statusReason": "string"
    }
}
```

---

### 5.2 `delete-logging-configuration`

Deletes the logging configuration for a workspace.

**Synopsis:**
```bash
aws amp delete-logging-configuration \
    --workspace-id <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | ID of the workspace |
| `--client-token` | No | string | auto-generated | Idempotency token |

**Output Schema:**
```json
{}
```

---

### 5.3 `describe-logging-configuration`

Describes the logging configuration for a workspace.

**Synopsis:**
```bash
aws amp describe-logging-configuration \
    --workspace-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | ID of the workspace |

**Output Schema:**
```json
{
    "loggingConfiguration": {
        "createdAt": "timestamp",
        "logGroupArn": "string",
        "modifiedAt": "timestamp",
        "status": {
            "statusCode": "CREATING|ACTIVE|UPDATING|DELETING|CREATION_FAILED|UPDATE_FAILED",
            "statusReason": "string"
        },
        "workspace": "string"
    }
}
```

---

### 5.4 `update-logging-configuration`

Updates the logging configuration for a workspace.

**Synopsis:**
```bash
aws amp update-logging-configuration \
    --workspace-id <value> \
    --log-group-arn <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | ID of the workspace |
| `--log-group-arn` | **Yes** | string | -- | New ARN of the CloudWatch Logs log group |
| `--client-token` | No | string | auto-generated | Idempotency token |

**Output Schema:**
```json
{
    "status": {
        "statusCode": "CREATING|ACTIVE|UPDATING|DELETING|CREATION_FAILED|UPDATE_FAILED",
        "statusReason": "string"
    }
}
```
