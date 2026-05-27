# Outputs

### 3.1 `add-flow-outputs`

Adds one or more outputs to a flow. A flow can have up to 50 outputs.

**Synopsis:**
```bash
aws mediaconnect add-flow-outputs \
    --flow-arn <value> \
    --outputs <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--flow-arn` | **Yes** | string | -- | ARN of the flow |
| `--outputs` | **Yes** | list | -- | Output configurations to add |

**Output Structure:**

| Field | Required | Type | Description |
|-------|----------|------|-------------|
| `Name` | No | string | Output name (unique within flow) |
| `Protocol` | No | string | `zixi-push`, `rtp-fec`, `rtp`, `zixi-pull`, `rist`, `srt-listener`, `srt-caller`, `udp`, `ndi-speed-hq` |
| `Destination` | No | string | Destination IP address |
| `Port` | No | integer | Destination port |
| `Description` | No | string | Output description |
| `CidrAllowList` | No | list | CIDR blocks for allowed connections |
| `MaxLatency` | No | integer | Max latency in ms |
| `MinLatency` | No | integer | Min latency in ms |
| `SmoothingLatency` | No | integer | Smoothing latency in ms |
| `Encryption` | No | structure | Encryption config (Algorithm, KeyType, RoleArn, SecretArn) |
| `VpcInterfaceAttachment` | No | structure | VPC interface to use |
| `MediaStreamOutputConfigurations` | No | list | Media stream associations |
| `OutputStatus` | No | string | `ENABLED` or `DISABLED` |
| `RemoteId` | No | string | Remote ID for Zixi-pull |
| `StreamId` | No | string | Stream ID for Zixi/SRT |
| `SenderControlPort` | No | integer | Port for outbound requests |

**Output Schema:**
```json
{
    "FlowArn": "string",
    "Outputs": [
        {
            "OutputArn": "string",
            "Name": "string",
            "Description": "string",
            "Destination": "string",
            "Port": "integer",
            "Transport": {
                "Protocol": "string",
                "SmoothingLatency": "integer",
                "MaxLatency": "integer",
                "MinLatency": "integer",
                "CidrAllowList": ["string"]
            },
            "Encryption": {},
            "OutputStatus": "ENABLED|DISABLED",
            "VpcInterfaceAttachment": {"VpcInterfaceName": "string"}
        }
    ]
}
```

---

### 3.2 `update-flow-output`

Updates an existing output on a flow.

**Synopsis:**
```bash
aws mediaconnect update-flow-output \
    --flow-arn <value> \
    --output-arn <value> \
    [--cidr-allow-list <value>] \
    [--description <value>] \
    [--destination <value>] \
    [--encryption <value>] \
    [--max-latency <value>] \
    [--min-latency <value>] \
    [--port <value>] \
    [--protocol <value>] \
    [--remote-id <value>] \
    [--smoothing-latency <value>] \
    [--stream-id <value>] \
    [--vpc-interface-attachment <value>] \
    [--output-status <value>] \
    [--sender-control-port <value>] \
    [--media-stream-output-configurations <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--flow-arn` | **Yes** | string | -- | ARN of the flow |
| `--output-arn` | **Yes** | string | -- | ARN of the output to update |
| `--destination` | No | string | None | Updated destination IP |
| `--port` | No | integer | None | Updated port |
| `--protocol` | No | string | None | Updated protocol |
| `--encryption` | No | structure | None | Updated encryption config |
| `--max-latency` | No | integer | None | Updated max latency |
| `--smoothing-latency` | No | integer | None | Updated smoothing latency |
| `--output-status` | No | string | None | `ENABLED` or `DISABLED` |
| `--cidr-allow-list` | No | list | None | Updated CIDR allow list |

**Output Schema:**
```json
{
    "FlowArn": "string",
    "Output": { "..." }
}
```

---

### 3.3 `remove-flow-output`

Removes an output from a flow.

**Synopsis:**
```bash
aws mediaconnect remove-flow-output \
    --flow-arn <value> \
    --output-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--flow-arn` | **Yes** | string | -- | ARN of the flow |
| `--output-arn` | **Yes** | string | -- | ARN of the output to remove |

**Output Schema:**
```json
{
    "FlowArn": "string",
    "OutputArn": "string"
}
```
