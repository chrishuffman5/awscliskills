# Notebooks

### 6.1 `create-notebook`

Creates a notebook in a workgroup.

**Synopsis:**
```bash
aws athena create-notebook \
    --work-group <value> \
    --name <value> \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--work-group` | **Yes** | string | -- | Workgroup |
| `--name` | **Yes** | string | -- | Notebook name |
| `--client-request-token` | No | string | -- | Idempotency token |

**Output Schema:**
```json
{
    "NotebookId": "string"
}
```

---

### 6.2 `delete-notebook`

Deletes a notebook.

**Synopsis:**
```bash
aws athena delete-notebook \
    --notebook-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--notebook-id` | **Yes** | string | -- | Notebook ID to delete |

No output on success.

---

### 6.3 `get-notebook-metadata`

Returns notebook metadata.

**Synopsis:**
```bash
aws athena get-notebook-metadata \
    --notebook-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--notebook-id` | **Yes** | string | -- | Notebook ID |

**Output Schema:**
```json
{
    "NotebookMetadata": {
        "NotebookId": "string",
        "Name": "string",
        "WorkGroup": "string",
        "CreationTime": "timestamp",
        "Type": "IPYNB",
        "LastModifiedTime": "timestamp"
    }
}
```

---

### 6.4 `update-notebook`

Updates the notebook content (cells).

**Synopsis:**
```bash
aws athena update-notebook \
    --notebook-id <value> \
    --payload <value> \
    --type <value> \
    [--session-id <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--notebook-id` | **Yes** | string | -- | Notebook ID |
| `--payload` | **Yes** | string | -- | Notebook content (JSON string) |
| `--type` | **Yes** | string | -- | Notebook type: `IPYNB` |
| `--session-id` | No | string | -- | Active session ID |
| `--client-request-token` | No | string | -- | Idempotency token |

No output on success.

---

### 6.5 `update-notebook-metadata`

Updates notebook metadata (name).

**Synopsis:**
```bash
aws athena update-notebook-metadata \
    --notebook-id <value> \
    --name <value> \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--notebook-id` | **Yes** | string | -- | Notebook ID |
| `--name` | **Yes** | string | -- | New name |
| `--client-request-token` | No | string | -- | Idempotency token |

No output on success.

---

### 6.6 `list-notebook-metadata`

Lists notebooks in a workgroup. **Paginated operation.**

**Synopsis:**
```bash
aws athena list-notebook-metadata \
    --work-group <value> \
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
| `--work-group` | **Yes** | string | -- | Workgroup |
| `--filters` | No | structure | -- | Filters. Shorthand: `Name=string` |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "NotebookMetadataList": [
        {
            "NotebookId": "string",
            "Name": "string",
            "WorkGroup": "string",
            "CreationTime": "timestamp",
            "Type": "IPYNB",
            "LastModifiedTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 6.7 `import-notebook`

Imports a notebook from an S3 location or payload.

**Synopsis:**
```bash
aws athena import-notebook \
    --work-group <value> \
    --name <value> \
    --type <value> \
    [--payload <value>] \
    [--notebook-s3-location-uri <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--work-group` | **Yes** | string | -- | Workgroup |
| `--name` | **Yes** | string | -- | Notebook name |
| `--type` | **Yes** | string | -- | `IPYNB` |
| `--payload` | No | string | -- | Notebook content (provide this or S3 location) |
| `--notebook-s3-location-uri` | No | string | -- | S3 URI of the notebook |
| `--client-request-token` | No | string | -- | Idempotency token |

**Output Schema:**
```json
{
    "NotebookId": "string"
}
```

---

### 6.8 `export-notebook`

Exports a notebook to its content payload.

**Synopsis:**
```bash
aws athena export-notebook \
    --notebook-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--notebook-id` | **Yes** | string | -- | Notebook ID |

**Output Schema:**
```json
{
    "NotebookMetadata": {
        "NotebookId": "string",
        "Name": "string",
        "WorkGroup": "string",
        "CreationTime": "timestamp",
        "Type": "IPYNB",
        "LastModifiedTime": "timestamp"
    },
    "Payload": "string"
}
```
