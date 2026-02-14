# Flows

### 1.1 `create-flow`

Creates a new flow for transporting live video content.

**Synopsis:**
```bash
aws mediaconnect create-flow \
    --name <value> \
    [--availability-zone <value>] \
    [--description <value>] \
    [--flow-size <value>] \
    [--source <value>] \
    [--sources <value>] \
    [--outputs <value>] \
    [--entitlements <value>] \
    [--media-streams <value>] \
    [--vpc-interfaces <value>] \
    [--source-failover-config <value>] \
    [--maintenance <value>] \
    [--source-monitoring-config <value>] \
    [--ndi-config <value>] \
    [--flow-tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the flow |
| `--availability-zone` | No | string | None | AZ for the flow |
| `--description` | No | string | None | Description of the flow |
| `--flow-size` | No | string | None | Processing capacity: `MEDIUM`, `LARGE`, `LARGE_4X` |
| `--source` | No | structure | None | Single source config (deprecated, use `--sources`) |
| `--sources` | No | list | None | Multiple source configurations |
| `--outputs` | No | list | None | Output configurations (up to 50) |
| `--entitlements` | No | list | None | Entitlement configurations (up to 50) |
| `--media-streams` | No | list | None | Media stream configurations |
| `--vpc-interfaces` | No | list | None | VPC interface configurations |
| `--source-failover-config` | No | structure | None | Source failover settings |
| `--maintenance` | No | structure | None | Maintenance window settings |
| `--source-monitoring-config` | No | structure | None | Source monitoring settings |
| `--ndi-config` | No | structure | None | NDI configuration |
| `--flow-tags` | No | map | None | Key-value tag pairs |

**Source Structure (key fields):**

| Field | Required | Type | Description |
|-------|----------|------|-------------|
| `Name` | **Yes** | string | Source name |
| `Protocol` | **Yes** | string | `zixi-push`, `rtp-fec`, `rtp`, `zixi-pull`, `rist`, `st2110-jpegxs`, `cdi`, `srt-listener`, `srt-caller`, `udp`, `ndi-speed-hq` |
| `IngestPort` | No | integer | Port for incoming content |
| `WhitelistCidr` | No | string | CIDR block for allowed IPs |
| `MaxBitrate` | No | integer | Max bitrate in bps |
| `MaxLatency` | No | integer | Max latency in ms |
| `MinLatency` | No | integer | Min latency in ms |
| `Decryption` | No | structure | Encryption config (Algorithm, KeyType, RoleArn, SecretArn) |
| `VpcInterfaceName` | No | string | VPC interface to use |
| `GatewayBridgeSource` | No | structure | Bridge source config |

**SourceFailoverConfig:**
```json
{
    "FailoverMode": "MERGE|FAILOVER",
    "RecoveryWindow": 200,
    "SourcePriority": {"PrimarySource": "source-name"},
    "State": "ENABLED|DISABLED"
}
```

**Output Schema:**
```json
{
    "Flow": {
        "FlowArn": "string",
        "Name": "string",
        "AvailabilityZone": "string",
        "Status": "STANDBY|ACTIVE|UPDATING|DELETING|STARTING|STOPPING|ERROR",
        "Description": "string",
        "EgressIp": "string",
        "FlowSize": "MEDIUM|LARGE|LARGE_4X",
        "Source": {},
        "Sources": [],
        "Outputs": [],
        "Entitlements": [],
        "MediaStreams": [],
        "VpcInterfaces": [],
        "Maintenance": {},
        "SourceMonitoringConfig": {}
    }
}
```

---

### 1.2 `describe-flow`

Describes a flow including its sources, outputs, entitlements, and status.

**Synopsis:**
```bash
aws mediaconnect describe-flow \
    --flow-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--flow-arn` | **Yes** | string | -- | ARN of the flow |

**Output Schema:** Same as `create-flow` output with additional `Messages` field containing error details.

---

### 1.3 `list-flows`

Lists all flows in the account. **Paginated operation.**

**Synopsis:**
```bash
aws mediaconnect list-flows \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--max-results` | No | integer | None | Max results per page (1-1000) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "Flows": [
        {
            "FlowArn": "string",
            "Name": "string",
            "AvailabilityZone": "string",
            "Description": "string",
            "Status": "STANDBY|ACTIVE|UPDATING|DELETING|STARTING|STOPPING|ERROR",
            "SourceType": "OWNED|ENTITLED",
            "Maintenance": {}
        }
    ],
    "NextToken": "string"
}
```

