# Recorders

### 3.1 `put-configuration-recorder`

Creates or updates a configuration recorder. The configuration recorder records configuration changes for supported resource types.

**Synopsis:**
```bash
aws configservice put-configuration-recorder \
    --configuration-recorder <value> \
    [--recording-group <value>] \
    [--recording-mode <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configuration-recorder` | **Yes** | structure | -- | Recorder configuration. Shorthand: `name=string,roleARN=string` |
| `--recording-group` | No | structure | None | Resource types to record |
| `--recording-mode` | No | structure | None | Recording frequency mode |

**Recording Group Structure:**
```json
{
    "allSupported": true|false,
    "includeGlobalResourceTypes": true|false,
    "resourceTypes": ["string"],
    "exclusionByResourceTypes": {
        "resourceTypes": ["string"]
    },
    "recordingStrategy": {
        "useOnly": "ALL_SUPPORTED_RESOURCE_TYPES|INCLUSION_BY_RESOURCE_TYPES|EXCLUSION_BY_RESOURCE_TYPES"
    }
}
```

**Recording Mode Structure:**
```json
{
    "recordingFrequency": "CONTINUOUS|DAILY",
    "recordingModeOverrides": [
        {
            "description": "string",
            "resourceTypes": ["string"],
            "recordingFrequency": "CONTINUOUS|DAILY"
        }
    ]
}
```

**Output Schema:**
```json
{}
```

---

### 3.2 `delete-configuration-recorder`

Deletes the configuration recorder. Stops recording and deletes all configuration items previously recorded.

**Synopsis:**
```bash
aws configservice delete-configuration-recorder \
    --configuration-recorder-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configuration-recorder-name` | **Yes** | string | -- | Name of the configuration recorder to delete |

**Output Schema:**
```json
{}
```

---

### 3.3 `describe-configuration-recorders`

Returns the details for the specified configuration recorders.

**Synopsis:**
```bash
aws configservice describe-configuration-recorders \
    [--configuration-recorder-names <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configuration-recorder-names` | No | list(string) | None | Specific recorder names (currently only one per account) |

**Output Schema:**
```json
{
    "ConfigurationRecorders": [
        {
            "name": "string",
            "roleARN": "string",
            "recordingGroup": {
                "allSupported": true|false,
                "includeGlobalResourceTypes": true|false,
                "resourceTypes": ["string"],
                "exclusionByResourceTypes": {
                    "resourceTypes": ["string"]
                },
                "recordingStrategy": {
                    "useOnly": "string"
                }
            },
            "recordingMode": {
                "recordingFrequency": "CONTINUOUS|DAILY",
                "recordingModeOverrides": []
            }
        }
    ]
}
```

---

### 3.4 `describe-configuration-recorder-status`

Returns the current status of the specified configuration recorder.

**Synopsis:**
```bash
aws configservice describe-configuration-recorder-status \
    [--configuration-recorder-names <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configuration-recorder-names` | No | list(string) | None | Specific recorder names |

**Output Schema:**
```json
{
    "ConfigurationRecordersStatus": [
        {
            "name": "string",
            "lastStartTime": "timestamp",
            "lastStopTime": "timestamp",
            "recording": true|false,
            "lastStatus": "Pending|Success|Failure",
            "lastErrorCode": "string",
            "lastErrorMessage": "string",
            "lastStatusChangeTime": "timestamp"
        }
    ]
}
```

---

### 3.5 `start-configuration-recorder`

Starts recording configurations of the specified resource types.

**Synopsis:**
```bash
aws configservice start-configuration-recorder \
    --configuration-recorder-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configuration-recorder-name` | **Yes** | string | -- | Name of the configuration recorder to start |

**Output Schema:**
```json
{}
```

---

### 3.6 `stop-configuration-recorder`

Stops recording configurations of the specified resource types.

**Synopsis:**
```bash
aws configservice stop-configuration-recorder \
    --configuration-recorder-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configuration-recorder-name` | **Yes** | string | -- | Name of the configuration recorder to stop |

**Output Schema:**
```json
{}
```
