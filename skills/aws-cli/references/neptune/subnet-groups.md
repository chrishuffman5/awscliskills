# Subnet Groups

### 6.1 `create-db-subnet-group`

Creates a new Neptune DB subnet group.

**Synopsis:**
```bash
aws neptune create-db-subnet-group \
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
| `--db-subnet-group-description` | **Yes** | string | -- | Description |
| `--subnet-ids` | **Yes** | list(string) | -- | List of subnet IDs |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "DBSubnetGroup": {
        "DBSubnetGroupName": "string",
        "DBSubnetGroupDescription": "string",
        "VpcId": "string",
        "SubnetGroupStatus": "Complete",
        "Subnets": [
            {
                "SubnetIdentifier": "string",
                "SubnetAvailabilityZone": {"Name": "string"},
                "SubnetStatus": "string"
            }
        ],
        "DBSubnetGroupArn": "string"
    }
}
```

---

### 6.2 `modify-db-subnet-group`

Modifies a Neptune DB subnet group.

**Synopsis:**
```bash
aws neptune modify-db-subnet-group \
    --db-subnet-group-name <value> \
    [--db-subnet-group-description <value>] \
    --subnet-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-subnet-group-name` | **Yes** | string | -- | Subnet group name |
| `--db-subnet-group-description` | No | string | -- | Updated description |
| `--subnet-ids` | **Yes** | list(string) | -- | Updated list of subnet IDs |

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
                "SubnetAvailabilityZone": {"Name": "string"},
                "SubnetStatus": "string"
            }
        ],
        "DBSubnetGroupArn": "string"
    }
}
```

---

### 6.3 `delete-db-subnet-group`

Deletes a Neptune DB subnet group.

**Synopsis:**
```bash
aws neptune delete-db-subnet-group \
    --db-subnet-group-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--db-subnet-group-name` | **Yes** | string | -- | Subnet group name |

**Output:** None

---

### 6.4 `describe-db-subnet-groups`

Describes Neptune DB subnet groups. **Paginated operation.**

**Synopsis:**
```bash
aws neptune describe-db-subnet-groups \
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
| `--db-subnet-group-name` | No | string | -- | Specific subnet group to describe |
| `--filters` | No | list | None | Filters |

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
                    "SubnetAvailabilityZone": {"Name": "string"},
                    "SubnetStatus": "string"
                }
            ],
            "DBSubnetGroupArn": "string"
        }
    ]
}
```
