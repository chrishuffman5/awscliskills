# FUOTA Tasks

### 6.1 `create-fuota-task`

Creates a firmware update over-the-air (FUOTA) task.

**Synopsis:**
```bash
aws iotwireless create-fuota-task \
    --firmware-update-image <value> \
    --firmware-update-role <value> \
    [--name <value>] \
    [--description <value>] \
    [--lorawan <value>] \
    [--redundancy-percent <value>] \
    [--fragment-size-bytes <value>] \
    [--fragment-interval-ms <value>] \
    [--descriptor <value>] \
    [--tags <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--firmware-update-image` | **Yes** | string | -- | S3 URI of the firmware image (max 4096 chars) |
| `--firmware-update-role` | **Yes** | string | -- | IAM role ARN for firmware access (max 2048 chars) |
| `--name` | No | string | None | Task name (max 256 chars) |
| `--description` | No | string | None | Description (max 2048 chars) |
| `--lorawan` | No | structure | None | LoRaWAN configuration with RfRegion |
| `--redundancy-percent` | No | integer | None | Redundant fragment percentage (0-100) |
| `--fragment-size-bytes` | No | integer | None | Fragment size in bytes (min 1) |
| `--fragment-interval-ms` | No | integer | None | Fragment sending interval in ms (min 1) |
| `--descriptor` | No | string | None | Base64-encoded file metadata (max 332 chars) |
| `--tags` | No | list | None | Tags (max 200) |
| `--client-request-token` | No | string | Auto | Idempotency token |

**LoRaWAN structure:**
```json
{
    "RfRegion": "US915|EU868|AU915|AS923-1|AS923-2|AS923-3|AS923-4|EU433|CN470|CN779|RU864|KR920|IN865"
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

### 6.2 `get-fuota-task`

Retrieves information about a FUOTA task.

**Synopsis:**
```bash
aws iotwireless get-fuota-task \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | FUOTA task ID |

**Output Schema:**
```json
{
    "Arn": "string",
    "Id": "string",
    "Status": "Pending|FuotaSession_Waiting|In_FuotaSession|FuotaDone|Delete_Waiting",
    "Name": "string",
    "Description": "string",
    "LoRaWAN": {
        "RfRegion": "string",
        "StartTime": "timestamp"
    },
    "FirmwareUpdateImage": "string",
    "FirmwareUpdateRole": "string",
    "RedundancyPercent": "integer",
    "FragmentSizeBytes": "integer",
    "FragmentIntervalMS": "integer",
    "CreatedAt": "timestamp"
}
```

---

### 6.3 `list-fuota-tasks`

Lists FUOTA tasks. **Paginated operation.**

**Synopsis:**
```bash
aws iotwireless list-fuota-tasks \
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
    "FuotaTaskList": [
        {
            "Id": "string",
            "Arn": "string",
            "Name": "string"
        }
    ]
}
```

---

### 6.4 `update-fuota-task`

Updates a FUOTA task.

**Synopsis:**
```bash
aws iotwireless update-fuota-task \
    --id <value> \
    [--name <value>] \
    [--description <value>] \
    [--lorawan <value>] \
    [--firmware-update-image <value>] \
    [--firmware-update-role <value>] \
    [--redundancy-percent <value>] \
    [--fragment-size-bytes <value>] \
    [--fragment-interval-ms <value>] \
    [--descriptor <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | FUOTA task ID |
| `--name` | No | string | None | Updated name |
| `--description` | No | string | None | Updated description |
| `--lorawan` | No | structure | None | Updated LoRaWAN config |
| `--firmware-update-image` | No | string | None | Updated firmware S3 URI |
| `--firmware-update-role` | No | string | None | Updated IAM role |
| `--redundancy-percent` | No | integer | None | Updated redundancy (0-100) |
| `--fragment-size-bytes` | No | integer | None | Updated fragment size |
| `--fragment-interval-ms` | No | integer | None | Updated fragment interval |
| `--descriptor` | No | string | None | Updated descriptor |

**Output:** None

---

### 6.5 `delete-fuota-task`

Deletes a FUOTA task.

**Synopsis:**
```bash
aws iotwireless delete-fuota-task \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | FUOTA task ID |

**Output:** None

---

### 6.6 `start-fuota-task`

Starts a FUOTA task, beginning the firmware update session.

**Synopsis:**
```bash
aws iotwireless start-fuota-task \
    --id <value> \
    [--lorawan <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | FUOTA task ID |
| `--lorawan` | No | structure | None | LoRaWAN start time config |

**LoRaWAN structure:**
```json
{
    "StartTime": "2024-01-15T10:00:00Z"
}
```

**Output:** None

---

### 6.7 `associate-wireless-device-with-fuota-task`

Associates a wireless device with a FUOTA task.

**Synopsis:**
```bash
aws iotwireless associate-wireless-device-with-fuota-task \
    --id <value> \
    --wireless-device-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | FUOTA task ID |
| `--wireless-device-id` | **Yes** | string | -- | Wireless device ID |

**Output:** None

---

### 6.8 `disassociate-wireless-device-from-fuota-task`

Disassociates a wireless device from a FUOTA task.

**Synopsis:**
```bash
aws iotwireless disassociate-wireless-device-from-fuota-task \
    --id <value> \
    --wireless-device-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | FUOTA task ID |
| `--wireless-device-id` | **Yes** | string | -- | Wireless device ID |

**Output:** None

---

### 6.9 `associate-multicast-group-with-fuota-task`

Associates a multicast group with a FUOTA task.

**Synopsis:**
```bash
aws iotwireless associate-multicast-group-with-fuota-task \
    --id <value> \
    --multicast-group-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | FUOTA task ID |
| `--multicast-group-id` | **Yes** | string | -- | Multicast group ID |

**Output:** None

---

### 6.10 `disassociate-multicast-group-from-fuota-task`

Disassociates a multicast group from a FUOTA task.

**Synopsis:**
```bash
aws iotwireless disassociate-multicast-group-from-fuota-task \
    --id <value> \
    --multicast-group-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | FUOTA task ID |
| `--multicast-group-id` | **Yes** | string | -- | Multicast group ID |

**Output:** None
