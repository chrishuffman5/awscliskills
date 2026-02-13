# Auto Scaling

> These commands use `aws autoscaling`, not `aws ec2`.

### 7.1 `aws autoscaling create-auto-scaling-group`

**Description:** Creates an Auto Scaling group. AWS strongly recommends using launch templates. Groups have three size properties: MinSize, MaxSize, DesiredCapacity.

#### Parameters

**Required:**

| Parameter | Type | Description |
|-----------|------|-------------|
| `--auto-scaling-group-name` | string | Unique name (1-255 chars, no colons) |
| `--min-size` | integer | Minimum group size |
| `--max-size` | integer | Maximum group size |

**Conditional (must specify one):**

| Parameter | Type | Description |
|-----------|------|-------------|
| `--launch-template` | structure | `{LaunchTemplateId, LaunchTemplateName, Version}` -- Version: `$Latest`, `$Default`, or number |
| `--launch-configuration-name` | string | Launch configuration name |
| `--mixed-instances-policy` | structure | Multiple instance types and purchasing options (see below) |
| `--instance-id` | string | Existing instance to use as template |

**Optional:**

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `--desired-capacity` | integer | MinSize | Initial and maintenance target |
| `--default-cooldown` | integer | 300 | Seconds between scaling activities |
| `--availability-zones` | list(string) | -- | AZs for instances |
| `--vpc-zone-identifier` | string | -- | Comma-separated subnet IDs |
| `--load-balancer-names` | list(string) | -- | Classic Load Balancer names |
| `--target-group-arns` | list(string) | -- | ALB/NLB/GLB target group ARNs |
| `--health-check-type` | string | EC2 | `EC2`, `EBS`, `ELB`, or `VPC_LATTICE` |
| `--health-check-grace-period` | integer | 0 | Seconds before first health check |
| `--placement-group` | string | -- | Placement group name |
| `--termination-policies` | list(string) | Default | `Default`, `AllocationStrategy`, `ClosestToNextInstanceHour`, `NewestInstance`, `OldestInstance`, `OldestLaunchConfiguration`, `OldestLaunchTemplate`, or Lambda ARN |
| `--new-instances-protected-from-scale-in` | boolean | false | Scale-in protection |
| `--capacity-rebalance` | boolean | false | Spot capacity rebalancing |
| `--tags` | list(structure) | -- | Tags: `{ResourceId, ResourceType, Key, Value, PropagateAtLaunch}` |
| `--service-linked-role-arn` | string | auto | Service-linked role |
| `--max-instance-lifetime` | integer | -- | Max instance lifetime seconds (>=86400 or 0) |
| `--desired-capacity-type` | string | units | `units`, `vcpu`, or `memory-mib` |
| `--default-instance-warmup` | integer | -- | Instance warmup seconds |
| `--lifecycle-hook-specification-list` | list(structure) | -- | Lifecycle hooks |
| `--traffic-sources` | list(structure) | -- | Traffic source configs |
| `--instance-maintenance-policy` | structure | -- | `{MinHealthyPercentage, MaxHealthyPercentage}` |
| `--availability-zone-distribution` | structure | -- | `{CapacityDistributionStrategy: [balanced-only/balanced-best-effort]}` |
| `--deletion-protection` | string | none | `none`, `prevent-force-deletion`, `prevent-all-deletion` |

**Mixed Instances Policy Structure:**

```json
{
  "LaunchTemplate": {
    "LaunchTemplateSpecification": {
      "LaunchTemplateId": "string",
      "LaunchTemplateName": "string",
      "Version": "string"
    },
    "Overrides": [
      {
        "InstanceType": "string",
        "WeightedCapacity": "string",
        "LaunchTemplateSpecification": {},
        "InstanceRequirements": {
          "VCpuCount": { "Min": 0, "Max": 0 },
          "MemoryMiB": { "Min": 0, "Max": 0 },
          "CpuManufacturers": ["intel", "amd", "amazon-web-services"],
          "ExcludedInstanceTypes": ["string"],
          "InstanceGenerations": ["current", "previous"],
          "BareMetal": "included|excluded|required",
          "BurstablePerformance": "included|excluded|required",
          "LocalStorage": "included|excluded|required"
        }
      }
    ]
  },
  "InstancesDistribution": {
    "OnDemandAllocationStrategy": "lowest-price|prioritized",
    "OnDemandBaseCapacity": 0,
    "OnDemandPercentageAboveBaseCapacity": 100,
    "SpotAllocationStrategy": "capacity-optimized|capacity-optimized-prioritized|lowest-price|price-capacity-optimized",
    "SpotInstancePools": 2,
    "SpotMaxPrice": "string"
  }
}
```

