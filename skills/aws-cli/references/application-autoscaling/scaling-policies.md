# Scaling Policies

### 2.1 `put-scaling-policy`

Creates or updates a scaling policy (target tracking, step scaling, or predictive).

**Synopsis:**
```bash
aws application-autoscaling put-scaling-policy \
    --policy-name <value> \
    --service-namespace <value> \
    --resource-id <value> \
    --scalable-dimension <value> \
    [--policy-type <value>] \
    [--step-scaling-policy-configuration <value>] \
    [--target-tracking-scaling-policy-configuration <value>] \
    [--predictive-scaling-policy-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-name` | **Yes** | string | -- | Policy name (1-256 chars) |
| `--service-namespace` | **Yes** | string | -- | Service namespace |
| `--resource-id` | **Yes** | string | -- | Resource identifier |
| `--scalable-dimension` | **Yes** | string | -- | Scalable dimension |
| `--policy-type` | No | string | None | `StepScaling`, `TargetTrackingScaling`, or `PredictiveScaling` |
| `--step-scaling-policy-configuration` | No | structure | None | Step scaling config (required for StepScaling) |
| `--target-tracking-scaling-policy-configuration` | No | structure | None | Target tracking config (required for TargetTrackingScaling) |
| `--predictive-scaling-policy-configuration` | No | structure | None | Predictive scaling config (required for PredictiveScaling) |

**Target Tracking configuration:**
```json
{
    "TargetValue": 75.0,
    "PredefinedMetricSpecification": {
        "PredefinedMetricType": "ECSServiceAverageCPUUtilization",
        "ResourceLabel": "string"
    },
    "CustomizedMetricSpecification": {
        "MetricName": "string",
        "Namespace": "string",
        "Dimensions": [{"Name": "string", "Value": "string"}],
        "Statistic": "Average|Minimum|Maximum|SampleCount|Sum",
        "Unit": "string"
    },
    "ScaleOutCooldown": 300,
    "ScaleInCooldown": 300,
    "DisableScaleIn": false
}
```

**Step Scaling configuration:**
```json
{
    "AdjustmentType": "ChangeInCapacity|PercentChangeInCapacity|ExactCapacity",
    "StepAdjustments": [
        {
            "MetricIntervalLowerBound": 0.0,
            "MetricIntervalUpperBound": 20.0,
            "ScalingAdjustment": 1
        }
    ],
    "MinAdjustmentMagnitude": 1,
    "Cooldown": 300,
    "MetricAggregationType": "Average|Minimum|Maximum"
}
```

**Predictive Scaling configuration:**
```json
{
    "MetricSpecifications": [
        {
            "TargetValue": 70.0,
            "PredefinedMetricPairSpecification": {
                "PredefinedMetricType": "string",
                "ResourceLabel": "string"
            },
            "PredefinedScalingMetricSpecification": {},
            "PredefinedLoadMetricSpecification": {},
            "CustomizedScalingMetricSpecification": {},
            "CustomizedLoadMetricSpecification": {},
            "CustomizedCapacityMetricSpecification": {}
        }
    ],
    "Mode": "ForecastOnly|ForecastAndScale",
    "SchedulingBufferTime": 300,
    "MaxCapacityBreachBehavior": "HonorMaxCapacity|IncreaseMaxCapacity",
    "MaxCapacityBuffer": 10
}
```

**Predefined Metric Types (target tracking):**
- `ECSServiceAverageCPUUtilization`, `ECSServiceAverageMemoryUtilization`
- `DynamoDBReadCapacityUtilization`, `DynamoDBWriteCapacityUtilization`
- `ALBRequestCountPerTarget`
- `RDSReaderAverageCPUUtilization`, `RDSReaderAverageDatabaseConnections`
- `SageMakerVariantInvocationsPerInstance`, `SageMakerVariantProvisionedConcurrencyUtilization`
- `ElastiCachePrimaryEngineCPUUtilization`, `ElastiCacheReplicaEngineCPUUtilization`, `ElastiCacheDatabaseMemoryUsageCountedForEvictPercentage`, `ElastiCacheDatabaseCapacityUsageCountedForEvictPercentage`
- `NeptuneReaderAverageCPUUtilization`
- `LambdaProvisionedConcurrencyUtilization`
- `CassandraReadCapacityUtilization`, `CassandraWriteCapacityUtilization`
- `KafkaBrokerStorageUtilization`
- `EC2SpotFleetRequestAverageCPUUtilization`, `EC2SpotFleetRequestAverageNetworkIn`, `EC2SpotFleetRequestAverageNetworkOut`

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

