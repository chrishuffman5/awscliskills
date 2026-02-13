# Pricing & Shipping

### 4.1 `create-long-term-pricing`

Creates a long-term pricing agreement for a Snow Family device with one-month, one-year, or three-year terms.

**Synopsis:**
```bash
aws snowball create-long-term-pricing \
    --long-term-pricing-type <value> \
    --snowball-type <value> \
    [--is-long-term-pricing-auto-renew | --no-is-long-term-pricing-auto-renew] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--long-term-pricing-type` | **Yes** | string | -- | Pricing type: `OneYear`, `ThreeYear`, `OneMonth` |
| `--snowball-type` | **Yes** | string | -- | Device type: `STANDARD`, `EDGE`, `EDGE_C`, `EDGE_CG`, `EDGE_S`, `SNC1_HDD`, `SNC1_SSD`, `V3_5C`, `V3_5S`, `RACK_5U_C` |
| `--is-long-term-pricing-auto-renew` | No | boolean | None | Auto-renew the contract before expiration |

**Output Schema:**
```json
{
    "LongTermPricingId": "string"
}
```

The ID format is `LTPID[0-9a-f]{8}-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{4}-[0-9a-f]{12}` (41 characters).

---

### 4.2 `update-long-term-pricing`

Updates a long-term pricing agreement. Can change auto-renewal settings or specify a replacement device.

**Synopsis:**
```bash
aws snowball update-long-term-pricing \
    --long-term-pricing-id <value> \
    [--replacement-job <value>] \
    [--is-long-term-pricing-auto-renew | --no-is-long-term-pricing-auto-renew] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--long-term-pricing-id` | **Yes** | string | -- | Long-term pricing ID (41 chars) |
| `--replacement-job` | No | string | None | Replacement job ID (39 chars) |
| `--is-long-term-pricing-auto-renew` | No | boolean | None | Auto-renew the contract |

**Output:** None

---

### 4.3 `list-long-term-pricing`

Returns all long-term pricing agreements in the account. **Paginated operation.**

**Synopsis:**
```bash
aws snowball list-long-term-pricing \
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
    "LongTermPricingEntries": [
        {
            "LongTermPricingId": "string",
            "LongTermPricingEndDate": "timestamp",
            "LongTermPricingStartDate": "timestamp",
            "LongTermPricingType": "OneYear|ThreeYear|OneMonth",
            "CurrentActiveJob": "string",
            "ReplacementJob": "string",
            "IsLongTermPricingAutoRenew": "boolean",
            "LongTermPricingStatus": "string",
            "SnowballType": "STANDARD|EDGE|EDGE_C|EDGE_CG|EDGE_S|SNC1_HDD|SNC1_SSD|V3_5C|V3_5S|RACK_5U_C",
            "JobIds": ["string"]
        }
    ],
    "NextToken": "string"
}
```

---

### 4.4 `create-return-shipping-label`

Creates a return shipping label for the specified job. Used when returning a Snow device to AWS.

**Synopsis:**
```bash
aws snowball create-return-shipping-label \
    --job-id <value> \
    [--shipping-option <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | Job ID (39 chars) |
| `--shipping-option` | No | string | None | Shipping speed: `SECOND_DAY`, `NEXT_DAY`, `EXPRESS`, `STANDARD` |

**Output Schema:**
```json
{
    "Status": "InProgress|TimedOut|Succeeded|Failed"
}
```

---

### 4.5 `describe-return-shipping-label`

Returns information about a return shipping label, including status, expiration date, and download URL.

**Synopsis:**
```bash
aws snowball describe-return-shipping-label \
    --job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | Job ID (39 chars) |

**Output Schema:**
```json
{
    "Status": "InProgress|TimedOut|Succeeded|Failed",
    "ExpirationDate": "timestamp",
    "ReturnShippingLabelURI": "string"
}
```
