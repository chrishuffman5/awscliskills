# Device Pools

### 2.1 `create-device-pool`

Creates a device pool.

**Synopsis:**
```bash
aws devicefarm create-device-pool \
    --project-arn <value> \
    --name <value> \
    --rules <value> \
    [--description <value>] \
    [--max-devices <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project-arn` | **Yes** | string | -- | ARN of the project for the device pool |
| `--name` | **Yes** | string | -- | Name of the device pool |
| `--rules` | **Yes** | list | -- | Rules for device selection. JSON: `[{"attribute":"string","operator":"string","value":"string"}]` |
| `--description` | No | string | None | Description of the device pool |
| `--max-devices` | No | integer | None | Maximum number of devices in the pool |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |

**Rule Attributes:** `ARN`, `PLATFORM`, `FORM_FACTOR`, `MANUFACTURER`, `REMOTE_ACCESS_ENABLED`, `REMOTE_DEBUG_ENABLED`, `APPIUM_VERSION`, `INSTANCE_ARN`, `INSTANCE_LABELS`, `FLEET_TYPE`, `OS_VERSION`, `MODEL`, `AVAILABILITY`

**Rule Operators:** `EQUALS`, `LESS_THAN`, `LESS_THAN_OR_EQUALS`, `GREATER_THAN`, `GREATER_THAN_OR_EQUALS`, `IN`, `NOT_IN`, `CONTAINS`

**Output Schema:**
```json
{
    "devicePool": {
        "arn": "string",
        "name": "string",
        "description": "string",
        "type": "CURATED|PRIVATE",
        "rules": [
            {
                "attribute": "ARN|PLATFORM|FORM_FACTOR|MANUFACTURER|REMOTE_ACCESS_ENABLED|REMOTE_DEBUG_ENABLED|APPIUM_VERSION|INSTANCE_ARN|INSTANCE_LABELS|FLEET_TYPE|OS_VERSION|MODEL|AVAILABILITY",
                "operator": "EQUALS|LESS_THAN|LESS_THAN_OR_EQUALS|GREATER_THAN|GREATER_THAN_OR_EQUALS|IN|NOT_IN|CONTAINS",
                "value": "string"
            }
        ],
        "maxDevices": "integer"
    }
}
```

---

### 2.2 `delete-device-pool`

Deletes a device pool.

**Synopsis:**
```bash
aws devicefarm delete-device-pool \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the device pool to delete |

**Output Schema:**
```json
{}
```

---

### 2.3 `get-device-pool`

Gets information about a device pool.

**Synopsis:**
```bash
aws devicefarm get-device-pool \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the device pool |

**Output Schema:**
```json
{
    "devicePool": {
        "arn": "string",
        "name": "string",
        "description": "string",
        "type": "CURATED|PRIVATE",
        "rules": [
            {
                "attribute": "string",
                "operator": "string",
                "value": "string"
            }
        ],
        "maxDevices": "integer"
    }
}
```

---

### 2.4 `list-device-pools`

Gets information about device pools. **Paginated operation.**

**Synopsis:**
```bash
aws devicefarm list-device-pools \
    --arn <value> \
    [--type <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the project |
| `--type` | No | string | None | Filter by type: `CURATED` or `PRIVATE` |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "devicePools": [
        {
            "arn": "string",
            "name": "string",
            "description": "string",
            "type": "CURATED|PRIVATE",
            "rules": [],
            "maxDevices": "integer"
        }
    ],
    "nextToken": "string"
}
```

---

### 2.5 `update-device-pool`

Modifies a device pool.

