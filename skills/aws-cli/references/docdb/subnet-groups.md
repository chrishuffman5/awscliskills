# Subnet Groups

### 5.1 `create-db-subnet-group`

Creates a new DB subnet group. DB subnet groups must contain at least one subnet in at least two AZs.

**Synopsis:**
```bash
aws docdb create-db-subnet-group \
    --db-subnet-group-name <value> \
    --db-subnet-group-description <value> \
    --subnet-ids <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-subnet-group-name` | **Yes** | string | -- | Subnet group name |
| `--db-subnet-group-description` | **Yes** | string | -- | Description for the subnet group |
| `--subnet-ids` | **Yes** | list(string) | -- | List of subnet IDs |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "DBSubnetGroup": {
        "DBSubnetGroupName": "string",
        "DBSubnetGroupDescription": "string",
        "VpcId": "string",
        "SubnetGroupStatus": "string",
        "Subnets": [
            {
                "SubnetIdentifier": "string",
                "SubnetAvailabilityZone": {
                    "Name": "string"
                },
                "SubnetStatus": "string"
            }
        ],
        "DBSubnetGroupArn": "string"
    }
}
```

---

### 5.2 `delete-db-subnet-group`

Deletes a DB subnet group. The subnet group must not be associated with any clusters.

**Synopsis:**
```bash
aws docdb delete-db-subnet-group \
    --db-subnet-group-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-subnet-group-name` | **Yes** | string | -- | Subnet group name to delete |

**Output:** None (HTTP 200 on success)

---

### 5.3 `describe-db-subnet-groups`

Returns a list of DB subnet group descriptions. **Paginated operation.**

**Synopsis:**
```bash
aws docdb describe-db-subnet-groups \
    [--db-subnet-group-name <value>] \
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
| `--db-subnet-group-name` | No | string | All | Subnet group name |
| `--filters` | No | list | None | Filters |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "DBSubnetGroups": [
        {
            "DBSubnetGroupName": "string",
            "DBSubnetGroupDescription": "string",
            "VpcId": "string",
            "SubnetGroupStatus": "string",
            "Subnets": [
                {
                    "SubnetIdentifier": "string",
                    "SubnetAvailabilityZone": {
                        "Name": "string"
                    },
                    "SubnetStatus": "string"
                }
            ],
            "DBSubnetGroupArn": "string"
        }
    ],
    "Marker": "string"
}
```

---

### 5.4 `modify-db-subnet-group`

Modifies an existing DB subnet group.

**Synopsis:**
```bash
aws docdb modify-db-subnet-group \
    --db-subnet-group-name <value> \
    --subnet-ids <value> \
    [--db-subnet-group-description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-subnet-group-name` | **Yes** | string | -- | Subnet group name to modify |
| `--subnet-ids` | **Yes** | list(string) | -- | New list of subnet IDs |
| `--db-subnet-group-description` | No | string | -- | New description |

**Output Schema:** Same as `create-db-subnet-group` output.
