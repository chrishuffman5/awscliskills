# Gateways

### 2.1 `create-direct-connect-gateway`

Creates a Direct Connect gateway, which connects virtual interfaces and virtual private gateways or transit gateways across regions.

**Synopsis:**
```bash
aws directconnect create-direct-connect-gateway \
    --direct-connect-gateway-name <value> \
    [--amazon-side-asn <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--direct-connect-gateway-name` | **Yes** | string | -- | The name of the Direct Connect gateway |
| `--amazon-side-asn` | No | long | 64512 | The ASN for the Amazon side of BGP. Range: 64512-65534 or 4200000000-4294967294 |
| `--tags` | No | list | None | Tags. Shorthand: `key=string,value=string ...` |

**Output Schema:**
```json
{
    "directConnectGateway": {
        "directConnectGatewayId": "string",
        "directConnectGatewayName": "string",
        "amazonSideAsn": "long",
        "ownerAccount": "string",
        "directConnectGatewayState": "pending|available|deleting|deleted",
        "stateChangeError": "string",
        "tags": [{"key": "string", "value": "string"}]
    }
}
```

---

### 2.2 `delete-direct-connect-gateway`

Deletes the specified Direct Connect gateway. You must first delete all virtual interfaces and associations.

**Synopsis:**
```bash
aws directconnect delete-direct-connect-gateway \
    --direct-connect-gateway-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--direct-connect-gateway-id` | **Yes** | string | -- | The ID of the Direct Connect gateway |

**Output Schema:**
Same as `create-direct-connect-gateway` output.

---

### 2.3 `describe-direct-connect-gateways`

Lists all Direct Connect gateways or a specific one. **Paginated.**

