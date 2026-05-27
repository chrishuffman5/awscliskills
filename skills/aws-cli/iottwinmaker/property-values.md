# Property Values

### 5.1 `get-property-value`

Gets the current value of entity properties.

**Synopsis:**
```bash
aws iottwinmaker get-property-value \
    --workspace-id <value> \
    --selected-properties <value> \
    [--entity-id <value>] \
    [--component-name <value>] \
    [--component-path <value>] \
    [--component-type-id <value>] \
    [--property-group-name <value>] \
    [--tabular-conditions <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | Workspace ID |
| `--selected-properties` | **Yes** | list | -- | Properties to retrieve (1-10) |
| `--entity-id` | No | string | None | Entity ID |
| `--component-name` | No | string | None | Component name |
| `--component-path` | No | string | None | Path to composite component |
| `--component-type-id` | No | string | None | Component type ID |
| `--property-group-name` | No | string | None | Property group name |
| `--tabular-conditions` | No | structure | None | Filtering and ordering |
| `--max-results` | No | integer | 25 | Max results (1-250) |
| `--next-token` | No | string | None | Pagination token |

**Tabular Conditions:**
```json
{
    "orderBy": [
        {"order": "ASCENDING|DESCENDING", "propertyName": "string"}
    ],
    "propertyFilters": [
        {
            "propertyName": "string",
            "operator": "string",
            "value": {"doubleValue": 0.0, "stringValue": "string"}
        }
    ]
}
```

**Output Schema:**
```json
{
    "propertyValues": {
        "propertyName": {
            "propertyReference": {
                "componentName": "string",
                "componentPath": "string",
                "entityId": "string",
                "propertyName": "string",
                "externalIdProperty": {}
            },
            "propertyValue": {
                "booleanValue": "boolean",
                "doubleValue": "double",
                "integerValue": "integer",
                "longValue": "long",
                "stringValue": "string",
                "listValue": [],
                "mapValue": {},
                "relationshipValue": {
                    "targetEntityId": "string",
                    "targetComponentName": "string"
                }
            }
        }
    },
    "tabularPropertyValues": [],
    "nextToken": "string"
}
```

---

### 5.2 `get-property-value-history`

Gets historical values of time-series properties. **Paginated operation.**

**Synopsis:**
```bash
aws iottwinmaker get-property-value-history \
    --workspace-id <value> \
    --selected-properties <value> \
    [--entity-id <value>] \
    [--component-name <value>] \
    [--component-path <value>] \
    [--component-type-id <value>] \
    [--property-filters <value>] \
    [--start-date-time <value>] \
    [--end-date-time <value>] \
    [--start-time <value>] \
    [--end-time <value>] \
    [--interpolation <value>] \
    [--order-by-time <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | Workspace ID |
| `--selected-properties` | **Yes** | list | -- | Properties to retrieve (1-10) |
| `--entity-id` | Conditional | string | None | Entity ID |
| `--component-name` | Conditional | string | None | Component name |
| `--component-path` | No | string | None | Path to composite component |
| `--component-type-id` | Conditional | string | None | Component type ID |
| `--property-filters` | No | list | None | Property filters (max 10) |
| `--start-date-time` | No | timestamp | None | Start time |
| `--end-date-time` | No | timestamp | None | End time |
| `--start-time` | No | string | None | ISO8601 start time |
| `--end-time` | No | string | None | ISO8601 end time |
| `--interpolation` | No | structure | None | `LINEAR` interpolation with interval |
| `--order-by-time` | No | string | None | `ASCENDING` or `DESCENDING` |
| `--max-results` | No | integer | 25 | Max results (1-250) |
| `--next-token` | No | string | None | Pagination token |

**Interpolation Structure:**
```json
{
    "interpolationType": "LINEAR",
    "intervalInSeconds": "long"
}
```

**Output Schema:**
```json
{
    "propertyValues": [
        {
            "entityPropertyReference": {
                "entityId": "string",
                "componentName": "string",
                "componentPath": "string",
                "propertyName": "string",
                "externalIdProperty": {}
            },
            "values": [
                {
                    "timestamp": "timestamp",
                    "time": "string",
                    "value": {
                        "booleanValue": "boolean",
                        "doubleValue": "double",
                        "integerValue": "integer",
                        "longValue": "long",
                        "stringValue": "string",
                        "listValue": [],
                        "mapValue": {}
                    }
                }
            ]
        }
    ],
    "nextToken": "string"
}
```

---

### 5.3 `batch-put-property-values`

Sends property values to entity components in batch (max 10 entries).

**Synopsis:**
```bash
aws iottwinmaker batch-put-property-values \
    --workspace-id <value> \
    --entries <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | Workspace ID |
| `--entries` | **Yes** | list | -- | Property value entries (1-10) |

**Entry Structure:**
```json
{
    "entityPropertyReference": {
        "entityId": "string",
        "componentName": "string",
        "componentPath": "string",
        "propertyName": "string",
        "externalIdProperty": {}
    },
    "propertyValues": [
        {
            "value": {
                "booleanValue": "boolean",
                "doubleValue": "double",
                "integerValue": "integer",
                "longValue": "long",
                "stringValue": "string"
            },
            "timestamp": "timestamp",
            "time": "string"
        }
    ]
}
```

**Output Schema:**
```json
{
    "errorEntries": [
        {
            "errors": [
                {
                    "errorCode": "string",
                    "errorMessage": "string",
                    "entry": {}
                }
            ]
        }
    ]
}
```
