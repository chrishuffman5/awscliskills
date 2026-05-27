# Wireless Devices

### 1.1 `create-wireless-device`

Creates a LoRaWAN or Sidewalk wireless device.

**Synopsis:**
```bash
aws iotwireless create-wireless-device \
    --type <value> \
    --destination-name <value> \
    [--name <value>] \
    [--description <value>] \
    [--lorawan <value>] \
    [--sidewalk <value>] \
    [--positioning <value>] \
    [--tags <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--type` | **Yes** | string | -- | `LoRaWAN` or `Sidewalk` |
| `--destination-name` | **Yes** | string | -- | Destination name (max 128 chars) |
| `--name` | No | string | None | Device name (max 256 chars) |
| `--description` | No | string | None | Description (max 2048 chars) |
| `--lorawan` | No | structure | None | LoRaWAN device configuration |
| `--sidewalk` | No | structure | None | Sidewalk device configuration |
| `--positioning` | No | string | None | `Enabled` or `Disabled` |
| `--tags` | No | list | None | Tags (max 200) |
| `--client-request-token` | No | string | Auto | Idempotency token (1-64 chars) |

**LoRaWAN OTAA v1.0.x:**
```json
{
    "DevEui": "ac12efc654d23fc2",
    "DeviceProfileId": "string",
    "ServiceProfileId": "string",
    "OtaaV1_0_x": {
        "AppKey": "3f4ca100e2fc675ea123f4eb12c4a012",
        "AppEui": "b4c231a359bc2e3d"
    }
}
```

**LoRaWAN OTAA v1.1:**
```json
{
    "DevEui": "ac12efc654d23fc2",
    "DeviceProfileId": "string",
    "ServiceProfileId": "string",
    "OtaaV1_1": {
        "AppKey": "string",
        "NwkKey": "string",
        "JoinEui": "string"
    }
}
```

**LoRaWAN ABP v1.0.x:**
```json
{
    "DevEui": "ac12efc654d23fc2",
    "DeviceProfileId": "string",
    "ServiceProfileId": "string",
    "AbpV1_0_x": {
        "DevAddr": "01234567",
        "SessionKeys": {
            "NwkSKey": "string",
            "AppSKey": "string"
        },
        "FCntStart": 0
    }
}
```

**Output Schema:**
```json
{
    "Arn": "string",
    "Id": "string"
}
```

---

### 1.2 `get-wireless-device`

Retrieves information about a wireless device.

**Synopsis:**
```bash
aws iotwireless get-wireless-device \
    --identifier <value> \
    --identifier-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identifier` | **Yes** | string | -- | Device identifier (max 256 chars) |
| `--identifier-type` | **Yes** | string | -- | `WirelessDeviceId`, `DevEui`, `ThingName`, or `SidewalkManufacturingSn` |

**Output Schema:**
```json
{
    "Type": "LoRaWAN|Sidewalk",
    "Name": "string",
    "Description": "string",
    "DestinationName": "string",
    "Id": "string",
    "Arn": "string",
    "ThingName": "string",
    "ThingArn": "string",
    "LoRaWAN": {
        "DevEui": "string",
        "DeviceProfileId": "string",
        "ServiceProfileId": "string",
        "OtaaV1_1": {},
        "OtaaV1_0_x": {},
        "AbpV1_1": {},
        "AbpV1_0_x": {},
        "FPorts": {}
    },
    "Sidewalk": {
        "AmazonId": "string",
        "SidewalkId": "string",
        "SidewalkManufacturingSn": "string",
        "DeviceProfileId": "string",
        "Status": "PROVISIONED|REGISTERED|ACTIVATED|UNKNOWN"
    },
    "Positioning": "Enabled|Disabled"
}
```

---

### 1.3 `list-wireless-devices`

Lists wireless devices. **Paginated operation.**

**Synopsis:**
```bash
aws iotwireless list-wireless-devices \
    [--max-results <value>] \
    [--next-token <value>] \
    [--destination-name <value>] \
    [--device-profile-id <value>] \
    [--service-profile-id <value>] \
    [--wireless-device-type <value>] \
    [--fuota-task-id <value>] \
    [--multicast-group-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--max-results` | No | integer | None | Max results (1-250) |
| `--next-token` | No | string | None | Pagination token |
| `--destination-name` | No | string | None | Filter by destination |
| `--device-profile-id` | No | string | None | Filter by device profile |
| `--service-profile-id` | No | string | None | Filter by service profile |
| `--wireless-device-type` | No | string | None | `LoRaWAN` or `Sidewalk` |
| `--fuota-task-id` | No | string | None | Filter by FUOTA task |
| `--multicast-group-id` | No | string | None | Filter by multicast group |

**Output Schema:**
```json
{
    "NextToken": "string",
    "WirelessDeviceList": [
        {
            "Arn": "string",
            "Id": "string",
            "Type": "LoRaWAN|Sidewalk",
            "Name": "string",
            "DestinationName": "string",
            "LastUplinkReceivedAt": "string",
            "LoRaWAN": {"DevEui": "string"},
            "Sidewalk": {"AmazonId": "string", "SidewalkId": "string", "SidewalkManufacturingSn": "string"},
            "FuotaDeviceStatus": "string",
            "MulticastDeviceStatus": "string",
            "McGroupId": "integer"
        }
    ]
}
```

