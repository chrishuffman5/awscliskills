# Reserved Nodes

### 11.1 `describe-reserved-nodes`

Returns descriptions of reserved nodes. **Paginated operation.**

**Synopsis:**
```bash
aws redshift describe-reserved-nodes \
    [--reserved-node-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--reserved-node-id` | No | string | -- | Specific reserved node ID |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "ReservedNodes": [
        {
            "ReservedNodeId": "string",
            "ReservedNodeOfferingId": "string",
            "NodeType": "string",
            "StartTime": "timestamp",
            "Duration": "integer",
            "FixedPrice": "double",
            "UsagePrice": "double",
            "CurrencyCode": "string",
            "NodeCount": "integer",
            "State": "active|payment-pending|payment-failed|retired|exchanging",
            "OfferingType": "string",
            "RecurringCharges": [
                {
                    "RecurringChargeAmount": "double",
                    "RecurringChargeFrequency": "Monthly"
                }
            ],
            "ReservedNodeOfferingType": "Regular|Upgradable"
        }
    ],
    "Marker": "string"
}
```

---

### 11.2 `describe-reserved-node-offerings`

Returns available reserved node offerings. **Paginated operation.**

**Synopsis:**
```bash
aws redshift describe-reserved-node-offerings \
    [--reserved-node-offering-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--reserved-node-offering-id` | No | string | -- | Specific offering ID |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "ReservedNodeOfferings": [
        {
            "ReservedNodeOfferingId": "string",
            "NodeType": "string",
            "Duration": "integer",
            "FixedPrice": "double",
            "UsagePrice": "double",
            "CurrencyCode": "string",
            "OfferingType": "string",
            "RecurringCharges": [
                {
                    "RecurringChargeAmount": "double",
                    "RecurringChargeFrequency": "Monthly"
                }
            ],
            "ReservedNodeOfferingType": "Regular|Upgradable"
        }
    ],
    "Marker": "string"
}
```

---

### 11.3 `purchase-reserved-node-offering`

Purchases a reserved node offering.

**Synopsis:**
```bash
aws redshift purchase-reserved-node-offering \
    --reserved-node-offering-id <value> \
    [--node-count <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--reserved-node-offering-id` | **Yes** | string | -- | Offering ID to purchase |
| `--node-count` | No | integer | 1 | Number of reserved nodes to purchase |

**Output Schema:**
```json
{
    "ReservedNode": {
        "ReservedNodeId": "string",
        "ReservedNodeOfferingId": "string",
        "NodeType": "string",
        "StartTime": "timestamp",
        "Duration": "integer",
        "FixedPrice": "double",
        "UsagePrice": "double",
        "CurrencyCode": "string",
        "NodeCount": "integer",
        "State": "payment-pending",
        "OfferingType": "string"
    }
}
```

---

### 11.4 `accept-reserved-node-exchange`

Exchanges a DC1 or DS2 reserved node for a DC2 reserved node.

**Synopsis:**
```bash
aws redshift accept-reserved-node-exchange \
    --reserved-node-id <value> \
    --target-reserved-node-offering-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--reserved-node-id` | **Yes** | string | -- | Reserved node to exchange |
| `--target-reserved-node-offering-id` | **Yes** | string | -- | Target offering ID |

**Output Schema:**
```json
{
    "ExchangedReservedNode": {
        "ReservedNodeId": "string",
        "ReservedNodeOfferingId": "string",
        "NodeType": "string",
        "NodeCount": "integer",
        "State": "exchanging"
    }
}
```

---

### 11.5 `describe-reserved-node-exchange-status`

Returns the status of reserved node exchanges. **Paginated operation.**

**Synopsis:**
```bash
aws redshift describe-reserved-node-exchange-status \
    [--reserved-node-id <value>] \
    [--reserved-node-exchange-request-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--reserved-node-id` | No | string | -- | Reserved node ID |
| `--reserved-node-exchange-request-id` | No | string | -- | Exchange request ID |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "ReservedNodeExchangeStatusDetails": [
        {
            "ReservedNodeExchangeRequestId": "string",
            "Status": "REQUESTED|PENDING|IN_PROGRESS|RETRYING|SUCCEEDED|FAILED",
            "RequestTime": "timestamp",
            "SourceReservedNodeId": "string",
            "SourceReservedNodeType": "string",
            "SourceReservedNodeCount": "integer",
            "TargetReservedNodeOfferingId": "string",
            "TargetReservedNodeType": "string",
            "TargetReservedNodeCount": "integer"
        }
    ],
    "Marker": "string"
}
```

---

### 11.6 `get-reserved-node-exchange-offerings`

Returns available exchange offerings for a reserved node. **Paginated operation.**

**Synopsis:**
```bash
aws redshift get-reserved-node-exchange-offerings \
    --reserved-node-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--reserved-node-id` | **Yes** | string | -- | Reserved node to get exchange offerings for |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "ReservedNodeOfferings": [
        {
            "ReservedNodeOfferingId": "string",
            "NodeType": "string",
            "Duration": "integer",
            "FixedPrice": "double",
            "UsagePrice": "double",
            "CurrencyCode": "string",
            "OfferingType": "string",
            "RecurringCharges": [],
            "ReservedNodeOfferingType": "Regular|Upgradable"
        }
    ],
    "Marker": "string"
}
```

---

### 11.7 `get-reserved-node-exchange-configuration-options`

Returns configuration options for exchanging a reserved node. **Paginated operation.**

**Synopsis:**
```bash
aws redshift get-reserved-node-exchange-configuration-options \
    --action-type <value> \
    [--cluster-identifier <value>] \
    [--snapshot-identifier <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--action-type` | **Yes** | string | -- | Action type: `restore-cluster`, `resize-cluster` |
| `--cluster-identifier` | No | string | -- | Cluster identifier |
| `--snapshot-identifier` | No | string | -- | Snapshot identifier |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "ReservedNodeConfigurationOptionList": [
        {
            "SourceReservedNode": {
                "ReservedNodeId": "string",
                "NodeType": "string",
                "NodeCount": "integer"
            },
            "TargetReservedNodeCount": "integer",
            "TargetReservedNodeOffering": {
                "ReservedNodeOfferingId": "string",
                "NodeType": "string",
                "Duration": "integer",
                "FixedPrice": "double"
            }
        }
    ],
    "Marker": "string"
}
```
