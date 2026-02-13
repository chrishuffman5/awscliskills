# Global Clusters

### 6.1 `create-global-cluster`

Creates a DocumentDB global cluster that can span multiple AWS Regions. The global cluster contains one primary cluster with read-write capability and up to five read-only secondary clusters.

**Synopsis:**
```bash
aws docdb create-global-cluster \
    --global-cluster-identifier <value> \
    [--source-db-cluster-identifier <value>] \
    [--engine <value>] \
    [--engine-version <value>] \
    [--deletion-protection | --no-deletion-protection] \
    [--database-name <value>] \
    [--storage-encrypted | --no-storage-encrypted] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-cluster-identifier` | **Yes** | string | -- | Global cluster identifier (1-63 chars) |
| `--source-db-cluster-identifier` | No | string | -- | ARN of an existing cluster to use as the primary |
| `--engine` | No | string | -- | Engine: `docdb` |
| `--engine-version` | No | string | -- | Engine version |
| `--deletion-protection` | No | boolean | false | Enable deletion protection |
| `--database-name` | No | string | -- | Database name |
| `--storage-encrypted` | No | boolean | false | Enable encryption at rest |

**Output Schema:**
```json
{
    "GlobalCluster": {
        "GlobalClusterIdentifier": "string",
        "GlobalClusterResourceId": "string",
        "GlobalClusterArn": "string",
        "Status": "string",
        "Engine": "string",
        "EngineVersion": "string",
        "DatabaseName": "string",
        "StorageEncrypted": true|false,
        "DeletionProtection": true|false,
        "GlobalClusterMembers": [
            {
                "DBClusterArn": "string",
                "Readers": ["string"],
                "IsWriter": true|false
            }
        ]
    }
}
```

---

### 6.2 `delete-global-cluster`

Deletes a global cluster. The primary and secondary clusters must be detached first using `remove-from-global-cluster`.

**Synopsis:**
```bash
aws docdb delete-global-cluster \
    --global-cluster-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-cluster-identifier` | **Yes** | string | -- | Global cluster identifier to delete |

**Output Schema:** Same as `create-global-cluster` output.

---

### 6.3 `describe-global-clusters`

Returns information about global clusters. **Paginated operation.**

**Synopsis:**
```bash
aws docdb describe-global-clusters \
    [--global-cluster-identifier <value>] \
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
| `--global-cluster-identifier` | No | string | All | Global cluster identifier |
| `--filters` | No | list | None | Filters |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "GlobalClusters": [
        {
            "GlobalClusterIdentifier": "string",
            "GlobalClusterResourceId": "string",
            "GlobalClusterArn": "string",
            "Status": "string",
            "Engine": "string",
            "EngineVersion": "string",
            "StorageEncrypted": true|false,
            "DeletionProtection": true|false,
            "GlobalClusterMembers": []
        }
    ],
    "Marker": "string"
}
```

---

### 6.4 `modify-global-cluster`

Modifies a setting for a global cluster. You can change the deletion protection setting or the global cluster identifier.

**Synopsis:**
```bash
aws docdb modify-global-cluster \
    --global-cluster-identifier <value> \
    [--new-global-cluster-identifier <value>] \
    [--deletion-protection | --no-deletion-protection] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-cluster-identifier` | **Yes** | string | -- | Global cluster identifier |
| `--new-global-cluster-identifier` | No | string | -- | New identifier (rename) |
| `--deletion-protection` | No | boolean | -- | Enable/disable deletion protection |

**Output Schema:** Same as `create-global-cluster` output.

---

### 6.5 `remove-from-global-cluster`

Detaches a secondary cluster from a global cluster. The secondary becomes a standalone cluster with read-write capability.

**Synopsis:**
```bash
aws docdb remove-from-global-cluster \
    --global-cluster-identifier <value> \
    --db-cluster-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-cluster-identifier` | **Yes** | string | -- | Global cluster identifier |
| `--db-cluster-identifier` | **Yes** | string | -- | ARN of the cluster to detach |

**Output Schema:** Same as `create-global-cluster` output.

---

### 6.6 `failover-global-cluster`

Promotes a secondary cluster to become the primary cluster of the global cluster. Used for planned failovers (disaster recovery testing).

**Synopsis:**
```bash
aws docdb failover-global-cluster \
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

**Output Schema:** Same as `create-global-cluster` output.

---

### 6.7 `switchover-global-cluster`

Switches the primary cluster of a global cluster to a secondary cluster. This is a planned operation that ensures no data loss during the switchover.

**Synopsis:**
```bash
aws docdb switchover-global-cluster \
    --global-cluster-identifier <value> \
    --target-db-cluster-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-cluster-identifier` | **Yes** | string | -- | Global cluster identifier |
| `--target-db-cluster-identifier` | **Yes** | string | -- | ARN of the secondary cluster to become primary |

**Output Schema:** Same as `create-global-cluster` output.
