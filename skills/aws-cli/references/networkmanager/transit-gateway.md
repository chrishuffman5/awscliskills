# Transit Gateway

### 6.1 `register-transit-gateway`

Registers a Transit Gateway in a global network.

**Synopsis:**
```bash
aws networkmanager register-transit-gateway \
    --global-network-id <value> \
    --transit-gateway-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-network-id` | **Yes** | string | -- | Global network ID |
| `--transit-gateway-arn` | **Yes** | string | -- | Transit Gateway ARN |

**Output Schema:**
```json
{
    "TransitGatewayRegistration": {
        "GlobalNetworkId": "string",
        "TransitGatewayArn": "string",
        "State": {
            "Code": "PENDING|AVAILABLE|DELETING|DELETED|FAILED",
            "Message": "string"
        }
    }
}
```

---

### 6.2 `deregister-transit-gateway`

Deregisters a Transit Gateway from a global network.

**Synopsis:**
```bash
aws networkmanager deregister-transit-gateway \
    --global-network-id <value> \
    --transit-gateway-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-network-id` | **Yes** | string | -- | Global network ID |
| `--transit-gateway-arn` | **Yes** | string | -- | Transit Gateway ARN |

**Output Schema:** Same as register-transit-gateway.

---

### 6.3 `get-transit-gateway-registrations`

Gets Transit Gateway registrations for a global network. **Paginated.**

**Synopsis:**
```bash
aws networkmanager get-transit-gateway-registrations \
    --global-network-id <value> \
    [--transit-gateway-arns <value>] \
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
| `--transit-gateway-arns` | No | list(string) | None | Filter by TGW ARNs |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "TransitGatewayRegistrations": [
        {
            "GlobalNetworkId": "string",
            "TransitGatewayArn": "string",
            "State": {
                "Code": "string",
                "Message": "string"
            }
        }
    ],
    "NextToken": "string"
}
```

---

### 6.4 `associate-transit-gateway-connect-peer`

Associates a Transit Gateway Connect peer with a device and optionally a link.

**Synopsis:**
```bash
aws networkmanager associate-transit-gateway-connect-peer \
    --global-network-id <value> \
    --transit-gateway-connect-peer-arn <value> \
    --device-id <value> \
    [--link-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-network-id` | **Yes** | string | -- | Global network ID |
| `--transit-gateway-connect-peer-arn` | **Yes** | string | -- | TGW Connect peer ARN |
| `--device-id` | **Yes** | string | -- | Device ID |
| `--link-id` | No | string | None | Link ID |

**Output Schema:**
```json
{
    "TransitGatewayConnectPeerAssociation": {
        "TransitGatewayConnectPeerArn": "string",
        "GlobalNetworkId": "string",
        "DeviceId": "string",
        "LinkId": "string",
        "State": "PENDING|AVAILABLE|DELETING|DELETED"
    }
}
```

---

### 6.5 `disassociate-transit-gateway-connect-peer`

Disassociates a Transit Gateway Connect peer from a device.

**Synopsis:**
```bash
aws networkmanager disassociate-transit-gateway-connect-peer \
    --global-network-id <value> \
    --transit-gateway-connect-peer-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-network-id` | **Yes** | string | -- | Global network ID |
| `--transit-gateway-connect-peer-arn` | **Yes** | string | -- | TGW Connect peer ARN |

**Output Schema:** Same as associate-transit-gateway-connect-peer.

---

### 6.6 `get-transit-gateway-connect-peer-associations`

Gets Transit Gateway Connect peer associations. **Paginated.**

**Synopsis:**
```bash
aws networkmanager get-transit-gateway-connect-peer-associations \
    --global-network-id <value> \
    [--transit-gateway-connect-peer-arns <value>] \
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
| `--transit-gateway-connect-peer-arns` | No | list(string) | None | Filter by TGW Connect peer ARNs |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "TransitGatewayConnectPeerAssociations": [
        {
            "TransitGatewayConnectPeerArn": "string",
            "GlobalNetworkId": "string",
            "DeviceId": "string",
            "LinkId": "string",
            "State": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 6.7 `create-transit-gateway-peering`

Creates a Transit Gateway peering connection with a core network.

**Synopsis:**
```bash
aws networkmanager create-transit-gateway-peering \
    --core-network-id <value> \
    --transit-gateway-arn <value> \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--core-network-id` | **Yes** | string | -- | Core network ID |
| `--transit-gateway-arn` | **Yes** | string | -- | Transit Gateway ARN |
| `--tags` | No | list | None | Tags |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "TransitGatewayPeering": {
        "Peering": {
            "CoreNetworkId": "string",
            "CoreNetworkArn": "string",
            "PeeringId": "string",
            "OwnerAccountId": "string",
            "PeeringType": "TRANSIT_GATEWAY",
            "State": "CREATING|FAILED|AVAILABLE|DELETING",
            "EdgeLocation": "string",
            "ResourceArn": "string",
            "Tags": [],
            "CreatedAt": "timestamp"
        },
        "TransitGatewayArn": "string",
        "TransitGatewayPeeringAttachmentId": "string"
    }
}
```

---

### 6.8 `get-transit-gateway-peering`

Gets information about a Transit Gateway peering.

**Synopsis:**
```bash
aws networkmanager get-transit-gateway-peering \
    --peering-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--peering-id` | **Yes** | string | -- | Peering ID |

**Output Schema:** Same as create-transit-gateway-peering.

---

### 6.9 `create-transit-gateway-route-table-attachment`

Creates a Transit Gateway route table attachment to a core network.

**Synopsis:**
```bash
aws networkmanager create-transit-gateway-route-table-attachment \
    --peering-id <value> \
    --transit-gateway-route-table-arn <value> \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--peering-id` | **Yes** | string | -- | Peering ID |
| `--transit-gateway-route-table-arn` | **Yes** | string | -- | TGW route table ARN |
| `--tags` | No | list | None | Tags |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "TransitGatewayRouteTableAttachment": {
        "Attachment": {
            "CoreNetworkId": "string",
            "AttachmentId": "string",
            "OwnerAccountId": "string",
            "AttachmentType": "TRANSIT_GATEWAY_ROUTE_TABLE",
            "State": "string",
            "EdgeLocation": "string",
            "ResourceArn": "string",
            "Tags": [],
            "CreatedAt": "timestamp",
            "UpdatedAt": "timestamp"
        },
        "PeeringId": "string",
        "TransitGatewayRouteTableArn": "string"
    }
}
```

---

### 6.10 `get-transit-gateway-route-table-attachment`

Gets information about a Transit Gateway route table attachment.

**Synopsis:**
```bash
aws networkmanager get-transit-gateway-route-table-attachment \
    --attachment-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--attachment-id` | **Yes** | string | -- | Attachment ID |

**Output Schema:** Same as create-transit-gateway-route-table-attachment.
