# Peerings

> Note: `create-transit-gateway-peering` and `get-transit-gateway-peering` are documented in [`transit-gateway.md`](transit-gateway.md). This file covers the `list-peerings` command.

### 10.1 `list-peerings`

Lists the peerings for a core network. **Paginated.**

**Synopsis:**
```bash
aws networkmanager list-peerings \
    [--core-network-id <value>] \
    [--peering-type <value>] \
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
| `--peering-type` | No | string | None | Filter by type: `TRANSIT_GATEWAY` |
| `--edge-location` | No | string | None | Filter by edge location |
| `--state` | No | string | None | Filter by state: `CREATING`, `FAILED`, `AVAILABLE`, `DELETING` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Peerings": [
        {
            "CoreNetworkId": "string",
            "CoreNetworkArn": "string",
            "PeeringId": "string",
            "OwnerAccountId": "string",
            "PeeringType": "TRANSIT_GATEWAY",
            "State": "CREATING|FAILED|AVAILABLE|DELETING",
            "EdgeLocation": "string",
            "ResourceArn": "string",
            "Tags": [{"Key": "string", "Value": "string"}],
            "CreatedAt": "timestamp",
            "LastModificationErrors": [
                {
                    "Code": "string",
                    "Message": "string",
                    "ResourceArn": "string",
                    "RequestId": "string"
                }
            ]
        }
    ],
    "NextToken": "string"
}
```
