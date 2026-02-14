# Multicast Groups

### 7.1 `create-multicast-group`

Creates a LoRaWAN multicast group for sending data to multiple devices simultaneously.

**Synopsis:**
```bash
aws iotwireless create-multicast-group \
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
| `--lorawan` | **Yes** | structure | -- | LoRaWAN multicast config |
| `--name` | No | string | None | Group name (max 256 chars) |
| `--description` | No | string | None | Description (max 2048 chars) |
| `--tags` | No | list | None | Tags (max 200) |
| `--client-request-token` | No | string | Auto | Idempotency token |

**LoRaWAN structure:**
```json
{
    "RfRegion": "US915",
    "DlClass": "ClassB|ClassC",
    "ParticipatingGateways": {
        "GatewayList": ["gateway-id-1", "gateway-id-2"],
        "TransmissionInterval": 1000
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

### 7.2 `get-multicast-group`

Retrieves information about a multicast group.

**Synopsis:**
```bash
aws iotwireless get-multicast-group \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Multicast group ID |

**Output Schema:**
```json
{
    "Arn": "string",
    "Id": "string",
    "Name": "string",
    "Description": "string",
    "Status": "string",
    "LoRaWAN": {
        "RfRegion": "string",
        "DlClass": "ClassB|ClassC",
        "NumberOfDevicesRequested": "integer",
        "NumberOfDevicesInGroup": "integer",
        "ParticipatingGateways": {
            "GatewayList": ["string"],
            "TransmissionInterval": "integer"
        }
    },
    "CreatedAt": "timestamp"
}
```

---

### 7.3 `list-multicast-groups`

Lists multicast groups. **Paginated operation.**

**Synopsis:**
```bash
aws iotwireless list-multicast-groups \
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
    "MulticastGroupList": [
        {
            "Id": "string",
            "Arn": "string",
            "Name": "string"
        }
    ]
}
```

---

### 7.4 `update-multicast-group`

Updates a multicast group.

**Synopsis:**
```bash
aws iotwireless update-multicast-group \
    --id <value> \
    [--name <value>] \
    [--description <value>] \
    [--lorawan <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Multicast group ID |
| `--name` | No | string | None | Updated name |
| `--description` | No | string | None | Updated description |
| `--lorawan` | No | structure | None | Updated LoRaWAN config |

**Output:** None

---

### 7.5 `delete-multicast-group`

Deletes a multicast group.

**Synopsis:**
```bash
aws iotwireless delete-multicast-group \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Multicast group ID |

**Output:** None

---

### 7.6 `get-multicast-group-session`

Gets session information for a multicast group.

**Synopsis:**
```bash
aws iotwireless get-multicast-group-session \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Multicast group ID |

**Output Schema:**
```json
{
    "LoRaWAN": {
        "DlDr": "integer",
        "DlFreq": "integer",
        "SessionStartTime": "timestamp",
        "SessionTimeout": "integer",
        "PingSlotPeriod": "integer"
    }
}
```

---

### 7.7 `start-multicast-group-session`

Starts a multicast group session.

**Synopsis:**
```bash
aws iotwireless start-multicast-group-session \
    --id <value> \
    --lorawan <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Multicast group ID |
| `--lorawan` | **Yes** | structure | -- | Session configuration |

**LoRaWAN structure:**
```json
{
    "DlDr": 0,
    "DlFreq": 923300000,
    "SessionStartTime": "2024-01-15T10:00:00Z",
    "SessionTimeout": 300,
    "PingSlotPeriod": 32
}
```

**Output:** None

---

### 7.8 `cancel-multicast-group-session`

Cancels a multicast group session.

**Synopsis:**
```bash
aws iotwireless cancel-multicast-group-session \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Multicast group ID |

**Output:** None

---

### 7.9 `send-data-to-multicast-group`

Sends data to all devices in a multicast group.

**Synopsis:**
```bash
aws iotwireless send-data-to-multicast-group \
    --id <value> \
    --payload-data <value> \
    --wireless-metadata <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Multicast group ID |
| `--payload-data` | **Yes** | string | -- | Base64-encoded payload (max 2048 chars) |
| `--wireless-metadata` | **Yes** | structure | -- | Multicast metadata |

**Wireless metadata:**
```json
{
    "LoRaWAN": {
        "FPort": 1
    }
}
```

**Output Schema:**
```json
{
    "MessageId": "string"
}
```

---

### 7.10 `associate-wireless-device-with-multicast-group`

Associates a wireless device with a multicast group.

**Synopsis:**
```bash
aws iotwireless associate-wireless-device-with-multicast-group \
    --id <value> \
    --wireless-device-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Multicast group ID |
| `--wireless-device-id` | **Yes** | string | -- | Wireless device ID |

**Output:** None

---

### 7.11 `disassociate-wireless-device-from-multicast-group`

Disassociates a wireless device from a multicast group.

**Synopsis:**
```bash
aws iotwireless disassociate-wireless-device-from-multicast-group \
    --id <value> \
    --wireless-device-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Multicast group ID |
| `--wireless-device-id` | **Yes** | string | -- | Wireless device ID |

**Output:** None

---

### 7.12 `start-bulk-associate-wireless-device-with-multicast-group`

Starts a bulk association of wireless devices with a multicast group.

**Synopsis:**
```bash
aws iotwireless start-bulk-associate-wireless-device-with-multicast-group \
    --id <value> \
    [--query-string <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Multicast group ID |
| `--query-string` | No | string | None | Query string to filter devices |
| `--tags` | No | list | None | Tags (max 200) |

**Output:** None

---

### 7.13 `start-bulk-disassociate-wireless-device-from-multicast-group`

Starts a bulk disassociation of wireless devices from a multicast group.

**Synopsis:**
```bash
aws iotwireless start-bulk-disassociate-wireless-device-from-multicast-group \
    --id <value> \
    [--query-string <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Multicast group ID |
| `--query-string` | No | string | None | Query string to filter devices |
| `--tags` | No | list | None | Tags (max 200) |

**Output:** None

---

### 7.14 `list-multicast-groups-by-fuota-task`

Lists multicast groups associated with a FUOTA task. **Paginated operation.**

**Synopsis:**
```bash
aws iotwireless list-multicast-groups-by-fuota-task \
    --id <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | FUOTA task ID |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (0-250) |

**Output Schema:**
```json
{
    "NextToken": "string",
    "MulticastGroupList": [
        {
            "Id": "string"
        }
    ]
}
```
