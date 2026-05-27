# Input Devices

### 4.1 `describe-input-device`

Describes a hardware input device (e.g., AWS Elemental Link).

**Synopsis:**
```bash
aws medialive describe-input-device \
    --input-device-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--input-device-id` | **Yes** | string | -- | Input device ID |

**Output Schema:**
```json
{
    "Arn": "string",
    "Id": "string",
    "Name": "string",
    "ConnectionState": "DISCONNECTED|CONNECTED",
    "DeviceSettingsSyncState": "SYNCED|SYNCING",
    "DeviceUpdateStatus": "UP_TO_DATE|NOT_UP_TO_DATE|UPDATING",
    "HdDeviceSettings": {},
    "UhdDeviceSettings": {},
    "MacAddress": "string",
    "NetworkSettings": {},
    "SerialNumber": "string",
    "Type": "HD|UHD",
    "AvailabilityZone": "string",
    "MedialiveInputArns": ["string"],
    "OutputType": "NONE|MEDIALIVE_INPUT|MEDIACONNECT_FLOW",
    "Tags": {}
}
```

---

### 4.2 `update-input-device`

Updates settings for an input device.

**Synopsis:**
```bash
aws medialive update-input-device \
    --input-device-id <value> \
    [--name <value>] \
    [--hd-device-settings <value>] \
    [--uhd-device-settings <value>] \
    [--availability-zone <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--input-device-id` | **Yes** | string | -- | Device ID to update |
| `--name` | No | string | None | Updated name |
| `--hd-device-settings` | No | structure | None | HD device configuration |
| `--uhd-device-settings` | No | structure | None | UHD device configuration |
| `--availability-zone` | No | string | None | AZ for the device |

**Output Schema:** Same as `describe-input-device` output.

---

### 4.3 `list-input-devices`

Lists input devices. **Paginated operation.**

**Synopsis:**
```bash
aws medialive list-input-devices \
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
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "NextToken": "string",
    "InputDevices": [
        {
            "Arn": "string",
            "Id": "string",
            "Name": "string",
            "ConnectionState": "string",
            "Type": "HD|UHD",
            "AvailabilityZone": "string",
            "OutputType": "string"
        }
    ]
}
```

---

### 4.4 `start-input-device`

Starts an input device that is attached to a MediaConnect flow.

**Synopsis:**
```bash
aws medialive start-input-device \
    --input-device-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--input-device-id` | **Yes** | string | -- | Device ID to start |

**Output:** None

---

### 4.5 `stop-input-device`

Stops an input device.

**Synopsis:**
```bash
aws medialive stop-input-device \
    --input-device-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--input-device-id` | **Yes** | string | -- | Device ID to stop |

**Output:** None

---

### 4.6 `reboot-input-device`

Reboots an input device, optionally forcing a specific reboot type.

**Synopsis:**
```bash
aws medialive reboot-input-device \
    --input-device-id <value> \
    [--force <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--input-device-id` | **Yes** | string | -- | Device ID to reboot |
| `--force` | No | string | None | `NO` or `YES` to force reboot |

**Output:** None

---

### 4.7 `describe-input-device-thumbnail`

Gets a thumbnail image of the input device's current video output.

**Synopsis:**
```bash
aws medialive describe-input-device-thumbnail \
    --input-device-id <value> \
    --accept <value> \
    <outfile> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--input-device-id` | **Yes** | string | -- | Device ID |
| `--accept` | **Yes** | string | -- | `image/jpeg` |
| `outfile` | **Yes** | string | -- | Output file path for the image |

**Output:** Binary image data saved to outfile.

---

### 4.8 `transfer-input-device`

Transfers an input device to another AWS account.

**Synopsis:**
```bash
aws medialive transfer-input-device \
    --input-device-id <value> \
    [--target-customer-id <value>] \
    [--target-region <value>] \
    [--transfer-message <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--input-device-id` | **Yes** | string | -- | Device ID to transfer |
| `--target-customer-id` | No | string | None | Target AWS account ID |
| `--target-region` | No | string | None | Target region |
| `--transfer-message` | No | string | None | Message to recipient |

**Output:** None

---

### 4.9 `accept-input-device-transfer`

Accepts a pending input device transfer.

**Synopsis:**
```bash
aws medialive accept-input-device-transfer \
    --input-device-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--input-device-id` | **Yes** | string | -- | Device ID to accept |

**Output:** None

---

### 4.10 `cancel-input-device-transfer`

Cancels a pending input device transfer (by the sender).

**Synopsis:**
```bash
aws medialive cancel-input-device-transfer \
    --input-device-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--input-device-id` | **Yes** | string | -- | Device ID to cancel transfer |

**Output:** None

---

### 4.11 `reject-input-device-transfer`

Rejects a pending input device transfer (by the recipient).

**Synopsis:**
```bash
aws medialive reject-input-device-transfer \
    --input-device-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--input-device-id` | **Yes** | string | -- | Device ID to reject |

**Output:** None

---

### 4.12 `list-input-device-transfers`

Lists pending input device transfers. **Paginated operation.**

**Synopsis:**
```bash
aws medialive list-input-device-transfers \
    --transfer-type <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--transfer-type` | **Yes** | string | -- | `INCOMING` or `OUTGOING` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "NextToken": "string",
    "InputDeviceTransfers": [
        {
            "Id": "string",
            "Message": "string",
            "TargetCustomerId": "string",
            "TransferType": "INCOMING|OUTGOING"
        }
    ]
}
```

---

### 4.13 `start-input-device-maintenance-window`

Starts a maintenance window for an input device.

**Synopsis:**
```bash
aws medialive start-input-device-maintenance-window \
    --input-device-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--input-device-id` | **Yes** | string | -- | Device ID |

**Output:** None
