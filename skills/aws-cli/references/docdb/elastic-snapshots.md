# Elastic Snapshots (`aws docdb-elastic`)

### 9.1 `create-cluster-snapshot`

Creates a snapshot of an elastic cluster.

**Synopsis:**
```bash
aws docdb-elastic create-cluster-snapshot \
    --cluster-arn <value> \
    --snapshot-name <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-arn` | **Yes** | string | -- | ARN of the elastic cluster |
| `--snapshot-name` | **Yes** | string | -- | Name for the snapshot |
| `--tags` | No | map | None | Tags. Shorthand: `KeyName1=string,KeyName2=string` |

**Output Schema:**
```json
{
    "snapshot": {
        "snapshotName": "string",
        "snapshotArn": "string",
        "clusterArn": "string",
        "clusterCreationTime": "string",
        "snapshotCreationTime": "string",
        "status": "CREATING|ACTIVE|DELETING|UPDATING|VPC_ENDPOINT_LIMIT_EXCEEDED|IP_ADDRESS_LIMIT_EXCEEDED|INVALID_SECURITY_GROUP_ID|INVALID_SUBNET_ID|INACCESSIBLE_ENCRYPTION_CREDS|INACCESSIBLE_SECRET_ARN",
        "subnetIds": ["string"],
        "vpcSecurityGroupIds": ["string"],
        "adminUserName": "string",
        "kmsKeyId": "string",
        "snapshotType": "MANUAL|AUTOMATED"
    }
}
```

---

### 9.2 `delete-cluster-snapshot`

Deletes an elastic cluster snapshot.

**Synopsis:**
```bash
aws docdb-elastic delete-cluster-snapshot \
    --snapshot-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--snapshot-arn` | **Yes** | string | -- | ARN of the snapshot to delete |

**Output Schema:** Same as `create-cluster-snapshot` output.

---

### 9.3 `get-cluster-snapshot`

Returns information about a specific elastic cluster snapshot.

**Synopsis:**
```bash
aws docdb-elastic get-cluster-snapshot \
    --snapshot-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--snapshot-arn` | **Yes** | string | -- | ARN of the snapshot |

**Output Schema:** Same as `create-cluster-snapshot` output.

---

### 9.4 `list-cluster-snapshots`

Returns information about elastic cluster snapshots. **Paginated operation.**

**Synopsis:**
```bash
aws docdb-elastic list-cluster-snapshots \
    [--cluster-arn <value>] \
    [--snapshot-type <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-arn` | No | string | All | Filter by cluster ARN |
| `--snapshot-type` | No | string | All | Snapshot type: `MANUAL`, `AUTOMATED` |
| `--max-results` | No | integer | None | Maximum results per page (1-100) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "snapshots": [
        {
            "snapshotName": "string",
            "snapshotArn": "string",
            "clusterArn": "string",
            "snapshotCreationTime": "string",
            "status": "string",
            "snapshotType": "MANUAL|AUTOMATED"
        }
    ],
    "nextToken": "string"
}
```

---

### 9.5 `copy-cluster-snapshot`

Copies an elastic cluster snapshot. Can be used for cross-region copies.

**Synopsis:**
```bash
aws docdb-elastic copy-cluster-snapshot \
    --snapshot-arn <value> \
    --target-snapshot-name <value> \
    [--kms-key-id <value>] \
    [--copy-tags | --no-copy-tags] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--snapshot-arn` | **Yes** | string | -- | ARN of the source snapshot |
| `--target-snapshot-name` | **Yes** | string | -- | Name for the target snapshot |
| `--kms-key-id` | No | string | -- | KMS key for encryption of the copied snapshot |
| `--copy-tags` | No | boolean | false | Copy tags from source snapshot |
| `--tags` | No | map | None | Additional tags |

**Output Schema:** Same as `create-cluster-snapshot` output.
