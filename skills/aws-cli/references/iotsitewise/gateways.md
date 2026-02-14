# Gateways

### 9.1 `create-gateway`

Creates a gateway for edge data collection using Greengrass or Siemens IE.

**Synopsis:**
```bash
aws iotsitewise create-gateway \
    --gateway-name <value> \
    --gateway-platform <value> \
    [--gateway-version <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-name` | **Yes** | string | -- | Gateway name (1-256 chars) |
| `--gateway-platform` | **Yes** | structure | -- | Platform config (choose one) |
| `--gateway-version` | No | string | `2` | `2` (Classic) or `3` (MQTT-enabled) |
| `--tags` | No | map | None | Tags (max 50) |

**Gateway Platform Structure (choose one):**
```json
{
    "greengrass": {
        "groupArn": "string"
    },
    "greengrassV2": {
        "coreDeviceThingName": "string",
        "coreDeviceOperatingSystem": "LINUX_AARCH64|LINUX_AMD64|WINDOWS_AMD64"
    },
    "siemensIE": {
        "iotCoreThingName": "string"
    }
}
```

**Output Schema:**
```json
{
    "gatewayId": "string",
    "gatewayArn": "string"
}
```

---

### 9.2 `describe-gateway`

Describes a gateway including its capabilities and sync status.

**Synopsis:**
```bash
aws iotsitewise describe-gateway \
    --gateway-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-id` | **Yes** | string | -- | Gateway ID (UUID) |

**Output Schema:**
```json
{
    "gatewayId": "string",
    "gatewayName": "string",
    "gatewayArn": "string",
    "gatewayPlatform": {
        "greengrass": {"groupArn": "string"},
        "greengrassV2": {"coreDeviceThingName": "string", "coreDeviceOperatingSystem": "string"},
        "siemensIE": {"iotCoreThingName": "string"}
    },
    "gatewayCapabilitySummaries": [
        {
            "capabilityNamespace": "string",
            "capabilitySyncStatus": "IN_SYNC|OUT_OF_SYNC|SYNC_FAILED|UNKNOWN"
        }
    ],
    "gatewayVersion": "string",
    "creationDate": "timestamp",
    "lastUpdateDate": "timestamp"
}
```

---

### 9.3 `list-gateways`

Lists gateways. **Paginated operation.**

**Synopsis:**
```bash
aws iotsitewise list-gateways \
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
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "gatewaySummaries": [
        {
            "gatewayId": "string",
            "gatewayName": "string",
            "gatewayPlatform": {},
            "gatewayCapabilitySummaries": [],
            "creationDate": "timestamp",
            "lastUpdateDate": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 9.4 `update-gateway`

Updates a gateway name.

**Synopsis:**
```bash
aws iotsitewise update-gateway \
    --gateway-id <value> \
    --gateway-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-id` | **Yes** | string | -- | Gateway ID |
| `--gateway-name` | **Yes** | string | -- | Updated name |

**Output:** None

---

### 9.5 `delete-gateway`

Deletes a gateway.

**Synopsis:**
```bash
aws iotsitewise delete-gateway \
    --gateway-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-id` | **Yes** | string | -- | Gateway ID |

**Output:** None

---

### 9.6 `describe-gateway-capability-configuration`

Describes a gateway capability configuration (e.g., OPC-UA sources).

**Synopsis:**
```bash
aws iotsitewise describe-gateway-capability-configuration \
    --gateway-id <value> \
    --capability-namespace <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-id` | **Yes** | string | -- | Gateway ID |
| `--capability-namespace` | **Yes** | string | -- | Capability namespace |

**Output Schema:**
```json
{
    "gatewayId": "string",
    "capabilityNamespace": "string",
    "capabilityConfiguration": "string",
    "capabilitySyncStatus": "IN_SYNC|OUT_OF_SYNC|SYNC_FAILED|UNKNOWN"
}
```

---

### 9.7 `update-gateway-capability-configuration`

Updates a gateway capability configuration.

**Synopsis:**
```bash
aws iotsitewise update-gateway-capability-configuration \
    --gateway-id <value> \
    --capability-namespace <value> \
    --capability-configuration <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-id` | **Yes** | string | -- | Gateway ID |
| `--capability-namespace` | **Yes** | string | -- | Capability namespace |
| `--capability-configuration` | **Yes** | string | -- | Configuration JSON |

**Output Schema:**
```json
{
    "capabilityNamespace": "string",
    "capabilitySyncStatus": "IN_SYNC|OUT_OF_SYNC|SYNC_FAILED|UNKNOWN"
}
```
