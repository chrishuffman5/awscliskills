# VPC Connections

VPC connections allow QuickSight to access data sources within a VPC.

### 14.1 `create-vpc-connection`

Creates a VPC connection.

**Synopsis:**
```bash
aws quicksight create-vpc-connection \
    --aws-account-id <value> \
    --vpc-connection-id <value> \
    --name <value> \
    --subnet-ids <value> \
    --security-group-ids <value> \
    --role-arn <value> \
    [--dns-resolvers <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-account-id` | **Yes** | string | -- | AWS account ID |
| `--vpc-connection-id` | **Yes** | string | -- | VPC connection ID |
| `--name` | **Yes** | string | -- | Display name |
| `--subnet-ids` | **Yes** | list(string) | -- | Subnet IDs (at least 2) |
| `--security-group-ids` | **Yes** | list(string) | -- | Security group IDs |
| `--role-arn` | **Yes** | string | -- | IAM role ARN for ENI creation |
| `--dns-resolvers` | No | list(string) | None | Custom DNS resolver IPs |
| `--tags` | No | list | None | Resource tags |

**Output Schema:**
```json
{
    "Arn": "string",
    "VPCConnectionId": "string",
    "CreationStatus": "CREATION_IN_PROGRESS|CREATION_SUCCESSFUL|CREATION_FAILED|UPDATE_IN_PROGRESS|UPDATE_SUCCESSFUL|UPDATE_FAILED|DELETION_IN_PROGRESS|DELETION_FAILED|DELETED",
    "AvailabilityStatus": "AVAILABLE|UNAVAILABLE|PARTIALLY_AVAILABLE",
    "RequestId": "string",
    "Status": "integer"
}
```

---

### 14.2 `describe-vpc-connection`

Describes a VPC connection.

**Synopsis:**
```bash
aws quicksight describe-vpc-connection \
    --aws-account-id <value> \
    --vpc-connection-id <value>
```

**Output Schema:**
```json
{
    "VPCConnection": {
        "VPCConnectionId": "string",
        "Arn": "string",
        "Name": "string",
        "VPCId": "string",
        "SecurityGroupIds": ["string"],
        "DnsResolvers": ["string"],
        "Status": "string",
        "AvailabilityStatus": "AVAILABLE|UNAVAILABLE|PARTIALLY_AVAILABLE",
        "NetworkInterfaces": [
            {
                "SubnetId": "string",
                "AvailabilityZone": "string",
                "ErrorMessage": "string",
                "Status": "string",
                "NetworkInterfaceId": "string"
            }
        ],
        "RoleArn": "string",
        "CreatedTime": "timestamp",
        "LastUpdatedTime": "timestamp"
    },
    "RequestId": "string",
    "Status": "integer"
}
```

---

### 14.3 `update-vpc-connection`

Updates a VPC connection.

**Synopsis:**
```bash
aws quicksight update-vpc-connection \
    --aws-account-id <value> \
    --vpc-connection-id <value> \
    --name <value> \
    --subnet-ids <value> \
    --security-group-ids <value> \
    --role-arn <value> \
    [--dns-resolvers <value>]
```

---

### 14.4 `delete-vpc-connection`

Deletes a VPC connection.

**Synopsis:**
```bash
aws quicksight delete-vpc-connection \
    --aws-account-id <value> \
    --vpc-connection-id <value>
```

---

### 14.5 `list-vpc-connections`

Lists VPC connections. **Paginated operation.**

**Synopsis:**
```bash
aws quicksight list-vpc-connections \
    --aws-account-id <value> \
    [--starting-token <value>] [--page-size <value>] [--max-items <value>]
```
