# Attachments

### 7.1 `create-vpc-attachment`

Creates a VPC attachment on a core network's edge location.

**Synopsis:**
```bash
aws networkmanager create-vpc-attachment \
    --core-network-id <value> \
    --vpc-arn <value> \
    --subnet-arns <value> \
    [--options <value>] \
    [--routing-policy-label <value>] \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--core-network-id` | **Yes** | string | -- | Core network ID |
| `--vpc-arn` | **Yes** | string | -- | VPC ARN |
| `--subnet-arns` | **Yes** | list(string) | -- | One or more subnet ARNs |
| `--options` | No | structure | None | VPC options. Shorthand: `Ipv6Support=boolean,ApplianceModeSupport=boolean,DnsSupport=boolean,SecurityGroupReferencingSupport=boolean` |
| `--routing-policy-label` | No | string | None | Routing policy label |
| `--tags` | No | list | None | Tags |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "VpcAttachment": {
        "Attachment": {
            "CoreNetworkId": "string",
            "AttachmentId": "string",
            "OwnerAccountId": "string",
            "AttachmentType": "VPC",
            "State": "REJECTED|PENDING_ATTACHMENT_ACCEPTANCE|CREATING|FAILED|AVAILABLE|UPDATING|PENDING_NETWORK_UPDATE|PENDING_TAG_ACCEPTANCE|DELETING",
            "EdgeLocation": "string",
            "ResourceArn": "string",
            "Tags": [{"Key": "string", "Value": "string"}],
            "CreatedAt": "timestamp",
            "UpdatedAt": "timestamp",
            "LastModificationErrors": [
                {
                    "Code": "string",
                    "Message": "string",
                    "ResourceArn": "string",
                    "RequestId": "string"
                }
            ]
        },
        "SubnetArns": ["string"],
        "Options": {
            "Ipv6Support": true|false,
            "ApplianceModeSupport": true|false,
            "DnsSupport": true|false,
            "SecurityGroupReferencingSupport": true|false
        }
    }
}
```

---

### 7.2 `update-vpc-attachment`

Updates a VPC attachment (add/remove subnets or change options).

**Synopsis:**
```bash
aws networkmanager update-vpc-attachment \
    --attachment-id <value> \
    [--add-subnet-arns <value>] \
    [--remove-subnet-arns <value>] \
    [--options <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--attachment-id` | **Yes** | string | -- | Attachment ID |
| `--add-subnet-arns` | No | list(string) | None | Subnet ARNs to add |
| `--remove-subnet-arns` | No | list(string) | None | Subnet ARNs to remove |
| `--options` | No | structure | None | Updated VPC options |

**Output Schema:** Same as create-vpc-attachment.

---

### 7.3 `get-vpc-attachment`

Returns information about a VPC attachment.

**Synopsis:**
```bash
aws networkmanager get-vpc-attachment \
    --attachment-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--attachment-id` | **Yes** | string | -- | Attachment ID |

**Output Schema:** Same as create-vpc-attachment.

---

### 7.4 `create-connect-attachment`

Creates a Connect attachment from a specified core network attachment.

**Synopsis:**
```bash
aws networkmanager create-connect-attachment \
    --core-network-id <value> \
    --edge-location <value> \
    --transport-attachment-id <value> \
    --options <value> \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--core-network-id` | **Yes** | string | -- | Core network ID |
| `--edge-location` | **Yes** | string | -- | Edge location for the Connect attachment |
| `--transport-attachment-id` | **Yes** | string | -- | Transport attachment ID (VPC or VPN) |
| `--options` | **Yes** | structure | -- | Connect options. Shorthand: `Protocol=GRE\|NO_ENCAP` |
| `--tags` | No | list | None | Tags |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "ConnectAttachment": {
        "Attachment": {
            "CoreNetworkId": "string",
            "AttachmentId": "string",
            "OwnerAccountId": "string",
            "AttachmentType": "CONNECT",
            "State": "string",
            "EdgeLocation": "string",
            "ResourceArn": "string",
            "Tags": [],
            "CreatedAt": "timestamp",
            "UpdatedAt": "timestamp"
        },
        "TransportAttachmentId": "string",
        "Options": {
            "Protocol": "GRE|NO_ENCAP"
        }
    }
}
```

---

### 7.5 `get-connect-attachment`

Returns information about a Connect attachment.

**Synopsis:**
```bash
aws networkmanager get-connect-attachment \
    --attachment-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--attachment-id` | **Yes** | string | -- | Attachment ID |

**Output Schema:** Same as create-connect-attachment.

---

### 7.6 `create-site-to-site-vpn-attachment`

Creates a site-to-site VPN attachment on a core network.

**Synopsis:**
```bash
aws networkmanager create-site-to-site-vpn-attachment \
    --core-network-id <value> \
    --vpn-connection-arn <value> \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--core-network-id` | **Yes** | string | -- | Core network ID |
| `--vpn-connection-arn` | **Yes** | string | -- | VPN connection ARN |
| `--tags` | No | list | None | Tags |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "SiteToSiteVpnAttachment": {
        "Attachment": {
            "CoreNetworkId": "string",
            "AttachmentId": "string",
            "OwnerAccountId": "string",
            "AttachmentType": "SITE_TO_SITE_VPN",
            "State": "string",
            "EdgeLocation": "string",
            "ResourceArn": "string",
            "Tags": [],
            "CreatedAt": "timestamp",
            "UpdatedAt": "timestamp"
        },
        "VpnConnectionArn": "string"
    }
}
```

---

### 7.7 `get-site-to-site-vpn-attachment`

Returns information about a site-to-site VPN attachment.

**Synopsis:**
```bash
aws networkmanager get-site-to-site-vpn-attachment \
    --attachment-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--attachment-id` | **Yes** | string | -- | Attachment ID |

**Output Schema:** Same as create-site-to-site-vpn-attachment.

---

### 7.8 `create-direct-connect-gateway-attachment`

Creates a Direct Connect gateway attachment on a core network.

**Synopsis:**
```bash
aws networkmanager create-direct-connect-gateway-attachment \
    --core-network-id <value> \
    --direct-connect-gateway-arn <value> \
    --edge-locations <value> \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--core-network-id` | **Yes** | string | -- | Core network ID |
| `--direct-connect-gateway-arn` | **Yes** | string | -- | Direct Connect gateway ARN |
| `--edge-locations` | **Yes** | list(string) | -- | One or more edge locations |
| `--tags` | No | list | None | Tags |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "DirectConnectGatewayAttachment": {
        "Attachment": {
            "CoreNetworkId": "string",
            "AttachmentId": "string",
            "OwnerAccountId": "string",
            "AttachmentType": "DIRECT_CONNECT_GATEWAY",
            "State": "string",
            "EdgeLocations": ["string"],
            "ResourceArn": "string",
            "Tags": [],
            "CreatedAt": "timestamp",
            "UpdatedAt": "timestamp"
        },
        "DirectConnectGatewayArn": "string"
    }
}
```

