# Network Analyzer

### 9.1 `create-network-analyzer-configuration`

Creates a network analyzer configuration for monitoring wireless device and gateway traffic.

**Synopsis:**
```bash
aws iotwireless create-network-analyzer-configuration \
    --name <value> \
    [--trace-content <value>] \
    [--wireless-devices <value>] \
    [--wireless-gateways <value>] \
    [--description <value>] \
    [--tags <value>] \
    [--multicast-groups <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Configuration name (1-1024 chars) |
| `--trace-content` | No | structure | None | Trace content configuration |
| `--wireless-devices` | No | list | None | Wireless device IDs to trace (max 250) |
| `--wireless-gateways` | No | list | None | Wireless gateway IDs to trace (max 250) |
| `--description` | No | string | None | Description (max 2048 chars) |
| `--tags` | No | list | None | Tags (max 200) |
| `--multicast-groups` | No | list | None | Multicast group IDs to trace |
| `--client-request-token` | No | string | Auto | Idempotency token |

**Trace content:**
```json
{
    "WirelessDeviceFrameInfo": "ENABLED|DISABLED",
    "LogLevel": "INFO|ERROR|DISABLED",
    "MulticastFrameInfo": "ENABLED|DISABLED"
}
```

**Output Schema:**
```json
{
    "Arn": "string",
    "Name": "string"
}
```

---

### 9.2 `get-network-analyzer-configuration`

Retrieves a network analyzer configuration.

**Synopsis:**
```bash
aws iotwireless get-network-analyzer-configuration \
    --configuration-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configuration-name` | **Yes** | string | -- | Configuration name |

**Output Schema:**
```json
{
    "TraceContent": {
        "WirelessDeviceFrameInfo": "ENABLED|DISABLED",
        "LogLevel": "INFO|ERROR|DISABLED",
        "MulticastFrameInfo": "ENABLED|DISABLED"
    },
    "WirelessDevices": ["string"],
    "WirelessGateways": ["string"],
    "Description": "string",
    "Arn": "string",
    "Name": "string",
    "MulticastGroups": ["string"]
}
```

---

### 9.3 `list-network-analyzer-configurations`

Lists network analyzer configurations. **Paginated operation.**

**Synopsis:**
```bash
aws iotwireless list-network-analyzer-configurations \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--max-results` | No | integer | None | Max results (0-250) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "NextToken": "string",
    "NetworkAnalyzerConfigurationList": [
        {
            "Arn": "string",
            "Name": "string"
        }
    ]
}
```

---

### 9.4 `update-network-analyzer-configuration`

Updates a network analyzer configuration.

**Synopsis:**
```bash
aws iotwireless update-network-analyzer-configuration \
    --configuration-name <value> \
    [--trace-content <value>] \
    [--wireless-devices-to-add <value>] \
    [--wireless-devices-to-remove <value>] \
    [--wireless-gateways-to-add <value>] \
    [--wireless-gateways-to-remove <value>] \
    [--description <value>] \
    [--multicast-groups-to-add <value>] \
    [--multicast-groups-to-remove <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configuration-name` | **Yes** | string | -- | Configuration name |
| `--trace-content` | No | structure | None | Updated trace content |
| `--wireless-devices-to-add` | No | list | None | Device IDs to add |
| `--wireless-devices-to-remove` | No | list | None | Device IDs to remove |
| `--wireless-gateways-to-add` | No | list | None | Gateway IDs to add |
| `--wireless-gateways-to-remove` | No | list | None | Gateway IDs to remove |
| `--description` | No | string | None | Updated description |
| `--multicast-groups-to-add` | No | list | None | Multicast group IDs to add |
| `--multicast-groups-to-remove` | No | list | None | Multicast group IDs to remove |

**Output:** None

---

### 9.5 `delete-network-analyzer-configuration`

Deletes a network analyzer configuration.

**Synopsis:**
```bash
aws iotwireless delete-network-analyzer-configuration \
    --configuration-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--configuration-name` | **Yes** | string | -- | Configuration name |

**Output:** None
