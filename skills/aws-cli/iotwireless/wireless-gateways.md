# Wireless Gateways

### 2.1 `create-wireless-gateway`

Creates a LoRaWAN wireless gateway.

**Synopsis:**
```bash
aws iotwireless create-wireless-gateway \
    --lorawan <value> \
    [--name <value>] \
    [--description <value>] \
    [--tags <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--lorawan` | **Yes** | structure | -- | LoRaWAN gateway configuration |
| `--name` | No | string | None | Gateway name (max 256 chars) |
| `--description` | No | string | None | Description (max 2048 chars) |
| `--tags` | No | list | None | Tags (max 200) |
| `--client-request-token` | No | string | Auto | Idempotency token |

**LoRaWAN structure:**
```json
{
    "GatewayEui": "a1b2c3d4567890ab",
    "RfRegion": "US915",
    "JoinEuiFilters": [["string", "string"]],
    "NetIdFilters": ["string"],
    "SubBands": [1],
    "Beaconing": {"DataRate": 0, "Frequencies": [923300000]},
    "MaxEirp": 30.0
}
```

**RF Regions:** `US915`, `EU868`, `AU915`, `AS923-1`, `AS923-2`, `AS923-3`, `AS923-4`, `EU433`, `CN470`, `CN779`, `RU864`, `KR920`, `IN865`

**Output Schema:**
```json
{
    "Arn": "string",
    "Id": "string"
}
```

---

### 2.2 `get-wireless-gateway`

Retrieves information about a wireless gateway.

**Synopsis:**
```bash
aws iotwireless get-wireless-gateway \
    --identifier <value> \
    --identifier-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identifier` | **Yes** | string | -- | Gateway identifier |
| `--identifier-type` | **Yes** | string | -- | `GatewayEui`, `WirelessGatewayId`, or `ThingName` |

**Output Schema:**
```json
{
    "Name": "string",
    "Id": "string",
    "Description": "string",
    "LoRaWAN": {
        "GatewayEui": "string",
        "RfRegion": "string",
        "JoinEuiFilters": [],
        "NetIdFilters": [],
        "SubBands": [],
        "Beaconing": {},
        "MaxEirp": "float"
    },
    "Arn": "string",
    "ThingName": "string",
    "ThingArn": "string"
}
```

---

### 2.3 `list-wireless-gateways`

Lists wireless gateways. **Paginated operation.**

**Synopsis:**
```bash
aws iotwireless list-wireless-gateways \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-250) |

**Output Schema:**
```json
{
    "NextToken": "string",
    "WirelessGatewayList": [
        {
            "Arn": "string",
            "Id": "string",
            "Name": "string",
            "Description": "string",
            "LoRaWAN": {"GatewayEui": "string", "RfRegion": "string"},
            "LastUplinkReceivedAt": "string"
        }
    ]
}
```

---

### 2.4 `update-wireless-gateway`

Updates a wireless gateway.

**Synopsis:**
```bash
aws iotwireless update-wireless-gateway \
    --id <value> \
    [--name <value>] \
    [--description <value>] \
    [--join-eui-filters <value>] \
    [--net-id-filters <value>] \
    [--max-eirp <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Wireless gateway ID |
| `--name` | No | string | None | Updated name |
| `--description` | No | string | None | Updated description |
| `--join-eui-filters` | No | list | None | Updated JoinEUI filters |
| `--net-id-filters` | No | list | None | Updated NetID filters |
| `--max-eirp` | No | float | None | Updated max EIRP (0-30) |

**Output:** None

---

### 2.5 `delete-wireless-gateway`

Deletes a wireless gateway.

**Synopsis:**
```bash
aws iotwireless delete-wireless-gateway \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Wireless gateway ID |

**Output:** None

---

### 2.6 `get-wireless-gateway-statistics`

Gets operating statistics for a wireless gateway.

**Synopsis:**
```bash
aws iotwireless get-wireless-gateway-statistics \
    --wireless-gateway-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--wireless-gateway-id` | **Yes** | string | -- | Gateway ID |

**Output Schema:**
```json
{
    "WirelessGatewayId": "string",
    "LastUplinkReceivedAt": "string",
    "ConnectionStatus": "Connected|Disconnected"
}
```

---

### 2.7 `get-wireless-gateway-certificate`

Gets the certificate associated with a wireless gateway.

**Synopsis:**
```bash
aws iotwireless get-wireless-gateway-certificate \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Gateway ID |

**Output Schema:**
```json
{
    "IotCertificateId": "string",
    "LoRaWANNetworkServerCertificateId": "string"
}
```

---

### 2.8 `get-wireless-gateway-firmware-information`

Gets firmware information for a wireless gateway.

**Synopsis:**
```bash
aws iotwireless get-wireless-gateway-firmware-information \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Gateway ID |

**Output Schema:**
```json
{
    "LoRaWAN": {
        "CurrentVersion": {
            "PackageVersion": "string",
            "Model": "string",
            "Station": "string"
        }
    }
}
```

---

### 2.9 `associate-wireless-gateway-with-certificate`

Associates a wireless gateway with a certificate.

**Synopsis:**
```bash
aws iotwireless associate-wireless-gateway-with-certificate \
    --id <value> \
    --iot-certificate-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Gateway ID |
| `--iot-certificate-id` | **Yes** | string | -- | IoT certificate ID |

**Output Schema:**
```json
{
    "IotCertificateId": "string"
}
```

---

### 2.10 `disassociate-wireless-gateway-from-certificate`

Disassociates a wireless gateway from its certificate.

**Synopsis:**
```bash
aws iotwireless disassociate-wireless-gateway-from-certificate \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Gateway ID |

**Output:** None

---

### 2.11 `associate-wireless-gateway-with-thing`

Associates a wireless gateway with an IoT thing.

**Synopsis:**
```bash
aws iotwireless associate-wireless-gateway-with-thing \
    --id <value> \
    --thing-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Gateway ID |
| `--thing-arn` | **Yes** | string | -- | ARN of the IoT thing |

**Output:** None

---

### 2.12 `disassociate-wireless-gateway-from-thing`

Disassociates a wireless gateway from an IoT thing.

**Synopsis:**
```bash
aws iotwireless disassociate-wireless-gateway-from-thing \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Gateway ID |

**Output:** None
