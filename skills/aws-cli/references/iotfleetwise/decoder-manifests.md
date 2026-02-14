# Decoder Manifests

### 3.1 `create-decoder-manifest`

Creates a decoder manifest that maps vehicle signals to network protocol decoders.

**Synopsis:**
```bash
aws iotfleetwise create-decoder-manifest \
    --name <value> \
    --model-manifest-arn <value> \
    [--description <value>] \
    [--signal-decoders <value>] \
    [--network-interfaces <value>] \
    [--default-for-unmapped-signals <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Decoder manifest name (1-100 chars) |
| `--model-manifest-arn` | **Yes** | string | -- | ARN of the model manifest |
| `--description` | No | string | None | Description (1-2048 chars) |
| `--signal-decoders` | No | list | None | Signal decoder configurations (1-500) |
| `--network-interfaces` | No | list | None | Network interface definitions (1-500) |
| `--default-for-unmapped-signals` | No | string | None | `CUSTOM_DECODING` |
| `--tags` | No | list | None | Tags (max 50) |

**Network Interface (tagged union):**

CAN Interface:
```json
{
    "interfaceId": "CAN1",
    "type": "CAN_INTERFACE",
    "canInterface": {
        "name": "CAN_Bus_1",
        "protocolName": "CAN",
        "protocolVersion": "2.0"
    }
}
```

OBD Interface:
```json
{
    "interfaceId": "OBD1",
    "type": "OBD_INTERFACE",
    "obdInterface": {
        "name": "OBD_Port",
        "requestMessageId": 2015,
        "obdStandard": "J1979",
        "pidRequestIntervalSeconds": 5,
        "dtcRequestIntervalSeconds": 60,
        "useExtendedIds": false,
        "hasTransmissionEcu": false
    }
}
```

Vehicle Middleware:
```json
{
    "interfaceId": "ROS1",
    "type": "VEHICLE_MIDDLEWARE",
    "vehicleMiddleware": {
        "name": "ROS2_Interface",
        "protocolName": "ROS_2"
    }
}
```

Custom Decoding Interface:
```json
{
    "interfaceId": "CUSTOM1",
    "type": "CUSTOM_DECODING_INTERFACE",
    "customDecodingInterface": {
        "name": "CustomDecoder"
    }
}
```

**Signal Decoder (tagged union):**

CAN Signal:
```json
{
    "fullyQualifiedName": "Vehicle.Speed",
    "type": "CAN_SIGNAL",
    "interfaceId": "CAN1",
    "canSignal": {
        "messageId": 100,
        "isBigEndian": false,
        "isSigned": false,
        "startBit": 0,
        "offset": 0.0,
        "factor": 0.1,
        "length": 16,
        "name": "VehicleSpeed",
        "signalValueType": "INTEGER"
    }
}
```

OBD Signal:
```json
{
    "fullyQualifiedName": "Vehicle.OBD.EngineSpeed",
    "type": "OBD_SIGNAL",
    "interfaceId": "OBD1",
    "obdSignal": {
        "pidResponseLength": 2,
        "serviceMode": 1,
        "pid": 12,
        "scaling": 0.25,
        "offset": 0.0,
        "startByte": 0,
        "byteLength": 2
    }
}
```

Custom Decoding Signal:
```json
{
    "fullyQualifiedName": "Vehicle.CustomSignal",
    "type": "CUSTOM_DECODING_SIGNAL",
    "interfaceId": "CUSTOM1",
    "customDecodingSignal": {
        "id": "my-custom-decoder"
    }
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

### 3.2 `get-decoder-manifest`

Retrieves information about a decoder manifest.

**Synopsis:**
```bash
aws iotfleetwise get-decoder-manifest \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Decoder manifest name |

**Output Schema:**
```json
{
    "name": "string",
    "arn": "string",
    "description": "string",
    "modelManifestArn": "string",
    "status": "ACTIVE|DRAFT|INVALID|VALIDATING",
    "creationTime": "timestamp",
    "lastModificationTime": "timestamp",
    "message": "string"
}
```

---

### 3.3 `list-decoder-manifests`

Lists decoder manifests. **Paginated operation.**

**Synopsis:**
```bash
aws iotfleetwise list-decoder-manifests \
    [--model-manifest-arn <value>] \
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
            "modelManifestArn": "string",
            "description": "string",
            "status": "ACTIVE|DRAFT|INVALID|VALIDATING",
            "creationTime": "timestamp",
            "lastModificationTime": "timestamp",
            "message": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 3.4 `update-decoder-manifest`

Updates a decoder manifest. Must set status to ACTIVE before use.

**Synopsis:**
```bash
aws iotfleetwise update-decoder-manifest \
    --name <value> \
    [--description <value>] \
    [--signal-decoders-to-add <value>] \
    [--signal-decoders-to-update <value>] \
    [--signal-decoders-to-remove <value>] \
    [--network-interfaces-to-add <value>] \
    [--network-interfaces-to-update <value>] \
    [--network-interfaces-to-remove <value>] \
    [--status <value>] \
    [--default-for-unmapped-signals <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Decoder manifest name |
| `--description` | No | string | None | Updated description |
| `--signal-decoders-to-add` | No | list | None | Signal decoders to add |
| `--signal-decoders-to-update` | No | list | None | Signal decoders to update |
| `--signal-decoders-to-remove` | No | list | None | Signal fully qualified names to remove |
| `--network-interfaces-to-add` | No | list | None | Network interfaces to add |
| `--network-interfaces-to-update` | No | list | None | Network interfaces to update |
| `--network-interfaces-to-remove` | No | list | None | Interface IDs to remove |
| `--status` | No | string | None | `ACTIVE` or `DRAFT` |
| `--default-for-unmapped-signals` | No | string | None | `CUSTOM_DECODING` |

**Output Schema:**
```json
{
    "name": "string",
    "arn": "string"
}
```

---

### 3.5 `delete-decoder-manifest`

Deletes a decoder manifest.

**Synopsis:**
```bash
aws iotfleetwise delete-decoder-manifest \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Decoder manifest name |

**Output Schema:**
```json
{
    "name": "string",
    "arn": "string"
}
```

---

### 3.6 `import-decoder-manifest`

Imports a decoder manifest from CAN DBC files.

**Synopsis:**
```bash
aws iotfleetwise import-decoder-manifest \
    --name <value> \
    --network-file-definitions <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Decoder manifest name (1-100 chars) |
| `--network-file-definitions` | **Yes** | list | -- | Network file definitions with CAN DBC files |

**Network File Definition:**
```json
{
    "canDbc": {
        "networkInterface": "string",
        "canDbcFiles": ["blob"],
        "signalsMap": {
            "signalName": "fullyQualifiedName"
        }
    }
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

### 3.7 `list-decoder-manifest-network-interfaces`

Lists network interfaces in a decoder manifest. **Paginated operation.**

**Synopsis:**
```bash
aws iotfleetwise list-decoder-manifest-network-interfaces \
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
| `--name` | **Yes** | string | -- | Decoder manifest name |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "networkInterfaces": [
        {
            "interfaceId": "string",
            "type": "CAN_INTERFACE|OBD_INTERFACE|VEHICLE_MIDDLEWARE|CUSTOM_DECODING_INTERFACE",
            "canInterface": {
                "name": "string",
                "protocolName": "string",
                "protocolVersion": "string"
            },
            "obdInterface": {
                "name": "string",
                "requestMessageId": "integer",
                "obdStandard": "string",
                "pidRequestIntervalSeconds": "integer",
                "dtcRequestIntervalSeconds": "integer",
                "useExtendedIds": "boolean",
                "hasTransmissionEcu": "boolean"
            }
        }
    ],
    "nextToken": "string"
}
```

---

### 3.8 `list-decoder-manifest-signals`

Lists signal decoders in a decoder manifest. **Paginated operation.**

**Synopsis:**
```bash
aws iotfleetwise list-decoder-manifest-signals \
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
| `--name` | **Yes** | string | -- | Decoder manifest name |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "signalDecoders": [
        {
            "fullyQualifiedName": "string",
            "type": "CAN_SIGNAL|OBD_SIGNAL|MESSAGE_SIGNAL|CUSTOM_DECODING_SIGNAL",
            "interfaceId": "string",
            "canSignal": {
                "messageId": "integer",
                "isBigEndian": "boolean",
                "isSigned": "boolean",
                "startBit": "integer",
                "offset": "double",
                "factor": "double",
                "length": "integer",
                "name": "string"
            },
            "obdSignal": {
                "pidResponseLength": "integer",
                "serviceMode": "integer",
                "pid": "integer",
                "scaling": "double",
                "offset": "double",
                "startByte": "integer",
                "byteLength": "integer"
            }
        }
    ],
    "nextToken": "string"
}
```
