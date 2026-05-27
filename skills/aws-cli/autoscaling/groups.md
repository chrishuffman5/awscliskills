# Groups

### 1.1 `create-auto-scaling-group`

Creates an Auto Scaling group with the specified name and attributes.

**Synopsis:**
```bash
aws autoscaling create-auto-scaling-group \
    --auto-scaling-group-name <value> \
    --min-size <value> \
    --max-size <value> \
    [--launch-configuration-name <value>] \
    [--launch-template <value>] \
    [--mixed-instances-policy <value>] \
    [--instance-id <value>] \
    [--desired-capacity <value>] \
    [--default-cooldown <value>] \
    [--availability-zones <value>] \
    [--load-balancer-names <value>] \
    [--target-group-arns <value>] \
    [--health-check-type <value>] \
    [--health-check-grace-period <value>] \
    [--placement-group <value>] \
    [--vpc-zone-identifier <value>] \
    [--termination-policies <value>] \
    [--new-instances-protected-from-scale-in | --no-new-instances-protected-from-scale-in] \
    [--capacity-rebalance | --no-capacity-rebalance] \
    [--lifecycle-hook-specification-list <value>] \
    [--tags <value>] \
    [--service-linked-role-arn <value>] \
    [--max-instance-lifetime <value>] \
    [--context <value>] \
    [--desired-capacity-type <value>] \
    [--default-instance-warmup <value>] \
    [--traffic-sources <value>] \
    [--instance-maintenance-policy <value>] \
    [--availability-zone-distribution <value>] \
    [--availability-zone-impairment-policy <value>] \
    [--capacity-reservation-specification <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-scaling-group-name` | **Yes** | string | -- | Name of the group (1-255 chars) |
