# Subnet Groups

### 5.1 `create-db-subnet-group`

Creates a DB subnet group.

**Synopsis:**
```bash
aws rds create-db-subnet-group \
    --db-subnet-group-name <value> \
    --db-subnet-group-description <value> \
    --subnet-ids <value> \
    [--tags <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--db-subnet-group-name` | **Yes** | string | Subnet group name (1-255 chars, lowercase) |
| `--db-subnet-group-description` | **Yes** | string | Description |
| `--subnet-ids` | **Yes** | list | VPC subnet IDs (at least 2 AZs) |
| `--tags` | No | list | Tags |

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
                "SubnetAvailabilityZone": { "Name": "string" },
                "SubnetOutpost": { "Arn": "string" },
                "SubnetStatus": "string"
            }
        ],
        "DBSubnetGroupArn": "string",
        "SupportedNetworkTypes": ["string"]
    }
}
```

---

### 5.2 `delete-db-subnet-group`

Deletes a DB subnet group.

```bash
aws rds delete-db-subnet-group \
    --db-subnet-group-name <value>
```

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--db-subnet-group-name` | **Yes** | string | Subnet group name |

**Output:** None on success.

---

### 5.3 `describe-db-subnet-groups`

Describes DB subnet groups. **Paginated.**

```bash
aws rds describe-db-subnet-groups \
    [--db-subnet-group-name <value>] \
    [--filters <value>] \
    [--max-items <value>] \
    [--starting-token <value>]
```

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-subnet-group-name` | No | string | all | Specific group |
| `--filters` | No | list | None | Filters |
| `--max-items` | No | integer | None | Total items |
| `--starting-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "DBSubnetGroups": [
        { "...same DBSubnetGroup structure..." }
    ],
    "Marker": "string"
}
```

---

### 5.4 `modify-db-subnet-group`

Modifies a DB subnet group.

```bash
aws rds modify-db-subnet-group \
    --db-subnet-group-name <value> \
    --subnet-ids <value> \
    [--db-subnet-group-description <value>]
```

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--db-subnet-group-name` | **Yes** | string | Subnet group name |
| `--subnet-ids` | **Yes** | list | New set of subnet IDs |
| `--db-subnet-group-description` | No | string | New description |

**Output Schema:** Same `DBSubnetGroup` structure.

---