**Synopsis:**
```bash
aws directconnect describe-direct-connect-gateways \
    [--direct-connect-gateway-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--direct-connect-gateway-id` | No | string | None | The ID of a specific gateway |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "directConnectGateways": [
        {
            "directConnectGatewayId": "string",
            "directConnectGatewayName": "string",
            "amazonSideAsn": "long",
            "ownerAccount": "string",
            "directConnectGatewayState": "pending|available|deleting|deleted",
            "stateChangeError": "string",
            "tags": [{"key": "string", "value": "string"}]
        }
    ],
    "nextToken": "string"
}
```

---

### 2.4 `update-direct-connect-gateway`

Updates the name of an existing Direct Connect gateway.

**Synopsis:**
```bash
aws directconnect update-direct-connect-gateway \
    --direct-connect-gateway-id <value> \
    --new-direct-connect-gateway-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--direct-connect-gateway-id` | **Yes** | string | -- | The ID of the Direct Connect gateway |
| `--new-direct-connect-gateway-name` | **Yes** | string | -- | The new name for the gateway |

**Output Schema:**
Same as `create-direct-connect-gateway` output.

---

### 2.5 `create-direct-connect-gateway-association`

Creates an association between a Direct Connect gateway and a virtual private gateway or transit gateway.

**Synopsis:**
```bash
aws directconnect create-direct-connect-gateway-association \
    --direct-connect-gateway-id <value> \
    [--gateway-id <value>] \
    [--virtual-gateway-id <value>] \
    [--add-allowed-prefixes-to-direct-connect-gateway <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--direct-connect-gateway-id` | **Yes** | string | -- | The ID of the Direct Connect gateway |
| `--gateway-id` | No | string | None | The ID of the virtual private gateway or transit gateway |
| `--virtual-gateway-id` | No | string | None | The ID of the virtual private gateway (deprecated, use `--gateway-id`) |
| `--add-allowed-prefixes-to-direct-connect-gateway` | No | list | None | VPC prefixes to advertise. Shorthand: `cidr=string ...` |

**Output Schema:**
```json
{
    "directConnectGatewayAssociation": {
        "directConnectGatewayId": "string",
        "directConnectGatewayOwnerAccount": "string",
        "associationState": "associating|associated|disassociating|disassociated|updating",
        "stateChangeError": "string",
        "associatedGateway": {
            "id": "string",
            "type": "virtualPrivateGateway|transitGateway",
            "ownerAccount": "string",
            "region": "string"
        },
        "associationId": "string",
        "allowedPrefixesToDirectConnectGateway": [{"cidr": "string"}],
        "virtualGatewayId": "string",
        "virtualGatewayRegion": "string",
        "virtualGatewayOwnerAccount": "string"
    }
}
```

---

### 2.6 `delete-direct-connect-gateway-association`

Deletes the association between a Direct Connect gateway and a virtual private gateway or transit gateway.

**Synopsis:**
```bash
aws directconnect delete-direct-connect-gateway-association \
    [--association-id <value>] \
    [--direct-connect-gateway-id <value>] \
    [--virtual-gateway-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--association-id` | No | string | None | The ID of the association (recommended) |
| `--direct-connect-gateway-id` | No | string | None | The ID of the Direct Connect gateway |
| `--virtual-gateway-id` | No | string | None | The ID of the virtual private gateway |

**Output Schema:**
Same as `create-direct-connect-gateway-association` output.

---

### 2.7 `describe-direct-connect-gateway-associations`

Lists the associations between Direct Connect gateways and virtual private or transit gateways. **Paginated.**

**Synopsis:**
```bash
aws directconnect describe-direct-connect-gateway-associations \
    [--association-id <value>] \
    [--associated-gateway-id <value>] \
    [--direct-connect-gateway-id <value>] \
    [--virtual-gateway-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--association-id` | No | string | None | The ID of a specific association |
| `--associated-gateway-id` | No | string | None | The ID of the associated VGW or TGW |
| `--direct-connect-gateway-id` | No | string | None | The ID of the Direct Connect gateway |
| `--virtual-gateway-id` | No | string | None | The ID of the virtual private gateway |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "directConnectGatewayAssociations": [
        {
            "directConnectGatewayId": "string",
            "directConnectGatewayOwnerAccount": "string",
            "associationState": "associating|associated|disassociating|disassociated|updating",
            "stateChangeError": "string",
            "associatedGateway": {
                "id": "string",
                "type": "virtualPrivateGateway|transitGateway",
                "ownerAccount": "string",
                "region": "string"
            },
            "associationId": "string",
            "allowedPrefixesToDirectConnectGateway": [{"cidr": "string"}],
            "virtualGatewayId": "string",
            "virtualGatewayRegion": "string",
            "virtualGatewayOwnerAccount": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 2.8 `update-direct-connect-gateway-association`

Updates the allowed prefixes advertised through a Direct Connect gateway association.

**Synopsis:**
```bash
aws directconnect update-direct-connect-gateway-association \
    [--association-id <value>] \
    [--add-allowed-prefixes-to-direct-connect-gateway <value>] \
    [--remove-allowed-prefixes-to-direct-connect-gateway <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--association-id` | No | string | None | The ID of the association |
| `--add-allowed-prefixes-to-direct-connect-gateway` | No | list | None | Prefixes to add. Shorthand: `cidr=string ...` |
| `--remove-allowed-prefixes-to-direct-connect-gateway` | No | list | None | Prefixes to remove. Shorthand: `cidr=string ...` |

**Output Schema:**
Same as `create-direct-connect-gateway-association` output.

---

### 2.9 `describe-direct-connect-gateway-attachments`

Lists the attachments between Direct Connect gateways and virtual interfaces. **Paginated.**

**Synopsis:**
```bash
aws directconnect describe-direct-connect-gateway-attachments \
    [--direct-connect-gateway-id <value>] \
    [--virtual-interface-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--direct-connect-gateway-id` | No | string | None | The ID of the Direct Connect gateway |
| `--virtual-interface-id` | No | string | None | The ID of the virtual interface |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "directConnectGatewayAttachments": [
        {
            "directConnectGatewayId": "string",
            "virtualInterfaceId": "string",
            "virtualInterfaceRegion": "string",
            "virtualInterfaceOwnerAccount": "string",
            "attachmentState": "attaching|attached|detaching|detached",
            "attachmentType": "TransitVirtualInterface|PrivateVirtualInterface",
            "stateChangeError": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 2.10 `create-direct-connect-gateway-association-proposal`

Creates a proposal to associate a gateway owned by another AWS account with a Direct Connect gateway.

**Synopsis:**
```bash
aws directconnect create-direct-connect-gateway-association-proposal \
    --direct-connect-gateway-id <value> \
    --direct-connect-gateway-owner-account <value> \
    --gateway-id <value> \
    [--add-allowed-prefixes-to-direct-connect-gateway <value>] \
    [--remove-allowed-prefixes-to-direct-connect-gateway <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--direct-connect-gateway-id` | **Yes** | string | -- | The ID of the Direct Connect gateway |
| `--direct-connect-gateway-owner-account` | **Yes** | string | -- | The account ID of the Direct Connect gateway owner |
| `--gateway-id` | **Yes** | string | -- | The ID of the VGW or TGW to associate |
| `--add-allowed-prefixes-to-direct-connect-gateway` | No | list | None | Prefixes to advertise. Shorthand: `cidr=string ...` |
| `--remove-allowed-prefixes-to-direct-connect-gateway` | No | list | None | Prefixes to stop advertising. Shorthand: `cidr=string ...` |

**Output Schema:**
```json
{
    "directConnectGatewayAssociationProposal": {
        "proposalId": "string",
        "directConnectGatewayId": "string",
        "directConnectGatewayOwnerAccount": "string",
        "proposalState": "requested|accepted|deleted",
        "associatedGateway": {
            "id": "string",
            "type": "virtualPrivateGateway|transitGateway",
            "ownerAccount": "string",
            "region": "string"
        },
        "existingAllowedPrefixesToDirectConnectGateway": [{"cidr": "string"}],
        "requestedAllowedPrefixesToDirectConnectGateway": [{"cidr": "string"}]
    }
}
```

---

### 2.11 `delete-direct-connect-gateway-association-proposal`

Deletes the association proposal.

**Synopsis:**
```bash
aws directconnect delete-direct-connect-gateway-association-proposal \
    --proposal-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--proposal-id` | **Yes** | string | -- | The ID of the proposal |

**Output Schema:**
Same as `create-direct-connect-gateway-association-proposal` output.

---

### 2.12 `accept-direct-connect-gateway-association-proposal`

Accepts a proposal to associate a VGW or TGW with a Direct Connect gateway (called by the gateway owner).

**Synopsis:**
```bash
aws directconnect accept-direct-connect-gateway-association-proposal \
    --direct-connect-gateway-id <value> \
    --proposal-id <value> \
    --associated-gateway-owner-account <value> \
    [--override-allowed-prefixes-to-direct-connect-gateway <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--direct-connect-gateway-id` | **Yes** | string | -- | The ID of the Direct Connect gateway |
| `--proposal-id` | **Yes** | string | -- | The ID of the proposal |
| `--associated-gateway-owner-account` | **Yes** | string | -- | The account ID of the VGW/TGW owner |
| `--override-allowed-prefixes-to-direct-connect-gateway` | No | list | None | Override advertised prefixes. Shorthand: `cidr=string ...` |

**Output Schema:**
Same as `create-direct-connect-gateway-association` output.

---

### 2.13 `describe-direct-connect-gateway-association-proposals`

Describes association proposals. **Paginated.**

**Synopsis:**
```bash
aws directconnect describe-direct-connect-gateway-association-proposals \
    [--direct-connect-gateway-id <value>] \
    [--proposal-id <value>] \
    [--associated-gateway-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--direct-connect-gateway-id` | No | string | None | The ID of the Direct Connect gateway |
| `--proposal-id` | No | string | None | The ID of a specific proposal |
| `--associated-gateway-id` | No | string | None | The ID of the associated VGW/TGW |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "directConnectGatewayAssociationProposals": [
        {
            "proposalId": "string",
            "directConnectGatewayId": "string",
            "directConnectGatewayOwnerAccount": "string",
            "proposalState": "requested|accepted|deleted",
            "associatedGateway": {
                "id": "string",
                "type": "virtualPrivateGateway|transitGateway",
                "ownerAccount": "string",
                "region": "string"
            },
            "existingAllowedPrefixesToDirectConnectGateway": [{"cidr": "string"}],
            "requestedAllowedPrefixesToDirectConnectGateway": [{"cidr": "string"}]
        }
    ],
    "nextToken": "string"
}
```

---

### 2.14 `describe-virtual-gateways`

Lists the virtual private gateways owned by the account. These are the gateways that can be associated with a Direct Connect gateway.

**Synopsis:**
```bash
aws directconnect describe-virtual-gateways \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

No command-specific parameters.

**Output Schema:**
```json
{
    "virtualGateways": [
        {
            "virtualGatewayId": "string",
            "virtualGatewayState": "pending|available|deleting|deleted"
        }
    ]
}
```
