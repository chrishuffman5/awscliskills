# VPC Endpoints

### 6.1 `create-vpc-endpoint-association`

Creates a VPC endpoint association for a firewall, allowing the firewall to inspect traffic in another VPC.

**Synopsis:**
```bash
aws network-firewall create-vpc-endpoint-association \
    --firewall-arn <value> \
    --vpc-id <value> \
    --subnet-mappings <value> \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--firewall-arn` | **Yes** | string | -- | ARN of the firewall |
| `--vpc-id` | **Yes** | string | -- | VPC ID for the endpoint association |
| `--subnet-mappings` | **Yes** | list | -- | Subnets for endpoints. Shorthand: `SubnetId=string,IPAddressType=DUALSTACK\|IPV4\|IPV6` |
| `--description` | No | string | None | Description (max 512 chars) |
| `--tags` | No | list | None | Tags (max 200) |

**Output Schema:**
```json
{
    "VpcEndpointAssociation": {
        "VpcEndpointAssociationId": "string",
        "VpcEndpointAssociationArn": "string",
        "FirewallArn": "string",
        "VpcId": "string",
        "SubnetMappings": [
            {
                "SubnetId": "string",
                "IPAddressType": "DUALSTACK|IPV4|IPV6"
            }
        ],
        "Description": "string",
        "Tags": []
    },
    "VpcEndpointAssociationStatus": {
        "Status": "PROVISIONING|READY|DELETING",
        "SyncStates": {}
    }
}
```

---

### 6.2 `delete-vpc-endpoint-association`

Deletes a VPC endpoint association.

**Synopsis:**
```bash
aws network-firewall delete-vpc-endpoint-association \
    --vpc-endpoint-association-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--vpc-endpoint-association-arn` | **Yes** | string | -- | ARN of the VPC endpoint association to delete |

**Output Schema:**
```json
{
    "VpcEndpointAssociation": {
        "VpcEndpointAssociationId": "string",
        "VpcEndpointAssociationArn": "string",
        "FirewallArn": "string",
        "VpcId": "string"
    },
    "VpcEndpointAssociationStatus": {
        "Status": "DELETING"
    }
}
```

---

### 6.3 `describe-vpc-endpoint-association`

Returns details about the specified VPC endpoint association.

**Synopsis:**
```bash
aws network-firewall describe-vpc-endpoint-association \
    --vpc-endpoint-association-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--vpc-endpoint-association-arn` | **Yes** | string | -- | ARN of the VPC endpoint association |

**Output Schema:**
```json
{
    "VpcEndpointAssociation": {
        "VpcEndpointAssociationId": "string",
        "VpcEndpointAssociationArn": "string",
        "FirewallArn": "string",
        "VpcId": "string",
        "SubnetMappings": [],
        "Description": "string",
        "Tags": []
    },
    "VpcEndpointAssociationStatus": {
        "Status": "PROVISIONING|READY|DELETING",
        "SyncStates": {}
    },
    "UpdateToken": "string"
}
```

---

### 6.4 `list-vpc-endpoint-associations`

Lists VPC endpoint associations for a firewall. **Paginated operation.**

**Synopsis:**
```bash
aws network-firewall list-vpc-endpoint-associations \
    --firewall-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--firewall-arn` | **Yes** | string | -- | ARN of the firewall |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "VpcEndpointAssociations": [
        {
            "VpcEndpointAssociationId": "string",
            "VpcEndpointAssociationArn": "string",
            "FirewallArn": "string",
            "VpcId": "string"
        }
    ],
    "NextToken": "string"
}
```
