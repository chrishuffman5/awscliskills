# LAGs

### 4.1 `create-lag`

Creates a link aggregation group (LAG) with the specified number of bundled physical dedicated connections between your network and a specific Direct Connect location.

**Synopsis:**
```bash
aws directconnect create-lag \
    --number-of-connections <value> \
    --location <value> \
    --connections-bandwidth <value> \
    --lag-name <value> \
    [--connection-id <value>] \
    [--tags <value>] \
    [--child-connection-tags <value>] \
    [--provider-name <value>] \
    [--request-mac-sec | --no-request-mac-sec] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--number-of-connections` | **Yes** | integer | -- | Number of physical connections. Max 4 for 1G/10G, 2 for 100G/400G |
| `--location` | **Yes** | string | -- | The location for the LAG |
| `--connections-bandwidth` | **Yes** | string | -- | Bandwidth per connection: `1Gbps`, `10Gbps`, `100Gbps`, `400Gbps` |
| `--lag-name` | **Yes** | string | -- | The name of the LAG |
| `--connection-id` | No | string | None | ID of existing connection to migrate to the LAG |
| `--tags` | No | list | None | Tags for the LAG. Shorthand: `key=string,value=string ...` |
| `--child-connection-tags` | No | list | None | Tags for auto-created connections |
| `--provider-name` | No | string | None | Service provider name |
| `--request-mac-sec` | No | boolean | false | Request MACsec support |

**Output Schema:**
```json
{
    "connectionsBandwidth": "string",
    "numberOfConnections": "integer",
    "lagId": "string",
    "ownerAccount": "string",
    "lagName": "string",
    "lagState": "requested|pending|available|down|deleting|deleted|unknown",
    "location": "string",
    "region": "string",
    "minimumLinks": "integer",
    "awsDevice": "string",
    "awsDeviceV2": "string",
    "awsLogicalDeviceId": "string",
    "connections": [
        {
            "ownerAccount": "string",
            "connectionId": "string",
            "connectionName": "string",
            "connectionState": "ordering|requested|pending|available|down|deleting|deleted|rejected|unknown",
            "region": "string",
            "location": "string",
            "bandwidth": "string",
            "vlan": "integer",
            "lagId": "string",
            "awsDevice": "string",
            "jumboFrameCapable": "boolean",
            "macSecCapable": "boolean",
            "encryptionMode": "string",
            "macSecKeys": [],
            "tags": []
        }
    ],
    "allowsHostedConnections": "boolean",
    "jumboFrameCapable": "boolean",
    "hasLogicalRedundancy": "unknown|yes|no",
    "tags": [{"key": "string", "value": "string"}],
    "providerName": "string",
    "macSecCapable": "boolean",
    "encryptionMode": "no_encrypt|should_encrypt|must_encrypt",
    "macSecKeys": [
        {
            "secretARN": "string",
            "ckn": "string",
            "state": "associating|associated|disassociating|disassociated",
            "startOn": "string"
        }
    ]
}
```

---

### 4.2 `delete-lag`

Deletes the specified LAG. You cannot delete a LAG that has active virtual interfaces or hosted connections.

**Synopsis:**
```bash
aws directconnect delete-lag \
    --lag-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--lag-id` | **Yes** | string | -- | The ID of the LAG |

**Output Schema:**
Same as `create-lag` output.

---

### 4.3 `describe-lags`

Describes the specified LAG or all LAGs in the current region. **Paginated.**

**Synopsis:**
```bash
aws directconnect describe-lags \
    [--lag-id <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--lag-id` | No | string | None | The ID of a specific LAG |
| `--max-results` | No | integer | None | Maximum number of results (max 100) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "lags": [
        {
            "connectionsBandwidth": "string",
            "numberOfConnections": "integer",
            "lagId": "string",
            "ownerAccount": "string",
            "lagName": "string",
            "lagState": "requested|pending|available|down|deleting|deleted|unknown",
            "location": "string",
            "region": "string",
            "minimumLinks": "integer",
            "awsDevice": "string",
            "awsDeviceV2": "string",
            "connections": [],
            "allowsHostedConnections": "boolean",
            "jumboFrameCapable": "boolean",
            "hasLogicalRedundancy": "unknown|yes|no",
            "tags": [],
            "macSecCapable": "boolean",
            "encryptionMode": "string",
            "macSecKeys": []
        }
    ],
    "nextToken": "string"
}
```

---

### 4.4 `update-lag`

Updates the attributes of the specified LAG.

**Synopsis:**
```bash
aws directconnect update-lag \
    --lag-id <value> \
    [--lag-name <value>] \
    [--minimum-links <value>] \
    [--encryption-mode <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--lag-id` | **Yes** | string | -- | The ID of the LAG |
| `--lag-name` | No | string | None | The new LAG name |
| `--minimum-links` | No | integer | None | Minimum number of operational connections required for the LAG to be operational |
| `--encryption-mode` | No | string | None | MACsec encryption mode: `no_encrypt`, `should_encrypt`, `must_encrypt` |

**Output Schema:**
Same as `create-lag` output.
