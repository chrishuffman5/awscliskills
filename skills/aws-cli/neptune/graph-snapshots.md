# Graph Snapshots (Neptune Analytics)

### 10.1 `create-graph-snapshot`

Creates a snapshot of a Neptune Analytics graph.

**Synopsis:**
```bash
aws neptune-graph create-graph-snapshot \
    --graph-identifier <value> \
    --snapshot-name <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--graph-identifier` | **Yes** | string | -- | Graph ID |
| `--snapshot-name` | **Yes** | string | -- | Snapshot name |
| `--tags` | No | map | None | Tags |

**Output Schema:**
```json
{
    "id": "string",
    "name": "string",
    "arn": "string",
    "sourceGraphId": "string",
    "snapshotCreateTime": "timestamp",
    "status": "CREATING",
    "kmsKeyIdentifier": "string"
}
```

---

### 10.2 `delete-graph-snapshot`

Deletes a Neptune Analytics graph snapshot.

**Synopsis:**
```bash
aws neptune-graph delete-graph-snapshot \
    --snapshot-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--snapshot-identifier` | **Yes** | string | -- | Snapshot ID |

**Output Schema:**
```json
{
    "id": "string",
    "name": "string",
    "arn": "string",
    "sourceGraphId": "string",
    "status": "DELETING",
    "kmsKeyIdentifier": "string"
}
```

---

### 10.3 `get-graph-snapshot`

Gets details about a Neptune Analytics graph snapshot.

**Synopsis:**
```bash
aws neptune-graph get-graph-snapshot \
    --snapshot-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--snapshot-identifier` | **Yes** | string | -- | Snapshot ID |

**Output Schema:**
```json
{
    "id": "string",
    "name": "string",
    "arn": "string",
    "sourceGraphId": "string",
    "snapshotCreateTime": "timestamp",
    "status": "string",
    "kmsKeyIdentifier": "string"
}
```

---

### 10.4 `list-graph-snapshots`

Lists Neptune Analytics graph snapshots. **Paginated operation.**

**Synopsis:**
```bash
aws neptune-graph list-graph-snapshots \
    [--graph-identifier <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--graph-identifier` | No | string | -- | Filter by graph ID |

**Output Schema:**
```json
{
    "graphSnapshots": [
        {
            "id": "string",
            "name": "string",
            "arn": "string",
            "sourceGraphId": "string",
            "snapshotCreateTime": "timestamp",
            "status": "string",
            "kmsKeyIdentifier": "string"
        }
    ]
}
```

---

### 10.5 `restore-graph-from-snapshot`

Restores a Neptune Analytics graph from a snapshot.

**Synopsis:**
```bash
aws neptune-graph restore-graph-from-snapshot \
    --snapshot-identifier <value> \
    --graph-name <value> \
    [--provisioned-memory <value>] \
    [--deletion-protection | --no-deletion-protection] \
    [--tags <value>] \
    [--replica-count <value>] \
    [--public-connectivity | --no-public-connectivity] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--snapshot-identifier` | **Yes** | string | -- | Snapshot ID to restore from |
| `--graph-name` | **Yes** | string | -- | Name for the new graph |
| `--provisioned-memory` | No | integer | -- | Memory in MiB (defaults to snapshot source) |
| `--deletion-protection` | No | boolean | false | Enable deletion protection |
| `--tags` | No | map | None | Tags |
| `--replica-count` | No | integer | 0 | Number of read replicas |
| `--public-connectivity` | No | boolean | false | Enable public connectivity |

**Output Schema:**
```json
{
    "id": "string",
    "name": "string",
    "arn": "string",
    "status": "CREATING",
    "provisionedMemory": "integer",
    "endpoint": "string",
    "publicConnectivity": "boolean",
    "replicaCount": "integer",
    "sourceSnapshotId": "string",
    "deletionProtection": "boolean"
}
```
