# Connect Peers

### 8.1 `create-connect-peer`

Creates a Connect peer for a Connect attachment. A Connect peer establishes a BGP session between the core network and your on-premises or third-party appliance.

**Synopsis:**
```bash
aws networkmanager create-connect-peer \
    --connect-attachment-id <value> \
    --peer-address <value> \
    [--core-network-address <value>] \
    [--bgp-options <value>] \
    [--inside-cidr-blocks <value>] \
    [--subnet-arn <value>] \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connect-attachment-id` | **Yes** | string | -- | Connect attachment ID |
| `--peer-address` | **Yes** | string | -- | IP address of the Connect peer |
| `--core-network-address` | No | string | None | Core network IP address for the peer |
| `--bgp-options` | No | structure | None | BGP options. Shorthand: `PeerAsn=long` |
| `--inside-cidr-blocks` | No | list(string) | None | Inside IP CIDR blocks for the tunnel |
| `--subnet-arn` | No | string | None | Subnet ARN for NO_ENCAP peers |
| `--tags` | No | list | None | Tags |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "ConnectPeer": {
        "CoreNetworkId": "string",
        "ConnectAttachmentId": "string",
        "ConnectPeerId": "string",
        "EdgeLocation": "string",
        "State": "CREATING|FAILED|AVAILABLE|DELETING",
        "CreatedAt": "timestamp",
        "Configuration": {
            "CoreNetworkAddress": "string",
            "PeerAddress": "string",
            "InsideCidrBlocks": ["string"],
            "Protocol": "GRE|NO_ENCAP",
            "BgpConfigurations": [
                {
                    "CoreNetworkAsn": "long",
                    "PeerAsn": "long",
                    "CoreNetworkAddress": "string",
                    "PeerAddress": "string"
                }
            ]
        },
        "Tags": [{"Key": "string", "Value": "string"}],
        "SubnetArn": "string",
        "LastModificationErrors": []
    }
}
```

---

### 8.2 `delete-connect-peer`

Deletes a Connect peer.

**Synopsis:**
```bash
aws networkmanager delete-connect-peer \
    --connect-peer-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connect-peer-id` | **Yes** | string | -- | Connect peer ID |

**Output Schema:** Same as create-connect-peer.

---

### 8.3 `get-connect-peer`

Returns information about a Connect peer.

**Synopsis:**
```bash
aws networkmanager get-connect-peer \
    --connect-peer-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connect-peer-id` | **Yes** | string | -- | Connect peer ID |

**Output Schema:** Same as create-connect-peer.

---

### 8.4 `list-connect-peers`

Returns a list of Connect peers. **Paginated.**

**Synopsis:**
```bash
aws networkmanager list-connect-peers \
    [--core-network-id <value>] \
    [--connect-attachment-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--core-network-id` | No | string | None | Filter by core network ID |
| `--connect-attachment-id` | No | string | None | Filter by Connect attachment ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ConnectPeers": [
        {
            "CoreNetworkId": "string",
            "ConnectAttachmentId": "string",
            "ConnectPeerId": "string",
            "EdgeLocation": "string",
            "ConnectPeerState": "CREATING|FAILED|AVAILABLE|DELETING",
            "CreatedAt": "timestamp",
            "Tags": [],
            "SubnetArn": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 8.5 `associate-connect-peer`

Associates a Connect peer with a device and optionally a link.

**Synopsis:**
```bash
aws networkmanager associate-connect-peer \
    --global-network-id <value> \
    --connect-peer-id <value> \
    --device-id <value> \
    [--link-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-network-id` | **Yes** | string | -- | Global network ID |
| `--connect-peer-id` | **Yes** | string | -- | Connect peer ID |
| `--device-id` | **Yes** | string | -- | Device ID |
| `--link-id` | No | string | None | Link ID |

**Output Schema:**
```json
{
    "ConnectPeerAssociation": {
        "ConnectPeerId": "string",
        "GlobalNetworkId": "string",
        "DeviceId": "string",
        "LinkId": "string",
        "State": "PENDING|AVAILABLE|DELETING|DELETED"
    }
}
```

---

### 8.6 `disassociate-connect-peer`

Disassociates a Connect peer from a device.

**Synopsis:**
```bash
aws networkmanager disassociate-connect-peer \
    --global-network-id <value> \
    --connect-peer-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-network-id` | **Yes** | string | -- | Global network ID |
| `--connect-peer-id` | **Yes** | string | -- | Connect peer ID |

**Output Schema:** Same as associate-connect-peer.

---

### 8.7 `get-connect-peer-associations`

Returns Connect peer associations. **Paginated.**

**Synopsis:**
```bash
aws networkmanager get-connect-peer-associations \
    --global-network-id <value> \
    [--connect-peer-ids <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-network-id` | **Yes** | string | -- | Global network ID |
| `--connect-peer-ids` | No | list(string) | None | Filter by Connect peer IDs |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ConnectPeerAssociations": [
        {
            "ConnectPeerId": "string",
            "GlobalNetworkId": "string",
            "DeviceId": "string",
            "LinkId": "string",
            "State": "string"
        }
    ],
    "NextToken": "string"
}
```
