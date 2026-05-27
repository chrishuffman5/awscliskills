# Route Analysis & Network Resources

## Route Analysis

### 11.1 `start-route-analysis`

Starts analyzing the routing path between a source and destination in your global network.

**Synopsis:**
```bash
aws networkmanager start-route-analysis \
    --global-network-id <value> \
    --source <value> \
    --destination <value> \
    [--include-return-path | --no-include-return-path] \
    [--use-middleboxes | --no-use-middleboxes] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-network-id` | **Yes** | string | -- | Global network ID |
| `--source` | **Yes** | structure | -- | Source endpoint. Shorthand: `TransitGatewayAttachmentArn=string,IpAddress=string` |
| `--destination` | **Yes** | structure | -- | Destination endpoint. Shorthand: `TransitGatewayAttachmentArn=string,IpAddress=string` |
| `--include-return-path` | No | boolean | false | Include return path analysis |
| `--use-middleboxes` | No | boolean | false | Include middlebox appliances |

**Output Schema:**
```json
{
    "RouteAnalysis": {
        "GlobalNetworkId": "string",
        "OwnerAccountId": "string",
        "RouteAnalysisId": "string",
        "StartTimestamp": "timestamp",
        "Status": "RUNNING|COMPLETED|FAILED",
        "Source": {
            "TransitGatewayAttachmentArn": "string",
            "TransitGatewayArn": "string",
            "IpAddress": "string"
        },
        "Destination": {
            "TransitGatewayAttachmentArn": "string",
            "TransitGatewayArn": "string",
            "IpAddress": "string"
        },
        "IncludeReturnPath": true|false,
        "UseMiddleboxes": true|false,
        "ForwardPath": {
            "CompletionStatus": {
                "ResultCode": "CONNECTED|NOT_CONNECTED",
                "ReasonCode": "TRANSIT_GATEWAY_ATTACHMENT_NOT_FOUND|TRANSIT_GATEWAY_ATTACHMENT_NOT_IN_TRANSIT_GATEWAY|TRANSIT_GATEWAY_ATTACHMENT_STABLE_ROUTE_TABLE_NOT_FOUND|...",
                "ReasonContext": {"key": "value"}
            },
            "Path": [
                {
                    "Sequence": "integer",
                    "Resource": {
                        "RegisteredGatewayArn": "string",
                        "ResourceArn": "string",
                        "ResourceType": "string",
                        "Definition": "string",
                        "NameTag": "string",
                        "IsMiddlebox": true|false
                    },
                    "DestinationCidrBlock": "string"
                }
            ]
        },
        "ReturnPath": {
            "CompletionStatus": {},
            "Path": []
        }
    }
}
```

---

### 11.2 `get-route-analysis`

Gets information about a route analysis.

**Synopsis:**
```bash
aws networkmanager get-route-analysis \
    --global-network-id <value> \
    --route-analysis-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-network-id` | **Yes** | string | -- | Global network ID |
| `--route-analysis-id` | **Yes** | string | -- | Route analysis ID |

**Output Schema:** Same as start-route-analysis.

---

## Network Resources

### 11.3 `get-network-routes`

Gets the network routes for a specified route table within a global network.

**Synopsis:**
```bash
aws networkmanager get-network-routes \
    --global-network-id <value> \
    --route-table-identifier <value> \
    [--exact-cidr-matches <value>] \
    [--longest-prefix-matches <value>] \
    [--subnet-of-matches <value>] \
    [--supernet-of-matches <value>] \
    [--prefix-list-ids <value>] \
    [--states <value>] \
    [--types <value>] \
    [--destination-filters <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-network-id` | **Yes** | string | -- | Global network ID |
| `--route-table-identifier` | **Yes** | structure | -- | Route table identifier. Shorthand: `TransitGatewayRouteTableArn=string` or `CoreNetworkSegmentEdge={CoreNetworkId=string,SegmentName=string,EdgeLocation=string}` or `CoreNetworkNetworkFunctionGroup=...` |
| `--exact-cidr-matches` | No | list(string) | None | Exact CIDR match filter |
| `--longest-prefix-matches` | No | list(string) | None | Longest prefix match filter |
| `--subnet-of-matches` | No | list(string) | None | Subnet-of filter |
| `--supernet-of-matches` | No | list(string) | None | Supernet-of filter |
| `--prefix-list-ids` | No | list(string) | None | Filter by prefix list IDs |
| `--states` | No | list(string) | None | Route states: `ACTIVE`, `BLACKHOLE` |
| `--types` | No | list(string) | None | Route types: `PROPAGATED`, `STATIC` |
| `--destination-filters` | No | map | None | Destination filters |

**Output Schema:**
```json
{
    "RouteTableArn": "string",
    "CoreNetworkSegmentEdge": {
        "CoreNetworkId": "string",
        "SegmentName": "string",
        "EdgeLocation": "string"
    },
    "RouteTableType": "TRANSIT_GATEWAY_ROUTE_TABLE|CORE_NETWORK_SEGMENT|NETWORK_FUNCTION_GROUP",
    "RouteTableTimestamp": "timestamp",
    "NetworkRoutes": [
        {
            "DestinationCidrBlock": "string",
            "Destinations": [
                {
                    "CoreNetworkAttachmentId": "string",
                    "TransitGatewayAttachmentId": "string",
                    "SegmentName": "string",
                    "NetworkFunctionGroupName": "string",
                    "EdgeLocation": "string",
                    "ResourceType": "string",
                    "ResourceId": "string"
                }
            ],
            "PrefixListId": "string",
            "State": "ACTIVE|BLACKHOLE",
            "Type": "PROPAGATED|STATIC"
        }
    ]
}
```

