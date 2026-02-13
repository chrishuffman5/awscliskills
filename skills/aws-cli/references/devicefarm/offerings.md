# Offerings

### 11.1 `list-offerings`

Returns a list of products or offerings that the user can manage through the API. **Paginated operation.**

**Synopsis:**
```bash
aws devicefarm list-offerings \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "offerings": [
        {
            "id": "string",
            "description": "string",
            "type": "RECURRING",
            "platform": "ANDROID|IOS",
            "recurringCharges": [
                {
                    "cost": {
                        "amount": "double",
                        "currencyCode": "USD"
                    },
                    "frequency": "MONTHLY"
                }
            ]
        }
    ],
    "nextToken": "string"
}
```

---

### 11.2 `list-offering-promotions`

Returns a list of offering promotions. **Paginated operation.**

**Synopsis:**
```bash
aws devicefarm list-offering-promotions \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "offeringPromotions": [
        {
            "id": "string",
            "description": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 11.3 `list-offering-transactions`

Returns a list of all historical purchases, renewals, and system renewal transactions. **Paginated operation.**

**Synopsis:**
```bash
aws devicefarm list-offering-transactions \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "offeringTransactions": [
        {
            "offeringStatus": {
                "type": "PURCHASE|RENEW|SYSTEM",
                "offering": {
                    "id": "string",
                    "description": "string",
                    "type": "RECURRING",
                    "platform": "ANDROID|IOS",
                    "recurringCharges": []
                },
                "quantity": "integer",
                "effectiveOn": "timestamp"
            },
            "transactionId": "string",
            "offeringPromotionId": "string",
            "createdOn": "timestamp",
            "cost": {
                "amount": "double",
                "currencyCode": "USD"
            }
        }
    ],
    "nextToken": "string"
}
```

---

### 11.4 `get-offering-status`

Gets the current status and future status of all offerings purchased by an account. **Paginated operation.**

**Synopsis:**
```bash
aws devicefarm get-offering-status \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "current": {
        "string": {
            "type": "PURCHASE|RENEW|SYSTEM",
            "offering": {
                "id": "string",
                "description": "string",
                "type": "RECURRING",
                "platform": "ANDROID|IOS",
                "recurringCharges": []
            },
            "quantity": "integer",
            "effectiveOn": "timestamp"
        }
    },
    "nextPeriod": {},
    "nextToken": "string"
}
```

---

### 11.5 `purchase-offering`

Immediately purchases offerings for an account. Purchasing requires sufficient unmetered or metered device slots.

**Synopsis:**
```bash
aws devicefarm purchase-offering \
    --offering-id <value> \
    --quantity <value> \
    [--offering-promotion-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--offering-id` | **Yes** | string | -- | ID of the offering to purchase |
| `--quantity` | **Yes** | integer | -- | Number of device slots to purchase |
| `--offering-promotion-id` | No | string | None | Promotion ID to apply |

**Output Schema:**
```json
{
    "offeringTransaction": {
        "offeringStatus": {
            "type": "PURCHASE",
            "offering": {
                "id": "string",
                "description": "string",
                "type": "RECURRING",
                "platform": "ANDROID|IOS",
                "recurringCharges": []
            },
            "quantity": "integer",
            "effectiveOn": "timestamp"
        },
        "transactionId": "string",
        "offeringPromotionId": "string",
        "createdOn": "timestamp",
        "cost": {
            "amount": "double",
            "currencyCode": "USD"
        }
    }
}
```

---

### 11.6 `renew-offering`

Explicitly sets the quantity of devices to renew for an offering.

**Synopsis:**
```bash
aws devicefarm renew-offering \
    --offering-id <value> \
    --quantity <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--offering-id` | **Yes** | string | -- | ID of the offering to renew |
| `--quantity` | **Yes** | integer | -- | Number of device slots to renew |

**Output Schema:**
```json
{
    "offeringTransaction": {
        "offeringStatus": {
            "type": "RENEW",
            "offering": {
                "id": "string",
                "description": "string",
                "type": "RECURRING",
                "platform": "ANDROID|IOS",
                "recurringCharges": []
            },
            "quantity": "integer",
            "effectiveOn": "timestamp"
        },
        "transactionId": "string",
        "createdOn": "timestamp",
        "cost": {
            "amount": "double",
            "currencyCode": "USD"
        }
    }
}
```