**Synopsis:**
```bash
aws devicefarm update-device-pool \
    --arn <value> \
    [--name <value>] \
    [--description <value>] \
    [--rules <value>] \
    [--max-devices <value>] \
    [--clear-max-devices | --no-clear-max-devices] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the device pool to update |
| `--name` | No | string | None | Updated name |
| `--description` | No | string | None | Updated description |
| `--rules` | No | list | None | Updated rules |
| `--max-devices` | No | integer | None | Updated max devices |
| `--clear-max-devices` | No | boolean | false | Clear the max devices setting |

**Output Schema:**
```json
{
    "devicePool": {
        "arn": "string",
        "name": "string",
        "description": "string",
        "type": "CURATED|PRIVATE",
        "rules": [],
        "maxDevices": "integer"
    }
}
```

---

### 2.6 `get-device-pool-compatibility`

Gets information about compatibility with a device pool.

**Synopsis:**
```bash
aws devicefarm get-device-pool-compatibility \
    --device-pool-arn <value> \
    [--app-arn <value>] \
    [--test-type <value>] \
    [--test <value>] \
    [--configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--device-pool-arn` | **Yes** | string | -- | ARN of the device pool |
| `--app-arn` | No | string | None | ARN of the app to check compatibility with |
| `--test-type` | No | string | None | Test type: `BUILTIN_FUZZ`, `APPIUM_JAVA_JUNIT`, `APPIUM_JAVA_TESTNG`, `APPIUM_PYTHON`, `APPIUM_NODE`, `APPIUM_RUBY`, `CALABASH`, `INSTRUMENTATION`, `UIAUTOMATION`, `UIAUTOMATOR`, `XCTEST`, `XCTEST_UI`, etc. |
| `--test` | No | structure | None | Test configuration |
| `--configuration` | No | structure | None | Run configuration |

**Output Schema:**
```json
{
    "compatibleDevices": [
        {
            "device": {
                "arn": "string",
                "name": "string",
                "manufacturer": "string",
                "model": "string",
                "modelId": "string",
                "formFactor": "PHONE|TABLET",
                "platform": "ANDROID|IOS",
                "os": "string",
                "cpu": {
                    "frequency": "string",
                    "architecture": "string",
                    "clock": "double"
                },
                "resolution": {
                    "width": "integer",
                    "height": "integer"
                },
                "heapSize": "long",
                "memory": "long",
                "image": "string",
                "carrier": "string",
                "radio": "string",
                "remoteAccessEnabled": "boolean",
                "remoteDebugEnabled": "boolean",
                "fleetType": "string",
                "fleetName": "string",
                "availability": "TEMPORARY_NOT_AVAILABLE|BUSY|AVAILABLE|HIGHLY_AVAILABLE"
            },
            "compatible": "boolean",
            "incompatibilityMessages": [
                {
                    "message": "string",
                    "type": "string"
                }
            ]
        }
    ],
    "incompatibleDevices": []
}
```

---

### 2.7 `get-device`

Gets information about a unique device type.

**Synopsis:**
```bash
aws devicefarm get-device \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the device |

**Output Schema:**
```json
{
    "device": {
        "arn": "string",
        "name": "string",
        "manufacturer": "string",
        "model": "string",
        "modelId": "string",
        "formFactor": "PHONE|TABLET",
        "platform": "ANDROID|IOS",
        "os": "string",
        "cpu": {
            "frequency": "string",
            "architecture": "string",
            "clock": "double"
        },
        "resolution": {
            "width": "integer",
            "height": "integer"
        },
        "heapSize": "long",
        "memory": "long",
        "image": "string",
        "carrier": "string",
        "radio": "string",
        "remoteAccessEnabled": "boolean",
        "remoteDebugEnabled": "boolean",
        "fleetType": "string",
        "fleetName": "string",
        "instances": [
            {
                "arn": "string",
                "deviceArn": "string",
                "labels": ["string"],
                "status": "IN_USE|PREPARING|AVAILABLE|NOT_AVAILABLE",
                "udid": "string",
                "instanceProfile": {
                    "arn": "string",
                    "packageCleanup": "boolean",
                    "excludeAppPackagesFromCleanup": ["string"],
                    "rebootAfterUse": "boolean",
                    "name": "string",
                    "description": "string"
                }
            }
        ],
        "availability": "TEMPORARY_NOT_AVAILABLE|BUSY|AVAILABLE|HIGHLY_AVAILABLE"
    }
}
```

---

### 2.8 `list-devices`

Gets information about unique device types. **Paginated operation.**

**Synopsis:**
```bash
aws devicefarm list-devices \
    [--arn <value>] \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | No | string | None | ARN of the project (to filter to project devices) |
| `--filters` | No | list | None | Filters. JSON: `[{"attribute":"string","operator":"string","values":["string"]}]` |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Filter Attributes:** `ARN`, `PLATFORM`, `OS_VERSION`, `MODEL`, `AVAILABILITY`, `FORM_FACTOR`, `MANUFACTURER`, `REMOTE_ACCESS_ENABLED`, `REMOTE_DEBUG_ENABLED`, `INSTANCE_ARN`, `INSTANCE_LABELS`, `FLEET_TYPE`

**Output Schema:**
```json
{
    "devices": [
        {
            "arn": "string",
            "name": "string",
            "manufacturer": "string",
            "model": "string",
            "modelId": "string",
            "formFactor": "PHONE|TABLET",
            "platform": "ANDROID|IOS",
            "os": "string",
            "cpu": {},
            "resolution": {},
            "heapSize": "long",
            "memory": "long",
            "remoteAccessEnabled": "boolean",
            "remoteDebugEnabled": "boolean",
            "fleetType": "string",
            "availability": "TEMPORARY_NOT_AVAILABLE|BUSY|AVAILABLE|HIGHLY_AVAILABLE"
        }
    ],
    "nextToken": "string"
}
```
