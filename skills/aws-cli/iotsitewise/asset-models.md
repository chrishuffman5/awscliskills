# Asset Models

### 1.1 `create-asset-model`

Creates an asset model that defines the structure and properties for assets.

**Synopsis:**
```bash
aws iotsitewise create-asset-model \
    --asset-model-name <value> \
    [--asset-model-id <value>] \
    [--asset-model-external-id <value>] \
    [--asset-model-type <value>] \
    [--asset-model-description <value>] \
    [--asset-model-properties <value>] \
    [--asset-model-hierarchies <value>] \
    [--asset-model-composite-models <value>] \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--asset-model-name` | **Yes** | string | -- | Model name (1-256 chars) |
| `--asset-model-id` | No | string | Auto | UUID for the model |
| `--asset-model-external-id` | No | string | None | External ID (2-128 chars) |
| `--asset-model-type` | No | string | `ASSET_MODEL` | `ASSET_MODEL`, `COMPONENT_MODEL`, or `INTERFACE` |
| `--asset-model-description` | No | string | None | Description (1-2048 chars) |
| `--asset-model-properties` | No | list | None | Property definitions (max 200) |
| `--asset-model-hierarchies` | No | list | None | Hierarchy definitions (max 10) |
| `--asset-model-composite-models` | No | list | None | Composite model definitions |
| `--tags` | No | map | None | Tags (max 50) |
| `--client-token` | No | string | Auto | Idempotency token |

**Property Definition Structure:**
```json
{
    "name": "string",
    "dataType": "STRING|INTEGER|DOUBLE|BOOLEAN|STRUCT",
    "dataTypeSpec": "string",
    "unit": "string",
    "type": {
        "attribute": {"defaultValue": "string"},
        "measurement": {"processingConfig": {"forwardingConfig": {"state": "ENABLED|DISABLED"}}},
        "transform": {
            "expression": "string",
            "variables": [{"name": "string", "value": {"propertyId": "string", "hierarchyId": "string"}}],
            "processingConfig": {"computeLocation": "EDGE|CLOUD"}
        },
        "metric": {
            "expression": "string",
            "variables": [{"name": "string", "value": {"propertyId": "string"}}],
            "window": {"tumbling": {"interval": "string", "offset": "string"}},
            "processingConfig": {"computeLocation": "EDGE|CLOUD"}
        }
    }
}
```

**Output Schema:**
```json
{
    "assetModelId": "string",
    "assetModelArn": "string",
    "assetModelStatus": {
        "state": "CREATING|ACTIVE|UPDATING|PROPAGATING|DELETING|FAILED",
        "error": {
            "code": "VALIDATION_ERROR|INTERNAL_FAILURE",
            "message": "string"
        }
    }
}
```

---

### 1.2 `describe-asset-model`

Describes an asset model including its properties, hierarchies, and status.

**Synopsis:**
```bash
aws iotsitewise describe-asset-model \
    --asset-model-id <value> \
    [--exclude-properties | --no-exclude-properties] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--asset-model-id` | **Yes** | string | -- | Asset model ID (UUID or `externalId:` prefix) |
| `--exclude-properties` | No | boolean | false | Exclude properties from response |

**Output Schema:**
```json
{
    "assetModelId": "string",
    "assetModelExternalId": "string",
    "assetModelArn": "string",
    "assetModelName": "string",
    "assetModelType": "ASSET_MODEL|COMPONENT_MODEL|INTERFACE",
    "assetModelDescription": "string",
    "assetModelProperties": [],
    "assetModelHierarchies": [
        {
            "id": "string",
            "externalId": "string",
            "name": "string",
            "childAssetModelId": "string"
        }
    ],
    "assetModelCompositeModels": [],
    "assetModelCreationDate": "timestamp",
    "assetModelLastUpdateDate": "timestamp",
    "assetModelStatus": {
        "state": "CREATING|ACTIVE|UPDATING|PROPAGATING|DELETING|FAILED",
        "error": {}
    },
    "assetModelCompositeModelSummaries": []
}
```

