# Serverless VPC

### 12.1 `create-vpc-endpoint` (serverless)

Creates a VPC endpoint for OpenSearch Serverless.

**Synopsis:**
```bash
aws opensearchserverless create-vpc-endpoint \
    --name <value> \
    --vpc-id <value> \
    --subnet-ids <value> \
    [--security-group-ids <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | VPC endpoint name (3-32 chars) |
| `--vpc-id` | **Yes** | string | -- | VPC ID |
| `--subnet-ids` | **Yes** | list(string) | -- | Subnet IDs (1-6) |
| `--security-group-ids` | No | list(string) | None | Security group IDs (1-5) |
| `--client-token` | No | string | -- | Idempotency token |

**Output Schema:**
```json
{
    "createVpcEndpointDetail": {
        "id": "string",
        "name": "string",
        "status": "PENDING|DELETING|ACTIVE|FAILED"
    }
}
```

---

### 12.2 `delete-vpc-endpoint` (serverless)

Deletes a serverless VPC endpoint.

**Synopsis:**
```bash
aws opensearchserverless delete-vpc-endpoint \
    --id <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | VPC endpoint ID |

**Output Schema:**
```json
{
    "deleteVpcEndpointDetail": {
        "id": "string",
        "name": "string",
        "status": "DELETING"
    }
}
```

---

### 12.3 `batch-get-vpc-endpoint`

Returns details about multiple serverless VPC endpoints.

**Synopsis:**
```bash
aws opensearchserverless batch-get-vpc-endpoint \
    --ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--ids` | **Yes** | list(string) | -- | VPC endpoint IDs (1-100) |

**Output Schema:**
```json
{
    "vpcEndpointDetails": [
        {
            "id": "string",
            "name": "string",
            "vpcId": "string",
            "subnetIds": ["string"],
            "securityGroupIds": ["string"],
            "status": "PENDING|DELETING|ACTIVE|FAILED",
            "createdDate": "long"
        }
    ],
    "vpcEndpointErrorDetails": [
        {
            "id": "string",
            "errorCode": "string",
            "errorMessage": "string"
        }
    ]
}
```

---

### 12.4 `list-vpc-endpoints` (serverless)

Lists serverless VPC endpoints. **Paginated operation.**

**Synopsis:**
```bash
aws opensearchserverless list-vpc-endpoints \
    [--vpc-endpoint-filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--vpc-endpoint-filters` | No | structure | None | Filters. Shorthand: `status=PENDING\|DELETING\|ACTIVE\|FAILED` |

**Output Schema:**
```json
{
    "vpcEndpointSummaries": [
        {
            "id": "string",
            "name": "string",
            "status": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 12.5 `update-vpc-endpoint` (serverless)

Updates a serverless VPC endpoint (add/remove subnets and security groups).

**Synopsis:**
```bash
aws opensearchserverless update-vpc-endpoint \
    --id <value> \
    [--add-subnet-ids <value>] \
    [--remove-subnet-ids <value>] \
    [--add-security-group-ids <value>] \
    [--remove-security-group-ids <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | VPC endpoint ID |
| `--add-subnet-ids` | No | list(string) | None | Subnet IDs to add |
| `--remove-subnet-ids` | No | list(string) | None | Subnet IDs to remove |
| `--add-security-group-ids` | No | list(string) | None | Security group IDs to add |
| `--remove-security-group-ids` | No | list(string) | None | Security group IDs to remove |

**Output Schema:**
```json
{
    "UpdateVpcEndpointDetail": {
        "id": "string",
        "name": "string",
        "status": "PENDING",
        "subnetIds": ["string"],
        "securityGroupIds": ["string"],
        "lastModifiedDate": "long"
    }
}
```
