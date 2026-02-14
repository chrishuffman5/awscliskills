# Signal Catalogs

### 1.1 `create-signal-catalog`

Creates a signal catalog containing vehicle signal definitions (branches, sensors, actuators, attributes).

**Synopsis:**
```bash
aws iotfleetwise create-signal-catalog \
    --name <value> \
    [--description <value>] \
    [--nodes <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Signal catalog name (1-100 chars) |
| `--description` | No | string | None | Description (1-2048 chars) |
| `--nodes` | No | list | None | Signal nodes to add (max 500) |
| `--tags` | No | list | None | Tags (max 50) |

**Node Types (tagged union — one type per node):**

Sensor:
```json
{
    "sensor": {
        "fullyQualifiedName": "Vehicle.Speed",
        "dataType": "DOUBLE",
        "description": "Vehicle speed",
        "unit": "km/h",
        "min": 0,
        "max": 300
    }
}
```

Branch:
```json
{
    "branch": {
        "fullyQualifiedName": "Vehicle",
        "description": "Top-level vehicle branch"
    }
}
```

Actuator:
```json
{
    "actuator": {
        "fullyQualifiedName": "Vehicle.Chassis.SteeringWheel.Angle",
        "dataType": "DOUBLE",
        "unit": "degrees"
    }
}
```

Attribute:
```json
{
    "attribute": {
        "fullyQualifiedName": "Vehicle.VehicleIdentification.VIN",
        "dataType": "STRING",
        "defaultValue": ""
    }
}
```

**Data types:** `INT8`, `UINT8`, `INT16`, `UINT16`, `INT32`, `UINT32`, `INT64`, `UINT64`, `BOOLEAN`, `FLOAT`, `DOUBLE`, `STRING`, `UNIX_TIMESTAMP`, `INT8_ARRAY`, `UINT8_ARRAY`, `INT16_ARRAY`, `UINT16_ARRAY`, `INT32_ARRAY`, `UINT32_ARRAY`, `INT64_ARRAY`, `UINT64_ARRAY`, `BOOLEAN_ARRAY`, `FLOAT_ARRAY`, `DOUBLE_ARRAY`, `STRING_ARRAY`, `UNIX_TIMESTAMP_ARRAY`, `UNKNOWN`, `STRUCT`, `STRUCT_ARRAY`

**Output Schema:**
```json
{
    "name": "string",
    "arn": "string"
}
```

---

### 1.2 `get-signal-catalog`

Retrieves information about a signal catalog.

**Synopsis:**
```bash
aws iotfleetwise get-signal-catalog \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Signal catalog name |

**Output Schema:**
```json
{
    "name": "string",
    "arn": "string",
    "description": "string",
    "nodeCounts": {
        "totalNodes": "integer",
        "totalBranches": "integer",
        "totalSensors": "integer",
        "totalAttributes": "integer",
        "totalActuators": "integer",
        "totalStructs": "integer",
        "totalProperties": "integer"
    },
    "creationTime": "timestamp",
    "lastModificationTime": "timestamp"
}
```

---

### 1.3 `list-signal-catalogs`

Lists signal catalogs. **Paginated operation.**

**Synopsis:**
```bash
aws iotfleetwise list-signal-catalogs \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
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
            "creationTime": "timestamp",
            "lastModificationTime": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 1.4 `update-signal-catalog`

Updates a signal catalog by adding, modifying, or removing nodes.

**Synopsis:**
```bash
aws iotfleetwise update-signal-catalog \
    --name <value> \
    [--description <value>] \
    [--nodes-to-add <value>] \
    [--nodes-to-update <value>] \
    [--nodes-to-remove <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Signal catalog name |
| `--description` | No | string | None | Updated description |
| `--nodes-to-add` | No | list | None | Nodes to add (max 500) |
| `--nodes-to-update` | No | list | None | Nodes to update (max 500) |
| `--nodes-to-remove` | No | list | None | Fully qualified names to remove (max 500) |

**Output Schema:**
```json
{
    "name": "string",
    "arn": "string"
}
```

---

### 1.5 `delete-signal-catalog`

Deletes a signal catalog.

**Synopsis:**
```bash
aws iotfleetwise delete-signal-catalog \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Signal catalog name |

**Output Schema:**
```json
{
    "name": "string",
    "arn": "string"
}
```

---

### 1.6 `import-signal-catalog`

Imports a signal catalog from a Vehicle Signal Specification (VSS) JSON file.

**Synopsis:**
```bash
aws iotfleetwise import-signal-catalog \
    --name <value> \
    [--description <value>] \
    [--vss <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Signal catalog name (1-100 chars) |
| `--description` | No | string | None | Description (1-2048 chars) |
| `--vss` | No | structure | None | VSS configuration |
| `--tags` | No | list | None | Tags (max 50) |

**VSS structure:**
```json
{
    "vssJson": "string"
}
```

**Output Schema:**
```json
{
    "name": "string",
    "arn": "string"
}
```

---

### 1.7 `list-signal-catalog-nodes`

Lists nodes (signals) in a signal catalog. **Paginated operation.**

**Synopsis:**
```bash
aws iotfleetwise list-signal-catalog-nodes \
    --name <value> \
    [--signal-node-type <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Signal catalog name |
| `--signal-node-type` | No | string | None | Filter: `SENSOR`, `ACTUATOR`, `ATTRIBUTE`, `BRANCH`, `CUSTOM_STRUCT`, `CUSTOM_PROPERTY` |
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
                "unit": "string",
                "min": "double",
                "max": "double"
            },
            "actuator": {
                "fullyQualifiedName": "string",
                "dataType": "string",
                "description": "string",
                "unit": "string"
            },
            "attribute": {
                "fullyQualifiedName": "string",
                "dataType": "string",
                "description": "string",
                "defaultValue": "string"
            }
        }
    ],
    "nextToken": "string"
}
```
