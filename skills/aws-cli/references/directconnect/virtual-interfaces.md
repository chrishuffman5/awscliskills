# Virtual Interfaces

### 3.1 `create-private-virtual-interface`

Creates a private virtual interface for access to a VPC through a virtual private gateway or Direct Connect gateway.

**Synopsis:**
```bash
aws directconnect create-private-virtual-interface \
    --connection-id <value> \
    --new-private-virtual-interface <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connection-id` | **Yes** | string | -- | The ID of the connection |
| `--new-private-virtual-interface` | **Yes** | structure | -- | Private virtual interface configuration (see below) |

**new-private-virtual-interface Structure:**

| Field | Required | Type | Default | Description |
|-------|----------|------|---------|-------------|
| `virtualInterfaceName` | **Yes** | string | -- | Name (max 100 chars: a-z, 0-9, hyphen) |
| `vlan` | **Yes** | integer | -- | The VLAN ID |
| `asn` | No | integer | -- | Customer-side ASN (1-2147483646). Use `asnLong` for larger values |
| `asnLong` | No | long | -- | Customer-side ASN (1-4294967294). Preferred over `asn` |
| `mtu` | No | integer | 1500 | MTU in bytes: 1500 or 8500 (jumbo frames) |
| `authKey` | No | string | None | BGP authentication key (6-80 chars) |
| `amazonAddress` | No | string | None | IP address assigned to Amazon interface |
| `customerAddress` | No | string | None | IP address assigned to customer interface |
| `addressFamily` | No | string | None | Address family: `ipv4` or `ipv6` |
| `virtualGatewayId` | No | string | None | ID of the virtual private gateway |
| `directConnectGatewayId` | No | string | None | ID of the Direct Connect gateway |
| `tags` | No | list | None | Tags. Shorthand: `key=string,value=string ...` |
| `enableSiteLink` | No | boolean | false | Enable SiteLink for inter-site traffic |

**Output Schema:**
```json
{
    "ownerAccount": "string",
    "virtualInterfaceId": "string",
    "location": "string",
    "connectionId": "string",
    "virtualInterfaceType": "private",
    "virtualInterfaceName": "string",
    "vlan": "integer",
    "asn": "integer",
    "asnLong": "long",
    "amazonSideAsn": "long",
    "authKey": "string",
    "amazonAddress": "string",
    "customerAddress": "string",
    "addressFamily": "ipv4|ipv6",
    "virtualInterfaceState": "confirming|verifying|pending|available|down|testing|deleting|deleted|rejected|unknown",
    "customerRouterConfig": "string",
    "mtu": "integer",
    "jumboFrameCapable": "boolean",
    "virtualGatewayId": "string",
    "directConnectGatewayId": "string",
    "routeFilterPrefixes": [{"cidr": "string"}],
    "bgpPeers": [
        {
            "bgpPeerId": "string",
            "asn": "integer",
            "asnLong": "long",
            "authKey": "string",
            "addressFamily": "ipv4|ipv6",
            "amazonAddress": "string",
            "customerAddress": "string",
            "bgpPeerState": "verifying|pending|available|deleting|deleted",
            "bgpStatus": "up|down|unknown",
            "awsDeviceV2": "string",
            "awsLogicalDeviceId": "string"
        }
    ],
    "region": "string",
    "awsDeviceV2": "string",
    "awsLogicalDeviceId": "string",
    "tags": [{"key": "string", "value": "string"}],
    "siteLinkEnabled": "boolean"
}
```

---

### 3.2 `create-public-virtual-interface`

Creates a public virtual interface for access to AWS public services (S3, DynamoDB, etc.).

**Synopsis:**
```bash
aws directconnect create-public-virtual-interface \
    --connection-id <value> \
    --new-public-virtual-interface <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connection-id` | **Yes** | string | -- | The ID of the connection |
| `--new-public-virtual-interface` | **Yes** | structure | -- | Public virtual interface configuration (see below) |

**new-public-virtual-interface Structure:**

