# Global Clusters

### 7.1 `create-global-cluster`

Creates a Neptune global database.

**Synopsis:**
```bash
aws neptune create-global-cluster \
    --global-cluster-identifier <value> \
    [--source-db-cluster-identifier <value>] \
    [--engine <value>] \
    [--engine-version <value>] \
    [--deletion-protection | --no-deletion-protection] \
    [--storage-encrypted | --no-storage-encrypted] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-cluster-identifier` | **Yes** | string | -- | Global cluster identifier |
| `--source-db-cluster-identifier` | No | string | -- | ARN of the primary cluster |
| `--engine` | No | string | -- | Engine: `neptune` |
| `--engine-version` | No | string | -- | Engine version |
| `--deletion-protection` | No | boolean | false | Enable deletion protection |
| `--storage-encrypted` | No | boolean | false | Enable encryption at rest |

**Output Schema:**
```json
{
    "GlobalCluster": {
        "GlobalClusterIdentifier": "string",
        "GlobalClusterResourceId": "string",
        "GlobalClusterArn": "string",
        "Status": "creating",
        "Engine": "neptune",
        "EngineVersion": "string",
        "StorageEncrypted": "boolean",
        "DeletionProtection": "boolean",
        "GlobalClusterMembers": []
    }
}
```

---

### 7.2 `modify-global-cluster`

Modifies a Neptune global database.

**Synopsis:**
```bash
aws neptune modify-global-cluster \
    --global-cluster-identifier <value> \
    [--new-global-cluster-identifier <value>] \
    [--deletion-protection | --no-deletion-protection] \
    [--engine-version <value>] \
    [--allow-major-version-upgrade | --no-allow-major-version-upgrade] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-cluster-identifier` | **Yes** | string | -- | Global cluster identifier |
| `--new-global-cluster-identifier` | No | string | -- | New global cluster identifier |
| `--deletion-protection` | No | boolean | -- | Toggle deletion protection |
| `--engine-version` | No | string | -- | New engine version |
| `--allow-major-version-upgrade` | No | boolean | false | Allow major version upgrade |

**Output Schema:**
```json
{
    "GlobalCluster": {
        "GlobalClusterIdentifier": "string",
        "GlobalClusterArn": "string",
        "Status": "string",
        "Engine": "neptune",
        "EngineVersion": "string",
        "DeletionProtection": "boolean"
    }
}
```

---

### 7.3 `delete-global-cluster`

Deletes a Neptune global database. The primary and secondary clusters must first be removed.

**Synopsis:**
```bash
aws neptune delete-global-cluster \
    --global-cluster-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-cluster-identifier` | **Yes** | string | -- | Global cluster identifier |

**Output Schema:**
```json
{
    "GlobalCluster": {
        "GlobalClusterIdentifier": "string",
        "GlobalClusterArn": "string",
        "Status": "deleting"
    }
}
```

---

### 7.4 `describe-global-clusters`

Describes Neptune global databases. **Paginated operation.**

**Synopsis:**
```bash
aws neptune describe-global-clusters \
    [--global-cluster-identifier <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-cluster-identifier` | No | string | -- | Specific global cluster to describe |

**Output Schema:**
```json
{
    "GlobalClusters": [
        {
            "GlobalClusterIdentifier": "string",
            "GlobalClusterResourceId": "string",
            "GlobalClusterArn": "string",
            "Status": "string",
            "Engine": "neptune",
            "EngineVersion": "string",
            "StorageEncrypted": "boolean",
            "DeletionProtection": "boolean",
            "GlobalClusterMembers": [
                {
                    "DBClusterArn": "string",
                    "Readers": ["string"],
                    "IsWriter": "boolean"
                }
            ]
        }
    ]
}
```

---

### 7.5 `failover-global-cluster`

Initiates a failover of a Neptune global database. Promotes a secondary cluster to become the new primary.

**Synopsis:**
```bash
aws neptune failover-global-cluster \
    --global-cluster-identifier <value> \
    --target-db-cluster-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-cluster-identifier` | **Yes** | string | -- | Global cluster identifier |
| `--target-db-cluster-identifier` | **Yes** | string | -- | ARN of the secondary cluster to promote |

**Output Schema:**
```json
{
    "GlobalCluster": {
        "GlobalClusterIdentifier": "string",
        "GlobalClusterArn": "string",
        "Status": "failing-over",
        "GlobalClusterMembers": [
            {
                "DBClusterArn": "string",
                "IsWriter": "boolean"
            }
        ]
    }
}
```

---

### 7.6 `switchover-global-cluster`

Performs a switchover of a Neptune global database. Unlike failover, this is a planned operation with no data loss.

**Synopsis:**
```bash
aws neptune switchover-global-cluster \
    --global-cluster-identifier <value> \
    --target-db-cluster-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-cluster-identifier` | **Yes** | string | -- | Global cluster identifier |
| `--target-db-cluster-identifier` | **Yes** | string | -- | ARN of the secondary cluster to promote |

**Output Schema:**
```json
{
    "GlobalCluster": {
        "GlobalClusterIdentifier": "string",
        "GlobalClusterArn": "string",
        "Status": "switching-over",
        "GlobalClusterMembers": [
            {
                "DBClusterArn": "string",
                "IsWriter": "boolean"
            }
        ]
    }
}
```

---

### 7.7 `remove-from-global-cluster`

Removes a Neptune DB cluster from a global database.

**Synopsis:**
```bash
aws neptune remove-from-global-cluster \
    --global-cluster-identifier <value> \
    --db-cluster-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-cluster-identifier` | **Yes** | string | -- | Global cluster identifier |
| `--db-cluster-identifier` | **Yes** | string | -- | ARN of the cluster to remove |

**Output Schema:**
```json
{
    "GlobalCluster": {
        "GlobalClusterIdentifier": "string",
        "GlobalClusterArn": "string",
        "Status": "string",
        "GlobalClusterMembers": [
            {
                "DBClusterArn": "string",
                "IsWriter": "boolean"
            }
        ]
    }
}
```