### 2.2 `delete-scaling-policy`

Deletes a scaling policy.

**Synopsis:**
```bash
aws application-autoscaling delete-scaling-policy \
    --policy-name <value> \
    --service-namespace <value> \
    --resource-id <value> \
    --scalable-dimension <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-name` | **Yes** | string | -- | Policy name to delete |
| `--service-namespace` | **Yes** | string | -- | Service namespace |
| `--resource-id` | **Yes** | string | -- | Resource identifier |
| `--scalable-dimension` | **Yes** | string | -- | Scalable dimension |

**Output:** None

---

### 2.3 `describe-scaling-policies`

Describes scaling policies. **Paginated operation.**

**Synopsis:**
```bash
aws application-autoscaling describe-scaling-policies \
    --service-namespace <value> \
    [--policy-names <value>] \
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
| `--policy-names` | No | list | None | Policy names to filter (max 50) |
| `--resource-id` | No | string | None | Filter by resource ID |
| `--scalable-dimension` | No | string | None | Filter by scalable dimension |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Size of each page |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "ScalingPolicies": [
        {
            "PolicyARN": "string",
            "PolicyName": "string",
            "ServiceNamespace": "string",
            "ResourceId": "string",
            "ScalableDimension": "string",
            "PolicyType": "StepScaling|TargetTrackingScaling|PredictiveScaling",
            "StepScalingPolicyConfiguration": {},
            "TargetTrackingScalingPolicyConfiguration": {},
            "PredictiveScalingPolicyConfiguration": {},
            "Alarms": [
                {
                    "AlarmName": "string",
                    "AlarmARN": "string"
                }
            ],
            "CreationTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.4 `describe-scaling-activities`

Describes scaling activities and history. **Paginated operation.**

**Synopsis:**
```bash
aws application-autoscaling describe-scaling-activities \
    --service-namespace <value> \
    [--resource-id <value>] \
    [--scalable-dimension <value>] \
    [--include-not-scaled-activities | --no-include-not-scaled-activities] \
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
| `--resource-id` | No | string | None | Filter by resource ID |
| `--scalable-dimension` | No | string | None | Filter by scalable dimension |
| `--include-not-scaled-activities` | No | boolean | false | Include activities that were not scaled |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Size of each page |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "ScalingActivities": [
        {
            "ActivityId": "string",
            "ServiceNamespace": "string",
            "ResourceId": "string",
            "ScalableDimension": "string",
            "Description": "string",
            "Cause": "string",
            "StartTime": "timestamp",
            "EndTime": "timestamp",
            "StatusCode": "Pending|InProgress|Successful|Overridden|Unfulfilled|Failed",
            "StatusMessage": "string",
            "Details": "string",
            "NotScaledReasons": [
                {
                    "Code": "string",
                    "MaxCapacity": "integer",
                    "MinCapacity": "integer",
                    "CurrentCapacity": "integer"
                }
            ]
        }
    ],
    "NextToken": "string"
}
```

---

### 2.5 `get-predictive-scaling-forecast`

Gets predictive scaling forecast data for load and capacity.

**Synopsis:**
```bash
aws application-autoscaling get-predictive-scaling-forecast \
    --service-namespace <value> \
    --resource-id <value> \
    --scalable-dimension <value> \
    --policy-name <value> \
    --start-time <value> \
    --end-time <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-namespace` | **Yes** | string | -- | Service namespace |
| `--resource-id` | **Yes** | string | -- | Resource identifier |
| `--scalable-dimension` | **Yes** | string | -- | Scalable dimension |
| `--policy-name` | **Yes** | string | -- | Predictive scaling policy name |
| `--start-time` | **Yes** | timestamp | -- | Forecast start time (max 1 year ago) |
| `--end-time` | **Yes** | timestamp | -- | Forecast end time (max 30-day range) |

**Output Schema:**
```json
{
    "LoadForecast": [
        {
            "Timestamps": ["timestamp"],
            "Values": ["double"],
            "MetricSpecification": {
                "TargetValue": "double",
                "PredefinedMetricPairSpecification": {},
                "PredefinedScalingMetricSpecification": {},
                "PredefinedLoadMetricSpecification": {},
                "CustomizedScalingMetricSpecification": {},
                "CustomizedLoadMetricSpecification": {},
                "CustomizedCapacityMetricSpecification": {}
            }
        }
    ],
    "CapacityForecast": {
        "Timestamps": ["timestamp"],
        "Values": ["double"]
    },
    "UpdateTime": "timestamp"
}
```
