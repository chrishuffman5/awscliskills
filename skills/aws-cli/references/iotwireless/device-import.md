# Device Import

### 8.1 `start-single-wireless-device-import-task`

Starts an import task for a single wireless device.

**Synopsis:**
```bash
aws iotwireless start-single-wireless-device-import-task \
    --destination-name <value> \
    --device-name <value> \
    [--sidewalk <value>] \
    [--tags <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--destination-name` | **Yes** | string | -- | Destination name (max 128 chars) |
| `--device-name` | **Yes** | string | -- | Device name (max 256 chars) |
| `--sidewalk` | No | structure | None | Sidewalk device configuration |
| `--tags` | No | list | None | Tags (max 200) |
| `--client-request-token` | No | string | Auto | Idempotency token |

**Sidewalk structure:**
```json
{
    "SidewalkManufacturingSn": "string"
}
```

**Output Schema:**
```json
{
    "Id": "string",
    "Arn": "string"
}
```

---

### 8.2 `start-wireless-device-import-task`

Starts a bulk wireless device import task.

**Synopsis:**
```bash
aws iotwireless start-wireless-device-import-task \
    --destination-name <value> \
    --sidewalk <value> \
    [--client-request-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--destination-name` | **Yes** | string | -- | Destination name |
| `--sidewalk` | **Yes** | structure | -- | Sidewalk import configuration |
| `--client-request-token` | No | string | Auto | Idempotency token |
| `--tags` | No | list | None | Tags (max 200) |

**Sidewalk structure:**
```json
{
    "DeviceCreationFile": "string",
    "Role": "string"
}
```

**Output Schema:**
```json
{
    "Id": "string",
    "Arn": "string"
}
```

---

### 8.3 `get-wireless-device-import-task`

Gets information about a wireless device import task.

**Synopsis:**
```bash
aws iotwireless get-wireless-device-import-task \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Import task ID |

**Output Schema:**
```json
{
    "Id": "string",
    "Arn": "string",
    "DestinationName": "string",
    "Sidewalk": {
        "DeviceCreationFile": "string",
        "DeviceCreationFileList": ["string"],
        "Role": "string"
    },
    "CreationTime": "timestamp",
    "Status": "INITIALIZING|INITIALIZED|PENDING|COMPLETE|FAILED|DELETING",
    "StatusReason": "string",
    "InitializedImportedDeviceCount": "long",
    "PendingImportedDeviceCount": "long",
    "OnboardedImportedDeviceCount": "long",
    "FailedImportedDeviceCount": "long"
}
```

---

### 8.4 `list-wireless-device-import-tasks`

Lists wireless device import tasks. **Paginated operation.**

**Synopsis:**
```bash
aws iotwireless list-wireless-device-import-tasks \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--max-results` | No | integer | None | Max results (0-250) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "NextToken": "string",
    "WirelessDeviceImportTaskList": [
        {
            "Id": "string",
            "Arn": "string",
            "DestinationName": "string",
            "Sidewalk": {},
            "CreationTime": "timestamp",
            "Status": "INITIALIZING|INITIALIZED|PENDING|COMPLETE|FAILED|DELETING",
            "StatusReason": "string",
            "InitializedImportedDeviceCount": "long",
            "PendingImportedDeviceCount": "long",
            "OnboardedImportedDeviceCount": "long",
            "FailedImportedDeviceCount": "long"
        }
    ]
}
```

---

### 8.5 `delete-wireless-device-import-task`

Deletes a wireless device import task.

**Synopsis:**
```bash
aws iotwireless delete-wireless-device-import-task \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Import task ID |

**Output:** None

---

### 8.6 `update-wireless-device-import-task`

Updates a wireless device import task.

**Synopsis:**
```bash
aws iotwireless update-wireless-device-import-task \
    --id <value> \
    --sidewalk <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Import task ID |
| `--sidewalk` | **Yes** | structure | -- | Updated Sidewalk config |

**Sidewalk structure:**
```json
{
    "DeviceCreationFile": "string"
}
```

**Output:** None

---

### 8.7 `list-devices-for-wireless-device-import-task`

Lists devices in a wireless device import task. **Paginated operation.**

**Synopsis:**
```bash
aws iotwireless list-devices-for-wireless-device-import-task \
    --id <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--status <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Import task ID |
| `--max-results` | No | integer | None | Max results (0-250) |
| `--next-token` | No | string | None | Pagination token |
| `--status` | No | string | None | `INITIALIZED`, `PENDING`, `ONBOARDED`, or `FAILED` |

**Output Schema:**
```json
{
    "NextToken": "string",
    "DestinationName": "string",
    "ImportedWirelessDeviceList": [
        {
            "Sidewalk": {
                "SidewalkManufacturingSn": "string",
                "OnboardingStatus": "INITIALIZED|PENDING|ONBOARDED|FAILED",
                "OnboardingStatusReason": "string",
                "LastUpdateTime": "timestamp"
            }
        }
    ]
}
```
