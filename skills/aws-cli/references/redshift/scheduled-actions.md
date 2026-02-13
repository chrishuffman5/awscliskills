# Scheduled Actions

### 6.1 `create-scheduled-action`

Creates a scheduled action for a cluster (e.g., resize, pause, resume).

**Synopsis:**
```bash
aws redshift create-scheduled-action \
    --scheduled-action-name <value> \
    --target-action <value> \
    --schedule <value> \
    --iam-role <value> \
    [--scheduled-action-description <value>] \
    [--start-time <value>] \
    [--end-time <value>] \
    [--enable | --no-enable] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--scheduled-action-name` | **Yes** | string | -- | Name for the scheduled action |
| `--target-action` | **Yes** | structure | -- | Action to execute (see structure below) |
| `--schedule` | **Yes** | string | -- | Cron or `at()` expression (e.g., `cron(0 8 * * ? *)`) |
| `--iam-role` | **Yes** | string | -- | IAM role ARN for executing the action |
| `--scheduled-action-description` | No | string | -- | Description |
| `--start-time` | No | timestamp | -- | Start time for the schedule |
| `--end-time` | No | timestamp | -- | End time for the schedule |
| `--enable` | No | boolean | true | Whether the action is enabled |

**Target Action Structure:**
```json
{
    "ResizeCluster": {
        "ClusterIdentifier": "string",
        "ClusterType": "string",
        "NodeType": "string",
        "NumberOfNodes": "integer",
        "Classic": true|false
    },
    "PauseCluster": {
        "ClusterIdentifier": "string"
    },
    "ResumeCluster": {
        "ClusterIdentifier": "string"
    }
}
```

**Output Schema:**
```json
{
    "ScheduledActionName": "string",
    "TargetAction": {
        "ResizeCluster": {},
        "PauseCluster": {},
        "ResumeCluster": {}
    },
    "Schedule": "string",
    "IamRole": "string",
    "ScheduledActionDescription": "string",
    "State": "ACTIVE|DISABLED",
    "NextInvocations": ["timestamp"],
    "StartTime": "timestamp",
    "EndTime": "timestamp"
}
```

---

### 6.2 `delete-scheduled-action`

Deletes a scheduled action.

**Synopsis:**
```bash
aws redshift delete-scheduled-action \
    --scheduled-action-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--scheduled-action-name` | **Yes** | string | -- | Scheduled action to delete |

No output on success.

---

### 6.3 `describe-scheduled-actions`

Describes scheduled actions. **Paginated operation.**

**Synopsis:**
```bash
aws redshift describe-scheduled-actions \
    [--scheduled-action-name <value>] \
    [--target-action-type <value>] \
    [--start-time <value>] \
    [--end-time <value>] \
    [--active | --no-active] \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--scheduled-action-name` | No | string | -- | Specific scheduled action |
| `--target-action-type` | No | string | -- | Filter: `ResizeCluster`, `PauseCluster`, `ResumeCluster` |
| `--start-time` | No | timestamp | -- | Filter by start time |
| `--end-time` | No | timestamp | -- | Filter by end time |
| `--active` | No | boolean | -- | Filter active only |
| `--filters` | No | list | -- | Additional filters. Shorthand: `Name=cluster-identifier,Values=string,string ...` |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "ScheduledActions": [
        {
            "ScheduledActionName": "string",
            "TargetAction": {},
            "Schedule": "string",
            "IamRole": "string",
            "ScheduledActionDescription": "string",
            "State": "ACTIVE|DISABLED",
            "NextInvocations": ["timestamp"],
            "StartTime": "timestamp",
            "EndTime": "timestamp"
        }
    ],
    "Marker": "string"
}
```

---

### 6.4 `modify-scheduled-action`

Modifies a scheduled action.

**Synopsis:**
```bash
aws redshift modify-scheduled-action \
    --scheduled-action-name <value> \
    [--target-action <value>] \
    [--schedule <value>] \
    [--iam-role <value>] \
    [--scheduled-action-description <value>] \
    [--start-time <value>] \
    [--end-time <value>] \
    [--enable | --no-enable] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--scheduled-action-name` | **Yes** | string | -- | Scheduled action to modify |
| `--target-action` | No | structure | -- | New target action |
| `--schedule` | No | string | -- | New schedule expression |
| `--iam-role` | No | string | -- | New IAM role ARN |
| `--scheduled-action-description` | No | string | -- | New description |
| `--start-time` | No | timestamp | -- | New start time |
| `--end-time` | No | timestamp | -- | New end time |
| `--enable` | No | boolean | -- | Enable or disable |

**Output Schema:**
```json
{
    "ScheduledActionName": "string",
    "TargetAction": {},
    "Schedule": "string",
    "IamRole": "string",
    "ScheduledActionDescription": "string",
    "State": "ACTIVE|DISABLED",
    "NextInvocations": ["timestamp"],
    "StartTime": "timestamp",
    "EndTime": "timestamp"
}
```
