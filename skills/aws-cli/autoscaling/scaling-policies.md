# Scaling Policies

### 3.1 `put-scaling-policy`

Creates or updates a scaling policy for an Auto Scaling group.

**Synopsis:**
```bash
aws autoscaling put-scaling-policy \
    --auto-scaling-group-name <value> \
    --policy-name <value> \
    --policy-type <value> \
    [--adjustment-type <value>] \
    [--min-adjustment-step <value>] \
    [--min-adjustment-magnitude <value>] \
    [--scaling-adjustment <value>] \
    [--cooldown <value>] \
    [--metric-aggregation-type <value>] \
    [--step-adjustments <value>] \
    [--estimated-instance-warmup <value>] \
    [--target-tracking-configuration <value>] \
    [--enabled | --no-enabled] \
    [--predictive-scaling-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-scaling-group-name` | **Yes** | string | -- | Name of the group |
| `--policy-name` | **Yes** | string | -- | Policy name |
| `--policy-type` | **Yes** | string | -- | `SimpleScaling`, `StepScaling`, `TargetTrackingScaling`, or `PredictiveScaling` |
| `--adjustment-type` | No | string | None | `ChangeInCapacity`, `ExactCapacity`, `PercentChangeInCapacity` (Simple/Step) |
| `--min-adjustment-step` | No | integer | None | Deprecated: use `--min-adjustment-magnitude` |
| `--min-adjustment-magnitude` | No | integer | None | Minimum adjustment for PercentChangeInCapacity |
| `--scaling-adjustment` | No | integer | None | Amount to scale (SimpleScaling) |
| `--cooldown` | No | integer | None | Cooldown period in seconds (SimpleScaling) |
| `--metric-aggregation-type` | No | string | `Average` | `Minimum`, `Maximum`, `Average` (StepScaling) |
| `--step-adjustments` | No | list | None | Step adjustments. Shorthand: `MetricIntervalLowerBound=double,MetricIntervalUpperBound=double,ScalingAdjustment=integer ...` |
| `--estimated-instance-warmup` | No | integer | None | Warmup time for new instances in seconds |
| `--target-tracking-configuration` | No | structure | None | Target tracking config (JSON, use `file://`) |
| `--enabled` | No | boolean | true | Enable or disable the policy |
| `--predictive-scaling-configuration` | No | structure | None | Predictive scaling config (JSON) |

**Target Tracking Configuration:**
```json
{
    "PredefinedMetricSpecification": {
        "PredefinedMetricType": "ASGAverageCPUUtilization|ASGAverageNetworkIn|ASGAverageNetworkOut|ALBRequestCountPerTarget",
        "ResourceLabel": "string"
    },
    "CustomizedMetricSpecification": {
        "MetricName": "string",
        "Namespace": "string",
        "Dimensions": [{"Name": "string", "Value": "string"}],
        "Statistic": "Average|Minimum|Maximum|SampleCount|Sum",
        "Unit": "string",
        "Metrics": []
    },
    "TargetValue": "double",
    "DisableScaleIn": true|false
}
```

**Output Schema:**
```json
{
    "PolicyARN": "string",
    "Alarms": [
        {
            "AlarmName": "string",
            "AlarmARN": "string"
        }
    ]
}
```

---

### 3.2 `delete-policy`

Deletes the specified scaling policy.

**Synopsis:**
```bash
aws autoscaling delete-policy \
    --policy-name <value> \
    [--auto-scaling-group-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-name` | **Yes** | string | -- | Policy name or ARN |
| `--auto-scaling-group-name` | No | string | None | Group name (required if policy-name is not an ARN) |

**Output:** No output on success.

---

### 3.3 `describe-policies`

Describes the policies for the specified Auto Scaling group. **Paginated operation.**

**Synopsis:**
```bash
aws autoscaling describe-policies \
    [--auto-scaling-group-name <value>] \
    [--policy-names <value>] \
    [--policy-types <value>] \
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
| `--policy-names` | No | list(string) | None | Policy names or ARNs |
| `--policy-types` | No | list(string) | None | Policy types to filter by |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "ScalingPolicies": [
        {
            "AutoScalingGroupName": "string",
            "PolicyName": "string",
            "PolicyARN": "string",
            "PolicyType": "string",
            "AdjustmentType": "string",
            "MinAdjustmentStep": "integer",
            "MinAdjustmentMagnitude": "integer",
            "ScalingAdjustment": "integer",
            "Cooldown": "integer",
            "StepAdjustments": [
                {
                    "MetricIntervalLowerBound": "double",
                    "MetricIntervalUpperBound": "double",
                    "ScalingAdjustment": "integer"
                }
            ],
            "MetricAggregationType": "string",
            "EstimatedInstanceWarmup": "integer",
            "Alarms": [
                {
                    "AlarmName": "string",
                    "AlarmARN": "string"
                }
            ],
            "TargetTrackingConfiguration": {},
            "Enabled": true|false,
            "PredictiveScalingConfiguration": {}
        }
    ],
    "NextToken": "string"
}
```

---

### 3.4 `execute-policy`

Executes the specified policy immediately. Useful for testing.

**Synopsis:**
```bash
aws autoscaling execute-policy \
    --policy-name <value> \
    [--auto-scaling-group-name <value>] \
    [--honor-cooldown | --no-honor-cooldown] \
    [--metric-value <value>] \
    [--breach-threshold <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-name` | **Yes** | string | -- | Policy name or ARN |
| `--auto-scaling-group-name` | No | string | None | Group name |
| `--honor-cooldown` | No | boolean | false | Honor the cooldown period |
| `--metric-value` | No | double | None | Metric value (for StepScaling) |
| `--breach-threshold` | No | double | None | Breach threshold (for StepScaling) |

**Output:** No output on success.

---

### 3.5 `describe-scaling-process-types`

Describes the scaling process types.

**Synopsis:**
```bash
aws autoscaling describe-scaling-process-types \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** No required parameters.

**Output Schema:**
```json
{
    "Processes": [
        {
            "ProcessName": "Launch|Terminate|AddToLoadBalancer|AlarmNotification|AZRebalance|HealthCheck|InstanceRefresh|ReplaceUnhealthy|ScheduledActions"
        }
    ]
}
```

---

### 3.6 `suspend-processes`

Suspends the specified scaling processes for the group.

**Synopsis:**
```bash
aws autoscaling suspend-processes \
    --auto-scaling-group-name <value> \
    [--scaling-processes <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-scaling-group-name` | **Yes** | string | -- | Name of the group |
| `--scaling-processes` | No | list(string) | None | Process names to suspend. Omit to suspend all |

**Output:** No output on success.

---

### 3.7 `resume-processes`

Resumes the specified suspended scaling processes.

**Synopsis:**
```bash
aws autoscaling resume-processes \
    --auto-scaling-group-name <value> \
    [--scaling-processes <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-scaling-group-name` | **Yes** | string | -- | Name of the group |
| `--scaling-processes` | No | list(string) | None | Process names to resume. Omit to resume all |

**Output:** No output on success.
