# Pricing

### 9.1 `get-pricing-plan`

Gets the current pricing plan.

**Synopsis:**
```bash
aws iottwinmaker get-pricing-plan \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output Schema:**
```json
{
    "currentPricingPlan": {
        "billableEntityCount": "long",
        "bundleInformation": {
            "bundleNames": ["string"],
            "pricingTier": "TIER_1|TIER_2|TIER_3|TIER_4"
        },
        "effectiveDateTime": "timestamp",
        "pricingMode": "BASIC|STANDARD|TIERED_BUNDLE",
        "updateDateTime": "timestamp",
        "updateReason": "DEFAULT|PRICING_TIER_UPDATE|ENTITY_COUNT_UPDATE|PRICING_MODE_UPDATE|OVERWRITTEN"
    },
    "pendingPricingPlan": {
        "billableEntityCount": "long",
        "bundleInformation": {
            "bundleNames": ["string"],
            "pricingTier": "TIER_1|TIER_2|TIER_3|TIER_4"
        },
        "effectiveDateTime": "timestamp",
        "pricingMode": "BASIC|STANDARD|TIERED_BUNDLE",
        "updateDateTime": "timestamp",
        "updateReason": "string"
    }
}
```

---

### 9.2 `update-pricing-plan`

Updates the pricing plan.

**Synopsis:**
```bash
aws iottwinmaker update-pricing-plan \
    --pricing-mode <value> \
    [--bundle-names <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pricing-mode` | **Yes** | string | -- | `BASIC`, `STANDARD`, or `TIERED_BUNDLE` |
| `--bundle-names` | No | list | None | Bundle names for tiered pricing |

**Output Schema:**
```json
{
    "currentPricingPlan": {
        "billableEntityCount": "long",
        "bundleInformation": {},
        "effectiveDateTime": "timestamp",
        "pricingMode": "BASIC|STANDARD|TIERED_BUNDLE",
        "updateDateTime": "timestamp",
        "updateReason": "string"
    },
    "pendingPricingPlan": {}
}
```
