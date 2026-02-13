# Scaling

### 4.1 `put-auto-scaling-policy`

Creates or updates an automatic scaling policy for an instance group.

**Synopsis:**
```bash
aws emr put-auto-scaling-policy \
    --cluster-id <value> \
    --instance-group-id <value> \
    --auto-scaling-policy <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | Cluster ID |
| `--instance-group-id` | **Yes** | string | -- | Instance group ID |
| `--auto-scaling-policy` | **Yes** | structure | -- | Scaling policy (JSON) |

**Auto Scaling Policy JSON:**
```json
{
    "Constraints": {
        "MinCapacity": 2,
        "MaxCapacity": 10
    },
    "Rules": [
        {
            "Name": "ScaleOut",
            "Description": "Scale out on high YARN memory",
            "Action": {
                "SimpleScalingPolicyConfiguration": {
                    "AdjustmentType": "CHANGE_IN_CAPACITY",
                    "ScalingAdjustment": 2,
                    "CoolDown": 300
                }
            },
            "Trigger": {
                "CloudWatchAlarmDefinition": {
                    "ComparisonOperator": "GREATER_THAN_OR_EQUAL",
                    "EvaluationPeriods": 1,
                    "MetricName": "YARNMemoryAvailablePercentage",
                    "Namespace": "AWS/ElasticMapReduce",
                    "Period": 300,
                    "Statistic": "AVERAGE",
                    "Threshold": 15,
                    "Unit": "PERCENT"
                }
            }
        }
    ]
}
```

**Output Schema:**
```json
{
    "ClusterId": "string",
    "InstanceGroupId": "string",
    "AutoScalingPolicy": {
        "Status": {
            "State": "PENDING|ATTACHING|ATTACHED|DETACHING|DETACHED|FAILED"
        },
        "Constraints": {},
        "Rules": [],
        "ClusterArn": "string"
    }
}
```

---

### 4.2 `remove-auto-scaling-policy`

Removes an automatic scaling policy from an instance group.

**Synopsis:**
```bash
aws emr remove-auto-scaling-policy \
    --cluster-id <value> \
    --instance-group-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | Cluster ID |
| `--instance-group-id` | **Yes** | string | -- | Instance group ID |

No output on success.

---

### 4.3 `put-managed-scaling-policy`

Creates or updates a managed scaling policy for a cluster. Managed scaling automatically adjusts instance counts based on workload.

**Synopsis:**
```bash
aws emr put-managed-scaling-policy \
    --cluster-id <value> \
    --managed-scaling-policy <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | Cluster ID |
| `--managed-scaling-policy` | **Yes** | structure | -- | Policy definition |

**Managed Scaling Policy JSON:**
```json
{
    "ComputeLimits": {
        "UnitType": "InstanceFleetUnits|Instances|VCPU",
        "MinimumCapacityUnits": 2,
        "MaximumCapacityUnits": 20,
        "MaximumOnDemandCapacityUnits": 10,
        "MaximumCoreCapacityUnits": 10
    }
}
```

No output on success.

---

### 4.4 `get-managed-scaling-policy`

Gets the managed scaling policy for a cluster.

**Synopsis:**
```bash
aws emr get-managed-scaling-policy \
    --cluster-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | Cluster ID |

**Output Schema:**
```json
{
    "ManagedScalingPolicy": {
        "ComputeLimits": {
            "UnitType": "InstanceFleetUnits|Instances|VCPU",
            "MinimumCapacityUnits": "integer",
            "MaximumCapacityUnits": "integer",
            "MaximumOnDemandCapacityUnits": "integer",
            "MaximumCoreCapacityUnits": "integer"
        }
    }
}
```

---

### 4.5 `remove-managed-scaling-policy`

Removes the managed scaling policy from a cluster.

**Synopsis:**
```bash
aws emr remove-managed-scaling-policy \
    --cluster-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | Cluster ID |

No output on success.
