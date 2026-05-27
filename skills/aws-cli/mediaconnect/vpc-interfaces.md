# VPC Interfaces

### 6.1 `add-flow-vpc-interfaces`

Adds VPC interfaces to a flow for private connectivity.

**Synopsis:**
```bash
aws mediaconnect add-flow-vpc-interfaces \
    --flow-arn <value> \
    --vpc-interfaces <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--flow-arn` | **Yes** | string | -- | ARN of the flow |
| `--vpc-interfaces` | **Yes** | list | -- | VPC interface configurations |

**VpcInterface Structure:**

| Field | Required | Type | Description |
|-------|----------|------|-------------|
| `Name` | **Yes** | string | Interface name (unique within flow) |
| `SubnetId` | **Yes** | string | VPC subnet ID |
| `SecurityGroupIds` | **Yes** | list | Security group IDs |
| `RoleArn` | **Yes** | string | IAM role ARN for ENI management |
| `NetworkInterfaceType` | No | string | `ena` (default) or `efa` |

**Output Schema:**
```json
{
    "FlowArn": "string",
    "VpcInterfaces": [
        {
            "Name": "string",
            "SubnetId": "string",
            "SecurityGroupIds": ["string"],
            "RoleArn": "string",
            "NetworkInterfaceIds": ["string"],
            "NetworkInterfaceType": "ena|efa"
        }
    ]
}
```

---

### 6.2 `remove-flow-vpc-interface`

Removes a VPC interface from a flow.

**Synopsis:**
```bash
aws mediaconnect remove-flow-vpc-interface \
    --flow-arn <value> \
    --vpc-interface-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--flow-arn` | **Yes** | string | -- | ARN of the flow |
| `--vpc-interface-name` | **Yes** | string | -- | Name of the VPC interface to remove |

**Output Schema:**
```json
{
    "FlowArn": "string",
    "NonDeletedNetworkInterfaceIds": ["string"],
    "VpcInterfaceName": "string"
}
```
