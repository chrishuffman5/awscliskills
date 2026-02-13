# Instance Refresh

### 6.1 `start-instance-refresh`

Starts a new instance refresh operation, which triggers a rolling replacement of instances in the Auto Scaling group.

**Synopsis:**
```bash
aws autoscaling start-instance-refresh \
    --auto-scaling-group-name <value> \
    [--strategy <value>] \
    [--desired-configuration <value>] \
    [--preferences <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-scaling-group-name` | **Yes** | string | -- | Group name |
| `--strategy` | No | string | `Rolling` | Refresh strategy: `Rolling` |
| `--desired-configuration` | No | structure | None | Desired configuration. Shorthand: `LaunchTemplate={LaunchTemplateId=string,LaunchTemplateName=string,Version=string},MixedInstancesPolicy={...}` |
| `--preferences` | No | structure | None | Refresh preferences |

**Preferences Structure:**
```json
{
    "MinHealthyPercentage": "integer",
    "MaxHealthyPercentage": "integer",
    "InstanceWarmup": "integer",
    "CheckpointPercentages": ["integer"],
    "CheckpointDelay": "integer",
    "SkipMatching": true|false,
    "AutoRollback": true|false,
    "ScaleInProtectedInstances": "Refresh|Ignore|Wait",
    "StandbyInstances": "Terminate|Ignore|Wait",
    "AlarmSpecification": {
        "Alarms": ["string"]
    },
    "BakeTime": "integer"
}
```

**Output Schema:**
```json
{
    "InstanceRefreshId": "string"
}
```

---

### 6.2 `cancel-instance-refresh`

Cancels an instance refresh that is in progress.

**Synopsis:**
```bash
aws autoscaling cancel-instance-refresh \
    --auto-scaling-group-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-scaling-group-name` | **Yes** | string | -- | Group name |

**Output Schema:**
```json
{
    "InstanceRefreshId": "string"
}
```

---

### 6.3 `describe-instance-refreshes`

Describes one or more instance refreshes. **Paginated operation.**

**Synopsis:**
```bash
aws autoscaling describe-instance-refreshes \
    --auto-scaling-group-name <value> \
    [--instance-refresh-ids <value>] \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-scaling-group-name` | **Yes** | string | -- | Group name |
| `--instance-refresh-ids` | No | list(string) | None | Instance refresh IDs |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "InstanceRefreshes": [
        {
            "InstanceRefreshId": "string",
            "AutoScalingGroupName": "string",
            "Status": "Pending|InProgress|Successful|Failed|Cancelling|Cancelled|RollbackInProgress|RollbackFailed|RollbackSuccessful",
            "StatusReason": "string",
            "StartTime": "timestamp",
            "EndTime": "timestamp",
            "PercentageComplete": "integer",
            "InstancesToUpdate": "integer",
            "ProgressDetails": {
                "LivePoolProgress": {
                    "PercentageComplete": "integer",
                    "InstancesToUpdate": "integer"
                },
                "WarmPoolProgress": {
                    "PercentageComplete": "integer",
                    "InstancesToUpdate": "integer"
                }
            },
            "Preferences": {},
            "DesiredConfiguration": {},
            "RollbackDetails": {
                "RollbackReason": "string",
                "RollbackStartTime": "timestamp",
                "PercentageCompleteOnRollback": "integer",
                "InstancesToUpdateOnRollback": "integer",
                "ProgressDetailsOnRollback": {}
            }
        }
    ],
    "NextToken": "string"
}
```

---

### 6.4 `rollback-instance-refresh`

Rolls back an instance refresh that is in progress.

**Synopsis:**
```bash
aws autoscaling rollback-instance-refresh \
    --auto-scaling-group-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-scaling-group-name` | **Yes** | string | -- | Group name |

**Output Schema:**
```json
{
    "InstanceRefreshId": "string"
}
```