| Field | Required | Type | Default | Description |
|-------|----------|------|---------|-------------|
| `virtualInterfaceName` | **Yes** | string | -- | Name (max 100 chars) |
| `vlan` | **Yes** | integer | -- | The VLAN ID |
| `asn` | No | integer | -- | Customer-side ASN (1-2147483646) |
| `asnLong` | No | long | -- | Customer-side ASN (1-4294967294) |
| `authKey` | No | string | None | BGP authentication key (6-80 chars) |
| `amazonAddress` | No | string | None | IP address assigned to Amazon interface |
| `customerAddress` | No | string | None | IP address assigned to customer interface |
| `addressFamily` | No | string | None | Address family: `ipv4` or `ipv6` |
| `routeFilterPrefixes` | No | list | None | Routes to advertise. Shorthand: `cidr=string ...` |
| `tags` | No | list | None | Tags |

**Output Schema:**
Same as `create-private-virtual-interface` output, with `virtualInterfaceType` = `"public"`.

---

### 3.3 `create-transit-virtual-interface`

Creates a transit virtual interface for access to one or more transit gateways through a Direct Connect gateway.

**Synopsis:**
```bash
aws directconnect create-transit-virtual-interface \
    --connection-id <value> \
    --new-transit-virtual-interface <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connection-id` | **Yes** | string | -- | The ID of the connection |
| `--new-transit-virtual-interface` | **Yes** | structure | -- | Transit virtual interface configuration (see below) |

**new-transit-virtual-interface Structure:**

| Field | Required | Type | Default | Description |
|-------|----------|------|---------|-------------|
| `virtualInterfaceName` | **Yes** | string | -- | Name (max 100 chars) |
| `vlan` | **Yes** | integer | -- | The VLAN ID |
| `asn` | No | integer | -- | Customer-side ASN (1-2147483646) |
| `asnLong` | No | long | -- | Customer-side ASN (1-4294967294) |
| `mtu` | No | integer | 1500 | MTU in bytes: 1500 or 8500 |
| `authKey` | No | string | None | BGP authentication key (6-80 chars) |
| `amazonAddress` | No | string | None | IP address assigned to Amazon interface |
| `customerAddress` | No | string | None | IP address assigned to customer interface |
| `addressFamily` | No | string | None | Address family: `ipv4` or `ipv6` |
| `directConnectGatewayId` | **Yes** | string | -- | The ID of the Direct Connect gateway |
| `tags` | No | list | None | Tags |
| `enableSiteLink` | No | boolean | false | Enable SiteLink |

**Output Schema:**
```json
{
    "virtualInterface": {
        "ownerAccount": "string",
        "virtualInterfaceId": "string",
        "location": "string",
        "connectionId": "string",
        "virtualInterfaceType": "transit",
        "virtualInterfaceName": "string",
        "vlan": "integer",
        "asn": "integer",
        "asnLong": "long",
        "amazonSideAsn": "long",
        "authKey": "string",
        "amazonAddress": "string",
        "customerAddress": "string",
        "addressFamily": "ipv4|ipv6",
        "virtualInterfaceState": "confirming|verifying|pending|available|down|testing|deleting|deleted|rejected|unknown",
        "mtu": "integer",
        "jumboFrameCapable": "boolean",
        "directConnectGatewayId": "string",
        "bgpPeers": [],
        "region": "string",
        "tags": [],
        "siteLinkEnabled": "boolean"
    }
}
```

---

### 3.4 `delete-virtual-interface`

Deletes a virtual interface.

**Synopsis:**
```bash
aws directconnect delete-virtual-interface \
    --virtual-interface-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--virtual-interface-id` | **Yes** | string | -- | The ID of the virtual interface |

**Output Schema:**
```json
{
    "virtualInterfaceState": "confirming|verifying|pending|available|down|testing|deleting|deleted|rejected|unknown"
}
```

---

### 3.5 `describe-virtual-interfaces`

