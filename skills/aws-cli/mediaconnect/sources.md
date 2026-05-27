# Sources

### 2.1 `add-flow-sources`

Adds one or more sources to an existing flow.

**Synopsis:**
```bash
aws mediaconnect add-flow-sources \
    --flow-arn <value> \
    --sources <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--flow-arn` | **Yes** | string | -- | ARN of the flow |
| `--sources` | **Yes** | list | -- | Source configurations to add |

**Source Structure:**

| Field | Required | Type | Description |
|-------|----------|------|-------------|
| `Name` | No | string | Source name |
| `Protocol` | No | string | Transport protocol (see flows.md for full list) |
| `IngestPort` | No | integer | Port for incoming content |
| `WhitelistCidr` | No | string | CIDR block for allowed IPs |
| `MaxBitrate` | No | integer | Max bitrate in bps |
| `MaxLatency` | No | integer | Max latency in ms |
| `MinLatency` | No | integer | Min latency in ms |
| `MaxSyncBuffer` | No | integer | Buffer size in ms for sync |
| `EntitlementArn` | No | string | ARN of entitlement for subscription |
| `Decryption` | No | structure | Decryption config (Algorithm, KeyType, RoleArn, SecretArn) |
| `VpcInterfaceName` | No | string | VPC interface to use |
| `GatewayBridgeSource` | No | structure | Bridge source (BridgeArn, VpcInterfaceAttachment) |
| `SenderIpAddress` | No | string | IP for initiating connection |
| `SenderControlPort` | No | integer | Port for outbound requests |
| `StreamId` | No | string | Stream ID for Zixi/SRT |
| `MediaStreamSourceConfigurations` | No | list | Media stream associations |
| `NdiSourceSettings` | No | structure | NDI source settings |

**Output Schema:**
```json
{
    "FlowArn": "string",
    "Sources": [
        {
            "SourceArn": "string",
            "Name": "string",
            "Description": "string",
            "IngestIp": "string",
            "IngestPort": "integer",
            "Transport": {
                "Protocol": "string",
                "MaxBitrate": "integer",
                "MaxLatency": "integer"
            },
            "Decryption": {},
            "VpcInterfaceName": "string"
        }
    ]
}
```

---

### 2.2 `update-flow-source`

Updates an existing source on a flow.

**Synopsis:**
```bash
aws mediaconnect update-flow-source \
    --flow-arn <value> \
    --source-arn <value> \
    [--decryption <value>] \
    [--description <value>] \
    [--entitlement-arn <value>] \
    [--ingest-port <value>] \
    [--max-bitrate <value>] \
    [--max-latency <value>] \
    [--min-latency <value>] \
    [--protocol <value>] \
    [--stream-id <value>] \
    [--vpc-interface-name <value>] \
    [--whitelist-cidr <value>] \
    [--max-sync-buffer <value>] \
    [--media-stream-source-configurations <value>] \
    [--sender-control-port <value>] \
    [--sender-ip-address <value>] \
    [--source-listener-address <value>] \
    [--source-listener-port <value>] \
    [--gateway-bridge-source <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--flow-arn` | **Yes** | string | -- | ARN of the flow |
| `--source-arn` | **Yes** | string | -- | ARN of the source to update |
| `--decryption` | No | structure | None | Updated decryption config |
| `--description` | No | string | None | Updated description |
| `--protocol` | No | string | None | Updated protocol |
| `--ingest-port` | No | integer | None | Updated ingest port |
| `--whitelist-cidr` | No | string | None | Updated CIDR whitelist |
| `--max-bitrate` | No | integer | None | Updated max bitrate |
| `--max-latency` | No | integer | None | Updated max latency |
| `--min-latency` | No | integer | None | Updated min latency |
| `--stream-id` | No | string | None | Updated stream ID |
| `--vpc-interface-name` | No | string | None | Updated VPC interface |

**Output Schema:**
```json
{
    "FlowArn": "string",
    "Source": { "..." }
}
```

---

### 2.3 `remove-flow-source`

Removes a source from a flow.

**Synopsis:**
```bash
aws mediaconnect remove-flow-source \
    --flow-arn <value> \
    --source-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--flow-arn` | **Yes** | string | -- | ARN of the flow |
| `--source-arn` | **Yes** | string | -- | ARN of the source to remove |

**Output Schema:**
```json
{
    "FlowArn": "string",
    "SourceArn": "string"
}
```
