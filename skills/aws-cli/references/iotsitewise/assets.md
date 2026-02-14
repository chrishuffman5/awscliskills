# Assets

### 2.1 `create-asset`

Creates an asset from an existing asset model.

**Synopsis:**
```bash
aws iotsitewise create-asset \
    --asset-name <value> \
    --asset-model-id <value> \
    [--asset-id <value>] \
    [--asset-external-id <value>] \
    [--asset-description <value>] \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--asset-name` | **Yes** | string | -- | Asset name (1-256 chars) |
| `--asset-model-id` | **Yes** | string | -- | Asset model ID (UUID or `externalId:`) |
| `--asset-id` | No | string | Auto | UUID for the asset |
| `--asset-external-id` | No | string | None | External ID (2-128 chars) |
| `--asset-description` | No | string | None | Description (1-2048 chars) |
| `--tags` | No | map | None | Tags (max 50) |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "assetId": "string",
    "assetArn": "string",
    "assetStatus": {
        "state": "CREATING|ACTIVE|UPDATING|DELETING|FAILED",
        "error": {
            "code": "VALIDATION_ERROR|INTERNAL_FAILURE",
            "message": "string"
        }
    }
}
```

---

### 2.2 `describe-asset`

Describes an asset including its properties, hierarchies, and status.

**Synopsis:**
```bash
aws iotsitewise describe-asset \
    --asset-id <value> \
    [--exclude-properties | --no-exclude-properties] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--asset-id` | **Yes** | string | -- | Asset ID (UUID or `externalId:`) |
| `--exclude-properties` | No | boolean | false | Exclude properties from response |

**Output Schema:**
```json
{
    "assetId": "string",
    "assetExternalId": "string",
    "assetArn": "string",
    "assetName": "string",
    "assetModelId": "string",
    "assetProperties": [
        {
            "id": "string",
            "externalId": "string",
            "name": "string",
            "alias": "string",
            "notification": {"topic": "string", "state": "ENABLED|DISABLED"},
            "dataType": "STRING|INTEGER|DOUBLE|BOOLEAN|STRUCT",
            "dataTypeSpec": "string",
            "unit": "string",
            "path": [{"id": "string", "name": "string"}]
        }
    ],
    "assetHierarchies": [
        {"id": "string", "externalId": "string", "name": "string"}
    ],
    "assetCompositeModels": [],
    "assetCreationDate": "timestamp",
    "assetLastUpdateDate": "timestamp",
    "assetStatus": {
        "state": "CREATING|ACTIVE|UPDATING|DELETING|FAILED",
        "error": {}
    },
    "assetDescription": "string"
}
```

---

### 2.3 `list-assets`

Lists assets. Optionally filters by asset model. **Paginated operation.**

**Synopsis:**
```bash
aws iotsitewise list-assets \
    [--asset-model-id <value>] \
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
| `--asset-model-id` | No | string | None | Filter by asset model ID |
| `--filter` | No | string | `ALL` | `ALL` or `TOP_LEVEL` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "assetSummaries": [
        {
            "id": "string",
            "externalId": "string",
            "arn": "string",
            "name": "string",
            "assetModelId": "string",
            "creationDate": "timestamp",
            "lastUpdateDate": "timestamp",
            "status": {"state": "CREATING|ACTIVE|UPDATING|DELETING|FAILED", "error": {}},
            "hierarchies": [{"id": "string", "externalId": "string", "name": "string"}],
            "description": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 2.4 `update-asset`

Updates an asset's name or description.

**Synopsis:**
```bash
aws iotsitewise update-asset \
    --asset-id <value> \
    --asset-name <value> \
    [--asset-external-id <value>] \
    [--asset-description <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--asset-id` | **Yes** | string | -- | Asset ID |
| `--asset-name` | **Yes** | string | -- | Updated name |
| `--asset-external-id` | No | string | None | Updated external ID |
| `--asset-description` | No | string | None | Updated description |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "assetStatus": {
        "state": "UPDATING",
        "error": {}
    }
}
```

---

### 2.5 `delete-asset`

Deletes an asset. The asset must be disassociated from all hierarchies first.

**Synopsis:**
```bash
aws iotsitewise delete-asset \
    --asset-id <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--asset-id` | **Yes** | string | -- | Asset ID |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "assetStatus": {
        "state": "DELETING",
        "error": {}
    }
}
```

---

### 2.6 `describe-asset-property`

Describes an asset property including its definition from the asset model.

**Synopsis:**
```bash
aws iotsitewise describe-asset-property \
    --asset-id <value> \
    --property-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--asset-id` | **Yes** | string | -- | Asset ID |
| `--property-id` | **Yes** | string | -- | Property ID |

**Output Schema:**
```json
{
    "assetId": "string",
    "assetExternalId": "string",
    "assetName": "string",
    "assetModelId": "string",
    "assetProperty": {
        "id": "string",
        "externalId": "string",
        "name": "string",
        "alias": "string",
        "notification": {"topic": "string", "state": "ENABLED|DISABLED"},
        "dataType": "STRING|INTEGER|DOUBLE|BOOLEAN|STRUCT",
        "unit": "string",
        "type": {},
        "path": []
    },
    "compositeModel": {}
}
```

---

### 2.7 `update-asset-property`

Updates an asset property's alias and notification state.

**Synopsis:**
```bash
aws iotsitewise update-asset-property \
    --asset-id <value> \
    --property-id <value> \
    [--property-alias <value>] \
    [--property-notification-state <value>] \
    [--property-unit <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--asset-id` | **Yes** | string | -- | Asset ID |
| `--property-id` | **Yes** | string | -- | Property ID |
| `--property-alias` | No | string | None | Property alias path |
| `--property-notification-state` | No | string | None | `ENABLED` or `DISABLED` |
| `--property-unit` | No | string | None | Unit of measure |
| `--client-token` | No | string | Auto | Idempotency token |

**Output:** None

---

### 2.8 `list-asset-properties`

Lists the properties of an asset. **Paginated operation.**

**Synopsis:**
```bash
aws iotsitewise list-asset-properties \
    --asset-id <value> \
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
| `--asset-id` | **Yes** | string | -- | Asset ID |
| `--filter` | No | string | `ALL` | `ALL` or `BASE` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "assetPropertySummaries": [
        {
            "id": "string",
            "externalId": "string",
            "alias": "string",
            "notification": {"topic": "string", "state": "ENABLED|DISABLED"},
            "assetCompositeModelId": "string",
            "path": [{"id": "string", "name": "string"}],
            "unit": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 2.9 `describe-asset-composite-model`

Describes a composite model for a specific asset.

**Synopsis:**
```bash
aws iotsitewise describe-asset-composite-model \
    --asset-id <value> \
    --asset-composite-model-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--asset-id` | **Yes** | string | -- | Asset ID |
| `--asset-composite-model-id` | **Yes** | string | -- | Composite model ID |

**Output Schema:**
```json
{
    "assetId": "string",
    "assetCompositeModelId": "string",
    "assetCompositeModelExternalId": "string",
    "assetCompositeModelPath": [],
    "assetCompositeModelName": "string",
    "assetCompositeModelDescription": "string",
    "assetCompositeModelType": "string",
    "assetCompositeModelProperties": [],
    "assetCompositeModelSummaries": [],
    "actionDefinitions": []
}
```

---

### 2.10 `list-asset-relationships`

Lists asset relationships. **Paginated operation.**

**Synopsis:**
```bash
aws iotsitewise list-asset-relationships \
    --asset-id <value> \
    --traversal-type <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--asset-id` | **Yes** | string | -- | Asset ID |
| `--traversal-type` | **Yes** | string | -- | `PATH_TO_ROOT` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "assetRelationshipSummaries": [
        {
            "hierarchyInfo": {
                "parentAssetId": "string",
                "childAssetId": "string"
            },
            "relationshipType": "HIERARCHY"
        }
    ],
    "nextToken": "string"
}
```

---

### 2.11 `associate-assets`

Associates a child asset to a parent asset through a hierarchy.

**Synopsis:**
```bash
aws iotsitewise associate-assets \
    --asset-id <value> \
    --hierarchy-id <value> \
    --child-asset-id <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--asset-id` | **Yes** | string | -- | Parent asset ID |
| `--hierarchy-id` | **Yes** | string | -- | Hierarchy ID in the parent model |
| `--child-asset-id` | **Yes** | string | -- | Child asset ID |
| `--client-token` | No | string | Auto | Idempotency token |

**Output:** None

---

### 2.12 `disassociate-assets`

Disassociates a child asset from a parent asset.

**Synopsis:**
```bash
aws iotsitewise disassociate-assets \
    --asset-id <value> \
    --hierarchy-id <value> \
    --child-asset-id <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--asset-id` | **Yes** | string | -- | Parent asset ID |
| `--hierarchy-id` | **Yes** | string | -- | Hierarchy ID |
| `--child-asset-id` | **Yes** | string | -- | Child asset ID |
| `--client-token` | No | string | Auto | Idempotency token |

**Output:** None

---

### 2.13 `list-associated-assets`

Lists assets associated to a parent asset through a hierarchy. **Paginated operation.**

**Synopsis:**
```bash
aws iotsitewise list-associated-assets \
    --asset-id <value> \
    [--hierarchy-id <value>] \
    [--traversal-direction <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--asset-id` | **Yes** | string | -- | Asset ID |
| `--hierarchy-id` | No | string | None | Hierarchy ID to filter by |
| `--traversal-direction` | No | string | `CHILD` | `CHILD` or `PARENT` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "assetSummaries": [
        {
            "id": "string",
            "externalId": "string",
            "arn": "string",
            "name": "string",
            "assetModelId": "string",
            "creationDate": "timestamp",
            "lastUpdateDate": "timestamp",
            "status": {"state": "string", "error": {}},
            "hierarchies": [],
            "description": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 2.14 `associate-time-series-to-asset-property`

Associates a time series with an asset property.

**Synopsis:**
```bash
aws iotsitewise associate-time-series-to-asset-property \
    --alias <value> \
    --asset-id <value> \
    --property-id <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--alias` | **Yes** | string | -- | Time series alias |
| `--asset-id` | **Yes** | string | -- | Asset ID |
| `--property-id` | **Yes** | string | -- | Property ID |
| `--client-token` | No | string | Auto | Idempotency token |

**Output:** None

---

### 2.15 `disassociate-time-series-from-asset-property`

Disassociates a time series from an asset property.

**Synopsis:**
```bash
aws iotsitewise disassociate-time-series-from-asset-property \
    --alias <value> \
    --asset-id <value> \
    --property-id <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--alias` | **Yes** | string | -- | Time series alias |
| `--asset-id` | **Yes** | string | -- | Asset ID |
| `--property-id` | **Yes** | string | -- | Property ID |
| `--client-token` | No | string | Auto | Idempotency token |

**Output:** None