---

### 1.3 `list-asset-models`

Lists asset models. **Paginated operation.**

**Synopsis:**
```bash
aws iotsitewise list-asset-models \
    [--asset-model-types <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--asset-model-types` | No | list | None | Filter: `ASSET_MODEL`, `COMPONENT_MODEL`, `INTERFACE` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "assetModelSummaries": [
        {
            "id": "string",
            "externalId": "string",
            "arn": "string",
            "name": "string",
            "assetModelType": "ASSET_MODEL|COMPONENT_MODEL|INTERFACE",
            "description": "string",
            "creationDate": "timestamp",
            "lastUpdateDate": "timestamp",
            "status": {
                "state": "CREATING|ACTIVE|UPDATING|PROPAGATING|DELETING|FAILED",
                "error": {}
            }
        }
    ],
    "nextToken": "string"
}
```

---

### 1.4 `update-asset-model`

Updates an asset model and all of the assets that were created from it.

**Synopsis:**
```bash
aws iotsitewise update-asset-model \
    --asset-model-id <value> \
    --asset-model-name <value> \
    [--asset-model-external-id <value>] \
    [--asset-model-description <value>] \
    [--asset-model-properties <value>] \
    [--asset-model-hierarchies <value>] \
    [--asset-model-composite-models <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--asset-model-id` | **Yes** | string | -- | Asset model ID |
| `--asset-model-name` | **Yes** | string | -- | Updated model name |
| `--asset-model-external-id` | No | string | None | Updated external ID |
| `--asset-model-description` | No | string | None | Updated description |
| `--asset-model-properties` | No | list | None | Updated property definitions |
| `--asset-model-hierarchies` | No | list | None | Updated hierarchy definitions |
| `--asset-model-composite-models` | No | list | None | Updated composite models |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "assetModelStatus": {
        "state": "CREATING|ACTIVE|UPDATING|PROPAGATING|DELETING|FAILED",
        "error": {}
    }
}
```

---

### 1.5 `delete-asset-model`

Deletes an asset model. All assets created from the model must be deleted first.

**Synopsis:**
```bash
aws iotsitewise delete-asset-model \
    --asset-model-id <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--asset-model-id` | **Yes** | string | -- | Asset model ID |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "assetModelStatus": {
        "state": "DELETING",
        "error": {}
    }
}
```

---

### 1.6 `list-asset-model-properties`

Lists the properties of an asset model. **Paginated operation.**

**Synopsis:**
```bash
aws iotsitewise list-asset-model-properties \
    --asset-model-id <value> \
    [--filter <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--asset-model-id` | **Yes** | string | -- | Asset model ID |
| `--filter` | No | string | `ALL` | `ALL` or `BASE` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "assetModelPropertySummaries": [
        {
            "id": "string",
            "externalId": "string",
            "name": "string",
            "dataType": "STRING|INTEGER|DOUBLE|BOOLEAN|STRUCT",
            "dataTypeSpec": "string",
            "unit": "string",
            "type": {},
            "path": [{"id": "string", "name": "string"}]
        }
    ],
    "nextToken": "string"
}
```

---

### 1.7 `create-asset-model-composite-model`

Creates a composite model within an existing asset model.

**Synopsis:**
```bash
aws iotsitewise create-asset-model-composite-model \
    --asset-model-id <value> \
    --asset-model-composite-model-name <value> \
    --asset-model-composite-model-type <value> \
    [--asset-model-composite-model-id <value>] \
    [--asset-model-composite-model-external-id <value>] \
    [--asset-model-composite-model-description <value>] \
    [--asset-model-composite-model-properties <value>] \
    [--composed-asset-model-id <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--asset-model-id` | **Yes** | string | -- | Parent asset model ID |
| `--asset-model-composite-model-name` | **Yes** | string | -- | Composite model name |
| `--asset-model-composite-model-type` | **Yes** | string | -- | Type (e.g., `AWS/ALARM`) |
| `--asset-model-composite-model-id` | No | string | Auto | UUID for composite model |
| `--asset-model-composite-model-external-id` | No | string | None | External ID |
| `--asset-model-composite-model-description` | No | string | None | Description |
| `--asset-model-composite-model-properties` | No | list | None | Property definitions |
| `--composed-asset-model-id` | No | string | None | Component model ID |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "assetModelCompositeModelId": "string",
    "assetModelCompositeModelPath": [
        {"id": "string", "name": "string"}
    ],
    "assetModelStatus": {
        "state": "CREATING|ACTIVE|UPDATING|PROPAGATING|DELETING|FAILED",
        "error": {}
    }
}
```

---

### 1.8 `describe-asset-model-composite-model`

Describes a composite model for an asset model.

**Synopsis:**
```bash
aws iotsitewise describe-asset-model-composite-model \
    --asset-model-id <value> \
    --asset-model-composite-model-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--asset-model-id` | **Yes** | string | -- | Asset model ID |
| `--asset-model-composite-model-id` | **Yes** | string | -- | Composite model ID |

**Output Schema:**
```json
{
    "assetModelId": "string",
    "assetModelCompositeModelId": "string",
    "assetModelCompositeModelExternalId": "string",
    "assetModelCompositeModelPath": [],
    "assetModelCompositeModelName": "string",
    "assetModelCompositeModelDescription": "string",
    "assetModelCompositeModelType": "string",
    "assetModelCompositeModelProperties": [],
    "compositionDetails": {
        "compositionRelationship": [
            {"id": "string", "type": "string"}
        ]
    },
    "assetModelCompositeModelSummaries": [],
    "actionDefinitions": []
}
```

---

### 1.9 `list-asset-model-composite-models`

Lists composite models for an asset model. **Paginated operation.**

**Synopsis:**
```bash
aws iotsitewise list-asset-model-composite-models \
    --asset-model-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--asset-model-id` | **Yes** | string | -- | Asset model ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "assetModelCompositeModelSummaries": [
        {
            "id": "string",
            "externalId": "string",
            "name": "string",
            "type": "string",
            "description": "string",
            "path": [{"id": "string", "name": "string"}]
        }
    ],
    "nextToken": "string"
}
```

