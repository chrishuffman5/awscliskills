# Instance Management

### 2.1 `add-instance-groups`

Adds instance groups to a running cluster.

**Synopsis:**
```bash
aws emr add-instance-groups \
    --cluster-id <value> \
    --instance-groups <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | Cluster ID |
| `--instance-groups` | **Yes** | JSON/list | -- | Instance group definitions |

**Instance Group JSON:**
```json
[
    {
        "InstanceCount": 3,
        "InstanceGroupType": "TASK",
        "InstanceType": "m5.xlarge",
        "Name": "Task Group",
        "Market": "ON_DEMAND|SPOT",
        "BidPrice": "0.10",
        "EbsConfiguration": {
            "EbsBlockDeviceConfigs": [
                {
                    "VolumeSpecification": {
                        "VolumeType": "gp3",
                        "SizeInGB": 100,
                        "Iops": 3000,
                        "Throughput": 125
                    },
                    "VolumesPerInstance": 1
                }
            ]
        },
        "AutoScalingPolicy": {}
    }
]
```

**Output Schema:**
```json
{
    "InstanceGroupIds": ["string"],
    "ClusterArn": "string"
}
```

---

### 2.2 `modify-instance-groups`

Modifies the number of nodes and configuration settings of an instance group.

**Synopsis:**
```bash
aws emr modify-instance-groups \
    [--cluster-id <value>] \
    --instance-groups <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | No | string | -- | Cluster ID |
| `--instance-groups` | **Yes** | list | -- | Modifications. Shorthand: `InstanceGroupId=string,InstanceCount=integer,ShrinkPolicy={...}` |

No output on success.

---

### 2.3 `list-instance-groups`

Lists all instance groups in a cluster. **Paginated operation.**

**Synopsis:**
```bash
aws emr list-instance-groups \
    --cluster-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | Cluster ID |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "InstanceGroups": [
        {
            "Id": "string",
            "Name": "string",
            "Market": "ON_DEMAND|SPOT",
            "InstanceGroupType": "MASTER|CORE|TASK",
            "BidPrice": "string",
            "InstanceType": "string",
            "RequestedInstanceCount": "integer",
            "RunningInstanceCount": "integer",
            "Status": {
                "State": "PROVISIONING|BOOTSTRAPPING|RUNNING|RECONFIGURING|RESIZING|SUSPENDED|TERMINATING|TERMINATED|ARRESTED|SHUTTING_DOWN|ENDED",
                "StateChangeReason": {},
                "Timeline": {}
            },
            "EbsBlockDevices": [],
            "EbsOptimized": "boolean",
            "ShrinkPolicy": {},
            "AutoScalingPolicy": {},
            "CustomAmiId": "string"
        }
    ],
    "Marker": "string"
}
```

---

### 2.4 `add-instance-fleet`

Adds an instance fleet to a running cluster.

**Synopsis:**
```bash
aws emr add-instance-fleet \
    --cluster-id <value> \
    --instance-fleet <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | Cluster ID |
| `--instance-fleet` | **Yes** | structure | -- | Instance fleet configuration (JSON) |

**Instance Fleet JSON:**
```json
{
    "Name": "Task Fleet",
    "InstanceFleetType": "TASK",
    "TargetOnDemandCapacity": 2,
    "TargetSpotCapacity": 4,
    "InstanceTypeConfigs": [
        {
            "InstanceType": "m5.xlarge",
            "WeightedCapacity": 1,
            "BidPriceAsPercentageOfOnDemandPrice": 50
        },
        {
            "InstanceType": "m5.2xlarge",
            "WeightedCapacity": 2
        }
    ],
    "LaunchSpecifications": {
        "SpotSpecification": {
            "TimeoutDurationMinutes": 60,
            "TimeoutAction": "SWITCH_TO_ON_DEMAND|TERMINATE_CLUSTER",
            "AllocationStrategy": "capacity-optimized|price-capacity-optimized|lowest-price|diversified"
        },
        "OnDemandSpecification": {
            "AllocationStrategy": "lowest-price",
            "CapacityReservationOptions": {}
        }
    }
}
```

**Output Schema:**
```json
{
    "ClusterId": "string",
    "InstanceFleetId": "string",
    "ClusterArn": "string"
}
```

---

### 2.5 `modify-instance-fleet`

Modifies the target capacity of an instance fleet.

**Synopsis:**
```bash
aws emr modify-instance-fleet \
    --cluster-id <value> \
    --instance-fleet <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | Cluster ID |
| `--instance-fleet` | **Yes** | structure | -- | Fleet modification. Shorthand: `InstanceFleetId=string,TargetOnDemandCapacity=integer,TargetSpotCapacity=integer` |

No output on success.

---

### 2.6 `list-instance-fleets`

Lists all instance fleets in a cluster. **Paginated operation.**

**Synopsis:**
```bash
aws emr list-instance-fleets \
    --cluster-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | Cluster ID |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "InstanceFleets": [
        {
            "Id": "string",
            "Name": "string",
            "Status": {
                "State": "PROVISIONING|BOOTSTRAPPING|RUNNING|RESIZING|SUSPENDED|TERMINATING|TERMINATED",
                "StateChangeReason": {},
                "Timeline": {}
            },
            "InstanceFleetType": "MASTER|CORE|TASK",
            "TargetOnDemandCapacity": "integer",
            "TargetSpotCapacity": "integer",
            "ProvisionedOnDemandCapacity": "integer",
            "ProvisionedSpotCapacity": "integer",
            "InstanceTypeSpecifications": [
                {
                    "InstanceType": "string",
                    "WeightedCapacity": "integer",
                    "BidPrice": "string",
                    "BidPriceAsPercentageOfOnDemandPrice": "double"
                }
            ],
            "LaunchSpecifications": {}
        }
    ],
    "Marker": "string"
}
```

---

### 2.7 `list-instances`

Lists all instances in a cluster, optionally filtered. **Paginated operation.**

**Synopsis:**
```bash
aws emr list-instances \
    --cluster-id <value> \
    [--instance-group-id <value>] \
    [--instance-fleet-id <value>] \
    [--instance-group-types <value>] \
    [--instance-states <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-id` | **Yes** | string | -- | Cluster ID |
| `--instance-group-id` | No | string | -- | Filter by instance group |
| `--instance-fleet-id` | No | string | -- | Filter by instance fleet |
| `--instance-group-types` | No | list(string) | -- | Filter: `MASTER`, `CORE`, `TASK` |
| `--instance-states` | No | list(string) | -- | Filter: `AWAITING_FULFILLMENT`, `PROVISIONING`, `BOOTSTRAPPING`, `RUNNING`, `TERMINATED` |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "Instances": [
        {
            "Id": "string",
            "Ec2InstanceId": "string",
            "PublicDnsName": "string",
            "PublicIpAddress": "string",
            "PrivateDnsName": "string",
            "PrivateIpAddress": "string",
            "Status": {
                "State": "string",
                "StateChangeReason": {},
                "Timeline": {}
            },
            "InstanceGroupId": "string",
            "InstanceFleetId": "string",
            "Market": "ON_DEMAND|SPOT",
            "InstanceType": "string",
            "EbsVolumes": [
                {
                    "Device": "string",
                    "VolumeId": "string"
                }
            ]
        }
    ],
    "Marker": "string"
}
```
