# Serverless Workgroups (`aws redshift-serverless`)

### 15.1 `create-workgroup`

Creates a serverless workgroup (compute resources for a namespace).

**Synopsis:**
```bash
aws redshift-serverless create-workgroup \
    --workgroup-name <value> \
    --namespace-name <value> \
    [--base-capacity <value>] \
    [--max-capacity <value>] \
    [--enhanced-vpc-routing | --no-enhanced-vpc-routing] \
    [--publicly-accessible | --no-publicly-accessible] \
    [--subnet-ids <value>] \
    [--security-group-ids <value>] \
    [--config-parameters <value>] \
    [--port <value>] \
    [--tags <value>] \
    [--price-performance-target <value>] \
    [--ip-address-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workgroup-name` | **Yes** | string | -- | Workgroup name (3-64 chars) |
| `--namespace-name` | **Yes** | string | -- | Namespace to associate |
| `--base-capacity` | No | integer | 128 | Base RPU capacity (8-512, in increments of 8) |
| `--max-capacity` | No | integer | -- | Maximum RPU capacity |
| `--enhanced-vpc-routing` | No | boolean | false | Enable enhanced VPC routing |
| `--publicly-accessible` | No | boolean | false | Enable public accessibility |
| `--subnet-ids` | No | list(string) | -- | VPC subnet IDs |
| `--security-group-ids` | No | list(string) | -- | Security group IDs |
| `--config-parameters` | No | list | -- | Configuration parameters. Shorthand: `parameterKey=string,parameterValue=string ...` |
| `--port` | No | integer | 5439 | Database port |
| `--tags` | No | list | -- | Tags |
| `--price-performance-target` | No | structure | -- | Price-performance target. Shorthand: `level=integer,status=ENABLED\|DISABLED` |
| `--ip-address-type` | No | string | -- | IP address type: `ipv4`, `dualstack` |

**Config Parameter Keys:**
- `datestyle` — Date display format
- `enable_user_activity_logging` — Enable user activity logging
- `query_group` — Default query group
- `search_path` — Schema search path
- `max_query_execution_time` — Max query execution time in seconds
- `auto_mv` — Automatic materialized views
- `enable_case_sensitive_identifier` — Case-sensitive identifiers

**Output Schema:**
```json
{
    "workgroup": {
        "workgroupName": "string",
        "workgroupId": "string",
        "workgroupArn": "string",
        "namespaceName": "string",
        "status": "CREATING|AVAILABLE|MODIFYING|DELETING",
        "baseCapacity": "integer",
        "maxCapacity": "integer",
        "enhancedVpcRouting": "boolean",
        "publiclyAccessible": "boolean",
        "subnetIds": ["string"],
        "securityGroupIds": ["string"],
        "configParameters": [
            {
                "parameterKey": "string",
                "parameterValue": "string"
            }
        ],
        "endpoint": {
            "address": "string",
            "port": "integer",
            "vpcEndpoints": [
                {
                    "vpcEndpointId": "string",
                    "vpcId": "string",
                    "networkInterfaces": [
                        {
                            "networkInterfaceId": "string",
                            "subnetId": "string",
                            "privateIpAddress": "string",
                            "availabilityZone": "string"
                        }
                    ]
                }
            ]
        },
        "creationDate": "timestamp",
        "port": "integer",
        "ipAddressType": "string",
        "pricePerformanceTarget": {
            "level": "integer",
            "status": "ENABLED|DISABLED"
        }
    }
}
```

---

### 15.2 `delete-workgroup`

Deletes a serverless workgroup.

**Synopsis:**
```bash
aws redshift-serverless delete-workgroup \
    --workgroup-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workgroup-name` | **Yes** | string | -- | Workgroup to delete |

**Output Schema:**
```json
{
    "workgroup": {
        "workgroupName": "string",
        "workgroupId": "string",
        "status": "DELETING"
    }
}
```

---

### 15.3 `get-workgroup`

Returns information about a workgroup.

**Synopsis:**
```bash
aws redshift-serverless get-workgroup \
    --workgroup-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workgroup-name` | **Yes** | string | -- | Workgroup to describe |

**Output Schema:**
```json
{
    "workgroup": {
        "workgroupName": "string",
        "workgroupId": "string",
        "workgroupArn": "string",
        "namespaceName": "string",
        "status": "string",
        "baseCapacity": "integer",
        "maxCapacity": "integer",
        "enhancedVpcRouting": "boolean",
        "publiclyAccessible": "boolean",
        "subnetIds": ["string"],
        "securityGroupIds": ["string"],
        "configParameters": [],
        "endpoint": {},
        "creationDate": "timestamp",
        "port": "integer"
    }
}
```

---

### 15.4 `list-workgroups`

Lists all serverless workgroups. **Paginated operation.**

**Synopsis:**
```bash
aws redshift-serverless list-workgroups \
    [--next-token <value>] \
    [--max-results <value>] \
    [--owner-account <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--next-token` | No | string | -- | Pagination token |
| `--max-results` | No | integer | -- | Maximum results (1-100) |
| `--owner-account` | No | string | -- | Filter by owner account |

**Output Schema:**
```json
{
    "workgroups": [
        {
            "workgroupName": "string",
            "workgroupId": "string",
            "workgroupArn": "string",
            "namespaceName": "string",
            "status": "string",
            "baseCapacity": "integer",
            "endpoint": {}
        }
    ],
    "nextToken": "string"
}
```

---

### 15.5 `update-workgroup`