---

### 11.4 `get-network-resources`

Describes the network resources in a global network. **Paginated.**

**Synopsis:**
```bash
aws networkmanager get-network-resources \
    --global-network-id <value> \
    [--core-network-id <value>] \
    [--registered-gateway-arn <value>] \
    [--aws-region <value>] \
    [--account-id <value>] \
    [--resource-type <value>] \
    [--resource-arn <value>] \
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
| `--core-network-id` | No | string | None | Filter by core network ID |
| `--registered-gateway-arn` | No | string | None | Filter by registered gateway ARN |
| `--aws-region` | No | string | None | Filter by AWS Region |
| `--account-id` | No | string | None | Filter by account ID |
| `--resource-type` | No | string | None | Filter by resource type |
| `--resource-arn` | No | string | None | Filter by specific resource ARN |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "NetworkResources": [
        {
            "RegisteredGatewayArn": "string",
            "CoreNetworkId": "string",
            "AwsRegion": "string",
            "AccountId": "string",
            "ResourceType": "string",
            "ResourceId": "string",
            "ResourceArn": "string",
            "Definition": "string",
            "DefinitionTimestamp": "timestamp",
            "Tags": [],
            "Metadata": {"key": "value"}
        }
    ],
    "NextToken": "string"
}
```

---

### 11.5 `get-network-resource-counts`

Gets network resource counts for a global network. **Paginated.**

**Synopsis:**
```bash
aws networkmanager get-network-resource-counts \
    --global-network-id <value> \
    [--resource-type <value>] \
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
| `--resource-type` | No | string | None | Filter by resource type |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "NetworkResourceCounts": [
        {
            "ResourceType": "string",
            "Count": "integer"
        }
    ],
    "NextToken": "string"
}
```

---

### 11.6 `get-network-resource-relationships`

Gets the network resource relationships for a global network. **Paginated.**

**Synopsis:**
```bash
aws networkmanager get-network-resource-relationships \
    --global-network-id <value> \
    [--core-network-id <value>] \
    [--registered-gateway-arn <value>] \
    [--aws-region <value>] \
    [--account-id <value>] \
    [--resource-type <value>] \
    [--resource-arn <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** Same filters as `get-network-resources`.

**Output Schema:**
```json
{
    "Relationships": [
        {
            "From": "string",
            "To": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 11.7 `get-network-telemetry`

Gets network telemetry data for a global network. **Paginated.**

**Synopsis:**
```bash
aws networkmanager get-network-telemetry \
    --global-network-id <value> \
    [--core-network-id <value>] \
    [--registered-gateway-arn <value>] \
    [--aws-region <value>] \
    [--account-id <value>] \
    [--resource-type <value>] \
    [--resource-arn <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** Same filters as `get-network-resources`.

**Output Schema:**
```json
{
    "NetworkTelemetry": [
        {
            "RegisteredGatewayArn": "string",
            "CoreNetworkId": "string",
            "AwsRegion": "string",
            "AccountId": "string",
            "ResourceType": "string",
            "ResourceId": "string",
            "ResourceArn": "string",
            "Address": "string",
            "Health": {
                "Type": "BGP|IPSEC",
                "Status": "UP|DOWN",
                "Timestamp": "timestamp"
            }
        }
    ],
    "NextToken": "string"
}
```

---

### 11.8 `update-network-resource-metadata`

Updates the metadata of a network resource.

**Synopsis:**
```bash
aws networkmanager update-network-resource-metadata \
    --global-network-id <value> \
    --resource-arn <value> \
    --metadata <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-network-id` | **Yes** | string | -- | Global network ID |
| `--resource-arn` | **Yes** | string | -- | Resource ARN |
| `--metadata` | **Yes** | map | -- | Metadata key-value pairs. Shorthand: `KeyName1=string,KeyName2=string` |

**Output Schema:**
```json
{
    "ResourceArn": "string",
    "Metadata": {"key": "value"}
}
```

---

## Attachment Routing Policy

### 11.9 `list-attachment-routing-policy-associations`

Lists routing policy associations for an attachment. **Paginated.**

**Synopsis:**
```bash
aws networkmanager list-attachment-routing-policy-associations \
    --core-network-id <value> \
    --attachment-id <value> \
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
| `--attachment-id` | **Yes** | string | -- | Attachment ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "AttachmentRoutingPolicyAssociations": [
        {
            "AttachmentId": "string",
            "SegmentName": "string",
            "RoutingPolicyLabel": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 11.10 `put-attachment-routing-policy-label`

Sets a routing policy label on an attachment.

**Synopsis:**
```bash
aws networkmanager put-attachment-routing-policy-label \
    --attachment-id <value> \
    --routing-policy-label <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--attachment-id` | **Yes** | string | -- | Attachment ID |
| `--routing-policy-label` | **Yes** | string | -- | Routing policy label |

**Output:** None

---

### 11.11 `remove-attachment-routing-policy-label`

Removes a routing policy label from an attachment.

**Synopsis:**
```bash
aws networkmanager remove-attachment-routing-policy-label \
    --attachment-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--attachment-id` | **Yes** | string | -- | Attachment ID |

**Output:** None
