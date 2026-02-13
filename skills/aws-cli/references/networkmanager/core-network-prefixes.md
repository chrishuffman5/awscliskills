# Core Network Prefixes

### 3.1 `create-core-network-prefix-list-association`

Associates a prefix list with a core network segment.

**Synopsis:**
```bash
aws networkmanager create-core-network-prefix-list-association \
    --core-network-id <value> \
    --prefix-list-id <value> \
    --segment-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--core-network-id` | **Yes** | string | -- | Core network ID |
| `--prefix-list-id` | **Yes** | string | -- | VPC prefix list ID |
| `--segment-name` | **Yes** | string | -- | Core network segment name |

**Output Schema:**
```json
{
    "CoreNetworkPrefixListAssociation": {
        "CoreNetworkId": "string",
        "PrefixListId": "string",
        "SegmentName": "string",
        "State": "string"
    }
}
```

---

### 3.2 `delete-core-network-prefix-list-association`

Removes a prefix list association from a core network segment.

**Synopsis:**
```bash
aws networkmanager delete-core-network-prefix-list-association \
    --core-network-id <value> \
    --prefix-list-id <value> \
    --segment-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--core-network-id` | **Yes** | string | -- | Core network ID |
| `--prefix-list-id` | **Yes** | string | -- | VPC prefix list ID |
| `--segment-name` | **Yes** | string | -- | Core network segment name |

**Output Schema:**
```json
{
    "CoreNetworkPrefixListAssociation": {
        "CoreNetworkId": "string",
        "PrefixListId": "string",
        "SegmentName": "string",
        "State": "string"
    }
}
```

---

### 3.3 `list-core-network-prefix-list-associations`

Lists prefix list associations for a core network. **Paginated.**

**Synopsis:**
```bash
aws networkmanager list-core-network-prefix-list-associations \
    --core-network-id <value> \
    [--segment-name <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--core-network-id` | **Yes** | string | -- | Core network ID |
| `--segment-name` | No | string | None | Filter by segment name |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "CoreNetworkPrefixListAssociations": [
        {
            "CoreNetworkId": "string",
            "PrefixListId": "string",
            "SegmentName": "string",
            "State": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.4 `list-core-network-routing-information`

Lists routing information for a core network including segment-level routes. **Paginated.**

**Synopsis:**
```bash
aws networkmanager list-core-network-routing-information \
    --core-network-id <value> \
    [--edge-location <value>] \
    [--segment-name <value>] \
    [--route-type <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--core-network-id` | **Yes** | string | -- | Core network ID |
| `--edge-location` | No | string | None | Filter by edge location |
| `--segment-name` | No | string | None | Filter by segment name |
| `--route-type` | No | string | None | Filter by route type: `PROPAGATED`, `STATIC` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "CoreNetworkRoutingInformation": [
        {
            "CoreNetworkId": "string",
            "EdgeLocation": "string",
            "SegmentName": "string",
            "DestinationCidrBlock": "string",
            "Destinations": [
                {
                    "CoreNetworkAttachmentId": "string",
                    "SegmentName": "string",
                    "EdgeLocation": "string",
                    "ResourceType": "string",
                    "ResourceId": "string"
                }
            ],
            "RouteType": "PROPAGATED|STATIC"
        }
    ],
    "NextToken": "string"
}
```
