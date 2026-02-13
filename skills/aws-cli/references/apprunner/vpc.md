# VPC

### 5.1 `create-vpc-connector`

Creates a VPC connector for App Runner to access resources in your VPC.

**Synopsis:**
```bash
aws apprunner create-vpc-connector \
    --vpc-connector-name <value> \
    --subnets <value> \
    [--security-groups <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--vpc-connector-name` | **Yes** | string | -- | Name for the VPC connector |
| `--subnets` | **Yes** | list | -- | List of subnet IDs |
| `--security-groups` | No | list | None | List of security group IDs |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "VpcConnector": {
        "VpcConnectorName": "string",
        "VpcConnectorArn": "string",
        "VpcConnectorRevision": "integer",
        "Subnets": ["string"],
        "SecurityGroups": ["string"],
        "Status": "ACTIVE|INACTIVE",
        "CreatedAt": "timestamp",
        "DeletedAt": "timestamp"
    }
}
```

---

### 5.2 `delete-vpc-connector`

Deletes a VPC connector.

**Synopsis:**
```bash
aws apprunner delete-vpc-connector \
    --vpc-connector-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--vpc-connector-arn` | **Yes** | string | -- | ARN of the VPC connector to delete |

**Output Schema:**
```json
{
    "VpcConnector": {
        "VpcConnectorName": "string",
        "VpcConnectorArn": "string",
        "VpcConnectorRevision": "integer",
        "Status": "INACTIVE"
    }
}
```

---

### 5.3 `describe-vpc-connector`

Returns a description of a VPC connector.

**Synopsis:**
```bash
aws apprunner describe-vpc-connector \
    --vpc-connector-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--vpc-connector-arn` | **Yes** | string | -- | ARN of the VPC connector |

**Output Schema:**
```json
{
    "VpcConnector": {
        "VpcConnectorName": "string",
        "VpcConnectorArn": "string",
        "VpcConnectorRevision": "integer",
        "Subnets": ["string"],
        "SecurityGroups": ["string"],
        "Status": "ACTIVE|INACTIVE",
        "CreatedAt": "timestamp",
        "DeletedAt": "timestamp"
    }
}
```

---

### 5.4 `list-vpc-connectors`

Lists VPC connectors. **Paginated operation.**

**Synopsis:**
```bash
aws apprunner list-vpc-connectors \
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
    "VpcConnectors": [
        {
            "VpcConnectorName": "string",
            "VpcConnectorArn": "string",
            "VpcConnectorRevision": "integer",
            "Subnets": ["string"],
            "SecurityGroups": ["string"],
            "Status": "ACTIVE|INACTIVE",
            "CreatedAt": "timestamp",
            "DeletedAt": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 5.5 `create-vpc-ingress-connection`

Creates a VPC ingress connection for private App Runner services.

**Synopsis:**
```bash
aws apprunner create-vpc-ingress-connection \
    --service-arn <value> \
    --vpc-ingress-connection-name <value> \
    --ingress-vpc-configuration <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-arn` | **Yes** | string | -- | ARN of the App Runner service |
| `--vpc-ingress-connection-name` | **Yes** | string | -- | Name for the VPC ingress connection |
| `--ingress-vpc-configuration` | **Yes** | structure | -- | VPC config. Shorthand: `VpcId=string,VpcEndpointId=string` |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "VpcIngressConnection": {
        "VpcIngressConnectionArn": "string",
        "VpcIngressConnectionName": "string",
        "ServiceArn": "string",
        "Status": "AVAILABLE|PENDING_CREATION|PENDING_UPDATE|PENDING_DELETION|FAILED_CREATION|FAILED_UPDATE|FAILED_DELETION|DELETED",
        "AccountId": "string",
        "DomainName": "string",
        "IngressVpcConfiguration": {
            "VpcId": "string",
            "VpcEndpointId": "string"
        },
        "CreatedAt": "timestamp",
        "DeletedAt": "timestamp"
    }
}
```

---

### 5.6 `delete-vpc-ingress-connection`

Deletes a VPC ingress connection.

**Synopsis:**
```bash
aws apprunner delete-vpc-ingress-connection \
    --vpc-ingress-connection-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--vpc-ingress-connection-arn` | **Yes** | string | -- | ARN of the VPC ingress connection to delete |

**Output Schema:**
```json
{
    "VpcIngressConnection": {
        "VpcIngressConnectionArn": "string",
        "VpcIngressConnectionName": "string",
        "ServiceArn": "string",
        "Status": "PENDING_DELETION"
    }
}
```

---

### 5.7 `describe-vpc-ingress-connection`

Returns a description of a VPC ingress connection.

**Synopsis:**
```bash
aws apprunner describe-vpc-ingress-connection \
    --vpc-ingress-connection-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--vpc-ingress-connection-arn` | **Yes** | string | -- | ARN of the VPC ingress connection |

**Output Schema:**
```json
{
    "VpcIngressConnection": {
        "VpcIngressConnectionArn": "string",
        "VpcIngressConnectionName": "string",
        "ServiceArn": "string",
        "Status": "AVAILABLE|PENDING_CREATION|PENDING_UPDATE|PENDING_DELETION|FAILED_CREATION|FAILED_UPDATE|FAILED_DELETION|DELETED",
        "AccountId": "string",
        "DomainName": "string",
        "IngressVpcConfiguration": {
            "VpcId": "string",
            "VpcEndpointId": "string"
        },
        "CreatedAt": "timestamp",
        "DeletedAt": "timestamp"
    }
}
```

---

### 5.8 `list-vpc-ingress-connections`

Lists VPC ingress connections. **Paginated operation.**

**Synopsis:**
```bash
aws apprunner list-vpc-ingress-connections \
    [--filter <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filter` | No | structure | None | Filter criteria. Shorthand: `ServiceArn=string,VpcEndpointId=string` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "VpcIngressConnectionSummaryList": [
        {
            "VpcIngressConnectionArn": "string",
            "ServiceArn": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 5.9 `update-vpc-ingress-connection`

Updates a VPC ingress connection.

**Synopsis:**
```bash
aws apprunner update-vpc-ingress-connection \
    --vpc-ingress-connection-arn <value> \
    --ingress-vpc-configuration <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--vpc-ingress-connection-arn` | **Yes** | string | -- | ARN of the VPC ingress connection to update |
| `--ingress-vpc-configuration` | **Yes** | structure | -- | Updated VPC config. Shorthand: `VpcId=string,VpcEndpointId=string` |

**Output Schema:**
```json
{
    "VpcIngressConnection": {
        "VpcIngressConnectionArn": "string",
        "VpcIngressConnectionName": "string",
        "ServiceArn": "string",
        "Status": "PENDING_UPDATE",
        "AccountId": "string",
        "DomainName": "string",
        "IngressVpcConfiguration": {
            "VpcId": "string",
            "VpcEndpointId": "string"
        },
        "CreatedAt": "timestamp"
    }
}
```
