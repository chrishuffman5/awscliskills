# BGP

### 5.1 `create-bgp-peer`

Creates a BGP peer on the specified virtual interface. You can create one IPv4 and one IPv6 BGP peer per virtual interface.

**Synopsis:**
```bash
aws directconnect create-bgp-peer \
    [--virtual-interface-id <value>] \
    [--new-bgp-peer <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--virtual-interface-id` | No | string | None | The ID of the virtual interface |
| `--new-bgp-peer` | No | structure | None | BGP peer configuration (see below) |

**new-bgp-peer Structure:**

| Field | Required | Type | Default | Description |
|-------|----------|------|---------|-------------|
| `asn` | No | integer | -- | Customer ASN (1-2147483646). Use `asnLong` for larger values |
| `asnLong` | No | long | -- | Customer ASN (1-4294967294). Preferred over `asn` |
| `authKey` | No | string | None | BGP authentication key (6-80 chars) |
| `addressFamily` | No | string | None | Address family: `ipv4` or `ipv6` |
| `amazonAddress` | No | string | None | IP address assigned to Amazon interface |
| `customerAddress` | No | string | None | IP address assigned to customer interface |

> **Note:** For IPv6 BGP peers, omit `amazonAddress` and `customerAddress`; IPv6 addresses are automatically assigned.

**Output Schema:**
```json
{
    "virtualInterface": {
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
}
```

---

### 5.2 `delete-bgp-peer`

Deletes the specified BGP peer from a virtual interface. You cannot delete the last BGP peer from a virtual interface.

**Synopsis:**
```bash
aws directconnect delete-bgp-peer \
    [--virtual-interface-id <value>] \
    [--asn <value>] \
    [--asn-long <value>] \
    [--customer-address <value>] \
    [--bgp-peer-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--virtual-interface-id` | No | string | None | The ID of the virtual interface |
| `--asn` | No | integer | None | The ASN (1-2147483646). Cannot be used with `--asn-long` |
| `--asn-long` | No | long | None | The long ASN (1-4294967294). Preferred over `--asn` |
| `--customer-address` | No | string | None | Customer IP address of the BGP peer |
| `--bgp-peer-id` | No | string | None | The ID of the BGP peer |

**Output Schema:**
Same as `create-bgp-peer` output.

---

### 5.3 `start-bgp-failover-test`

Starts the BGP failover test from the specified virtual interface to the specified BGP peers. The test causes the BGP peering session to go down for a specified duration.

**Synopsis:**
```bash
aws directconnect start-bgp-failover-test \
    --virtual-interface-id <value> \
    [--bgp-peers <value>] \
    [--test-duration-in-minutes <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--virtual-interface-id` | **Yes** | string | -- | The ID of the virtual interface |
| `--bgp-peers` | No | list(string) | None | The BGP peers to test (if omitted, tests all peers) |
| `--test-duration-in-minutes` | No | integer | 180 | Duration of the test in minutes (1-180) |

**Output Schema:**
```json
{
    "virtualInterfaceTest": {
        "testId": "string",
        "virtualInterfaceId": "string",
        "bgpPeers": ["string"],
        "status": "string",
        "ownerAccount": "string",
        "testDurationInMinutes": "integer",
        "startTime": "timestamp",
        "endTime": "timestamp"
    }
}
```

---

### 5.4 `stop-bgp-failover-test`

Stops the BGP failover test.

**Synopsis:**
```bash
aws directconnect stop-bgp-failover-test \
    --virtual-interface-id <value> \
    --test-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--virtual-interface-id` | **Yes** | string | -- | The ID of the virtual interface |
| `--test-id` | **Yes** | string | -- | The ID of the failover test |

**Output Schema:**
Same as `start-bgp-failover-test` output.

---

### 5.5 `list-virtual-interface-test-history`

Lists the BGP failover test history for the specified virtual interface.

**Synopsis:**
```bash
aws directconnect list-virtual-interface-test-history \
    [--test-id <value>] \
    [--virtual-interface-id <value>] \
    [--bgp-peers <value>] \
    [--status <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--test-id` | No | string | None | The ID of a specific test |
| `--virtual-interface-id` | No | string | None | Filter by virtual interface |
| `--bgp-peers` | No | list(string) | None | Filter by BGP peers |
| `--status` | No | string | None | Filter by status |
| `--max-results` | No | integer | None | Maximum results (max 100) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "virtualInterfaceTestHistory": [
        {
            "testId": "string",
            "virtualInterfaceId": "string",
            "bgpPeers": ["string"],
            "status": "string",
            "ownerAccount": "string",
            "testDurationInMinutes": "integer",
            "startTime": "timestamp",
            "endTime": "timestamp"
        }
    ],
    "nextToken": "string"
}
```
