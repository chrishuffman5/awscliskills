# Graph (Neptune Analytics)

### 9.1 `create-graph`

Creates a Neptune Analytics graph.

**Synopsis:**
```bash
aws neptune-graph create-graph \
    --graph-name <value> \
    --provisioned-memory <value> \
    [--tags <value>] \
    [--public-connectivity | --no-public-connectivity] \
    [--kms-key-identifier <value>] \
    [--vector-search-configuration <value>] \
    [--replica-count <value>] \
    [--deletion-protection | --no-deletion-protection] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--graph-name` | **Yes** | string | -- | Graph name (1-63 chars) |
| `--provisioned-memory` | **Yes** | integer | -- | Memory in mebibytes (MiB): 16, 32, 64, 128, 256, 512, 1024, 2048, 3072, 4096, 6144, 8192 |
| `--tags` | No | map | None | Tags |
| `--public-connectivity` | No | boolean | false | Enable public connectivity |
| `--kms-key-identifier` | No | string | -- | KMS key ARN for encryption |
| `--vector-search-configuration` | No | structure | None | Vector search config. Shorthand: `dimension=integer` |
| `--replica-count` | No | integer | 0 | Number of read replicas (0-2) |
| `--deletion-protection` | No | boolean | false | Enable deletion protection |

**Output Schema:**
```json
{
    "id": "string",
    "name": "string",
    "arn": "string",
    "status": "CREATING",
    "statusReason": "string",
    "createTime": "timestamp",
    "provisionedMemory": "integer",
    "endpoint": "string",
    "publicConnectivity": "boolean",
    "vectorSearchConfiguration": {"dimension": "integer"},
    "replicaCount": "integer",
    "kmsKeyIdentifier": "string",
    "sourceSnapshotId": "string",
    "deletionProtection": "boolean",
    "buildNumber": "string"
}
```

---

### 9.2 `delete-graph`

Deletes a Neptune Analytics graph.

**Synopsis:**
```bash
aws neptune-graph delete-graph \
    --graph-identifier <value> \
    --skip-snapshot | --no-skip-snapshot \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--graph-identifier` | **Yes** | string | -- | Graph ID (e.g., `g-abc1234567`) |
| `--skip-snapshot` | **Yes** | boolean | -- | Whether to skip the final snapshot |

**Output Schema:**
```json
{
    "id": "string",
    "name": "string",
    "arn": "string",
    "status": "DELETING",
    "provisionedMemory": "integer",
    "endpoint": "string",
    "publicConnectivity": "boolean",
    "replicaCount": "integer",
    "deletionProtection": "boolean"
}
```

---

### 9.3 `get-graph`

Gets details about a Neptune Analytics graph.

**Synopsis:**
```bash
aws neptune-graph get-graph \
    --graph-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--graph-identifier` | **Yes** | string | -- | Graph ID |

**Output Schema:**
```json
{
    "id": "string",
    "name": "string",
    "arn": "string",
    "status": "string",
    "statusReason": "string",
    "createTime": "timestamp",
    "provisionedMemory": "integer",
    "endpoint": "string",
    "publicConnectivity": "boolean",
    "vectorSearchConfiguration": {"dimension": "integer"},
    "replicaCount": "integer",
    "kmsKeyIdentifier": "string",
    "sourceSnapshotId": "string",
    "deletionProtection": "boolean",
    "buildNumber": "string"
}
```

---

### 9.4 `list-graphs`

Lists all Neptune Analytics graphs. **Paginated operation.**

**Synopsis:**
```bash
aws neptune-graph list-graphs \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** Pagination only.

**Output Schema:**
```json
{
    "graphs": [
        {
            "id": "string",
            "name": "string",
            "arn": "string",
            "status": "string",
            "provisionedMemory": "integer",
            "publicConnectivity": "boolean",
            "endpoint": "string",
            "replicaCount": "integer",
            "kmsKeyIdentifier": "string",
            "deletionProtection": "boolean"
        }
    ]
}
```

---

### 9.5 `update-graph`

Updates a Neptune Analytics graph configuration.

**Synopsis:**
```bash
aws neptune-graph update-graph \
    --graph-identifier <value> \
    [--public-connectivity | --no-public-connectivity] \
    [--provisioned-memory <value>] \
    [--deletion-protection | --no-deletion-protection] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--graph-identifier` | **Yes** | string | -- | Graph ID |
| `--public-connectivity` | No | boolean | -- | Toggle public connectivity |
| `--provisioned-memory` | No | integer | -- | New provisioned memory (MiB) |
| `--deletion-protection` | No | boolean | -- | Toggle deletion protection |

**Output Schema:**
```json
{
    "id": "string",
    "name": "string",
    "arn": "string",
    "status": "UPDATING",
    "provisionedMemory": "integer",
    "endpoint": "string",
    "publicConnectivity": "boolean",
    "replicaCount": "integer",
    "deletionProtection": "boolean"
}
```

---

### 9.6 `reset-graph`

Resets a Neptune Analytics graph, removing all data while preserving the graph configuration.

**Synopsis:**
```bash
aws neptune-graph reset-graph \
    --graph-identifier <value> \
    --skip-snapshot | --no-skip-snapshot \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--graph-identifier` | **Yes** | string | -- | Graph ID |
| `--skip-snapshot` | **Yes** | boolean | -- | Whether to skip the snapshot before reset |

**Output Schema:**
```json
{
    "id": "string",
    "name": "string",
    "arn": "string",
    "status": "RESETTING",
    "provisionedMemory": "integer",
    "endpoint": "string"
}
```

---

### 9.7 `start-graph`

Starts a stopped Neptune Analytics graph.

**Synopsis:**
```bash
aws neptune-graph start-graph \
    --graph-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--graph-identifier` | **Yes** | string | -- | Graph ID |

**Output Schema:**
```json
{
    "id": "string",
    "name": "string",
    "arn": "string",
    "status": "STARTING",
    "endpoint": "string"
}
```

---

### 9.8 `stop-graph`

Stops a running Neptune Analytics graph. Stopped graphs do not incur compute charges.

**Synopsis:**
```bash
aws neptune-graph stop-graph \
    --graph-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--graph-identifier` | **Yes** | string | -- | Graph ID |

**Output Schema:**
```json
{
    "id": "string",
    "name": "string",
    "arn": "string",
    "status": "STOPPING",
    "endpoint": "string"
}
```

---

### 9.9 `get-graph-summary`

Returns summary statistics about a Neptune Analytics graph.

**Synopsis:**
```bash
aws neptune-graph get-graph-summary \
    --graph-identifier <value> \
    [--mode <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--graph-identifier` | **Yes** | string | -- | Graph ID |
| `--mode` | No | string | `BASIC` | Summary mode: `BASIC`, `DETAILED` |

**Output Schema:**
```json
{
    "version": "string",
    "lastStatisticsComputationTime": "timestamp",
    "graphSummary": {
        "numNodes": "long",
        "numEdges": "long",
        "numNodeLabels": "long",
        "numEdgeLabels": "long",
        "nodeLabels": ["string"],
        "edgeLabels": ["string"],
        "numNodeProperties": "long",
        "numEdgeProperties": "long",
        "nodeProperties": [{"string": "long"}],
        "edgeProperties": [{"string": "long"}],
        "totalNodePropertyValues": "long",
        "totalEdgePropertyValues": "long",
        "nodeStructures": [{"count": "long", "nodeProperties": ["string"]}],
        "edgeStructures": [{"count": "long", "edgeProperties": ["string"]}]
    }
}
```
