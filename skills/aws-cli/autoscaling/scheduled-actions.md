# Scheduled Actions

### 5.1 `put-scheduled-update-group-action`

Creates or updates a scheduled scaling action for an Auto Scaling group.

**Synopsis:**
```bash
aws autoscaling put-scheduled-update-group-action \
    --auto-scaling-group-name <value> \
    --scheduled-action-name <value> \
    [--time <value>] \
    [--start-time <value>] \
    [--end-time <value>] \
    [--recurrence <value>] \
    [--min-size <value>] \
    [--max-size <value>] \
    [--desired-capacity <value>] \
    [--time-zone <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-scaling-group-name` | **Yes** | string | -- | Group name |
| `--scheduled-action-name` | **Yes** | string | -- | Scheduled action name |
| `--time` | No | timestamp | None | Deprecated: use `--start-time` |
| `--start-time` | No | timestamp | None | Start time (UTC). Format: `YYYY-MM-DDThh:mm:ssZ` |
| `--end-time` | No | timestamp | None | End time for recurring actions |
| `--recurrence` | No | string | None | Cron expression: `"minute hour day-of-month month day-of-week"` |
| `--min-size` | No | integer | None | New minimum size |
| `--max-size` | No | integer | None | New maximum size |
| `--desired-capacity` | No | integer | None | New desired capacity |
| `--time-zone` | No | string | None | IANA time zone (e.g., `America/New_York`) |

**Output:** No output on success.

---

### 5.2 `delete-scheduled-action`

Deletes the specified scheduled action.

**Synopsis:**
```bash
aws autoscaling delete-scheduled-action \
    --auto-scaling-group-name <value> \
    --scheduled-action-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-scaling-group-name` | **Yes** | string | -- | Group name |
| `--scheduled-action-name` | **Yes** | string | -- | Scheduled action name |

**Output:** No output on success.

---

### 5.3 `describe-scheduled-actions`

Describes the scheduled actions for the specified Auto Scaling group. **Paginated operation.**

**Synopsis:**
```bash
aws autoscaling describe-scheduled-actions \
    [--auto-scaling-group-name <value>] \
    [--scheduled-action-names <value>] \
    [--start-time <value>] \
    [--end-time <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-scaling-group-name` | No | string | None | Group name |
| `--scheduled-action-names` | No | list(string) | None | Scheduled action names |
| `--start-time` | No | timestamp | None | Filter: actions starting at or after this time |
| `--end-time` | No | timestamp | None | Filter: actions ending at or before this time |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "ScheduledUpdateGroupActions": [
        {
            "AutoScalingGroupName": "string",
            "ScheduledActionName": "string",
            "ScheduledActionARN": "string",
            "Time": "timestamp",
            "StartTime": "timestamp",
            "EndTime": "timestamp",
            "Recurrence": "string",
            "MinSize": "integer",
            "MaxSize": "integer",
            "DesiredCapacity": "integer",
            "TimeZone": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 5.4 `batch-put-scheduled-update-group-action`

Creates or updates one or more scheduled actions in a single call.

**Synopsis:**
```bash
aws autoscaling batch-put-scheduled-update-group-action \
    --auto-scaling-group-name <value> \
    --scheduled-update-group-actions <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-scaling-group-name` | **Yes** | string | -- | Group name |
| `--scheduled-update-group-actions` | **Yes** | list | -- | List of scheduled actions |

**Output Schema:**
```json
{
    "FailedScheduledUpdateGroupActions": [
        {
            "ScheduledActionName": "string",
            "ErrorCode": "string",
            "ErrorMessage": "string"
        }
    ]
}
```

---

### 5.5 `batch-delete-scheduled-action`

Deletes one or more scheduled actions in a single call.

**Synopsis:**
```bash
aws autoscaling batch-delete-scheduled-action \
    --auto-scaling-group-name <value> \
    --scheduled-action-names <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-scaling-group-name` | **Yes** | string | -- | Group name |
| `--scheduled-action-names` | **Yes** | list(string) | -- | Scheduled action names to delete |

**Output Schema:**
```json
{
    "FailedScheduledActions": [
        {
            "ScheduledActionName": "string",
            "ErrorCode": "string",
            "ErrorMessage": "string"
        }
    ]
}
```
