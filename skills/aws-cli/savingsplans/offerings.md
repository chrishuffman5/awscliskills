# Offerings

### 2.1 `describe-savings-plans-offerings`

Describes available Savings Plans offerings. Use this to browse and find offering IDs before purchasing.

**Synopsis:**
```bash
aws savingsplans describe-savings-plans-offerings \
    [--offering-ids <value>] \
    [--payment-options <value>] \
    [--product-type <value>] \
    [--plan-types <value>] \
    [--durations <value>] \
    [--currencies <value>] \
    [--descriptions <value>] \
    [--service-codes <value>] \
    [--usage-types <value>] \
    [--operations <value>] \
    [--filters <value>] \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--offering-ids` | No | list(string) | None | Specific offering IDs |
| `--payment-options` | No | list(string) | None | `All Upfront`, `Partial Upfront`, `No Upfront` |
| `--product-type` | No | string | None | `EC2`, `Fargate`, `Lambda`, `SageMaker`, `RDS`, `DSQL`, `DynamoDB`, `ElastiCache`, `DocDB`, `Neptune`, `Timestream`, `Keyspaces`, `DMS` |
| `--plan-types` | No | list(string) | None | `Compute`, `EC2Instance`, `SageMaker`, `Database` |
| `--durations` | No | list(long) | None | Duration in seconds (e.g., 31536000 for 1 year) |
| `--currencies` | No | list(string) | None | `CNY`, `USD`, `EUR` |
| `--descriptions` | No | list(string) | None | Description text filter |
| `--service-codes` | No | list(string) | None | AWS service codes |
| `--usage-types` | No | list(string) | None | Usage type from billing |
| `--operations` | No | list(string) | None | AWS operation from billing |
| `--filters` | No | list | None | Filters by `region` or `instanceFamily` |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (0-1000) |

**Output Schema:**
```json
{
    "searchResults": [
        {
            "offeringId": "string",
            "productTypes": ["string"],
            "planType": "Compute|EC2Instance|SageMaker|Database",
            "description": "string",
            "paymentOption": "All Upfront|Partial Upfront|No Upfront",
            "durationSeconds": "long",
            "currency": "CNY|USD|EUR",
            "serviceCode": "string",
            "usageType": "string",
            "operation": "string",
            "properties": [
                {
                    "name": "region|instanceFamily",
                    "value": "string"
                }
            ]
        }
    ],
    "nextToken": "string"
}
```

---

### 2.2 `describe-savings-plans-offering-rates`

Describes the rates for a specific Savings Plans offering.

**Synopsis:**
```bash
aws savingsplans describe-savings-plans-offering-rates \
    [--savings-plan-offering-ids <value>] \
    [--savings-plan-payment-options <value>] \
    [--savings-plan-types <value>] \
    [--products <value>] \
    [--service-codes <value>] \
    [--usage-types <value>] \
    [--operations <value>] \
    [--filters <value>] \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--savings-plan-offering-ids` | No | list(string) | None | Specific offering IDs |
| `--savings-plan-payment-options` | No | list(string) | None | `All Upfront`, `Partial Upfront`, `No Upfront` |
| `--savings-plan-types` | No | list(string) | None | `Compute`, `EC2Instance`, `SageMaker`, `Database` |
| `--products` | No | list(string) | None | Product types to filter |
| `--service-codes` | No | list(string) | None | AWS service codes |
| `--usage-types` | No | list(string) | None | Usage types |
| `--operations` | No | list(string) | None | Operations |
| `--filters` | No | list | None | Filters by `region`, `instanceFamily`, `instanceType`, `productDescription`, `tenancy`, `productId` |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (0-1000) |

**Output Schema:**
```json
{
    "searchResults": [
        {
            "savingsPlanOffering": {
                "offeringId": "string",
                "paymentOption": "All Upfront|Partial Upfront|No Upfront",
                "planType": "Compute|EC2Instance|SageMaker|Database",
                "durationSeconds": "long",
                "currency": "CNY|USD|EUR",
                "planDescription": "string"
            },
            "rate": "string",
            "unit": "Hrs|Lambda-GB-Second|Request",
            "productType": "string",
            "serviceCode": "string",
            "usageType": "string",
            "operation": "string",
            "properties": [
                {
                    "name": "string",
                    "value": "string"
                }
            ]
        }
    ],
    "nextToken": "string"
}
```
