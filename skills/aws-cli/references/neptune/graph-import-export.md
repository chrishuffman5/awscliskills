# Graph Import/Export (Neptune Analytics)

### 11.1 `start-import-task`

Starts a data import task into a Neptune Analytics graph.

**Synopsis:**
```bash
aws neptune-graph start-import-task \
    --graph-identifier <value> \
    --source <value> \
    --role-arn <value> \
    [--format <value>] \
    [--parquet-type <value>] \
    [--blank-node-handling <value>] \
    [--import-options <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--graph-identifier` | **Yes** | string | -- | Graph ID to import into |
| `--source` | **Yes** | string | -- | S3 URI for source data (e.g., `s3://bucket/path/`) |
| `--role-arn` | **Yes** | string | -- | IAM role ARN for S3 access |
| `--format` | No | string | `CSV` | Data format: `CSV`, `OPEN_CYPHER`, `PARQUET`, `NTRIPLES` |
| `--parquet-type` | No | string | -- | Parquet type: `COLUMNAR` |
| `--blank-node-handling` | No | string | -- | RDF blank node handling: `convertToIri` |
| `--import-options` | No | structure | None | Additional import options |

**Output Schema:**
```json
{
    "graphId": "string",
    "taskId": "string",
    "source": "string",
    "format": "string",
    "roleArn": "string",
    "status": "INITIALIZING",
    "importOptions": {}
}
```

---

### 11.2 `cancel-import-task`

Cancels a running import task.

**Synopsis:**
```bash
aws neptune-graph cancel-import-task \
    --task-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--task-identifier` | **Yes** | string | -- | Import task ID |

**Output Schema:**
```json
{
    "graphId": "string",
    "taskId": "string",
    "source": "string",
    "format": "string",
    "roleArn": "string",
    "status": "CANCELLING"
}
```

---

### 11.3 `get-import-task`

Gets the status and details of an import task.

**Synopsis:**
```bash
aws neptune-graph get-import-task \
    --task-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--task-identifier` | **Yes** | string | -- | Import task ID |

**Output Schema:**
```json
{
    "graphId": "string",
    "taskId": "string",
    "source": "string",
    "format": "string",
    "roleArn": "string",
    "status": "string",
    "importOptions": {},
    "importTaskDetails": {
        "status": "string",
        "startTime": "timestamp",
        "timeElapsedSeconds": "long",
        "progressPercentage": "integer",
        "errorCount": "integer",
        "errorDetails": "string",
        "statementCount": "long",
        "dictionaryEntryCount": "long"
    },
    "attemptNumber": "integer",
    "statusReason": "string"
}
```

---

### 11.4 `list-import-tasks`

Lists import tasks for Neptune Analytics graphs. **Paginated operation.**

**Synopsis:**
```bash
aws neptune-graph list-import-tasks \
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
    "tasks": [
        {
            "graphId": "string",
            "taskId": "string",
            "source": "string",
            "format": "string",
            "roleArn": "string",
            "status": "string"
        }
    ]
}
```

---

### 11.5 `start-export-task`

Starts a data export task from a Neptune Analytics graph.

**Synopsis:**
```bash
aws neptune-graph start-export-task \
    --graph-identifier <value> \
    --role-arn <value> \
    --format <value> \
    --destination <value> \
    [--kms-key-identifier <value>] \
    [--parquet-type <value>] \
    [--export-filter <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--graph-identifier` | **Yes** | string | -- | Graph ID to export from |
| `--role-arn` | **Yes** | string | -- | IAM role ARN for S3 access |
| `--format` | **Yes** | string | -- | Export format: `PARQUET`, `CSV` |
| `--destination` | **Yes** | string | -- | S3 URI for output (e.g., `s3://bucket/path/`) |
| `--kms-key-identifier` | No | string | -- | KMS key for encrypting exported data |
| `--parquet-type` | No | string | -- | Parquet type: `COLUMNAR` |
| `--export-filter` | No | structure | None | Filter to export subset of data |
| `--tags` | No | map | None | Tags |

**Output Schema:**
```json
{
    "graphId": "string",
    "roleArn": "string",
    "taskId": "string",
    "status": "INITIALIZING",
    "format": "string",
    "destination": "string",
    "kmsKeyIdentifier": "string",
    "parquetType": "string",
    "statusReason": "string",
    "exportFilter": {}
}
```

---

### 11.6 `cancel-export-task`

Cancels a running export task.

**Synopsis:**
```bash
aws neptune-graph cancel-export-task \
    --task-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--task-identifier` | **Yes** | string | -- | Export task ID |

**Output Schema:**
```json
{
    "graphId": "string",
    "roleArn": "string",
    "taskId": "string",
    "status": "CANCELLING",
    "format": "string",
    "destination": "string"
}
```

---

### 11.7 `get-export-task`

Gets the status and details of an export task.

**Synopsis:**
```bash
aws neptune-graph get-export-task \
    --task-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--task-identifier` | **Yes** | string | -- | Export task ID |

**Output Schema:**
```json
{
    "graphId": "string",
    "roleArn": "string",
    "taskId": "string",
    "status": "string",
    "format": "string",
    "destination": "string",
    "kmsKeyIdentifier": "string",
    "parquetType": "string",
    "statusReason": "string",
    "exportFilter": {},
    "exportTaskDetails": {
        "startTime": "timestamp",
        "timeElapsedSeconds": "long",
        "progressPercentage": "integer",
        "numVerticesWritten": "long",
        "numEdgesWritten": "long"
    }
}
```

---

### 11.8 `list-export-tasks`

Lists export tasks for Neptune Analytics graphs. **Paginated operation.**

**Synopsis:**
```bash
aws neptune-graph list-export-tasks \
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
    "tasks": [
        {
            "graphId": "string",
            "roleArn": "string",
            "taskId": "string",
            "status": "string",
            "format": "string",
            "destination": "string"
        }
    ]
}
```