| `--min-size` | **Yes** | integer | -- | Minimum number of instances |
| `--max-size` | **Yes** | integer | -- | Maximum number of instances |
| `--launch-configuration-name` | No | string | None | Name of the launch configuration (legacy) |
| `--launch-template` | No | structure | None | Launch template. Shorthand: `LaunchTemplateId=string,LaunchTemplateName=string,Version=string` |
| `--mixed-instances-policy` | No | structure | None | Mixed instances policy (JSON, use `--cli-input-json`) |
| `--instance-id` | No | string | None | EC2 instance ID to create the group from |
| `--desired-capacity` | No | integer | min-size | Desired number of instances |
| `--default-cooldown` | No | integer | 300 | Default cooldown period in seconds |
| `--availability-zones` | No | list(string) | None | AZs for the group (required if no VPC subnets) |
| `--load-balancer-names` | No | list(string) | None | Classic Load Balancer names |
| `--target-group-arns` | No | list(string) | None | ALB/NLB target group ARNs |
| `--health-check-type` | No | string | `EC2` | `EC2`, `ELB`, or `VPC_LATTICE` |
| `--health-check-grace-period` | No | integer | 0 | Seconds after launch before health checks start |
| `--placement-group` | No | string | None | Placement group name |
| `--vpc-zone-identifier` | No | string | None | Comma-separated subnet IDs |
| `--termination-policies` | No | list(string) | `["Default"]` | Policies for choosing which instances to terminate |
| `--new-instances-protected-from-scale-in` | No | boolean | false | Protect new instances from scale-in |
| `--capacity-rebalance` | No | boolean | false | Enable Capacity Rebalancing for Spot |
| `--lifecycle-hook-specification-list` | No | list | None | Lifecycle hooks to create with the group |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string,PropagateAtLaunch=boolean,ResourceId=string,ResourceType=string ...` |
| `--service-linked-role-arn` | No | string | None | Service-linked role ARN |
| `--max-instance-lifetime` | No | integer | None | Maximum instance lifetime in seconds (604800-31536000) |
| `--context` | No | string | None | Reserved context string |
| `--desired-capacity-type` | No | string | `units` | `units`, `vcpu`, or `memory-mib` |
| `--default-instance-warmup` | No | integer | None | Default instance warmup in seconds |
| `--traffic-sources` | No | list | None | Traffic sources. Shorthand: `Identifier=string,Type=string` |
| `--instance-maintenance-policy` | No | structure | None | Instance maintenance policy. Shorthand: `MinHealthyPercentage=integer,MaxHealthyPercentage=integer` |
| `--availability-zone-distribution` | No | structure | None | AZ distribution. Shorthand: `CapacityDistributionStrategy=balanced-only\|balanced-best-effort` |
| `--availability-zone-impairment-policy` | No | structure | None | AZ impairment policy. Shorthand: `ZonalShiftEnabled=boolean,ImpairedZoneHealthCheckBehavior=ReplaceUnhealthy\|IgnoreUnhealthy` |
| `--capacity-reservation-specification` | No | structure | None | Capacity reservation specification |

**Output:** No output on success.

---

### 1.2 `update-auto-scaling-group`

Updates the configuration for the specified Auto Scaling group.

**Synopsis:**
```bash
aws autoscaling update-auto-scaling-group \
    --auto-scaling-group-name <value> \
    [--launch-configuration-name <value>] \
    [--launch-template <value>] \
    [--mixed-instances-policy <value>] \
    [--min-size <value>] \
    [--max-size <value>] \
    [--desired-capacity <value>] \
    [--default-cooldown <value>] \
    [--availability-zones <value>] \
    [--health-check-type <value>] \
    [--health-check-grace-period <value>] \
    [--placement-group <value>] \
    [--vpc-zone-identifier <value>] \
    [--termination-policies <value>] \
    [--new-instances-protected-from-scale-in | --no-new-instances-protected-from-scale-in] \
    [--service-linked-role-arn <value>] \
    [--max-instance-lifetime <value>] \
    [--capacity-rebalance | --no-capacity-rebalance] \
    [--context <value>] \
    [--desired-capacity-type <value>] \
    [--default-instance-warmup <value>] \
    [--instance-maintenance-policy <value>] \
    [--availability-zone-distribution <value>] \
    [--availability-zone-impairment-policy <value>] \
    [--capacity-reservation-specification <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-scaling-group-name` | **Yes** | string | -- | Name of the group |
| `--launch-configuration-name` | No | string | None | Updated launch configuration |
| `--launch-template` | No | structure | None | Updated launch template |
| `--mixed-instances-policy` | No | structure | None | Updated mixed instances policy |
| `--min-size` | No | integer | None | Updated minimum size |
| `--max-size` | No | integer | None | Updated maximum size |
| `--desired-capacity` | No | integer | None | Updated desired capacity |
| `--default-cooldown` | No | integer | None | Updated cooldown |
| `--availability-zones` | No | list(string) | None | Updated AZs |
| `--health-check-type` | No | string | None | Updated health check type |
| `--health-check-grace-period` | No | integer | None | Updated grace period |
| `--placement-group` | No | string | None | Updated placement group |
| `--vpc-zone-identifier` | No | string | None | Updated subnet IDs |
| `--termination-policies` | No | list(string) | None | Updated termination policies |
| `--new-instances-protected-from-scale-in` | No | boolean | None | Updated scale-in protection |
| `--max-instance-lifetime` | No | integer | None | Updated max lifetime (0 to clear) |
| `--default-instance-warmup` | No | integer | None | Updated default warmup |
| `--instance-maintenance-policy` | No | structure | None | Updated maintenance policy |

**Output:** No output on success.

---

### 1.3 `delete-auto-scaling-group`

Deletes the specified Auto Scaling group.

**Synopsis:**
```bash
aws autoscaling delete-auto-scaling-group \
    --auto-scaling-group-name <value> \
    [--force-delete | --no-force-delete] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-scaling-group-name` | **Yes** | string | -- | Name of the group |
| `--force-delete` | No | boolean | false | Force delete even if group has instances |

**Output:** No output on success.

---

### 1.4 `describe-auto-scaling-groups`

Describes one or more Auto Scaling groups. **Paginated operation.**

**Synopsis:**
```bash
aws autoscaling describe-auto-scaling-groups \
    [--auto-scaling-group-names <value>] \
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
| `--auto-scaling-group-names` | No | list(string) | None | Group names (up to 50) |
| `--filters` | No | list | None | Filters. Shorthand: `Name=string,Values=string,string ...` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "AutoScalingGroups": [
        {
            "AutoScalingGroupName": "string",
            "AutoScalingGroupARN": "string",
            "LaunchConfigurationName": "string",
            "LaunchTemplate": {
                "LaunchTemplateId": "string",
                "LaunchTemplateName": "string",
                "Version": "string"
            },
            "MixedInstancesPolicy": {},
            "MinSize": "integer",
            "MaxSize": "integer",
            "DesiredCapacity": "integer",
            "PredictedCapacity": "integer",
            "DefaultCooldown": "integer",
            "AvailabilityZones": ["string"],
            "LoadBalancerNames": ["string"],
            "TargetGroupARNs": ["string"],
            "HealthCheckType": "string",
            "HealthCheckGracePeriod": "integer",
            "Instances": [
                {
                    "InstanceId": "string",
                    "InstanceType": "string",
                    "AvailabilityZone": "string",
                    "LifecycleState": "string",
                    "HealthStatus": "string",
                    "LaunchConfigurationName": "string",
                    "LaunchTemplate": {},
                    "ProtectedFromScaleIn": true|false,
                    "WeightedCapacity": "string"
                }
            ],
            "CreatedTime": "timestamp",
            "SuspendedProcesses": [
                {
                    "ProcessName": "string",
                    "SuspensionReason": "string"
                }
            ],
            "PlacementGroup": "string",
            "VPCZoneIdentifier": "string",
            "EnabledMetrics": [
                {
                    "Metric": "string",
                    "Granularity": "string"
                }
            ],
            "Status": "string",
            "Tags": [
                {
                    "ResourceId": "string",
                    "ResourceType": "string",
                    "Key": "string",
                    "Value": "string",
                    "PropagateAtLaunch": true|false
                }
            ],
            "TerminationPolicies": ["string"],
            "NewInstancesProtectedFromScaleIn": true|false,
            "ServiceLinkedRoleARN": "string",
            "MaxInstanceLifetime": "integer",
            "CapacityRebalance": true|false,
            "WarmPoolConfiguration": {
                "MaxGroupPreparedCapacity": "integer",
                "MinSize": "integer",
                "PoolState": "Stopped|Running|Hibernated",
                "Status": "PendingDelete",
                "InstanceReusePolicy": {
                    "ReuseOnScaleIn": true|false
                }
            },
            "WarmPoolSize": "integer",
            "Context": "string",
            "DesiredCapacityType": "string",
            "DefaultInstanceWarmup": "integer",
            "TrafficSources": [
                {
                    "Identifier": "string",
                    "Type": "string"
                }
            ],
            "InstanceMaintenancePolicy": {
                "MinHealthyPercentage": "integer",
                "MaxHealthyPercentage": "integer"
            },
            "AvailabilityZoneDistribution": {
                "CapacityDistributionStrategy": "string"
            },
            "AvailabilityZoneImpairmentPolicy": {
                "ZonalShiftEnabled": true|false,
                "ImpairedZoneHealthCheckBehavior": "string"
            }
        }
    ],
    "NextToken": "string"
}
```

---

### 1.5 `set-desired-capacity`

Sets the size of the specified Auto Scaling group.

**Synopsis:**
```bash
aws autoscaling set-desired-capacity \
    --auto-scaling-group-name <value> \
    --desired-capacity <value> \
    [--honor-cooldown | --no-honor-cooldown] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-scaling-group-name` | **Yes** | string | -- | Name of the group |
| `--desired-capacity` | **Yes** | integer | -- | New desired capacity |
| `--honor-cooldown` | No | boolean | false | Honor the default cooldown period |

**Output:** No output on success.

---

### 1.6 `attach-instances`

Attaches one or more EC2 instances to the specified Auto Scaling group.

**Synopsis:**
```bash
aws autoscaling attach-instances \
    --auto-scaling-group-name <value> \
    [--instance-ids <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-scaling-group-name` | **Yes** | string | -- | Name of the group |
| `--instance-ids` | No | list(string) | None | Instance IDs to attach |

**Output:** No output on success.

---

### 1.7 `detach-instances`

Removes one or more instances from the specified Auto Scaling group.

**Synopsis:**
```bash
aws autoscaling detach-instances \
    --auto-scaling-group-name <value> \
    --should-decrement-desired-capacity | --no-should-decrement-desired-capacity \
    [--instance-ids <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-scaling-group-name` | **Yes** | string | -- | Name of the group |
| `--should-decrement-desired-capacity` | **Yes** | boolean | -- | Whether to decrement desired capacity |
| `--instance-ids` | No | list(string) | None | Instance IDs to detach |

**Output Schema:**
```json
{
    "Activities": [
        {
            "ActivityId": "string",
            "AutoScalingGroupName": "string",
            "Description": "string",
            "Cause": "string",
            "StartTime": "timestamp",
            "EndTime": "timestamp",
            "StatusCode": "PendingSpotBidPlacement|WaitingForSpotInstanceRequestId|WaitingForSpotInstanceId|WaitingForInstanceId|PreInService|InProgress|WaitingForELBConnectionDraining|MidLifecycleAction|WaitingForInstanceWarmup|Successful|Failed|Cancelled|WaitingForConnectionDraining",
            "StatusMessage": "string",
            "Progress": "integer",
            "Details": "string",
            "AutoScalingGroupState": "string",
            "AutoScalingGroupARN": "string"
        }
    ]
}
```

---

### 1.8 `enter-standby`

Moves the specified instances into standby mode. Instances in standby are still part of the group but are not actively in service.

**Synopsis:**
```bash
aws autoscaling enter-standby \
    --auto-scaling-group-name <value> \
    --should-decrement-desired-capacity | --no-should-decrement-desired-capacity \
    [--instance-ids <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-scaling-group-name` | **Yes** | string | -- | Name of the group |
| `--should-decrement-desired-capacity` | **Yes** | boolean | -- | Whether to decrement desired capacity |
| `--instance-ids` | No | list(string) | None | Instance IDs |

**Output Schema:**
```json
{
    "Activities": [
        {
            "ActivityId": "string",
            "AutoScalingGroupName": "string",
            "Description": "string",
            "Cause": "string",
            "StartTime": "timestamp",
            "StatusCode": "string",
            "Progress": "integer"
        }
    ]
}
```

---

### 1.9 `exit-standby`

Moves the specified instances out of standby mode and into InService.

**Synopsis:**
```bash
aws autoscaling exit-standby \
    --auto-scaling-group-name <value> \
    [--instance-ids <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-scaling-group-name` | **Yes** | string | -- | Name of the group |
| `--instance-ids` | No | list(string) | None | Instance IDs |

**Output Schema:**
```json
{
    "Activities": [
        {
            "ActivityId": "string",
            "AutoScalingGroupName": "string",
            "Description": "string",
            "Cause": "string",
            "StartTime": "timestamp",
            "StatusCode": "string",
            "Progress": "integer"
        }
    ]
}
```

---

### 1.10 `set-instance-protection`

Updates the instance protection settings for the specified instances.

**Synopsis:**
```bash
aws autoscaling set-instance-protection \
    --instance-ids <value> \
    --auto-scaling-group-name <value> \
    --protected-from-scale-in | --no-protected-from-scale-in \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-ids` | **Yes** | list(string) | -- | Instance IDs |
| `--auto-scaling-group-name` | **Yes** | string | -- | Name of the group |
| `--protected-from-scale-in` | **Yes** | boolean | -- | Enable or disable protection |

**Output:** No output on success (empty JSON `{}`).

---

### 1.11 `terminate-instance-in-auto-scaling-group`

Terminates the specified instance and optionally adjusts the desired capacity.

**Synopsis:**
```bash
aws autoscaling terminate-instance-in-auto-scaling-group \
    --instance-id <value> \
    --should-decrement-desired-capacity | --no-should-decrement-desired-capacity \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID to terminate |
| `--should-decrement-desired-capacity` | **Yes** | boolean | -- | Whether to decrement desired capacity |

**Output Schema:**
```json
{
    "Activity": {
        "ActivityId": "string",
        "AutoScalingGroupName": "string",
        "Description": "string",
        "Cause": "string",
        "StartTime": "timestamp",
        "StatusCode": "string",
        "Progress": "integer"
    }
}
```

---

### 1.12 `set-instance-health`

Sets the health status of the specified instance.

**Synopsis:**
```bash
aws autoscaling set-instance-health \
    --instance-id <value> \
    --health-status <value> \
    [--should-respect-grace-period | --no-should-respect-grace-period] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID |
| `--health-status` | **Yes** | string | -- | `Healthy` or `Unhealthy` |
| `--should-respect-grace-period` | No | boolean | false | Respect the health check grace period |

**Output:** No output on success.

---

### 1.13 `describe-auto-scaling-instances`

Describes one or more Auto Scaling instances. **Paginated operation.**

**Synopsis:**
```bash
aws autoscaling describe-auto-scaling-instances \
    [--instance-ids <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-ids` | No | list(string) | None | Instance IDs (up to 50) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "AutoScalingInstances": [
        {
            "InstanceId": "string",
            "InstanceType": "string",
            "AutoScalingGroupName": "string",
            "AvailabilityZone": "string",
            "LifecycleState": "string",
            "HealthStatus": "string",
            "LaunchConfigurationName": "string",
            "LaunchTemplate": {
                "LaunchTemplateId": "string",
                "LaunchTemplateName": "string",
                "Version": "string"
            },
            "ProtectedFromScaleIn": true|false,
            "WeightedCapacity": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.14 `describe-scaling-activities`

Describes one or more scaling activities. **Paginated operation.**

**Synopsis:**
```bash
aws autoscaling describe-scaling-activities \
    [--activity-ids <value>] \
    [--auto-scaling-group-name <value>] \
    [--include-deleted-groups | --no-include-deleted-groups] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--activity-ids` | No | list(string) | None | Activity IDs |
| `--auto-scaling-group-name` | No | string | None | Group name |
| `--include-deleted-groups` | No | boolean | false | Include activities from deleted groups |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "Activities": [
        {
            "ActivityId": "string",
            "AutoScalingGroupName": "string",
            "Description": "string",
            "Cause": "string",
            "StartTime": "timestamp",
            "EndTime": "timestamp",
            "StatusCode": "string",
            "StatusMessage": "string",
            "Progress": "integer",
            "Details": "string",
            "AutoScalingGroupState": "string",
            "AutoScalingGroupARN": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.15 `describe-adjustment-types`

Describes the policy adjustment types for use with `put-scaling-policy`.

**Synopsis:**
```bash
aws autoscaling describe-adjustment-types \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** No required parameters.

**Output Schema:**
```json
{
    "AdjustmentTypes": [
        {
            "AdjustmentType": "ChangeInCapacity|ExactCapacity|PercentChangeInCapacity"
        }
    ]
}
```
