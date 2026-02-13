# Serverless Scheduling (`aws redshift-serverless`)

### 17.1 `create-scheduled-action`

Creates a serverless scheduled action.

**Synopsis:**
```bash
aws redshift-serverless create-scheduled-action \
    --scheduled-action-name <value> \
    --namespace-name <value> \
    --role-arn <value> \
    --schedule <value> \
    --target-action <value> \
    [--scheduled-action-description <value>] \
    [--start-time <value>] \
    [--end-time <value>] \
    [--enabled | --no-enabled] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--scheduled-action-name` | **Yes** | string | -- | Scheduled action name |
| `--namespace-name` | **Yes** | string | -- | Namespace for the action |
| `--role-arn` | **Yes** | string | -- | IAM role ARN for execution |
| `--schedule` | **Yes** | structure | -- | Schedule. Shorthand: `at=timestamp` or `cron=string` |
| `--target-action` | **Yes** | structure | -- | Target action (see structure below) |
| `--scheduled-action-description` | No | string | -- | Description |
| `--start-time` | No | timestamp | -- | Start time |
| `--end-time` | No | timestamp | -- | End time |
| `--enabled` | No | boolean | true | Whether the action is enabled |

**Target Action Structure (create snapshot):**
```json
{
    "createSnapshot": {
        "namespaceName": "string",
        "snapshotNamePrefix": "string",
        "retentionPeriod": "integer",
        "tags": [{"key": "string", "value": "string"}]
    }
}
```

**Schedule Structure:**
```
at=2026-03-01T00:00:00Z
cron(0 8 * * ? *)
```

**Output Schema:**
```json
{
    "scheduledAction": {
        "scheduledActionName": "string",
        "scheduledActionDescription": "string",
        "namespaceName": "string",
        "roleArn": "string",
        "state": "ACTIVE|DISABLED",
        "schedule": {
            "at": "timestamp",
            "cron": "string"
        },
        "targetAction": {
            "createSnapshot": {
                "namespaceName": "string",
                "snapshotNamePrefix": "string",
                "retentionPeriod": "integer",
                "tags": []
            }
        },
        "startTime": "timestamp",
        "endTime": "timestamp",
        "nextInvocations": ["timestamp"],
        "scheduledActionUuid": "string"
    }
}
```

---

### 17.2 `delete-scheduled-action`

Deletes a serverless scheduled action.

**Synopsis:**
```bash
aws redshift-serverless delete-scheduled-action \
    --scheduled-action-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--scheduled-action-name` | **Yes** | string | -- | Scheduled action to delete |

**Output Schema:**
```json
{
    "scheduledAction": {
        "scheduledActionName": "string",
        "namespaceName": "string"
    }
}
```

---

### 17.3 `get-scheduled-action`

Returns information about a serverless scheduled action.

**Synopsis:**
```bash
aws redshift-serverless get-scheduled-action \
    --scheduled-action-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--scheduled-action-name` | **Yes** | string | -- | Scheduled action to describe |

**Output Schema:**
```json
{
    "scheduledAction": {
        "scheduledActionName": "string",
        "scheduledActionDescription": "string",
        "namespaceName": "string",
        "roleArn": "string",
        "state": "ACTIVE|DISABLED",
        "schedule": {},
        "targetAction": {},
        "startTime": "timestamp",
        "endTime": "timestamp",
        "nextInvocations": ["timestamp"],
        "scheduledActionUuid": "string"
    }
}
```

---

### 17.4 `list-scheduled-actions`

Lists serverless scheduled actions. **Paginated operation.**

**Synopsis:**
```bash
aws redshift-serverless list-scheduled-actions \
    [--namespace-name <value>] \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--namespace-name` | No | string | -- | Filter by namespace |
| `--next-token` | No | string | -- | Pagination token |
| `--max-results` | No | integer | -- | Maximum results |

**Output Schema:**
```json
{
    "scheduledActions": [
        {
            "scheduledActionName": "string",
            "namespaceName": "string",
            "scheduledActionDescription": "string",
            "state": "ACTIVE|DISABLED"
        }
    ],
    "nextToken": "string"
}
```

---

### 17.5 `update-scheduled-action`

Updates a serverless scheduled action.

**Synopsis:**
```bash
aws redshift-serverless update-scheduled-action \
    --scheduled-action-name <value> \
    [--role-arn <value>] \
    [--schedule <value>] \
    [--target-action <value>] \
    [--scheduled-action-description <value>] \
    [--start-time <value>] \
    [--end-time <value>] \
    [--enabled | --no-enabled] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--scheduled-action-name` | **Yes** | string | -- | Scheduled action to update |
| `--role-arn` | No | string | -- | New IAM role ARN |
| `--schedule` | No | structure | -- | New schedule |
| `--target-action` | No | structure | -- | New target action |
| `--scheduled-action-description` | No | string | -- | New description |
| `--start-time` | No | timestamp | -- | New start time |
| `--end-time` | No | timestamp | -- | New end time |
| `--enabled` | No | boolean | -- | Enable or disable |

**Output Schema:**
```json
{
    "scheduledAction": {
        "scheduledActionName": "string",
        "scheduledActionDescription": "string",
        "namespaceName": "string",
        "roleArn": "string",
        "state": "ACTIVE|DISABLED",
        "schedule": {},
        "targetAction": {},
        "startTime": "timestamp",
        "endTime": "timestamp",
        "nextInvocations": ["timestamp"]
    }
}
```
