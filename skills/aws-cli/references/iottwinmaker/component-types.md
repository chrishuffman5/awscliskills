# Component Types

### 2.1 `create-component-type`

Creates a component type that defines property schemas and functions.

**Synopsis:**
```bash
aws iottwinmaker create-component-type \
    --workspace-id <value> \
    --component-type-id <value> \
    [--is-singleton | --no-is-singleton] \
    [--description <value>] \
    [--component-type-name <value>] \
    [--property-definitions <value>] \
    [--extends-from <value>] \
    [--functions <value>] \
    [--property-groups <value>] \
    [--composite-component-types <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | Workspace ID |
| `--component-type-id` | **Yes** | string | -- | Component type ID (1-256 chars) |
| `--is-singleton` | No | boolean | false | Only one component of this type per entity |
| `--description` | No | string | None | Description (0-2048 chars) |
| `--component-type-name` | No | string | None | Display name (0-256 chars) |
| `--property-definitions` | No | map | None | Property definitions |
| `--extends-from` | No | list | None | Parent component types to extend |
| `--functions` | No | map | None | Lambda functions |
| `--property-groups` | No | map | None | Property group definitions |
| `--composite-component-types` | No | map | None | Composite component types |
| `--tags` | No | map | None | Tags (max 50) |

**Property Definition Structure:**
```json
{
    "propertyName": {
        "dataType": {
            "type": "STRING|LONG|BOOLEAN|INTEGER|DOUBLE|LIST|MAP|RELATIONSHIP",
            "nestedType": {},
            "allowedValues": [],
            "unitOfMeasure": "string",
            "relationship": {
                "targetComponentTypeId": "string",
                "relationshipType": "string"
            }
        },
        "isRequiredInEntity": "boolean",
        "isExternalId": "boolean",
        "isStoredExternally": "boolean",
        "isTimeSeries": "boolean",
        "defaultValue": {},
        "configuration": {"key": "value"},
        "displayName": "string"
    }
}
```

**Functions Structure:**
```json
{
    "functionName": {
        "requiredProperties": ["string"],
        "scope": "ENTITY|WORKSPACE",
        "implementedBy": {
            "lambda": {"arn": "string"},
            "isNative": "boolean"
        }
    }
}
```

**Output Schema:**
```json
{
    "arn": "string",
    "creationDateTime": "timestamp",
    "state": "CREATING|UPDATING|DELETING|ACTIVE|ERROR"
}
```

---

### 2.2 `get-component-type`

Gets details of a component type including its properties and functions.

**Synopsis:**
```bash
aws iottwinmaker get-component-type \
    --workspace-id <value> \
    --component-type-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | Workspace ID |
| `--component-type-id` | **Yes** | string | -- | Component type ID |

**Output Schema:**
```json
{
    "workspaceId": "string",
    "componentTypeId": "string",
    "componentTypeName": "string",
    "isSingleton": "boolean",
    "description": "string",
    "propertyDefinitions": {},
    "extendsFrom": ["string"],
    "functions": {},
    "creationDateTime": "timestamp",
    "updateDateTime": "timestamp",
    "arn": "string",
    "isAbstract": "boolean",
    "isSchemaInitialized": "boolean",
    "status": {
        "state": "CREATING|UPDATING|DELETING|ACTIVE|ERROR",
        "error": {"code": "string", "message": "string"}
    },
    "propertyGroups": {},
    "syncSource": "string",
    "compositeComponentTypes": {}
}
```

---

### 2.3 `list-component-types`

Lists component types in a workspace. **Paginated operation.**

**Synopsis:**
```bash
aws iottwinmaker list-component-types \
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
| `--filters` | No | list | None | Filters (by `extendsFrom`, `namespace`, or `isAbstract`) |
| `--max-results` | No | integer | 25 | Max results per page (1-250) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "workspaceId": "string",
    "componentTypeSummaries": [
        {
            "arn": "string",
            "componentTypeId": "string",
            "componentTypeName": "string",
            "creationDateTime": "timestamp",
            "updateDateTime": "timestamp",
            "description": "string",
            "status": {"state": "string", "error": {}}
        }
    ],
    "nextToken": "string"
}
```

---

### 2.4 `update-component-type`

Updates a component type.

**Synopsis:**
```bash
aws iottwinmaker update-component-type \
    --workspace-id <value> \
    --component-type-id <value> \
    [--is-singleton | --no-is-singleton] \
    [--description <value>] \
    [--component-type-name <value>] \
    [--property-definitions <value>] \
    [--extends-from <value>] \
    [--functions <value>] \
    [--property-groups <value>] \
    [--composite-component-types <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | Workspace ID |
| `--component-type-id` | **Yes** | string | -- | Component type ID |
| `--is-singleton` | No | boolean | None | Updated singleton setting |
| `--description` | No | string | None | Updated description |
| `--component-type-name` | No | string | None | Updated display name |
| `--property-definitions` | No | map | None | Updated property definitions |
| `--extends-from` | No | list | None | Updated parent types |
| `--functions` | No | map | None | Updated functions |
| `--property-groups` | No | map | None | Updated property groups |
| `--composite-component-types` | No | map | None | Updated composite types |

**Output Schema:**
```json
{
    "workspaceId": "string",
    "arn": "string",
    "componentTypeId": "string",
    "state": "CREATING|UPDATING|DELETING|ACTIVE|ERROR"
}
```

---

### 2.5 `delete-component-type`

Deletes a component type. No entities can reference this type.

**Synopsis:**
```bash
aws iottwinmaker delete-component-type \
    --workspace-id <value> \
    --component-type-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | Workspace ID |
| `--component-type-id` | **Yes** | string | -- | Component type ID |

**Output Schema:**
```json
{
    "state": "DELETING"
}
```
