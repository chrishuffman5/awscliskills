# Core Devices

### 2.1 `get-core-device`

Retrieves details about a Greengrass core device.

**Synopsis:**
```bash
aws greengrassv2 get-core-device \
    --core-device-thing-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--core-device-thing-name` | **Yes** | string | -- | Core device name (IoT thing name, 1-128 chars) |

**Output Schema:**
```json
{
    "coreDeviceThingName": "string",
    "coreVersion": "string",
    "platform": "string",
    "architecture": "string",
    "runtime": "aws_nucleus_classic|aws_nucleus_lite",
    "status": "HEALTHY|UNHEALTHY",
    "lastStatusUpdateTimestamp": "timestamp",
    "tags": {"string": "string"}
}
```

---

### 2.2 `list-core-devices`

Lists Greengrass core devices. **Paginated operation.**

**Synopsis:**
```bash
aws greengrassv2 list-core-devices \
    [--thing-group-arn <value>] \
    [--status <value>] \
    [--runtime <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--thing-group-arn` | No | string | None | Filter by IoT thing group ARN |
| `--status` | No | string | None | Filter: `HEALTHY` or `UNHEALTHY` |
| `--runtime` | No | string | None | Filter: `aws_nucleus_classic` or `aws_nucleus_lite` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "coreDevices": [
        {
            "coreDeviceThingName": "string",
            "status": "HEALTHY|UNHEALTHY",
            "lastStatusUpdateTimestamp": "timestamp",
            "platform": "string",
            "architecture": "string",
            "runtime": "aws_nucleus_classic|aws_nucleus_lite"
        }
    ],
    "nextToken": "string"
}
```

---

### 2.3 `delete-core-device`

Deletes a Greengrass core device. This removes the core device from the IoT Greengrass service but does not delete the IoT thing.

**Synopsis:**
```bash
aws greengrassv2 delete-core-device \
    --core-device-thing-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--core-device-thing-name` | **Yes** | string | -- | Core device name (1-128 chars) |

**Output:** None

---

### 2.4 `get-connectivity-info`

Retrieves connectivity information for a core device.

**Synopsis:**
```bash
aws greengrassv2 get-connectivity-info \
    --thing-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--thing-name` | **Yes** | string | -- | Core device name (1-128 chars) |

**Output Schema:**
```json
{
    "connectivityInfo": [
        {
            "id": "string",
            "hostAddress": "string",
            "portNumber": "integer",
            "metadata": "string"
        }
    ],
    "message": "string"
}
```

---

### 2.5 `update-connectivity-info`

Updates connectivity information for a core device. Client devices use this to find the core device's MQTT broker.

**Synopsis:**
```bash
aws greengrassv2 update-connectivity-info \
    --thing-name <value> \
    --connectivity-info <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--thing-name` | **Yes** | string | -- | Core device name (1-128 chars) |
| `--connectivity-info` | **Yes** | list | -- | Connectivity endpoints |

**Connectivity info structure:**
```json
[
    {
        "id": "localIP",
        "hostAddress": "192.168.1.10",
        "portNumber": 8883,
        "metadata": "string"
    }
]
```

**Output Schema:**
```json
{
    "version": "string",
    "message": "string"
}
```

---

### 2.6 `batch-associate-client-device-with-core-device`

Associates multiple client devices with a core device.

**Synopsis:**
```bash
aws greengrassv2 batch-associate-client-device-with-core-device \
    --core-device-thing-name <value> \
    [--entries <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--core-device-thing-name` | **Yes** | string | -- | Core device name (1-128 chars) |
| `--entries` | No | list | None | Client devices to associate (1-100) |

**Entries structure:**
```json
[
    {"thingName": "ClientDevice1"},
    {"thingName": "ClientDevice2"}
]
```

**Output Schema:**
```json
{
    "errorEntries": [
        {
            "thingName": "string",
            "code": "string",
            "message": "string"
        }
    ]
}
```

---

### 2.7 `batch-disassociate-client-device-from-core-device`

Disassociates multiple client devices from a core device.

**Synopsis:**
```bash
aws greengrassv2 batch-disassociate-client-device-from-core-device \
    --core-device-thing-name <value> \
    [--entries <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--core-device-thing-name` | **Yes** | string | -- | Core device name (1-128 chars) |
| `--entries` | No | list | None | Client devices to disassociate (1-100) |

**Entries structure:**
```json
[
    {"thingName": "ClientDevice1"},
    {"thingName": "ClientDevice2"}
]
```

**Output Schema:**
```json
{
    "errorEntries": [
        {
            "thingName": "string",
            "code": "string",
            "message": "string"
        }
    ]
}
```

---

### 2.8 `list-client-devices-associated-with-core-device`

Lists client devices associated with a core device. **Paginated operation.**

**Synopsis:**
```bash
aws greengrassv2 list-client-devices-associated-with-core-device \
    --core-device-thing-name <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--core-device-thing-name` | **Yes** | string | -- | Core device name (1-128 chars) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "associatedClientDevices": [
        {
            "thingName": "string",
            "associationTimestamp": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 2.9 `list-installed-components`

Lists components installed on a core device. **Paginated operation.**

**Synopsis:**
```bash
aws greengrassv2 list-installed-components \
    --core-device-thing-name <value> \
    [--topology-filter <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--core-device-thing-name` | **Yes** | string | -- | Core device name (1-128 chars) |
| `--topology-filter` | No | string | ROOT | `ALL` (all components) or `ROOT` (root components only) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "installedComponents": [
        {
            "componentName": "string",
            "componentVersion": "string",
            "lifecycleState": "NEW|INSTALLED|STARTING|RUNNING|STOPPING|ERRORED|BROKEN|FINISHED",
            "lifecycleStateDetails": "string",
            "isRoot": "boolean",
            "lastStatusChangeTimestamp": "timestamp",
            "lastReportedTimestamp": "timestamp",
            "lastInstallationSource": "string",
            "lifecycleStatusCodes": ["string"]
        }
    ],
    "nextToken": "string"
}
```
