# Launch Configurations

> **Note:** Launch configurations are a legacy feature. AWS recommends using launch templates instead.

### 2.1 `create-launch-configuration`

Creates a launch configuration. If you exceed your maximum limit of launch configurations, the call fails.

**Synopsis:**
```bash
aws autoscaling create-launch-configuration \
    --launch-configuration-name <value> \
    [--image-id <value>] \
    [--key-name <value>] \
    [--security-groups <value>] \
    [--classic-link-vpc-id <value>] \
    [--classic-link-vpc-security-groups <value>] \
    [--user-data <value>] \
    [--instance-id <value>] \
    [--instance-type <value>] \
    [--kernel-id <value>] \
    [--ramdisk-id <value>] \
    [--block-device-mappings <value>] \
    [--instance-monitoring <value>] \
    [--spot-price <value>] \
    [--iam-instance-profile <value>] \
    [--ebs-optimized | --no-ebs-optimized] \
    [--associate-public-ip-address | --no-associate-public-ip-address] \
    [--placement-tenancy <value>] \
    [--metadata-options <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--launch-configuration-name` | **Yes** | string | -- | Name of the launch configuration (1-255 chars) |
| `--image-id` | No | string | None | AMI ID (required unless instance-id specified) |
| `--key-name` | No | string | None | EC2 key pair name |
| `--security-groups` | No | list(string) | None | Security group IDs |
| `--user-data` | No | string | None | Base64-encoded user data |
| `--instance-id` | No | string | None | Instance ID to derive config from |
| `--instance-type` | No | string | `m1.small` | EC2 instance type |
| `--block-device-mappings` | No | list | None | Block device mappings |
| `--instance-monitoring` | No | structure | `Enabled=true` | Instance monitoring. Shorthand: `Enabled=boolean` |
| `--spot-price` | No | string | None | Maximum Spot price |
| `--iam-instance-profile` | No | string | None | IAM instance profile name or ARN |
| `--ebs-optimized` | No | boolean | false | EBS-optimized instances |
| `--associate-public-ip-address` | No | boolean | None | Associate public IP (VPC only) |
| `--placement-tenancy` | No | string | None | `default`, `dedicated` |
| `--metadata-options` | No | structure | None | Instance metadata options |

**Output:** No output on success.

---

### 2.2 `delete-launch-configuration`

Deletes the specified launch configuration.

**Synopsis:**
```bash
aws autoscaling delete-launch-configuration \
    --launch-configuration-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--launch-configuration-name` | **Yes** | string | -- | Name of the launch configuration |

**Output:** No output on success.

---

### 2.3 `describe-launch-configurations`

Describes one or more launch configurations. **Paginated operation.**

**Synopsis:**
```bash
aws autoscaling describe-launch-configurations \
    [--launch-configuration-names <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--launch-configuration-names` | No | list(string) | None | Launch configuration names |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "LaunchConfigurations": [
        {
            "LaunchConfigurationName": "string",
            "LaunchConfigurationARN": "string",
            "ImageId": "string",
            "KeyName": "string",
            "SecurityGroups": ["string"],
            "ClassicLinkVPCId": "string",
            "ClassicLinkVPCSecurityGroups": ["string"],
            "UserData": "string",
            "InstanceType": "string",
            "KernelId": "string",
            "RamdiskId": "string",
            "BlockDeviceMappings": [
                {
                    "VirtualName": "string",
                    "DeviceName": "string",
                    "Ebs": {
                        "SnapshotId": "string",
                        "VolumeSize": "integer",
                        "VolumeType": "string",
                        "DeleteOnTermination": true|false,
                        "Iops": "integer",
                        "Encrypted": true|false,
                        "Throughput": "integer"
                    },
                    "NoDevice": true|false
                }
            ],
            "InstanceMonitoring": {
                "Enabled": true|false
            },
            "SpotPrice": "string",
            "IamInstanceProfile": "string",
            "CreatedTime": "timestamp",
            "EbsOptimized": true|false,
            "AssociatePublicIpAddress": true|false,
            "PlacementTenancy": "string",
            "MetadataOptions": {
                "HttpTokens": "optional|required",
                "HttpPutResponseHopLimit": "integer",
                "HttpEndpoint": "disabled|enabled"
            }
        }
    ],
    "NextToken": "string"
}
```
