# Scheduled Actions

### 3.1 `put-scheduled-action`

Creates or updates a scheduled scaling action using at, rate, or cron expressions.

**Synopsis:**
```bash
aws application-autoscaling put-scheduled-action \
    --service-namespace <value> \
    --scheduled-action-name <value> \
    --resource-id <value> \
    --scalable-dimension <value> \
    [--schedule <value>] \
    [--timezone <value>] \
    [--start-time <value>] \
    [--end-time <value>] \
    [--scalable-target-action <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-namespace` | **Yes** | string | -- | Service namespace |
| `--scheduled-action-name` | **Yes** | string | -- | Action name (1-256 chars, unique per target) |
| `--resource-id` | **Yes** | string | -- | Resource identifier |
| `--scalable-dimension` | **Yes** | string | -- | Scalable dimension |
| `--schedule` | No | string | None | Schedule expression: `at(yyyy-mm-ddThh:mm:ss)`, `rate(value unit)`, or `cron(fields)` |
| `--timezone` | No | string | UTC | IANA time zone (e.g., `America/New_York`) |
| `--start-time` | No | timestamp | None | When the action starts (UTC) |
| `--end-time` | No | timestamp | None | When recurring schedule ends (UTC) |
| `--scalable-target-action` | No | structure | None | New min/max capacity |

**ScalableTargetAction structure:**
```json
{
    "MinCapacity": 5,
    "MaxCapacity": 20
}
```

**Schedule expression examples:**
- One-time: `at(2026-03-01T08:00:00)`
- Recurring rate: `rate(5 minutes)`
- Cron: `cron(0 8 * * ? *)` (daily at 8 AM)

**Output:** None

---

### 3.2 `delete-scheduled-action`

Deletes a scheduled scaling action.

**Synopsis:**
```bash
aws application-autoscaling delete-scheduled-action \
    --service-namespace <value> \
    --scheduled-action-name <value> \
    --resource-id <value> \
    --scalable-dimension <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-namespace` | **Yes** | string | -- | Service namespace |
| `--scheduled-action-name` | **Yes** | string | -- | Action name to delete |
| `--resource-id` | **Yes** | string | -- | Resource identifier |
| `--scalable-dimension` | **Yes** | string | -- | Scalable dimension |

**Output:** None

---

### 3.3 `describe-scheduled-actions`

Describes scheduled actions. **Paginated operation.**

**Synopsis:**
```bash
aws application-autoscaling describe-scheduled-actions \
    --service-namespace <value> \
    [--scheduled-action-names <value>] \
    [--resource-id <value>] \
    [--scalable-dimension <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-namespace` | **Yes** | string | -- | Service namespace |
| `--scheduled-action-names` | No | list | None | Action names to filter (max 50) |
| `--resource-id` | No | string | None | Filter by resource ID |
| `--scalable-dimension` | No | string | None | Filter by scalable dimension |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Size of each page |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "ScheduledActions": [
        {
            "ScheduledActionName": "string",
            "ScheduledActionARN": "string",
            "ServiceNamespace": "string",
            "Schedule": "string",
            "Timezone": "string",
            "ResourceId": "string",
            "ScalableDimension": "string",
            "StartTime": "timestamp",
            "EndTime": "timestamp",
            "ScalableTargetAction": {
                "MinCapacity": "integer",
                "MaxCapacity": "integer"
            },
            "CreationTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```
