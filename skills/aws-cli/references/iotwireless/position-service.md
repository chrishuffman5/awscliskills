# Position & Service

### 12.1 `get-position-estimate`

Gets a position estimate based on measurement data from wireless devices.

**Synopsis:**
```bash
aws iotwireless get-position-estimate \
    [--wi-fi-access-points <value>] \
    [--cell-towers <value>] \
    [--ip <value>] \
    [--gnss <value>] \
    [--timestamp <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--wi-fi-access-points` | No | list | None | Wi-Fi access point data (min 1) |
| `--cell-towers` | No | structure | None | Cell tower measurement data |
| `--ip` | No | structure | None | IP address for position estimation |
| `--gnss` | No | structure | None | GNSS measurement data |
| `--timestamp` | No | timestamp | None | Measurement timestamp |

**Wi-Fi access points:**
```json
[
    {
        "MacAddress": "string",
        "Rss": -65
    }
]
```

**IP structure:**
```json
{
    "IpAddress": "192.168.1.1"
}
```

**GNSS structure:**
```json
{
    "Payload": "base64-encoded-string",
    "CaptureTime": 1234567890.0,
    "CaptureTimeAccuracy": 300.0,
    "AssistPosition": [47.6062, -122.3321],
    "AssistAltitude": 100.0,
    "Use2DSolver": false
}
```

**Output:** Returns a binary stream (GeoJSON) with the position estimate.

---

### 12.2 `get-resource-position`

Gets the position of a wireless device or gateway resource.

**Synopsis:**
```bash
aws iotwireless get-resource-position \
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

**Output:** Returns a binary stream (GeoJSON) with position data.

---

### 12.3 `update-resource-position`

Updates the position of a wireless device or gateway resource.

**Synopsis:**
```bash
aws iotwireless update-resource-position \
    --resource-identifier <value> \
    --resource-type <value> \
    [--geo-json-payload <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-identifier` | **Yes** | string | -- | Resource identifier |
| `--resource-type` | **Yes** | string | -- | `WirelessDevice` or `WirelessGateway` |
| `--geo-json-payload` | No | blob | None | GeoJSON payload with position data |

**Output:** None

---

### 12.4 `get-service-endpoint`

Gets the IoT Wireless service endpoint URL.

**Synopsis:**
```bash
aws iotwireless get-service-endpoint \
    [--service-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-type` | No | string | None | `CUPS` or `LNS` |

**Output Schema:**
```json
{
    "ServiceType": "CUPS|LNS",
    "ServiceEndpoint": "string",
    "ServerTrust": "string"
}
```

---

### 12.5 `associate-wireless-device-with-thing`

Associates a wireless device with an IoT thing.

**Synopsis:**
```bash
aws iotwireless associate-wireless-device-with-thing \
    --id <value> \
    --thing-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Wireless device ID |
| `--thing-arn` | **Yes** | string | -- | ARN of the IoT thing |

**Output:** None

---

### 12.6 `disassociate-wireless-device-from-thing`

Disassociates a wireless device from an IoT thing.

**Synopsis:**
```bash
aws iotwireless disassociate-wireless-device-from-thing \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Wireless device ID |

**Output:** None
