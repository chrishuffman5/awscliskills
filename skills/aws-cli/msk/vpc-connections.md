# VPC Connections

## 6.1 `create-vpc-connection`

Creates a new VPC connection to an MSK cluster.

**Synopsis:**
```bash
aws kafka create-vpc-connection \
    --target-cluster-arn <value> \
    --authentication <value> \
    --vpc-id <value> \
    --client-subnets <value> \
    --security-groups <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--target-cluster-arn` | **Yes** | string | -- | ARN of the target cluster |
| `--authentication` | **Yes** | string | -- | Authentication type for the VPC connection |
| `--vpc-id` | **Yes** | string | -- | VPC ID for the connection |
| `--client-subnets` | **Yes** | list(string) | -- | Client subnet IDs |
| `--security-groups` | **Yes** | list(string) | -- | Security group IDs |
| `--tags` | No | map | None | Key-value tags |

**Output Schema:**
```json
{
    "VpcConnectionArn": "string",
    "State": "CREATING|AVAILABLE|INACTIVE|DEACTIVATING|DELETING|FAILED|REJECTED|REJECTING",
    "Authentication": "string",
    "VpcId": "string",
    "ClientSubnets": ["string"],
    "SecurityGroups": ["string"],
    "CreationTime": "timestamp",
    "Tags": { "string": "string" }
}
```

---

## 6.2 `delete-vpc-connection`

Deletes a VPC connection.

**Synopsis:**
```bash
aws kafka delete-vpc-connection \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the VPC connection to delete |

**Output Schema:**
```json
{
    "VpcConnectionArn": "string",
    "State": "CREATING|AVAILABLE|INACTIVE|DEACTIVATING|DELETING|FAILED|REJECTED|REJECTING"
}
```

---

## 6.3 `describe-vpc-connection`

Returns details for the specified VPC connection.

**Synopsis:**
```bash
aws kafka describe-vpc-connection \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the VPC connection |

**Output Schema:**
```json
{
    "VpcConnectionArn": "string",
    "TargetClusterArn": "string",
    "State": "CREATING|AVAILABLE|INACTIVE|DEACTIVATING|DELETING|FAILED|REJECTED|REJECTING",
    "Authentication": "string",
    "VpcId": "string",
    "Subnets": ["string"],
    "SecurityGroups": ["string"],
    "CreationTime": "timestamp",
    "Tags": { "string": "string" }
}
```

---

## 6.4 `list-vpc-connections`

Lists all VPC connections in the account. **Paginated operation.**

**Synopsis:**
```bash
aws kafka list-vpc-connections \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "VpcConnections": [
        {
            "VpcConnectionArn": "string",
            "TargetClusterArn": "string",
            "CreationTime": "timestamp",
            "Authentication": "string",
            "VpcId": "string",
            "State": "string"
        }
    ],
    "NextToken": "string"
}
```

---

## 6.5 `list-client-vpc-connections`

Lists client VPC connections for a specific cluster. **Paginated operation.**

**Synopsis:**
```bash
aws kafka list-client-vpc-connections \
    --cluster-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-arn` | **Yes** | string | -- | ARN of the cluster |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ClientVpcConnections": [
        {
            "Authentication": "string",
            "CreationTime": "timestamp",
            "Owner": "string",
            "State": "string",
            "VpcConnectionArn": "string"
        }
    ],
    "NextToken": "string"
}
```

---

## 6.6 `reject-client-vpc-connection`

Rejects a client VPC connection request.

**Synopsis:**
```bash
aws kafka reject-client-vpc-connection \
    --cluster-arn <value> \
    --vpc-connection-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-arn` | **Yes** | string | -- | ARN of the cluster |
| `--vpc-connection-arn` | **Yes** | string | -- | ARN of the VPC connection to reject |

**Output Schema:**

None (HTTP 200 on success).
