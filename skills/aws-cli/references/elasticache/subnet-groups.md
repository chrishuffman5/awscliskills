# Subnet Groups

### 4.1 `create-cache-subnet-group`

Creates a new cache subnet group. A subnet group is a collection of subnets that you can designate for your cache clusters in a VPC.

**Synopsis:**
```bash
aws elasticache create-cache-subnet-group \
    --cache-subnet-group-name <value> \
    --cache-subnet-group-description <value> \
    --subnet-ids <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cache-subnet-group-name` | **Yes** | string | -- | Name for the subnet group |
| `--cache-subnet-group-description` | **Yes** | string | -- | Description of the subnet group |
| `--subnet-ids` | **Yes** | list(string) | -- | List of VPC subnet IDs |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "CacheSubnetGroup": {
        "CacheSubnetGroupName": "string",
        "CacheSubnetGroupDescription": "string",
        "VpcId": "string",
        "Subnets": [
            {
                "SubnetIdentifier": "string",
                "SubnetAvailabilityZone": {
                    "Name": "string"
                },
                "SubnetOutpost": {
                    "SubnetOutpostArn": "string"
                },
                "SupportedNetworkTypes": ["ipv4", "ipv6", "dual_stack"]
            }
        ],
        "ARN": "string",
        "SupportedNetworkTypes": ["ipv4", "ipv6", "dual_stack"]
    }
}
```

---

### 4.2 `delete-cache-subnet-group`

Deletes a cache subnet group. Cannot delete a group that is associated with any cache clusters.

**Synopsis:**
```bash
aws elasticache delete-cache-subnet-group \
    --cache-subnet-group-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cache-subnet-group-name` | **Yes** | string | -- | Name of the subnet group to delete |

**Output:** None on success.

---

### 4.3 `describe-cache-subnet-groups`

Returns a list of cache subnet group descriptions. **Paginated operation.**

**Synopsis:**
```bash
aws elasticache describe-cache-subnet-groups \
    [--cache-subnet-group-name <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cache-subnet-group-name` | No | string | -- | Specific subnet group to describe |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "CacheSubnetGroups": [
        {
            "CacheSubnetGroupName": "string",
            "CacheSubnetGroupDescription": "string",
            "VpcId": "string",
            "Subnets": [
                {
                    "SubnetIdentifier": "string",
                    "SubnetAvailabilityZone": {
                        "Name": "string"
                    },
                    "SubnetOutpost": {
                        "SubnetOutpostArn": "string"
                    },
                    "SupportedNetworkTypes": ["string"]
                }
            ],
            "ARN": "string",
            "SupportedNetworkTypes": ["string"]
        }
    ],
    "NextToken": "string"
}
```

---

### 4.4 `modify-cache-subnet-group`

Modifies an existing cache subnet group. Can update the description or the list of subnets.

**Synopsis:**
```bash
aws elasticache modify-cache-subnet-group \
    --cache-subnet-group-name <value> \
    [--cache-subnet-group-description <value>] \
    [--subnet-ids <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cache-subnet-group-name` | **Yes** | string | -- | Name of the subnet group to modify |
| `--cache-subnet-group-description` | No | string | -- | New description |
| `--subnet-ids` | No | list(string) | -- | New list of subnet IDs (replaces existing) |

**Output Schema:** Same as `create-cache-subnet-group` output.