Displays the specified virtual interface or all virtual interfaces. **Paginated.**

**Synopsis:**
```bash
aws directconnect describe-virtual-interfaces \
    [--connection-id <value>] \
    [--virtual-interface-id <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connection-id` | No | string | None | Filter by connection ID |
| `--virtual-interface-id` | No | string | None | A specific virtual interface ID |
| `--max-results` | No | integer | None | Maximum number of results (max 100) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "virtualInterfaces": [
        {
            "ownerAccount": "string",
            "virtualInterfaceId": "string",
            "location": "string",
            "connectionId": "string",
            "virtualInterfaceType": "private|public|transit",
            "virtualInterfaceName": "string",
            "vlan": "integer",
            "asn": "integer",
            "asnLong": "long",
            "amazonSideAsn": "long",
            "authKey": "string",
            "amazonAddress": "string",
            "customerAddress": "string",
            "addressFamily": "ipv4|ipv6",
            "virtualInterfaceState": "confirming|verifying|pending|available|down|testing|deleting|deleted|rejected|unknown",
            "customerRouterConfig": "string",
            "mtu": "integer",
            "jumboFrameCapable": "boolean",
            "virtualGatewayId": "string",
            "directConnectGatewayId": "string",
            "routeFilterPrefixes": [{"cidr": "string"}],
            "bgpPeers": [
                {
                    "bgpPeerId": "string",
                    "asn": "integer",
                    "asnLong": "long",
                    "authKey": "string",
                    "addressFamily": "ipv4|ipv6",
                    "amazonAddress": "string",
                    "customerAddress": "string",
                    "bgpPeerState": "verifying|pending|available|deleting|deleted",
                    "bgpStatus": "up|down|unknown",
                    "awsDeviceV2": "string",
                    "awsLogicalDeviceId": "string"
                }
            ],
            "region": "string",
            "awsDeviceV2": "string",
            "awsLogicalDeviceId": "string",
            "tags": [{"key": "string", "value": "string"}],
            "siteLinkEnabled": "boolean"
        }
    ],
    "nextToken": "string"
}
```

---

### 3.6 `update-virtual-interface-attributes`

Updates the MTU of a virtual interface.

**Synopsis:**
```bash
aws directconnect update-virtual-interface-attributes \
    --virtual-interface-id <value> \
    [--mtu <value>] \
    [--enable-site-link | --no-enable-site-link] \
    [--virtual-interface-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--virtual-interface-id` | **Yes** | string | -- | The ID of the virtual interface |
| `--mtu` | No | integer | None | MTU in bytes: 1500 or 8500 |
| `--enable-site-link` | No | boolean | None | Enable SiteLink |
| `--virtual-interface-name` | No | string | None | New name for the virtual interface |

**Output Schema:**
Same as the virtual interface object in `describe-virtual-interfaces`.

---

### 3.7 `confirm-private-virtual-interface`

Accepts ownership of a private virtual interface created by another account.

**Synopsis:**
```bash
aws directconnect confirm-private-virtual-interface \
    --virtual-interface-id <value> \
    [--virtual-gateway-id <value>] \
    [--direct-connect-gateway-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--virtual-interface-id` | **Yes** | string | -- | The ID of the virtual interface |
| `--virtual-gateway-id` | No | string | None | The ID of the virtual private gateway |
| `--direct-connect-gateway-id` | No | string | None | The ID of the Direct Connect gateway |

**Output Schema:**
```json
{
    "virtualInterfaceState": "confirming|verifying|pending|available|down|testing|deleting|deleted|rejected|unknown"
}
```

---

### 3.8 `confirm-public-virtual-interface`

Accepts ownership of a public virtual interface created by another account.

**Synopsis:**
```bash
aws directconnect confirm-public-virtual-interface \
    --virtual-interface-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--virtual-interface-id` | **Yes** | string | -- | The ID of the virtual interface |

**Output Schema:**
```json
{
    "virtualInterfaceState": "confirming|verifying|pending|available|down|testing|deleting|deleted|rejected|unknown"
}
```

---

### 3.9 `confirm-transit-virtual-interface`

Accepts ownership of a transit virtual interface created by another account.

**Synopsis:**
```bash
aws directconnect confirm-transit-virtual-interface \
    --virtual-interface-id <value> \
    --direct-connect-gateway-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--virtual-interface-id` | **Yes** | string | -- | The ID of the virtual interface |
| `--direct-connect-gateway-id` | **Yes** | string | -- | The ID of the Direct Connect gateway |

**Output Schema:**
```json
{
    "virtualInterfaceState": "confirming|verifying|pending|available|down|testing|deleting|deleted|rejected|unknown"
}
```

---

### 3.10 `allocate-private-virtual-interface`

Provisions a private virtual interface to be owned by the specified account.

**Synopsis:**
```bash
aws directconnect allocate-private-virtual-interface \
    --connection-id <value> \
    --owner-account <value> \
    --new-private-virtual-interface-allocation <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connection-id` | **Yes** | string | -- | The ID of the connection |
| `--owner-account` | **Yes** | string | -- | The account ID of the virtual interface owner |
| `--new-private-virtual-interface-allocation` | **Yes** | structure | -- | Virtual interface allocation config |

**Output Schema:**
Same as the virtual interface object in `create-private-virtual-interface`.

---

### 3.11 `allocate-public-virtual-interface`

Provisions a public virtual interface to be owned by the specified account.

**Synopsis:**
```bash
aws directconnect allocate-public-virtual-interface \
    --connection-id <value> \
    --owner-account <value> \
    --new-public-virtual-interface-allocation <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connection-id` | **Yes** | string | -- | The ID of the connection |
| `--owner-account` | **Yes** | string | -- | The account ID of the virtual interface owner |
| `--new-public-virtual-interface-allocation` | **Yes** | structure | -- | Virtual interface allocation config |

**Output Schema:**
Same as the virtual interface object in `create-public-virtual-interface`.

---

### 3.12 `allocate-transit-virtual-interface`

Provisions a transit virtual interface to be owned by the specified account.

**Synopsis:**
```bash
aws directconnect allocate-transit-virtual-interface \
    --connection-id <value> \
    --owner-account <value> \
    --new-transit-virtual-interface-allocation <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connection-id` | **Yes** | string | -- | The ID of the connection |
| `--owner-account` | **Yes** | string | -- | The account ID of the virtual interface owner |
| `--new-transit-virtual-interface-allocation` | **Yes** | structure | -- | Virtual interface allocation config |

**Output Schema:**
Same as `create-transit-virtual-interface` output.

---

### 3.13 `associate-virtual-interface`

Associates a virtual interface with a specified owner account. The virtual interface must already be created but not yet confirmed.

**Synopsis:**
```bash
aws directconnect associate-virtual-interface \
    --virtual-interface-id <value> \
    --connection-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--virtual-interface-id` | **Yes** | string | -- | The ID of the virtual interface |
| `--connection-id` | **Yes** | string | -- | The ID of the LAG or connection to associate with |

**Output Schema:**
Same as the virtual interface object in `create-private-virtual-interface`.

---

### 3.14 `describe-router-configuration`

Gets the router configuration for a virtual interface, providing vendor-specific configuration instructions.

**Synopsis:**
```bash
aws directconnect describe-router-configuration \
    --virtual-interface-id <value> \
    [--router-type-identifier <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--virtual-interface-id` | **Yes** | string | -- | The ID of the virtual interface |
| `--router-type-identifier` | No | string | None | The router type identifier |

**Output Schema:**
```json
{
    "customerRouterConfig": "string",
    "router": {
        "vendor": "string",
        "platform": "string",
        "software": "string",
        "xsltTemplateName": "string",
        "xsltTemplateNameForMacSec": "string",
        "routerTypeIdentifier": "string"
    },
    "virtualInterfaceId": "string",
    "virtualInterfaceName": "string"
}
```