---

### 1.10 `update-asset-model-composite-model`

Updates a composite model within an asset model.

**Synopsis:**
```bash
aws iotsitewise update-asset-model-composite-model \
    --asset-model-id <value> \
    --asset-model-composite-model-id <value> \
    --asset-model-composite-model-name <value> \
    [--asset-model-composite-model-external-id <value>] \
    [--asset-model-composite-model-description <value>] \
    [--asset-model-composite-model-properties <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--asset-model-id` | **Yes** | string | -- | Asset model ID |
| `--asset-model-composite-model-id` | **Yes** | string | -- | Composite model ID |
| `--asset-model-composite-model-name` | **Yes** | string | -- | Updated name |
| `--asset-model-composite-model-external-id` | No | string | None | Updated external ID |
| `--asset-model-composite-model-description` | No | string | None | Updated description |
| `--asset-model-composite-model-properties` | No | list | None | Updated properties |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "assetModelCompositeModelPath": [
        {"id": "string", "name": "string"}
    ],
    "assetModelStatus": {
        "state": "CREATING|ACTIVE|UPDATING|PROPAGATING|DELETING|FAILED",
        "error": {}
    }
}
```

---

### 1.11 `delete-asset-model-composite-model`

Deletes a composite model from an asset model.

**Synopsis:**
```bash
aws iotsitewise delete-asset-model-composite-model \
    --asset-model-id <value> \
    --asset-model-composite-model-id <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--asset-model-id` | **Yes** | string | -- | Asset model ID |
| `--asset-model-composite-model-id` | **Yes** | string | -- | Composite model ID to delete |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "assetModelStatus": {
        "state": "DELETING",
        "error": {}
    }
}
```