---

### 1.4 `update-flow`

Updates a flow's configuration.

**Synopsis:**
```bash
aws mediaconnect update-flow \
    --flow-arn <value> \
    [--source-failover-config <value>] \
    [--maintenance <value>] \
    [--source-monitoring-config <value>] \
    [--flow-size <value>] \
    [--ndi-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--flow-arn` | **Yes** | string | -- | ARN of the flow |
| `--source-failover-config` | No | structure | None | Updated failover config |
| `--maintenance` | No | structure | None | Updated maintenance window |
| `--source-monitoring-config` | No | structure | None | Updated monitoring config |
| `--flow-size` | No | string | None | Updated capacity: `MEDIUM`, `LARGE`, `LARGE_4X` |
| `--ndi-config` | No | structure | None | Updated NDI config |

**Output Schema:**
```json
{
    "Flow": { "..." }
}
```

---

### 1.5 `delete-flow`

Deletes a flow. The flow must be stopped before deletion.

**Synopsis:**
```bash
aws mediaconnect delete-flow \
    --flow-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--flow-arn` | **Yes** | string | -- | ARN of the flow to delete |

**Output Schema:**
```json
{
    "FlowArn": "string",
    "Status": "STANDBY|ACTIVE|UPDATING|DELETING|STARTING|STOPPING|ERROR"
}
```

---

### 1.6 `start-flow`

Starts a flow.

**Synopsis:**
```bash
aws mediaconnect start-flow \
    --flow-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--flow-arn` | **Yes** | string | -- | ARN of the flow to start |

**Output Schema:**
```json
{
    "FlowArn": "string",
    "Status": "STARTING"
}
```

---

### 1.7 `stop-flow`

Stops a flow.

**Synopsis:**
```bash
aws mediaconnect stop-flow \
    --flow-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--flow-arn` | **Yes** | string | -- | ARN of the flow to stop |

**Output Schema:**
```json
{
    "FlowArn": "string",
    "Status": "STOPPING"
}
```

---

### 1.8 `describe-flow-source-metadata`

Retrieves metadata about a flow's source, including transport stream details.

**Synopsis:**
```bash
aws mediaconnect describe-flow-source-metadata \
    --flow-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--flow-arn` | **Yes** | string | -- | ARN of the flow |

**Output Schema:**
```json
{
    "FlowArn": "string",
    "Messages": [{"Code": "string", "Message": "string", "ResourceName": "string"}],
    "Timestamp": "timestamp",
    "TransportMediaInfo": {
        "Programs": [
            {
                "PcrPid": "integer",
                "ProgramNumber": "integer",
                "ProgramPid": "integer",
                "Streams": [
                    {
                        "Channels": "integer",
                        "Codec": "string",
                        "FrameRate": "string",
                        "FrameResolution": {"FrameHeight": "integer", "FrameWidth": "integer"},
                        "Pid": "integer",
                        "SampleRate": "integer",
                        "SampleSize": "integer",
                        "StreamType": "string"
                    }
                ]
            }
        ]
    }
}
```

---

### 1.9 `describe-flow-source-thumbnail`

Retrieves a thumbnail for the flow source.

**Synopsis:**
```bash
aws mediaconnect describe-flow-source-thumbnail \
    --flow-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--flow-arn` | **Yes** | string | -- | ARN of the flow |

**Output Schema:**
```json
{
    "ThumbnailDetails": {
        "FlowArn": "string",
        "Thumbnail": "string",
        "ThumbnailMessages": [{"Code": "string", "Message": "string", "ResourceName": "string"}],
        "Timecode": "string",
        "Timestamp": "timestamp"
    }
}
```
