# VPC Endpoints

### 5.1 `create-vpc-endpoint`

Creates a VPC endpoint for an OpenSearch Service domain.

**Synopsis:**
```bash
aws opensearch create-vpc-endpoint \
    --domain-arn <value> \
    --vpc-options <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-arn` | **Yes** | string | -- | ARN of the domain |
| `--vpc-options` | **Yes** | structure | -- | VPC config. Shorthand: `SubnetIds=string,string,SecurityGroupIds=string,string` |
| `--client-token` | No | string | -- | Idempotency token |

**Output Schema:**
```json
{
    "VpcEndpoint": {
        "VpcEndpointId": "string",
        "VpcEndpointOwner": "string",
        "DomainArn": "string",
        "VpcOptions": {
            "VPCId": "string",
            "SubnetIds": ["string"],
            "SecurityGroupIds": ["string"]
        },
        "Status": "CREATING|CREATE_FAILED|ACTIVE|UPDATING|UPDATE_FAILED|DELETING|DELETE_FAILED",
        "Endpoint": "string"
    }
}
```

---

### 5.2 `delete-vpc-endpoint`

Deletes a VPC endpoint.

**Synopsis:**
```bash
aws opensearch delete-vpc-endpoint \
    --vpc-endpoint-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--vpc-endpoint-id` | **Yes** | string | -- | VPC endpoint ID |

**Output Schema:**
```json
{
    "VpcEndpointSummary": {
        "VpcEndpointId": "string",
        "VpcEndpointOwner": "string",
        "DomainArn": "string",
        "Status": "DELETING"
    }
}
```

---

### 5.3 `describe-vpc-endpoints`

Describes one or more VPC endpoints.

**Synopsis:**
```bash
aws opensearch describe-vpc-endpoints \
    --vpc-endpoint-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--vpc-endpoint-ids` | **Yes** | list(string) | -- | VPC endpoint IDs to describe |

**Output Schema:**
```json
{
    "VpcEndpoints": [
        {
            "VpcEndpointId": "string",
            "VpcEndpointOwner": "string",
            "DomainArn": "string",
            "VpcOptions": {},
            "Status": "string",
            "Endpoint": "string"
        }
    ],
    "VpcEndpointErrors": [
        {
            "VpcEndpointId": "string",
            "ErrorCode": "ENDPOINT_NOT_FOUND|SERVER_ERROR",
            "ErrorMessage": "string"
        }
    ]
}
```

---

### 5.4 `list-vpc-endpoints-for-domain`

Lists VPC endpoints for a domain.

**Synopsis:**
```bash
aws opensearch list-vpc-endpoints-for-domain \
    --domain-name <value> \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Domain name |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "VpcEndpointSummaryList": [
        {
            "VpcEndpointId": "string",
            "VpcEndpointOwner": "string",
            "DomainArn": "string",
            "Status": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 5.5 `authorize-vpc-endpoint-access`

Authorizes an AWS account to access a VPC endpoint.

**Synopsis:**
```bash
aws opensearch authorize-vpc-endpoint-access \
    --domain-name <value> \
    [--account <value>] \
    [--service <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Domain name |
| `--account` | No | string | -- | AWS account ID to authorize |
| `--service` | No | structure | None | AWS service principal to authorize |

**Output Schema:**
```json
{
    "AuthorizedPrincipal": {
        "PrincipalType": "AWS_ACCOUNT|AWS_SERVICE",
        "Principal": "string"
    }
}
```

---

### 5.6 `revoke-vpc-endpoint-access`

Revokes VPC endpoint access for an AWS account.

**Synopsis:**
```bash
aws opensearch revoke-vpc-endpoint-access \
    --domain-name <value> \
    [--account <value>] \
    [--service <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Domain name |
| `--account` | No | string | -- | AWS account ID to revoke |
| `--service` | No | structure | None | AWS service principal to revoke |

**Output:** None

---

### 5.7 `list-vpc-endpoint-access`

Lists AWS accounts authorized to access a VPC endpoint.

**Synopsis:**
```bash
aws opensearch list-vpc-endpoint-access \
    --domain-name <value> \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Domain name |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "AuthorizedPrincipalList": [
        {
            "PrincipalType": "AWS_ACCOUNT|AWS_SERVICE",
            "Principal": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 5.8 `update-vpc-endpoint`

Updates a VPC endpoint configuration (subnets and security groups).

**Synopsis:**
```bash
aws opensearch update-vpc-endpoint \
    --vpc-endpoint-id <value> \
    --vpc-options <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--vpc-endpoint-id` | **Yes** | string | -- | VPC endpoint ID |
| `--vpc-options` | **Yes** | structure | -- | Updated VPC options |

**Output Schema:**
```json
{
    "VpcEndpoint": {
        "VpcEndpointId": "string",
        "VpcOptions": {},
        "Status": "UPDATING"
    }
}
```
