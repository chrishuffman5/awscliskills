# Orders

### 3.1 `create-order`

Creates an order for an Outpost.

**Synopsis:**
```bash
aws outposts create-order \
    --outpost-identifier <value> \
    --line-items <value> \
    --payment-option <value> \
    [--payment-term <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--outpost-identifier` | **Yes** | string | -- | ID or ARN of the Outpost |
| `--line-items` | **Yes** | list | -- | Line items for the order. Shorthand: `CatalogItemId=string,Quantity=integer ...` |
| `--payment-option` | **Yes** | string | -- | Payment option: `ALL_UPFRONT`, `NO_UPFRONT`, `PARTIAL_UPFRONT` |
| `--payment-term` | No | string | -- | Payment term: `THREE_YEARS`, `ONE_YEAR` |

**Line Item Structure:**
```json
{
    "CatalogItemId": "string",
    "Quantity": "integer"
}
```

**Output Schema:**
```json
{
    "Order": {
        "OutpostId": "string",
        "OrderId": "string",
        "Status": "RECEIVED|PENDING|PROCESSING|INSTALLING|FULFILLED|CANCELLED|PREPARING|IN_PROGRESS|COMPLETED|ERROR",
        "LineItems": [
            {
                "CatalogItemId": "string",
                "LineItemId": "string",
                "Quantity": "integer",
                "Status": "PREPARING|BUILDING|SHIPPED|DELIVERED|INSTALLING|INSTALLED|ERROR|CANCELLED|REPLACED",
                "ShipmentInformation": {
                    "ShipmentTrackingNumber": "string",
                    "ShipmentCarrier": "DHL|DBS|FEDEX|UPS|EXPEDITORS"
                },
                "AssetInformationList": [
                    {
                        "AssetId": "string",
                        "MacAddressList": ["string"]
                    }
                ],
                "PreviousLineItemId": "string",
                "PreviousOrderId": "string"
            }
        ],
        "PaymentOption": "ALL_UPFRONT|NO_UPFRONT|PARTIAL_UPFRONT",
        "OrderSubmissionDate": "timestamp",
        "OrderFulfilledDate": "timestamp",
        "PaymentTerm": "THREE_YEARS|ONE_YEAR",
        "OrderType": "OUTPOST|REPLACEMENT"
    }
}
```

---

### 3.2 `get-order`

Gets information about the specified order.

**Synopsis:**
```bash
aws outposts get-order \
    --order-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--order-id` | **Yes** | string | -- | ID of the order |

**Output Schema:**
```json
{
    "Order": {
        "OutpostId": "string",
        "OrderId": "string",
        "Status": "RECEIVED|PENDING|PROCESSING|INSTALLING|FULFILLED|CANCELLED|PREPARING|IN_PROGRESS|COMPLETED|ERROR",
        "LineItems": [
            {
                "CatalogItemId": "string",
                "LineItemId": "string",
                "Quantity": "integer",
                "Status": "string",
                "ShipmentInformation": {
                    "ShipmentTrackingNumber": "string",
                    "ShipmentCarrier": "string"
                },
                "AssetInformationList": [
                    {
                        "AssetId": "string",
                        "MacAddressList": ["string"]
                    }
                ],
                "PreviousLineItemId": "string",
                "PreviousOrderId": "string"
            }
        ],
        "PaymentOption": "ALL_UPFRONT|NO_UPFRONT|PARTIAL_UPFRONT",
        "OrderSubmissionDate": "timestamp",
        "OrderFulfilledDate": "timestamp",
        "PaymentTerm": "THREE_YEARS|ONE_YEAR",
        "OrderType": "OUTPOST|REPLACEMENT"
    }
}
```

---

### 3.3 `list-orders`

Lists the Outpost orders for your AWS account. **Paginated operation.**

**Synopsis:**
```bash
aws outposts list-orders \
    --outpost-identifier-filter <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--outpost-identifier-filter` | **Yes** | string | -- | ID or ARN of the Outpost to filter orders |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Orders": [
        {
            "OutpostId": "string",
            "OrderId": "string",
            "OrderType": "OUTPOST|REPLACEMENT",
            "Status": "RECEIVED|PENDING|PROCESSING|INSTALLING|FULFILLED|CANCELLED|PREPARING|IN_PROGRESS|COMPLETED|ERROR",
            "LineItemCountsByStatus": {
                "string": "integer"
            },
            "OrderSubmissionDate": "timestamp",
            "OrderFulfilledDate": "timestamp"
        }
    ],
    "NextToken": "string"
}
```
