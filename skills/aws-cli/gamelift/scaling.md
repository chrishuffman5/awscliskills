# Scaling

### 10.1 `put-scaling-policy`

Creates or updates a fleet auto-scaling policy. Supports target-based and rule-based policies.

**Synopsis:**
```bash
aws gamelift put-scaling-policy \
    --name <value> \
    --fleet-id <value> \
    --metric-name <value> \
    [--scaling-adjustment <value>] \
    [--scaling-adjustment-type <value>] \
    [--threshold <value>] \
    [--comparison-operator <value>] \
    [--evaluation-periods <value>] \
    [--policy-type <value>] \
    [--target-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Descriptive label (1-1024 chars) |
| `--fleet-id` | **Yes** | string | -- | Fleet ID or ARN |
| `--metric-name` | **Yes** | string | -- | Metric to trigger scaling (see values below) |
| `--scaling-adjustment` | No | integer | None | Adjustment amount (rule-based only) |
| `--scaling-adjustment-type` | No | string | None | `ChangeInCapacity`, `ExactCapacity`, `PercentChangeInCapacity` |
| `--threshold` | No | double | None | Metric value that triggers scaling (rule-based) |
| `--comparison-operator` | No | string | None | `GreaterThanOrEqualToThreshold`, `GreaterThanThreshold`, `LessThanThreshold`, `LessThanOrEqualToThreshold` |
| `--evaluation-periods` | No | integer | None | Minutes metric must breach threshold (min: 1) |
| `--policy-type` | No | string | None | `RuleBased` or `TargetBased` |
| `--target-configuration` | No | structure | None | Target-based settings. Shorthand: `TargetValue=double` |

**Metric Names:**
- `ActivatingGameSessions` — Game sessions being activated
- `ActiveGameSessions` — Active game sessions
- `ActiveInstances` — Active instances
- `AvailableGameSessions` — Available game sessions
- `AvailablePlayerSessions` — Available player sessions
- `CurrentPlayerSessions` — Current player sessions
- `IdleInstances` — Idle instances
- `PercentAvailableGameSessions` — Percentage available (recommended for target-based)
- `PercentIdleInstances` — Percentage idle
- `QueueDepth` — Queue depth
- `WaitTime` — Wait time
- `ConcurrentActivatableGameSessions` — Concurrent activatable sessions

**Output Schema:**
```json
{
    "Name": "string"
}
```

---

### 10.2 `delete-scaling-policy`

Deletes a fleet scaling policy.

**Synopsis:**
```bash
aws gamelift delete-scaling-policy \
    --name <value> \
    --fleet-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Policy name |
| `--fleet-id` | **Yes** | string | -- | Fleet ID or ARN |

**Output Schema:**
```json
None
```

---

### 10.3 `describe-scaling-policies`

Retrieves all scaling policies for a fleet. **Paginated.**

**Synopsis:**
```bash
aws gamelift describe-scaling-policies \
    --fleet-id <value> \
    [--status-filter <value>] \
    [--location <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fleet-id` | **Yes** | string | -- | Fleet ID or ARN |
| `--status-filter` | No | string | None | `ACTIVE`, `UPDATE_REQUESTED`, `UPDATING`, `DELETE_REQUESTED`, `DELETING`, `DELETED`, `ERROR` |
| `--location` | No | string | None | Fleet location |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ScalingPolicies": [
        {
            "FleetId": "string",
            "FleetArn": "string",
            "Name": "string",
            "Status": "ACTIVE|UPDATE_REQUESTED|UPDATING|DELETE_REQUESTED|DELETING|DELETED|ERROR",
            "ScalingAdjustment": "integer",
            "ScalingAdjustmentType": "string",
            "ComparisonOperator": "string",
            "Threshold": "double",
            "EvaluationPeriods": "integer",
            "MetricName": "string",
            "PolicyType": "RuleBased|TargetBased",
            "TargetConfiguration": {
                "TargetValue": "double"
            },
            "UpdateStatus": "string",
            "Location": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 10.4 `start-fleet-actions`

Resumes auto-scaling activity for a fleet that was previously stopped.

**Synopsis:**
```bash
aws gamelift start-fleet-actions \
    --fleet-id <value> \
    --actions <value> \
    [--location <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fleet-id` | **Yes** | string | -- | Fleet ID or ARN |
| `--actions` | **Yes** | list(string) | -- | Actions to start: `AUTO_SCALING` |
| `--location` | No | string | None | Fleet location |

**Output Schema:**
```json
{
    "FleetId": "string",
    "FleetArn": "string"
}
```

---

### 10.5 `stop-fleet-actions`

Suspends auto-scaling activity for a fleet.

**Synopsis:**
```bash
aws gamelift stop-fleet-actions \
    --fleet-id <value> \
    --actions <value> \
    [--location <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fleet-id` | **Yes** | string | -- | Fleet ID or ARN |
| `--actions` | **Yes** | list(string) | -- | Actions to stop: `AUTO_SCALING` |
| `--location` | No | string | None | Fleet location |

**Output Schema:**
```json
{
    "FleetId": "string",
    "FleetArn": "string"
}
```
