# Events & Logging

### 10.1 `get-event-configuration-by-resource-types`

Gets the event configuration for all resource types.

**Synopsis:**
```bash
aws iotwireless get-event-configuration-by-resource-types \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output Schema:**
```json
{
    "DeviceRegistrationState": {
        "Sidewalk": {"AmazonIdEventTopic": "Enabled|Disabled"},
        "WirelessDeviceIdEventTopic": "Enabled|Disabled"
    },
    "Proximity": {
        "Sidewalk": {"AmazonIdEventTopic": "Enabled|Disabled"},
        "WirelessDeviceIdEventTopic": "Enabled|Disabled"
    },
    "Join": {
        "LoRaWAN": {"DevEuiEventTopic": "Enabled|Disabled"},
        "WirelessDeviceIdEventTopic": "Enabled|Disabled"
    },
    "ConnectionStatus": {
        "LoRaWAN": {"GatewayEuiEventTopic": "Enabled|Disabled"},
        "WirelessGatewayIdEventTopic": "Enabled|Disabled"
    },
    "MessageDeliveryStatus": {
        "Sidewalk": {"AmazonIdEventTopic": "Enabled|Disabled"},
        "WirelessDeviceIdEventTopic": "Enabled|Disabled"
    }
}
```

---

### 10.2 `update-event-configuration-by-resource-types`

Updates event configuration for all resource types.

**Synopsis:**
```bash
aws iotwireless update-event-configuration-by-resource-types \
    [--device-registration-state <value>] \
    [--proximity <value>] \
    [--join <value>] \
    [--connection-status <value>] \
    [--message-delivery-status <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--device-registration-state` | No | structure | None | Device registration event config |
| `--proximity` | No | structure | None | Proximity event config |
| `--join` | No | structure | None | Join event config |
| `--connection-status` | No | structure | None | Connection status event config |
| `--message-delivery-status` | No | structure | None | Message delivery event config |

**Output:** None

---

### 10.3 `get-resource-event-configuration`

Gets event configuration for a specific resource.

**Synopsis:**
```bash
aws iotwireless get-resource-event-configuration \
    --identifier <value> \
    --identifier-type <value> \
    [--partner-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identifier` | **Yes** | string | -- | Resource identifier |
| `--identifier-type` | **Yes** | string | -- | `PartnerAccountId`, `DevEui`, `GatewayEui`, or `WirelessDeviceId` |
| `--partner-type` | No | string | None | `Sidewalk` |

**Output Schema:**
```json
{
    "DeviceRegistrationState": {
        "Sidewalk": {"AmazonIdEventTopic": "Enabled|Disabled"},
        "WirelessDeviceIdEventTopic": "Enabled|Disabled"
    },
    "Proximity": {
        "Sidewalk": {"AmazonIdEventTopic": "Enabled|Disabled"},
        "WirelessDeviceIdEventTopic": "Enabled|Disabled"
    },
    "Join": {
        "LoRaWAN": {"DevEuiEventTopic": "Enabled|Disabled"},
        "WirelessDeviceIdEventTopic": "Enabled|Disabled"
    },
    "ConnectionStatus": {
        "LoRaWAN": {"GatewayEuiEventTopic": "Enabled|Disabled"},
        "WirelessGatewayIdEventTopic": "Enabled|Disabled"
    },
    "MessageDeliveryStatus": {
        "Sidewalk": {"AmazonIdEventTopic": "Enabled|Disabled"},
        "WirelessDeviceIdEventTopic": "Enabled|Disabled"
    }
}
```

---

### 10.4 `update-resource-event-configuration`

Updates event configuration for a specific resource.

**Synopsis:**
```bash
aws iotwireless update-resource-event-configuration \
    --identifier <value> \
    --identifier-type <value> \
    [--partner-type <value>] \
    [--device-registration-state <value>] \
    [--proximity <value>] \
    [--join <value>] \
    [--connection-status <value>] \
    [--message-delivery-status <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identifier` | **Yes** | string | -- | Resource identifier |
| `--identifier-type` | **Yes** | string | -- | `PartnerAccountId`, `DevEui`, `GatewayEui`, or `WirelessDeviceId` |
| `--partner-type` | No | string | None | `Sidewalk` |
| `--device-registration-state` | No | structure | None | Device registration config |
| `--proximity` | No | structure | None | Proximity config |
| `--join` | No | structure | None | Join config |
| `--connection-status` | No | structure | None | Connection status config |
| `--message-delivery-status` | No | structure | None | Message delivery config |

**Output:** None

---

### 10.5 `list-event-configurations`

Lists event configurations. **Paginated operation.**

**Synopsis:**
```bash
aws iotwireless list-event-configurations \
    --resource-type <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-type` | **Yes** | string | -- | `SidewalkAccount`, `WirelessDevice`, or `WirelessGateway` |
| `--max-results` | No | integer | None | Max results (0-250) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "NextToken": "string",
    "EventConfigurationsList": [
        {
            "Identifier": "string",
            "IdentifierType": "PartnerAccountId|DevEui|GatewayEui|WirelessDeviceId|WirelessGatewayId",
            "PartnerType": "Sidewalk",
            "Events": {
                "DeviceRegistrationState": {},
                "Proximity": {},
                "Join": {},
                "ConnectionStatus": {},
                "MessageDeliveryStatus": {}
            }
        }
    ]
}
```

---

### 10.6 `get-log-levels-by-resource-types`

Gets log levels configured by resource types.

**Synopsis:**
```bash
aws iotwireless get-log-levels-by-resource-types \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output Schema:**
```json
{
    "DefaultLogLevel": "INFO|ERROR|DISABLED",
    "WirelessGatewayLogOptions": [
        {
            "Type": "LoRaWAN",
            "LogLevel": "INFO|ERROR|DISABLED",
            "Events": [
                {
                    "Event": "CUPS_Request|Certificate",
                    "LogLevel": "INFO|ERROR|DISABLED"
                }
            ]
        }
    ],
    "WirelessDeviceLogOptions": [
        {
            "Type": "Sidewalk|LoRaWAN",
            "LogLevel": "INFO|ERROR|DISABLED",
            "Events": [
                {
                    "Event": "Join|Rejoin|Uplink_Data|Downlink_Data|Registration",
                    "LogLevel": "INFO|ERROR|DISABLED"
                }
            ]
        }
    ]
}
```

---

### 10.7 `update-log-levels-by-resource-types`

Updates log levels by resource types.

**Synopsis:**
```bash
aws iotwireless update-log-levels-by-resource-types \
    [--default-log-level <value>] \
    [--wireless-device-log-options <value>] \
    [--wireless-gateway-log-options <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--default-log-level` | No | string | None | `INFO`, `ERROR`, or `DISABLED` |
| `--wireless-device-log-options` | No | list | None | Device log options |
| `--wireless-gateway-log-options` | No | list | None | Gateway log options |

**Output:** None

---

### 10.8 `get-resource-log-level`

Gets the log level for a specific resource.

**Synopsis:**
```bash
aws iotwireless get-resource-log-level \
    --resource-identifier <value> \
    --resource-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-identifier` | **Yes** | string | -- | Resource identifier |
| `--resource-type` | **Yes** | string | -- | `WirelessDevice` or `WirelessGateway` |

**Output Schema:**
```json
{
    "LogLevel": "INFO|ERROR|DISABLED"
}
```

---

### 10.9 `put-resource-log-level`

Sets the log level for a specific resource.

**Synopsis:**
```bash
aws iotwireless put-resource-log-level \
    --resource-identifier <value> \
    --resource-type <value> \
    --log-level <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-identifier` | **Yes** | string | -- | Resource identifier |
| `--resource-type` | **Yes** | string | -- | `WirelessDevice` or `WirelessGateway` |
| `--log-level` | **Yes** | string | -- | `INFO`, `ERROR`, or `DISABLED` |

**Output:** None

---

### 10.10 `reset-resource-log-level`

Resets the log level for a specific resource to the default.

**Synopsis:**
```bash
aws iotwireless reset-resource-log-level \
    --resource-identifier <value> \
    --resource-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-identifier` | **Yes** | string | -- | Resource identifier |
| `--resource-type` | **Yes** | string | -- | `WirelessDevice` or `WirelessGateway` |

**Output:** None

---

### 10.11 `reset-all-resource-log-levels`

Resets log levels for all resources to the default.

**Synopsis:**
```bash
aws iotwireless reset-all-resource-log-levels \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output:** None
