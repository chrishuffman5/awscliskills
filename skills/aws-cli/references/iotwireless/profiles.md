# Profiles

### 5.1 `create-device-profile`

Creates a device profile for LoRaWAN or Sidewalk devices.

**Synopsis:**
```bash
aws iotwireless create-device-profile \
    [--name <value>] \
    [--lorawan <value>] \
    [--sidewalk <value>] \
    [--tags <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | No | string | None | Profile name (max 256 chars) |
| `--lorawan` | No | structure | None | LoRaWAN device profile configuration |
| `--sidewalk` | No | structure | None | Sidewalk device profile (empty structure) |
| `--tags` | No | list | None | Tags (max 200) |
| `--client-request-token` | No | string | Auto | Idempotency token |

**LoRaWAN structure:**
```json
{
    "SupportsClassB": false,
    "ClassBTimeout": 0,
    "PingSlotPeriod": 32,
    "PingSlotDr": 0,
    "PingSlotFreq": 923300000,
    "SupportsClassC": false,
    "ClassCTimeout": 0,
    "MacVersion": "1.0.3",
    "RegParamsRevision": "RP002-1.0.1",
    "RxDelay1": 1,
    "RxDrOffset1": 0,
    "RxDataRate2": 0,
    "RxFreq2": 923300000,
    "FactoryPresetFreqsList": [923300000, 923900000],
    "MaxEirp": 15,
    "MaxDutyCycle": 10,
    "RfRegion": "US915",
    "SupportsJoin": true,
    "Supports32BitFCnt": true
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

### 5.2 `get-device-profile`

Retrieves information about a device profile.

**Synopsis:**
```bash
aws iotwireless get-device-profile \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Device profile ID |

**Output Schema:**
```json
{
    "Arn": "string",
    "Name": "string",
    "Id": "string",
    "LoRaWAN": {
        "SupportsClassB": "boolean",
        "ClassBTimeout": "integer",
        "PingSlotPeriod": "integer",
        "PingSlotDr": "integer",
        "PingSlotFreq": "integer",
        "SupportsClassC": "boolean",
        "ClassCTimeout": "integer",
        "MacVersion": "string",
        "RegParamsRevision": "string",
        "RxDelay1": "integer",
        "RxDrOffset1": "integer",
        "RxDataRate2": "integer",
        "RxFreq2": "integer",
        "FactoryPresetFreqsList": ["integer"],
        "MaxEirp": "integer",
        "MaxDutyCycle": "integer",
        "RfRegion": "string",
        "SupportsJoin": "boolean",
        "Supports32BitFCnt": "boolean"
    },
    "Sidewalk": {
        "ApplicationServerPublicKey": "string",
        "QualificationStatus": "boolean",
        "DakCertificateMetadata": []
    }
}
```

---

### 5.3 `list-device-profiles`

Lists device profiles. **Paginated operation.**

**Synopsis:**
```bash
aws iotwireless list-device-profiles \
    [--next-token <value>] \
    [--max-results <value>] \
    [--device-profile-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (0-250) |
| `--device-profile-type` | No | string | None | `Sidewalk` or `LoRaWAN` |

**Output Schema:**
```json
{
    "NextToken": "string",
    "DeviceProfileList": [
        {
            "Arn": "string",
            "Name": "string",
            "Id": "string"
        }
    ]
}
```

---

### 5.4 `delete-device-profile`

Deletes a device profile.

**Synopsis:**
```bash
aws iotwireless delete-device-profile \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Device profile ID |

**Output:** None

---

### 5.5 `create-service-profile`

Creates a service profile for LoRaWAN devices.

**Synopsis:**
```bash
aws iotwireless create-service-profile \
    [--name <value>] \
    [--lorawan <value>] \
    [--tags <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | No | string | None | Profile name (max 256 chars) |
| `--lorawan` | No | structure | None | LoRaWAN service profile config |
| `--tags` | No | list | None | Tags (max 200) |
| `--client-request-token` | No | string | Auto | Idempotency token |

**LoRaWAN structure:**
```json
{
    "AddGwMetadata": true,
    "DrMin": 0,
    "DrMax": 15,
    "PrAllowed": false,
    "RaAllowed": false
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

### 5.6 `get-service-profile`

Retrieves information about a service profile.

**Synopsis:**
```bash
aws iotwireless get-service-profile \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Service profile ID |

**Output Schema:**
```json
{
    "Arn": "string",
    "Name": "string",
    "Id": "string",
    "LoRaWAN": {
        "UlRate": "integer",
        "UlBucketSize": "integer",
        "UlRatePolicy": "string",
        "DlRate": "integer",
        "DlBucketSize": "integer",
        "DlRatePolicy": "string",
        "AddGwMetadata": "boolean",
        "DevStatusReqFreq": "integer",
        "ReportDevStatusBattery": "boolean",
        "ReportDevStatusMargin": "boolean",
        "DrMin": "integer",
        "DrMax": "integer",
        "ChannelMask": "string",
        "PrAllowed": "boolean",
        "HrAllowed": "boolean",
        "RaAllowed": "boolean",
        "NwkGeoLoc": "boolean",
        "TargetPer": "integer",
        "MinGwDiversity": "integer"
    }
}
```

---

### 5.7 `list-service-profiles`

Lists service profiles. **Paginated operation.**

**Synopsis:**
```bash
aws iotwireless list-service-profiles \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (0-250) |

**Output Schema:**
```json
{
    "NextToken": "string",
    "ServiceProfileList": [
        {
            "Arn": "string",
            "Name": "string",
            "Id": "string"
        }
    ]
}
```

---

### 5.8 `delete-service-profile`

Deletes a service profile.

**Synopsis:**
```bash
aws iotwireless delete-service-profile \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Service profile ID |

**Output:** None
