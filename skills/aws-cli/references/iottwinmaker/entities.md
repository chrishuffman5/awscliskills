# Entities

### 3.1 `create-entity`

Creates an entity in a workspace with optional components.

**Synopsis:**
```bash
aws iottwinmaker create-entity \
    --workspace-id <value> \
    --entity-name <value> \
    [--entity-id <value>] \
    [--description <value>] \
    [--components <value>] \
    [--composite-components <value>] \
    [--parent-entity-id <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | Workspace ID |
| `--entity-name` | **Yes** | string | -- | Entity name (1-256 chars) |
| `--entity-id` | No | string | Auto | Entity ID (1-128 chars) |
| `--description` | No | string | None | Description (0-2048 chars) |
| `--components` | No | map | None | Component definitions |
| `--composite-components` | No | map | None | Composite component definitions |
| `--parent-entity-id` | No | string | None | Parent entity ID |
| `--tags` | No | map | None | Tags (max 50) |

**Component Structure:**
```json
{
    "componentName": {
        "description": "string",
        "componentTypeId": "string",
        "properties": {
            "propertyName": {
                "definition": {
                    "dataType": {"type": "STRING|LONG|BOOLEAN|INTEGER|DOUBLE|LIST|MAP|RELATIONSHIP"},
                    "isRequiredInEntity": "boolean",
                    "isTimeSeries": "boolean"
                },
                "value": {"doubleValue": 0.0, "stringValue": "string"},
                "updateType": "UPDATE|DELETE|CREATE|RESET_VALUE"
            }
        },
        "propertyGroups": {}
    }
}
```

**Output Schema:**
```json
{
    "entityId": "string",
    "arn": "string",
    "creationDateTime": "timestamp",
    "state": "CREATING|ACTIVE|UPDATING|DELETING|ERROR"
}
```

---

### 3.2 `get-entity`

Gets details of an entity including its components and properties.

**Synopsis:**
```bash
aws iottwinmaker get-entity \
    --workspace-id <value> \
    --entity-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | Workspace ID |
| `--entity-id` | **Yes** | string | -- | Entity ID |

**Output Schema:**
```json
{
    "entityId": "string",
    "entityName": "string",
    "arn": "string",
    "status": {
        "state": "CREATING|UPDATING|DELETING|ACTIVE|ERROR",
        "error": {"code": "string", "message": "string"}
    },
    "workspaceId": "string",
    "description": "string",
    "components": {
        "componentName": {
            "componentName": "string",
            "description": "string",
            "componentTypeId": "string",
            "status": {"state": "string", "error": {}},
            "definedIn": "string",
            "properties": {},
            "propertyGroups": {},
            "syncSource": "string",
            "areAllPropertiesReturned": "boolean",
            "compositeComponents": {},
            "areAllCompositeComponentsReturned": "boolean"
        }
    },
    "parentEntityId": "string",
    "hasChildEntities": "boolean",
    "creationDateTime": "timestamp",
    "updateDateTime": "timestamp",
    "syncSource": "string",
    "areAllComponentsReturned": "boolean"
}
```

---

### 3.3 `list-entities`

Lists entities in a workspace. **Paginated operation.**

**Synopsis:**
```bash
aws iottwinmaker list-entities \
    --workspace-id <value> \
    [--filters <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | Workspace ID |
| `--filters` | No | list | None | Filters (by `parentEntityId`, `componentTypeId`, or `externalId`) |
| `--max-results` | No | integer | 25 | Max results per page (1-250) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "entitySummaries": [
        {
            "entityId": "string",
            "entityName": "string",
            "arn": "string",
            "parentEntityId": "string",
            "status": {"state": "string", "error": {}},
            "description": "string",
            "hasChildEntities": "boolean",
            "creationDateTime": "timestamp",
            "updateDateTime": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 3.4 `update-entity`

Updates an entity's components, properties, or parent.

**Synopsis:**
```bash
aws iottwinmaker update-entity \
    --workspace-id <value> \
    --entity-id <value> \
    [--entity-name <value>] \
    [--description <value>] \
    [--component-updates <value>] \
    [--composite-component-updates <value>] \
    [--parent-entity-update <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | Workspace ID |
| `--entity-id` | **Yes** | string | -- | Entity ID |
| `--entity-name` | No | string | None | Updated name |
| `--description` | No | string | None | Updated description |
| `--component-updates` | No | map | None | Component updates |
| `--composite-component-updates` | No | map | None | Composite component updates |
| `--parent-entity-update` | No | structure | None | Parent entity update |

**Component Update Structure:**
```json
{
    "componentName": {
        "updateType": "CREATE|UPDATE|DELETE",
        "description": "string",
        "componentTypeId": "string",
        "propertyUpdates": {
            "propertyName": {
                "definition": {},
                "value": {},
                "updateType": "UPDATE|DELETE|CREATE|RESET_VALUE"
            }
        },
        "propertyGroupUpdates": {}
    }
}
```

**Parent Entity Update:**
```json
{
    "updateType": "UPDATE|DELETE",
    "parentEntityId": "string"
}
```

**Output Schema:**
```json
{
    "updateDateTime": "timestamp",
    "state": "CREATING|UPDATING|DELETING|ACTIVE|ERROR"
}
```

---

### 3.5 `delete-entity`

Deletes an entity and optionally its child entities.

**Synopsis:**
```bash
aws iottwinmaker delete-entity \
    --workspace-id <value> \
    --entity-id <value> \
    [--is-recursive | --no-is-recursive] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | Workspace ID |
| `--entity-id` | **Yes** | string | -- | Entity ID |
| `--is-recursive` | No | boolean | false | Delete child entities recursively |

**Output Schema:**
```json
{
    "state": "DELETING|ERROR"
}
```

---

### 3.6 `list-components`

Lists the components of an entity. **Paginated operation.**

**Synopsis:**
```bash
aws iottwinmaker list-components \
    --workspace-id <value> \
    --entity-id <value> \
    [--component-path <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | Workspace ID |
| `--entity-id` | **Yes** | string | -- | Entity ID |
| `--component-path` | No | string | None | Path to composite component |
| `--max-results` | No | integer | 25 | Max results per page |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "componentSummaries": [
        {
            "componentName": "string",
            "componentTypeId": "string",
            "definedIn": "string",
            "description": "string",
            "propertyGroups": {},
            "status": {"state": "string", "error": {}},
            "syncSource": "string",
            "componentPath": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 3.7 `list-properties`

Lists the properties of a component. **Paginated operation.**

**Synopsis:**
```bash
aws iottwinmaker list-properties \
    --workspace-id <value> \
    --entity-id <value> \
    --component-name <value> \
    [--component-path <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | Workspace ID |
| `--entity-id` | **Yes** | string | -- | Entity ID |
| `--component-name` | **Yes** | string | -- | Component name |
| `--component-path` | No | string | None | Path to composite component |
| `--max-results` | No | integer | 25 | Max results per page |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "propertySummaries": [
        {
            "definition": {
                "dataType": {"type": "string"},
                "isTimeSeries": "boolean",
                "isRequiredInEntity": "boolean",
                "isExternalId": "boolean",
                "isStoredExternally": "boolean",
                "isImported": "boolean",
                "isFinal": "boolean",
                "isInherited": "boolean",
                "defaultValue": {},
                "configuration": {},
                "displayName": "string"
            },
            "propertyName": "string",
            "value": {},
            "areAllPropertyValuesReturned": "boolean"
        }
    ],
    "nextToken": "string"
}
```
