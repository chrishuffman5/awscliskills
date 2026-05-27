# Task Protection

### 13.1 `get-task-protection`

Retrieves the protection status of tasks in an ECS service.

**Synopsis:**
```bash
aws ecs get-task-protection \
    --cluster <value> \
    [--tasks <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster` | **Yes** | string | -- | Cluster short name or ARN |
| `--tasks` | No | list(string) | None | Up to 100 task IDs or ARNs |

**Output Schema:**
```json
{
    "protectedTasks": [
        {
            "taskArn": "string",
            "protectionEnabled": true|false,
            "expirationDate": "timestamp"
        }
    ],
    "failures": [
        {
            "arn": "string",
            "reason": "string",
            "detail": "string"
        }
    ]
}
```

---

### 13.2 `update-task-protection`

Updates the protection status of a task. Protected tasks are not terminated during scale-in events.

**Synopsis:**
```bash
aws ecs update-task-protection \
    --cluster <value> \
    --tasks <value> \
    --protection-enabled \
    [--expires-in-minutes <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster` | **Yes** | string | -- | Cluster short name or ARN |
| `--tasks` | **Yes** | list(string) | -- | Up to 10 task IDs or ARNs |
| `--protection-enabled` / `--no-protection-enabled` | **Yes** | boolean | -- | Enable or disable scale-in protection |
| `--expires-in-minutes` | No | integer | 1440 (24h) | Protection duration in minutes (max 2880 = 48h) |

**Output Schema:**
```json
{
    "protectedTasks": [
        {
            "taskArn": "string",
            "protectionEnabled": true|false,
            "expirationDate": "timestamp"
        }
    ],
    "failures": [
        {
            "arn": "string",
            "reason": "string",
            "detail": "string"
        }
    ]
}
```