---

### 1.4 `update-wireless-device`

Updates a wireless device.

**Synopsis:**
```bash
aws iotwireless update-wireless-device \
    --id <value> \
    [--destination-name <value>] \
    [--name <value>] \
    [--description <value>] \
    [--lorawan <value>] \
    [--positioning <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Wireless device ID |
| `--destination-name` | No | string | None | Updated destination |
| `--name` | No | string | None | Updated name |
| `--description` | No | string | None | Updated description |
| `--lorawan` | No | structure | None | Updated LoRaWAN config |
| `--positioning` | No | string | None | `Enabled` or `Disabled` |

**Output:** None

---

### 1.5 `delete-wireless-device`

Deletes a wireless device.

**Synopsis:**
```bash
aws iotwireless delete-wireless-device \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Wireless device ID |

**Output:** None

---

### 1.6 `get-wireless-device-statistics`

Gets operating statistics for a wireless device.

**Synopsis:**
```bash
aws iotwireless get-wireless-device-statistics \
    --wireless-device-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--wireless-device-id` | **Yes** | string | -- | Wireless device ID |

**Output Schema:**
```json
{
    "WirelessDeviceId": "string",
    "LastUplinkReceivedAt": "string",
    "LoRaWAN": {
        "DevEui": "string",
        "FPort": "integer",
        "DataRate": "integer",
        "Frequency": "integer",
        "Timestamp": "string",
        "Gateways": [
            {
                "GatewayEui": "string",
                "Snr": "double",
                "Rssi": "double"
            }
        ],
        "PublicGateways": []
    },
    "Sidewalk": {
        "Rssi": "integer",
        "BatteryLevel": "normal|low|critical",
        "Event": "discovered|joined|ack|nack",
        "DeviceState": "Provisioned|RegisteredNotSeen|RegisteredReachable|RegisteredUnreachable"
    }
}
```

---

### 1.7 `send-data-to-wireless-device`

Sends a downlink message to a wireless device.

**Synopsis:**
```bash
aws iotwireless send-data-to-wireless-device \
    --id <value> \
    --transmit-mode <value> \
    --payload-data <value> \
    [--wireless-metadata <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Wireless device ID |
| `--transmit-mode` | **Yes** | integer | -- | 0 (unconfirmed) or 1 (confirmed) |
| `--payload-data` | **Yes** | string | -- | Base64-encoded payload (max 2048 chars) |
| `--wireless-metadata` | No | structure | None | Transmission metadata |

**Wireless metadata:**
```json
{
    "LoRaWAN": {"FPort": 1},
    "Sidewalk": {"Seq": 1, "MessageType": "CUSTOM_COMMAND_ID_NOTIFY|CUSTOM_COMMAND_ID_GET|CUSTOM_COMMAND_ID_SET|CUSTOM_COMMAND_ID_RESP"}
}
```

**Output Schema:**
```json
{
    "MessageId": "string"
}
```

---

### 1.8 `test-wireless-device`

Simulates a provisioned device for testing.

**Synopsis:**
```bash
aws iotwireless test-wireless-device \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Wireless device ID (max 256 chars) |

**Output Schema:**
```json
{
    "Result": "string"
}
```

---

### 1.9 `deregister-wireless-device`

Deregisters a wireless device from IoT Wireless.

**Synopsis:**
```bash
aws iotwireless deregister-wireless-device \
    --identifier <value> \
    [--wireless-device-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identifier` | **Yes** | string | -- | Device identifier (max 256 chars) |
| `--wireless-device-type` | No | string | None | `Sidewalk` or `LoRaWAN` |

**Output:** None

---

### 1.10 `delete-queued-messages`

Deletes queued downlink messages for a device.

**Synopsis:**
```bash
aws iotwireless delete-queued-messages \
    --id <value> \
    --message-id <value> \
    [--wireless-device-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Wireless device ID |
| `--message-id` | **Yes** | string | -- | Message ID or `*` for all messages |
| `--wireless-device-type` | No | string | None | `Sidewalk` or `LoRaWAN` |

**Output:** None

---

### 1.11 `list-queued-messages`

Lists queued downlink messages for a device. **Paginated operation.**

**Synopsis:**
```bash
aws iotwireless list-queued-messages \
    --id <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--wireless-device-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Wireless device ID |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results per page |
| `--wireless-device-type` | No | string | None | `Sidewalk` or `LoRaWAN` |

**Output Schema:**
```json
{
    "NextToken": "string",
    "DownlinkQueueMessagesList": [
        {
            "MessageId": "string",
            "TransmitMode": "integer",
            "ReceivedAt": "string",
            "LoRaWAN": {"FPort": "integer"},
            "ParamsForLoRaWANMulticast": {}
        }
    ]
}
```