#### Output Schema

**None** -- no output on success.

---

### 7.2 `aws autoscaling delete-auto-scaling-group`

**Description:** Deletes an Auto Scaling group. Use `--force-delete` to terminate instances and delete warm pools. Also deletes associated scaling policies and alarms.

#### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `--auto-scaling-group-name` | string | **Required** | ASG name (1-255 chars) |
| `--force-delete` / `--no-force-delete` | boolean | Optional | Force delete with running instances |

#### Output Schema

**None** -- no output on success.

---

### 7.3 `aws autoscaling describe-auto-scaling-groups`

**Description:** Gets information about Auto Scaling groups. Paginated.

#### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `--auto-scaling-group-names` | list(string) | Optional | Specific ASG names (max 50) |
| `--filters` | list(structure) | Optional | Tag filters: `tag-key`, `tag-value`, `tag:<key>` |
| `--include-instances` / `--no-include-instances` | boolean | Optional | Include instance details (default: true) |
| `--starting-token` | string | Optional | Pagination token |
| `--page-size` | integer | Optional | Items per API call |
| `--max-items` | integer | Optional | Max total items |

#### Output Schema

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
      "MixedInstancesPolicy": {
        "LaunchTemplate": { "LaunchTemplateSpecification": {}, "Overrides": [] },
        "InstancesDistribution": {}
      },
      "MinSize": 0,
      "MaxSize": 0,
      "DesiredCapacity": 0,
      "PredictedCapacity": 0,
      "DefaultCooldown": 300,
      "AvailabilityZones": ["string"],
      "LoadBalancerNames": ["string"],
      "TargetGroupARNs": ["string"],
      "HealthCheckType": "string",
      "HealthCheckGracePeriod": 0,
      "Instances": [
        {
          "InstanceId": "string",
          "InstanceType": "string",
          "AvailabilityZone": "string",
          "LifecycleState": "string",
          "HealthStatus": "string",
          "LaunchConfigurationName": "string",
          "LaunchTemplate": {},
          "ProtectedFromScaleIn": false,
          "WeightedCapacity": "string"
        }
      ],
      "CreatedTime": "timestamp",
      "SuspendedProcesses": [
        { "ProcessName": "string", "SuspensionReason": "string" }
      ],
      "PlacementGroup": "string",
      "VPCZoneIdentifier": "string",
      "EnabledMetrics": [{ "Metric": "string", "Granularity": "string" }],
      "Status": "string",
      "Tags": [
        {
          "ResourceId": "string",
          "ResourceType": "string",
          "Key": "string",
          "Value": "string",
          "PropagateAtLaunch": true
        }
      ],
      "TerminationPolicies": ["string"],
      "NewInstancesProtectedFromScaleIn": false,
      "ServiceLinkedRoleARN": "string",
      "MaxInstanceLifetime": 0,
      "CapacityRebalance": false,
      "WarmPoolSize": 0,
      "DesiredCapacityType": "string",
      "DefaultInstanceWarmup": 0,
      "DeletionProtection": "string"
    }
  ],
  "NextToken": "string"
}
```

---

### 7.4 `aws autoscaling update-auto-scaling-group`

**Description:** Updates an existing Auto Scaling group. Unspecified properties remain unchanged. New settings apply to subsequent scaling activities only; existing instances retain their original configuration.

#### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `--auto-scaling-group-name` | string | **Required** | ASG name |
| `--launch-configuration-name` | string | Optional | New launch configuration |
| `--launch-template` | structure | Optional | New launch template spec |
| `--mixed-instances-policy` | structure | Optional | New mixed instances policy |
| `--min-size` | integer | Optional | New minimum size |
| `--max-size` | integer | Optional | New maximum size |
| `--desired-capacity` | integer | Optional | New desired capacity |
| `--default-cooldown` | integer | Optional | New cooldown seconds |
| `--availability-zones` | list(string) | Optional | New AZs |
| `--health-check-type` | string | Optional | `EC2`, `EBS`, `ELB`, `VPC_LATTICE` |
| `--health-check-grace-period` | integer | Optional | New grace period |
| `--placement-group` | string | Optional | Placement group (empty to remove) |
| `--vpc-zone-identifier` | string | Optional | Comma-separated subnet IDs |
| `--termination-policies` | list(string) | Optional | New termination policies |
| `--new-instances-protected-from-scale-in` | boolean | Optional | Scale-in protection |
| `--service-linked-role-arn` | string | Optional | Service-linked role |
| `--max-instance-lifetime` | integer | Optional | Max instance lifetime |
| `--capacity-rebalance` | boolean | Optional | Spot rebalancing |
| `--desired-capacity-type` | string | Optional | `units`, `vcpu`, `memory-mib` |
| `--default-instance-warmup` | integer | Optional | Warmup period |
| `--instance-maintenance-policy` | structure | Optional | `{MinHealthyPercentage, MaxHealthyPercentage}` |
| `--availability-zone-distribution` | structure | Optional | Capacity distribution |
| `--deletion-protection` | string | Optional | Protection level |

#### Output Schema

**None** -- no output on success.

---

### 7.5 `aws autoscaling create-launch-configuration`

**Description:** Creates a launch configuration template for Auto Scaling. **Note:** AWS recommends using launch templates instead, as launch configurations do not support full EC2 functionality.

#### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `--launch-configuration-name` | string | **Required** | Name (1-255 chars, unique per region) |
| `--image-id` | string | Optional | AMI ID |
| `--instance-type` | string | Optional | Instance type |
| `--key-name` | string | Optional | Key pair name |
| `--security-groups` | list(string) | Optional | Security group IDs |
| `--user-data` | string | Optional | Base64-encoded user data (max 21,847 chars) |
| `--instance-id` | string | Optional | EC2 instance to use as template |
| `--iam-instance-profile` | string | Optional | IAM profile name or ARN |
| `--ebs-optimized` / `--no-ebs-optimized` | boolean | Optional | EBS optimization (default: false) |
| `--associate-public-ip-address` / `--no-associate-public-ip-address` | boolean | Optional | Public IP assignment |
| `--placement-tenancy` | string | Optional | `default` or `dedicated` |
| `--spot-price` | string | Optional | Max hourly Spot price |
| `--instance-monitoring` | structure | Optional | `{Enabled: bool}` (default: true) |
| `--block-device-mappings` | list(structure) | Optional | Block device config: `{DeviceName, Ebs: {SnapshotId, VolumeSize, VolumeType, DeleteOnTermination, Iops, Encrypted, Throughput}, VirtualName, NoDevice}` |
| `--metadata-options` | structure | Optional | `{HttpTokens: [optional/required], HttpPutResponseHopLimit: int, HttpEndpoint: [enabled/disabled]}` |

#### Output Schema

**None** -- no output on success.

---

### 7.6 `aws autoscaling delete-launch-configuration`

**Description:** Deletes a launch configuration. Must not be attached to any Auto Scaling group.

#### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `--launch-configuration-name` | string | **Required** | Name (1-255 chars) |

#### Output Schema

**None** -- no output on success.

---

### 7.7 `aws autoscaling describe-launch-configurations`

**Description:** Gets information about launch configurations. Paginated.

#### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `--launch-configuration-names` | list(string) | Optional | Specific names (max 50) |
| `--starting-token` | string | Optional | Pagination token |
| `--page-size` | integer | Optional | Items per API call |
| `--max-items` | integer | Optional | Max total items |

#### Output Schema

```json
{
  "LaunchConfigurations": [
    {
      "LaunchConfigurationName": "string",
      "LaunchConfigurationARN": "string",
      "ImageId": "string",
      "KeyName": "string",
      "SecurityGroups": ["string"],
      "UserData": "string",
      "InstanceType": "string",
      "BlockDeviceMappings": [
        {
          "DeviceName": "string",
          "Ebs": {
            "SnapshotId": "string",
            "VolumeSize": 0,
            "VolumeType": "string",
            "DeleteOnTermination": true,
            "Iops": 0,
            "Encrypted": false,
            "Throughput": 0
          },
          "VirtualName": "string",
          "NoDevice": false
        }
      ],
      "InstanceMonitoring": { "Enabled": true },
      "SpotPrice": "string",
      "IamInstanceProfile": "string",
      "CreatedTime": "timestamp",
      "EbsOptimized": false,
      "AssociatePublicIpAddress": false,
      "PlacementTenancy": "string",
      "MetadataOptions": {
        "HttpTokens": "optional|required",
        "HttpPutResponseHopLimit": 0,
        "HttpEndpoint": "disabled|enabled"
      }
    }
  ],
  "NextToken": "string"
}
```
