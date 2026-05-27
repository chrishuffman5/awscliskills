# Model Manifests

### 2.1 `create-model-manifest`

Creates a vehicle model manifest defining which signals a vehicle type supports.

**Synopsis:**
```bash
aws iotfleetwise create-model-manifest \
    --name <value> \
    --nodes <value> \
    --signal-catalog-arn <value> \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Model manifest name (1-100 chars) |
| `--nodes` | **Yes** | list | -- | Fully qualified signal names from the signal catalog (max 500) |
| `--signal-catalog-arn` | **Yes** | string | -- | ARN of the signal catalog |
| `--description` | No | string | None | Description (1-2048 chars) |
| `--tags` | No | list | None | Tags (max 50) |

**Output Schema:**
```json
{
    "name": "string",
    "arn": "string"
}
```

---

### 2.2 `get-model-manifest`

Retrieves information about a model manifest.

**Synopsis:**
```bash
aws iotfleetwise get-model-manifest \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Model manifest name |

**Output Schema:**
```json
{
    "name": "string",
    "arn": "string",
    "description": "string",
    "signalCatalogArn": "string",
    "status": "ACTIVE|DRAFT|INVALID|VALIDATING",
    "creationTime": "timestamp",
    "lastModificationTime": "timestamp"
}
```

---

### 2.3 `list-model-manifests`

Lists model manifests. **Paginated operation.**

**Synopsis:**
```bash
aws iotfleetwise list-model-manifests \
    [--signal-catalog-arn <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--signal-catalog-arn` | No | string | None | Filter by signal catalog ARN |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "summaries": [
        {
            "name": "string",
            "arn": "string",
            "signalCatalogArn": "string",
            "description": "string",
            "status": "ACTIVE|DRAFT|INVALID|VALIDATING",
            "creationTime": "timestamp",
            "lastModificationTime": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 2.4 `update-model-manifest`

Updates a model manifest. Must set status to ACTIVE before use.

**Synopsis:**
```bash
aws iotfleetwise update-model-manifest \
    --name <value> \
    [--description <value>] \
    [--nodes-to-add <value>] \
    [--nodes-to-remove <value>] \
    [--status <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Model manifest name |
| `--description` | No | string | None | Updated description |
| `--nodes-to-add` | No | list | None | Fully qualified signal names to add |
| `--nodes-to-remove` | No | list | None | Fully qualified signal names to remove |
| `--status` | No | string | None | `ACTIVE` or `DRAFT` |

**Output Schema:**
```json
{
    "name": "string",
    "arn": "string"
}
```

---

### 2.5 `delete-model-manifest`

Deletes a model manifest.

**Synopsis:**
```bash
aws iotfleetwise delete-model-manifest \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Model manifest name |

**Output Schema:**
```json
{
    "name": "string",
    "arn": "string"
}
```

---

### 2.6 `list-model-manifest-nodes`

Lists nodes (signals) in a model manifest. **Paginated operation.**

**Synopsis:**
```bash
aws iotfleetwise list-model-manifest-nodes \
    --name <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Model manifest name |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "nodes": [
        {
            "branch": {
                "fullyQualifiedName": "string",
                "description": "string"
            },
            "sensor": {
                "fullyQualifiedName": "string",
                "dataType": "string",
                "description": "string",
                "unit": "string"
            },
            "actuator": {
                "fullyQualifiedName": "string",
                "dataType": "string",
                "description": "string"
            },
            "attribute": {
                "fullyQualifiedName": "string",
                "dataType": "string",
                "description": "string"
            }
        }
    ],
    "nextToken": "string"
}
```
