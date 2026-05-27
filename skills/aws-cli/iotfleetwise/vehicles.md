# Vehicles

### 4.1 `create-vehicle`

Creates a vehicle and associates it with a model manifest and decoder manifest.

**Synopsis:**
```bash
aws iotfleetwise create-vehicle \
    --vehicle-name <value> \
    --model-manifest-arn <value> \
    --decoder-manifest-arn <value> \
    [--attributes <value>] \
    [--association-behavior <value>] \
    [--tags <value>] \
    [--state-templates <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--vehicle-name` | **Yes** | string | -- | Vehicle name (1-100 chars) |
| `--model-manifest-arn` | **Yes** | string | -- | ARN of the vehicle model manifest |
| `--decoder-manifest-arn` | **Yes** | string | -- | ARN of the decoder manifest |
| `--attributes` | No | map | None | Static key-value pairs (e.g., make, model, year) |
| `--association-behavior` | No | string | CreateIotThing | `CreateIotThing` or `ValidateIotThingExists` |
| `--tags` | No | list | None | Tags (max 50) |
| `--state-templates` | No | list | None | State templates to associate (1-20) |

**State Template Association:**
```json
[
    {
        "identifier": "string",
        "stateTemplateUpdateStrategy": {
            "periodic": {
                "stateTemplateUpdateRate": {
                    "unit": "MILLISECOND|SECOND|MINUTE|HOUR",
                    "value": 60
                }
            }
        }
    }
]
```

**Output Schema:**
```json
{
    "vehicleName": "string",
    "arn": "string",
    "thingArn": "string"
}
```

---

### 4.2 `get-vehicle`

Retrieves information about a vehicle.

**Synopsis:**
```bash
aws iotfleetwise get-vehicle \
    --vehicle-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--vehicle-name` | **Yes** | string | -- | Vehicle name |

**Output Schema:**
```json
{
    "vehicleName": "string",
    "arn": "string",
    "modelManifestArn": "string",
    "decoderManifestArn": "string",
    "attributes": {
        "string": "string"
    },
    "stateTemplates": [
        {
            "identifier": "string",
            "stateTemplateUpdateStrategy": {
                "periodic": {
                    "stateTemplateUpdateRate": {
                        "unit": "MILLISECOND|SECOND|MINUTE|HOUR",
                        "value": "integer"
                    }
                },
                "onChange": {}
            }
        }
    ],
    "creationTime": "timestamp",
    "lastModificationTime": "timestamp"
}
```

---

### 4.3 `list-vehicles`

Lists vehicles. **Paginated operation.**

**Synopsis:**
```bash
aws iotfleetwise list-vehicles \
    [--model-manifest-arn <value>] \
    [--attribute-names <value>] \
    [--attribute-values <value>] \
    [--list-response-scope <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--model-manifest-arn` | No | string | None | Filter by model manifest ARN |
| `--attribute-names` | No | list | None | Filter by attribute names (1-5) |
| `--attribute-values` | No | list | None | Corresponding attribute values (1-5) |
| `--list-response-scope` | No | string | None | `METADATA_ONLY` for name/ARN/timestamps only |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "vehicleSummaries": [
        {
            "vehicleName": "string",
            "arn": "string",
            "modelManifestArn": "string",
            "decoderManifestArn": "string",
            "creationTime": "timestamp",
            "lastModificationTime": "timestamp",
            "attributes": {
                "string": "string"
            }
        }
    ],
    "nextToken": "string"
}
```

---

### 4.4 `update-vehicle`

Updates a vehicle's attributes, model manifest, decoder manifest, or state templates.

**Synopsis:**
```bash
aws iotfleetwise update-vehicle \
    --vehicle-name <value> \
    [--model-manifest-arn <value>] \
    [--decoder-manifest-arn <value>] \
    [--attributes <value>] \
    [--attribute-update-mode <value>] \
    [--state-templates-to-add <value>] \
    [--state-templates-to-remove <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--vehicle-name` | **Yes** | string | -- | Vehicle name |
| `--model-manifest-arn` | No | string | None | Updated model manifest ARN |
| `--decoder-manifest-arn` | No | string | None | Updated decoder manifest ARN |
| `--attributes` | No | map | None | Updated attributes |
| `--attribute-update-mode` | No | string | None | `Merge` or `Overwrite` |
| `--state-templates-to-add` | No | list | None | State templates to add (1-20) |
| `--state-templates-to-remove` | No | list | None | State template IDs to remove |

**Output Schema:**
```json
{
    "vehicleName": "string",
    "arn": "string"
}
```

---

### 4.5 `delete-vehicle`

Deletes a vehicle and its associated IoT thing.

**Synopsis:**
```bash
aws iotfleetwise delete-vehicle \
    --vehicle-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--vehicle-name` | **Yes** | string | -- | Vehicle name |

**Output Schema:**
```json
{
    "vehicleName": "string",
    "arn": "string"
}
```

---

### 4.6 `batch-create-vehicle`

Creates multiple vehicles in a single batch operation.

**Synopsis:**
```bash
aws iotfleetwise batch-create-vehicle \
    --vehicles <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--vehicles` | **Yes** | list | -- | Vehicle definitions (1-10 per batch) |

**Vehicle definition:**
```json
[
    {
        "vehicleName": "string",
        "modelManifestArn": "string",
        "decoderManifestArn": "string",
        "attributes": {"string": "string"},
        "associationBehavior": "CreateIotThing|ValidateIotThingExists",
        "tags": [{"Key": "string", "Value": "string"}],
        "stateTemplates": [{"identifier": "string", "stateTemplateUpdateStrategy": {}}]
    }
]
```

**Output Schema:**
```json
{
    "vehicles": [
        {
            "vehicleName": "string",
            "arn": "string",
            "thingArn": "string"
        }
    ],
    "errors": [
        {
            "vehicleName": "string",
            "code": "string",
            "message": "string"
        }
    ]
}
```

---

### 4.7 `batch-update-vehicle`

Updates multiple vehicles in a single batch operation.

**Synopsis:**
```bash
aws iotfleetwise batch-update-vehicle \
    --vehicles <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--vehicles` | **Yes** | list | -- | Vehicle update definitions (1-10 per batch) |

**Vehicle update definition:**
```json
[
    {
        "vehicleName": "string",
        "modelManifestArn": "string",
        "decoderManifestArn": "string",
        "attributes": {"string": "string"},
        "attributeUpdateMode": "Merge|Overwrite"
    }
]
```

**Output Schema:**
```json
{
    "vehicles": [
        {
            "vehicleName": "string",
            "arn": "string"
        }
    ],
    "errors": [
        {
            "vehicleName": "string",
            "code": "string",
            "message": "string"
        }
    ]
}
```

---

### 4.8 `get-vehicle-status`

Retrieves the provisioning status of a vehicle's campaigns. **Paginated operation.**

**Synopsis:**
```bash
aws iotfleetwise get-vehicle-status \
    --vehicle-name <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--vehicle-name` | **Yes** | string | -- | Vehicle name |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "campaigns": [
        {
            "campaignName": "string",
            "vehicleName": "string",
            "status": "CREATED|READY|HEALTHY|SUSPENDED|DELETING|FAILED"
        }
    ],
    "nextToken": "string"
}
```
