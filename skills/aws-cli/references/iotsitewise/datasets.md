# Datasets

### 12.1 `create-dataset`

Creates a dataset backed by an external knowledge base (e.g., Amazon Kendra).

**Synopsis:**
```bash
aws iotsitewise create-dataset \
    --dataset-name <value> \
    --dataset-source <value> \
    [--dataset-id <value>] \
    [--dataset-description <value>] \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--dataset-name` | **Yes** | string | -- | Dataset name (1-256 chars) |
| `--dataset-source` | **Yes** | structure | -- | Data source configuration |
| `--dataset-id` | No | string | Auto | UUID for the dataset |
| `--dataset-description` | No | string | None | Description (1-2048 chars) |
| `--tags` | No | map | None | Tags (max 50) |
| `--client-token` | No | string | Auto | Idempotency token |

**Dataset Source Structure:**
```json
{
    "sourceType": "KENDRA",
    "sourceFormat": "KNOWLEDGE_BASE",
    "sourceDetail": {
        "kendra": {
            "knowledgeBaseArn": "string",
            "roleArn": "string"
        }
    }
}
```

**Output Schema:**
```json
{
    "datasetId": "string",
    "datasetArn": "string",
    "datasetStatus": {
        "state": "CREATING|ACTIVE|UPDATING|DELETING|FAILED",
        "error": {
            "code": "VALIDATION_ERROR|INTERNAL_FAILURE",
            "message": "string"
        }
    }
}
```

---

### 12.2 `describe-dataset`

Describes a dataset.

**Synopsis:**
```bash
aws iotsitewise describe-dataset \
    --dataset-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--dataset-id` | **Yes** | string | -- | Dataset ID |

**Output Schema:**
```json
{
    "datasetId": "string",
    "datasetArn": "string",
    "datasetName": "string",
    "datasetDescription": "string",
    "datasetSource": {
        "sourceType": "KENDRA",
        "sourceFormat": "KNOWLEDGE_BASE",
        "sourceDetail": {}
    },
    "datasetStatus": {
        "state": "CREATING|ACTIVE|UPDATING|DELETING|FAILED",
        "error": {}
    },
    "datasetCreationDate": "timestamp",
    "datasetLastUpdateDate": "timestamp",
    "datasetVersion": "string"
}
```

---

### 12.3 `list-datasets`

Lists datasets. **Paginated operation.**

**Synopsis:**
```bash
aws iotsitewise list-datasets \
    --source-type <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-type` | **Yes** | string | -- | `KENDRA` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "datasetSummaries": [
        {
            "id": "string",
            "arn": "string",
            "name": "string",
            "description": "string",
            "creationDate": "timestamp",
            "lastUpdateDate": "timestamp",
            "status": {"state": "string", "error": {}}
        }
    ],
    "nextToken": "string"
}
```

---

### 12.4 `update-dataset`

Updates a dataset.

**Synopsis:**
```bash
aws iotsitewise update-dataset \
    --dataset-id <value> \
    --dataset-name <value> \
    --dataset-source <value> \
    [--dataset-description <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--dataset-id` | **Yes** | string | -- | Dataset ID |
| `--dataset-name` | **Yes** | string | -- | Updated name |
| `--dataset-source` | **Yes** | structure | -- | Updated source config |
| `--dataset-description` | No | string | None | Updated description |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "datasetId": "string",
    "datasetArn": "string",
    "datasetStatus": {
        "state": "CREATING|ACTIVE|UPDATING|DELETING|FAILED",
        "error": {}
    }
}
```

---

### 12.5 `delete-dataset`

Deletes a dataset.

**Synopsis:**
```bash
aws iotsitewise delete-dataset \
    --dataset-id <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--dataset-id` | **Yes** | string | -- | Dataset ID |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "datasetStatus": {
        "state": "DELETING",
        "error": {}
    }
}
```