---

### 7.9 `get-direct-connect-gateway-attachment`

Returns information about a Direct Connect gateway attachment.

**Synopsis:**
```bash
aws networkmanager get-direct-connect-gateway-attachment \
    --attachment-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--attachment-id` | **Yes** | string | -- | Attachment ID |

**Output Schema:** Same as create-direct-connect-gateway-attachment.

---

### 7.10 `update-direct-connect-gateway-attachment`

Updates a Direct Connect gateway attachment's edge locations.

**Synopsis:**
```bash
aws networkmanager update-direct-connect-gateway-attachment \
    --attachment-id <value> \
    [--edge-locations <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--attachment-id` | **Yes** | string | -- | Attachment ID |
| `--edge-locations` | No | list(string) | None | Updated edge locations |

**Output Schema:** Same as create-direct-connect-gateway-attachment.

---

### 7.11 `accept-attachment`

Accepts a core network attachment request (from a VPC, VPN, or other attachment type).

**Synopsis:**
```bash
aws networkmanager accept-attachment \
    --attachment-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--attachment-id` | **Yes** | string | -- | Attachment ID |

**Output Schema:**
```json
{
    "Attachment": {
        "CoreNetworkId": "string",
        "AttachmentId": "string",
        "OwnerAccountId": "string",
        "AttachmentType": "string",
        "State": "string",
        "EdgeLocation": "string",
        "ResourceArn": "string",
        "Tags": [],
        "CreatedAt": "timestamp",
        "UpdatedAt": "timestamp"
    }
}
```

---

### 7.12 `reject-attachment`

Rejects a core network attachment request.

**Synopsis:**
```bash
aws networkmanager reject-attachment \
    --attachment-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--attachment-id` | **Yes** | string | -- | Attachment ID |

**Output Schema:** Same as accept-attachment.

---

### 7.13 `delete-attachment`

Deletes an attachment.

**Synopsis:**
```bash
aws networkmanager delete-attachment \
    --attachment-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--attachment-id` | **Yes** | string | -- | Attachment ID |

**Output Schema:** Same as accept-attachment.

---

### 7.14 `list-attachments`

Returns a list of core network attachments. **Paginated.**

**Synopsis:**
```bash
aws networkmanager list-attachments \
    [--core-network-id <value>] \
    [--attachment-type <value>] \
    [--edge-location <value>] \
    [--state <value>] \
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
| `--attachment-type` | No | string | None | Filter by type: `CONNECT`, `SITE_TO_SITE_VPN`, `VPC`, `DIRECT_CONNECT_GATEWAY`, `TRANSIT_GATEWAY_ROUTE_TABLE` |
| `--edge-location` | No | string | None | Filter by edge location |
| `--state` | No | string | None | Filter by state |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Attachments": [
        {
            "CoreNetworkId": "string",
            "AttachmentId": "string",
            "OwnerAccountId": "string",
            "AttachmentType": "string",
            "State": "string",
            "EdgeLocation": "string",
            "ResourceArn": "string",
            "Tags": [],
            "CreatedAt": "timestamp",
            "UpdatedAt": "timestamp"
        }
    ],
    "NextToken": "string"
}
```
