# Replication Subnet Groups

### 4.1 `create-replication-subnet-group`

Creates a replication subnet group given a list of the subnet IDs in a VPC. The VPC must have at least one subnet in at least two availability zones.

**Synopsis:**
```bash
aws dms create-replication-subnet-group \
    --replication-subnet-group-identifier <value> \
    --replication-subnet-group-description <value> \
    --subnet-ids <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replication-subnet-group-identifier` | **Yes** | string | -- | Subnet group name (max 255 chars, cannot be `default`) |
| `--replication-subnet-group-description` | **Yes** | string | -- | Description for the subnet group |
| `--subnet-ids` | **Yes** | list(string) | -- | Two or more subnet IDs spanning multiple AZs |
| `--tags` | No | list | -- | Tags: `key=string,value=string ...` |

**Output Schema:**
```json
{
    "ReplicationSubnetGroup": {
        "ReplicationSubnetGroupIdentifier": "string",
        "ReplicationSubnetGroupDescription": "string",
        "VpcId": "string",
        "SubnetGroupStatus": "string",
        "Subnets": [
            {
                "SubnetIdentifier": "string",
                "SubnetAvailabilityZone": { "Name": "string" },
                "SubnetStatus": "string"
            }
        ],
        "SupportedNetworkTypes": ["string"],
        "IsReadOnly": "boolean"
    }
}
```

---

### 4.2 `delete-replication-subnet-group`

Deletes a subnet group.

**Synopsis:**
```bash
aws dms delete-replication-subnet-group \
    --replication-subnet-group-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replication-subnet-group-identifier` | **Yes** | string | -- | Identifier of the subnet group to delete |

**Output Schema:** None (HTTP 200 on success).

---

### 4.3 `describe-replication-subnet-groups`

Returns information about the replication subnet groups. **Paginated operation.**

**Synopsis:**
```bash
aws dms describe-replication-subnet-groups \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | list | -- | Filters: `replication-subnet-group-id` |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "Marker": "string",
    "ReplicationSubnetGroups": [
        {
            "ReplicationSubnetGroupIdentifier": "string",
            "ReplicationSubnetGroupDescription": "string",
            "VpcId": "string",
            "SubnetGroupStatus": "string",
            "Subnets": [
                {
                    "SubnetIdentifier": "string",
                    "SubnetAvailabilityZone": { "Name": "string" },
                    "SubnetStatus": "string"
                }
            ],
            "SupportedNetworkTypes": ["string"],
            "IsReadOnly": "boolean"
        }
    ]
}
```

---

### 4.4 `modify-replication-subnet-group`

Modifies the settings for an existing replication subnet group.

**Synopsis:**
```bash
aws dms modify-replication-subnet-group \
    --replication-subnet-group-identifier <value> \
    --subnet-ids <value> \
    [--replication-subnet-group-description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replication-subnet-group-identifier` | **Yes** | string | -- | Subnet group identifier |
| `--subnet-ids` | **Yes** | list(string) | -- | Updated list of subnet IDs |
| `--replication-subnet-group-description` | No | string | -- | Updated description |

**Output Schema:** Same as `create-replication-subnet-group`.