Updates a serverless workgroup.

**Synopsis:**
```bash
aws redshift-serverless update-workgroup \
    --workgroup-name <value> \
    [--base-capacity <value>] \
    [--max-capacity <value>] \
    [--enhanced-vpc-routing | --no-enhanced-vpc-routing] \
    [--publicly-accessible | --no-publicly-accessible] \
    [--subnet-ids <value>] \
    [--security-group-ids <value>] \
    [--config-parameters <value>] \
    [--port <value>] \
    [--price-performance-target <value>] \
    [--ip-address-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workgroup-name` | **Yes** | string | -- | Workgroup to update |
| `--base-capacity` | No | integer | -- | New base RPU capacity |
| `--max-capacity` | No | integer | -- | New max RPU capacity |
| `--enhanced-vpc-routing` | No | boolean | -- | Update enhanced VPC routing |
| `--publicly-accessible` | No | boolean | -- | Update public accessibility |
| `--subnet-ids` | No | list(string) | -- | New subnet IDs |
| `--security-group-ids` | No | list(string) | -- | New security group IDs |
| `--config-parameters` | No | list | -- | Updated config parameters |
| `--port` | No | integer | -- | New port |
| `--price-performance-target` | No | structure | -- | Updated price-performance target |
| `--ip-address-type` | No | string | -- | IP address type |

**Output Schema:**
```json
{
    "workgroup": {
        "workgroupName": "string",
        "workgroupId": "string",
        "status": "MODIFYING",
        "baseCapacity": "integer",
        "maxCapacity": "integer",
        "enhancedVpcRouting": "boolean",
        "publiclyAccessible": "boolean",
        "configParameters": [],
        "endpoint": {}
    }
}
```

---

### 15.6 `create-endpoint-access`

Creates a VPC endpoint for a serverless workgroup.

**Synopsis:**
```bash
aws redshift-serverless create-endpoint-access \
    --endpoint-name <value> \
    --workgroup-name <value> \
    --subnet-ids <value> \
    [--vpc-security-group-ids <value>] \
    [--owner-account <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-name` | **Yes** | string | -- | Endpoint name |
| `--workgroup-name` | **Yes** | string | -- | Workgroup to create endpoint for |
| `--subnet-ids` | **Yes** | list(string) | -- | Subnet IDs for the endpoint |
| `--vpc-security-group-ids` | No | list(string) | -- | Security group IDs |
| `--owner-account` | No | string | -- | Owner account |

**Output Schema:**
```json
{
    "endpoint": {
        "endpointName": "string",
        "endpointArn": "string",
        "endpointStatus": "CREATING|ACTIVE|DELETING|UPDATING",
        "workgroupName": "string",
        "port": "integer",
        "address": "string",
        "subnetIds": ["string"],
        "vpcSecurityGroups": [
            {
                "vpcSecurityGroupId": "string",
                "status": "string"
            }
        ],
        "vpcEndpoint": {
            "vpcEndpointId": "string",
            "vpcId": "string",
            "networkInterfaces": []
        },
        "endpointCreateTime": "timestamp"
    }
}
```

---

### 15.7 `delete-endpoint-access`

Deletes a VPC endpoint for a serverless workgroup.

**Synopsis:**
```bash
aws redshift-serverless delete-endpoint-access \
    --endpoint-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-name` | **Yes** | string | -- | Endpoint to delete |

**Output Schema:**
```json
{
    "endpoint": {
        "endpointName": "string",
        "endpointStatus": "DELETING"
    }
}
```

---

### 15.8 `get-endpoint-access`

Returns information about a VPC endpoint.

**Synopsis:**
```bash
aws redshift-serverless get-endpoint-access \
    --endpoint-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-name` | **Yes** | string | -- | Endpoint to describe |

**Output Schema:**
```json
{
    "endpoint": {
        "endpointName": "string",
        "endpointArn": "string",
        "endpointStatus": "string",
        "workgroupName": "string",
        "port": "integer",
        "address": "string",
        "subnetIds": ["string"],
        "vpcSecurityGroups": [],
        "vpcEndpoint": {}
    }
}
```

---

### 15.9 `list-endpoint-access`

Lists VPC endpoints. **Paginated operation.**

**Synopsis:**
```bash
aws redshift-serverless list-endpoint-access \
    [--workgroup-name <value>] \
    [--vpc-id <value>] \
    [--owner-account <value>] \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workgroup-name` | No | string | -- | Filter by workgroup |
| `--vpc-id` | No | string | -- | Filter by VPC |
| `--owner-account` | No | string | -- | Filter by owner account |
| `--next-token` | No | string | -- | Pagination token |
| `--max-results` | No | integer | -- | Maximum results |

**Output Schema:**
```json
{
    "endpoints": [
        {
            "endpointName": "string",
            "endpointArn": "string",
            "endpointStatus": "string",
            "workgroupName": "string",
            "port": "integer",
            "address": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 15.10 `update-endpoint-access`

Updates a VPC endpoint.

**Synopsis:**
```bash
aws redshift-serverless update-endpoint-access \
    --endpoint-name <value> \
    [--vpc-security-group-ids <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-name` | **Yes** | string | -- | Endpoint to update |
| `--vpc-security-group-ids` | No | list(string) | -- | New security group IDs |

**Output Schema:**
```json
{
    "endpoint": {
        "endpointName": "string",
        "endpointStatus": "UPDATING",
        "vpcSecurityGroups": []
    }
}
```
