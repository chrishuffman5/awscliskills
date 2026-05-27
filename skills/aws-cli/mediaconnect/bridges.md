# Bridges

### 7.1 `create-bridge`

Creates a bridge for hybrid cloud-to-ground or ground-to-cloud workflows.

**Synopsis:**
```bash
aws mediaconnect create-bridge \
    --name <value> \
    --placement-arn <value> \
    --sources <value> \
    [--egress-gateway-bridge <value>] \
    [--ingress-gateway-bridge <value>] \
    [--outputs <value>] \
    [--source-failover-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Bridge name (immutable) |
| `--placement-arn` | **Yes** | string | -- | Gateway ARN for bridge placement |
| `--sources` | **Yes** | list | -- | Bridge source configurations |
| `--egress-gateway-bridge` | No | structure | None | Egress bridge config (cloud-to-ground): `MaxBitrate` |
| `--ingress-gateway-bridge` | No | structure | None | Ingress bridge config (ground-to-cloud): `MaxBitrate`, `MaxOutputs` |
| `--outputs` | No | list | None | Bridge output configurations |
| `--source-failover-config` | No | structure | None | Source failover settings |

**Bridge Source Types:**
```json
{
    "FlowSource": {
        "FlowArn": "string",
        "FlowVpcInterfaceAttachment": {"VpcInterfaceName": "string"},
        "Name": "string"
    },
    "NetworkSource": {
        "MulticastIp": "string",
        "Name": "string",
        "NetworkName": "string",
        "Port": "integer",
        "Protocol": "string"
    }
}
```

**Bridge Output Types:**
```json
{
    "NetworkOutput": {
        "IpAddress": "string",
        "Name": "string",
        "NetworkName": "string",
        "Port": "integer",
        "Protocol": "string",
        "Ttl": "integer"
    }
}
```

**Output Schema:**
```json
{
    "Bridge": {
        "BridgeArn": "string",
        "BridgeState": "CREATING|STANDBY|STARTING|DEPLOYING|ACTIVE|STOPPING|DELETING|DELETED|START_FAILED|START_PENDING|STOP_FAILED|UPDATING",
        "Name": "string",
        "PlacementArn": "string",
        "Sources": [],
        "Outputs": [],
        "EgressGatewayBridge": {"InstanceId": "string", "MaxBitrate": "integer"},
        "IngressGatewayBridge": {"InstanceId": "string", "MaxBitrate": "integer", "MaxOutputs": "integer"},
        "SourceFailoverConfig": {},
        "BridgeMessages": [{"Code": "string", "Message": "string"}]
    }
}
```

---

### 7.2 `describe-bridge`

Describes a bridge.

**Synopsis:**
```bash
aws mediaconnect describe-bridge \
    --bridge-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bridge-arn` | **Yes** | string | -- | ARN of the bridge |

**Output Schema:** Same as `create-bridge` output.

---

### 7.3 `list-bridges`

Lists all bridges. **Paginated operation.**

**Synopsis:**
```bash
aws mediaconnect list-bridges \
    [--filter-arn <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filter-arn` | No | string | None | Filter by gateway ARN |
| `--max-results` | No | integer | None | Max results per page |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "Bridges": [
        {
            "BridgeArn": "string",
            "BridgeState": "string",
            "BridgeType": "string",
            "Name": "string",
            "PlacementArn": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 7.4 `update-bridge`

Updates a bridge's configuration.

**Synopsis:**
```bash
aws mediaconnect update-bridge \
    --bridge-arn <value> \
    [--egress-gateway-bridge <value>] \
    [--ingress-gateway-bridge <value>] \
    [--source-failover-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bridge-arn` | **Yes** | string | -- | ARN of the bridge |
| `--egress-gateway-bridge` | No | structure | None | Updated egress config |
| `--ingress-gateway-bridge` | No | structure | None | Updated ingress config |
| `--source-failover-config` | No | structure | None | Updated failover config |

**Output Schema:** Same as `create-bridge` output.

---

### 7.5 `update-bridge-state`

Starts or stops a bridge.

**Synopsis:**
```bash
aws mediaconnect update-bridge-state \
    --bridge-arn <value> \
    --desired-state <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bridge-arn` | **Yes** | string | -- | ARN of the bridge |
| `--desired-state` | **Yes** | string | -- | `ACTIVE` or `STANDBY` |

**Output Schema:**
```json
{
    "BridgeArn": "string",
    "DesiredState": "ACTIVE|STANDBY"
}
```

---

### 7.6 `delete-bridge`

Deletes a bridge.

**Synopsis:**
```bash
aws mediaconnect delete-bridge \
    --bridge-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bridge-arn` | **Yes** | string | -- | ARN of the bridge to delete |

**Output Schema:**
```json
{
    "BridgeArn": "string"
}
```

---

### 7.7 `add-bridge-sources`

Adds sources to a bridge.

**Synopsis:**
```bash
aws mediaconnect add-bridge-sources \
    --bridge-arn <value> \
    --sources <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bridge-arn` | **Yes** | string | -- | ARN of the bridge |
| `--sources` | **Yes** | list | -- | Source configurations (FlowSource or NetworkSource) |

**Output Schema:**
```json
{
    "BridgeArn": "string",
    "Sources": []
}
```

---

### 7.8 `update-bridge-source`

Updates a bridge source.

**Synopsis:**
```bash
aws mediaconnect update-bridge-source \
    --bridge-arn <value> \
    --source-name <value> \
    [--flow-source <value>] \
    [--network-source <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bridge-arn` | **Yes** | string | -- | ARN of the bridge |
| `--source-name` | **Yes** | string | -- | Name of the source to update |
| `--flow-source` | No | structure | None | Updated flow source config |
| `--network-source` | No | structure | None | Updated network source config |

**Output Schema:**
```json
{
    "BridgeArn": "string",
    "Source": { "..." }
}
```

---

### 7.9 `remove-bridge-source`

Removes a source from a bridge.

**Synopsis:**
```bash
aws mediaconnect remove-bridge-source \
    --bridge-arn <value> \
    --source-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bridge-arn` | **Yes** | string | -- | ARN of the bridge |
| `--source-name` | **Yes** | string | -- | Name of the source to remove |

**Output:** `BridgeArn` (string)

---

### 7.10 `add-bridge-outputs`

Adds outputs to a bridge.

**Synopsis:**
```bash
aws mediaconnect add-bridge-outputs \
    --bridge-arn <value> \
    --outputs <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bridge-arn` | **Yes** | string | -- | ARN of the bridge |
| `--outputs` | **Yes** | list | -- | Output configurations (NetworkOutput) |

**Output Schema:**
```json
{
    "BridgeArn": "string",
    "Outputs": []
}
```

---

### 7.11 `update-bridge-output`

Updates a bridge output.

**Synopsis:**
```bash
aws mediaconnect update-bridge-output \
    --bridge-arn <value> \
    --output-name <value> \
    [--network-output <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bridge-arn` | **Yes** | string | -- | ARN of the bridge |
| `--output-name` | **Yes** | string | -- | Name of the output to update |
| `--network-output` | No | structure | None | Updated network output config |

**Output Schema:**
```json
{
    "BridgeArn": "string",
    "Output": { "..." }
}
```

---

### 7.12 `remove-bridge-output`

Removes an output from a bridge.

**Synopsis:**
```bash
aws mediaconnect remove-bridge-output \
    --bridge-arn <value> \
    --output-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bridge-arn` | **Yes** | string | -- | ARN of the bridge |
| `--output-name` | **Yes** | string | -- | Name of the output to remove |

**Output:** `BridgeArn` (string)
