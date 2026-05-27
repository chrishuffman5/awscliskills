# Replication Sets

### 6.1 `create-replication-set`

A replication set replicates and encrypts your data to the provided Regions with the provided KMS key.

**Synopsis:**
```bash
aws ssm-incidents create-replication-set \
    --regions <value> \
    [--client-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--regions` | **Yes** | map | -- | Regions to replicate to. Map of region name to config: `{"us-east-1":{"sseKmsKeyId":"DefaultKey"}}` |
| `--client-token` | No | string | None | Idempotency token |
| `--tags` | No | map | None | Tags |

**Output Schema:**
```json
{
    "arn": "string"
}
```

---

### 6.2 `delete-replication-set`

Deletes all Regions and the replication set.

**Synopsis:**
```bash
aws ssm-incidents delete-replication-set \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | Replication set ARN |

**Output Schema:**
```json
{}
```

---

### 6.3 `get-replication-set`

Get the replication set details.

**Synopsis:**
```bash
aws ssm-incidents get-replication-set \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | Replication set ARN |

**Output Schema:**
```json
{
    "replicationSet": {
        "arn": "string",
        "createdBy": "string",
        "createdTime": "timestamp",
        "deletionProtected": "boolean",
        "lastModifiedBy": "string",
        "regionMap": {
            "string": {
                "sseKmsKeyId": "string",
                "status": "ACTIVE|CREATING|UPDATING|DELETING|FAILED",
                "statusMessage": "string",
                "statusUpdateDateTime": "timestamp"
            }
        },
        "status": "ACTIVE|CREATING|UPDATING|DELETING|FAILED"
    }
}
```

---

### 6.4 `list-replication-sets`

Lists details about the replication set configured in your account. **Paginated operation.**

**Synopsis:**
```bash
aws ssm-incidents list-replication-sets \
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
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Maximum items |

**Output Schema:**
```json
{
    "replicationSetArns": ["string"],
    "nextToken": "string"
}
```

---

### 6.5 `update-replication-set`

Add or delete Regions from your replication set.

**Synopsis:**
```bash
aws ssm-incidents update-replication-set \
    --arn <value> \
    --actions <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | Replication set ARN |
| `--actions` | **Yes** | list | -- | Update actions (add or delete regions) |
| `--client-token` | No | string | None | Idempotency token |

**Actions Structure:**
```json
[
    {
        "addRegionAction": {
            "regionName": "string",
            "sseKmsKeyId": "string"
        }
    }
]
```
or
```json
[
    {
        "deleteRegionAction": {
            "regionName": "string"
        }
    }
]
```

**Output Schema:**
```json
{}
```
