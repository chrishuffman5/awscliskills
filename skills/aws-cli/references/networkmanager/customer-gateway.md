# Customer Gateway

### 9.1 `associate-customer-gateway`

Associates a customer gateway with a device and optionally a link.

**Synopsis:**
```bash
aws networkmanager associate-customer-gateway \
    --customer-gateway-arn <value> \
    --global-network-id <value> \
    --device-id <value> \
    [--link-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--customer-gateway-arn` | **Yes** | string | -- | Customer gateway ARN |
| `--global-network-id` | **Yes** | string | -- | Global network ID |
| `--device-id` | **Yes** | string | -- | Device ID |
| `--link-id` | No | string | None | Link ID |

**Output Schema:**
```json
{
    "CustomerGatewayAssociation": {
        "CustomerGatewayArn": "string",
        "GlobalNetworkId": "string",
        "DeviceId": "string",
        "LinkId": "string",
        "State": "PENDING|AVAILABLE|DELETING|DELETED"
    }
}
```

---

### 9.2 `disassociate-customer-gateway`

Disassociates a customer gateway from a device and link.

**Synopsis:**
```bash
aws networkmanager disassociate-customer-gateway \
    --global-network-id <value> \
    --customer-gateway-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--global-network-id` | **Yes** | string | -- | Global network ID |
| `--customer-gateway-arn` | **Yes** | string | -- | Customer gateway ARN |

**Output Schema:** Same as associate-customer-gateway.

---

### 9.3 `get-customer-gateway-associations`

Gets customer gateway associations. **Paginated.**

**Synopsis:**
```bash
aws networkmanager get-customer-gateway-associations \
    --global-network-id <value> \
    [--customer-gateway-arns <value>] \
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
| `--customer-gateway-arns` | No | list(string) | None | Filter by customer gateway ARNs |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "CustomerGatewayAssociations": [
        {
            "CustomerGatewayArn": "string",
            "GlobalNetworkId": "string",
            "DeviceId": "string",
            "LinkId": "string",
            "State": "string"
        }
    ],
    "NextToken": "string"
}
```
