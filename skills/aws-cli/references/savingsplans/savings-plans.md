# Savings Plans

### 1.1 `create-savings-plan`

Purchases a Savings Plan with the specified offering and commitment.

**Synopsis:**
```bash
aws savingsplans create-savings-plan \
    --savings-plan-offering-id <value> \
    --commitment <value> \
    [--upfront-payment-amount <value>] \
    [--purchase-time <value>] \
    [--client-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--savings-plan-offering-id` | **Yes** | string | -- | ID of the offering to purchase |
| `--commitment` | **Yes** | string | -- | Hourly commitment amount (0.001-1000000, max 5 decimal places) |
| `--upfront-payment-amount` | No | string | None | Upfront payment (50-99% of total). Only for Partial Upfront |
| `--purchase-time` | No | timestamp | None | Future purchase time (UTC: `YYYY-MM-DDTHH:MM:SSZ`) |
| `--client-token` | No | string | None | Idempotency token |
| `--tags` | No | map | None | Key-value tags. Shorthand: `KeyName1=string,KeyName2=string` |

**Output Schema:**
```json
{
    "savingsPlanId": "string"
}
```

---

### 1.2 `delete-queued-savings-plan`

Deletes a Savings Plan that is in the `queued` state (not yet active).

**Synopsis:**
```bash
aws savingsplans delete-queued-savings-plan \
    --savings-plan-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--savings-plan-id` | **Yes** | string | -- | ID of the queued Savings Plan to delete |

**Output Schema:**
```json
{}
```

---

### 1.3 `describe-savings-plans`

Describes your Savings Plans with optional filtering by state, ARN, or ID.

**Synopsis:**
```bash
aws savingsplans describe-savings-plans \
    [--savings-plan-arns <value>] \
    [--savings-plan-ids <value>] \
    [--states <value>] \
    [--filters <value>] \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--savings-plan-arns` | No | list(string) | None | Specific plan ARNs (max 100) |
| `--savings-plan-ids` | No | list(string) | None | Specific plan IDs |
| `--states` | No | list(string) | None | Filter by state: `payment-pending`, `payment-failed`, `active`, `retired`, `queued`, `queued-deleted`, `pending-return`, `returned` |
| `--filters` | No | list | None | Filters by `region`, `ec2-instance-family`, `commitment`, `upfront`, `term`, `savings-plan-type`, `payment-option`, `start`, `end` |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-1000) |

**Output Schema:**
```json
{
    "savingsPlans": [
        {
            "offeringId": "string",
            "savingsPlanId": "string",
            "savingsPlanArn": "string",
            "description": "string",
            "start": "string",
            "end": "string",
            "state": "payment-pending|payment-failed|active|retired|queued|queued-deleted|pending-return|returned",
            "region": "string",
            "ec2InstanceFamily": "string",
            "savingsPlanType": "Compute|EC2Instance|SageMaker|Database",
            "paymentOption": "All Upfront|Partial Upfront|No Upfront",
            "productTypes": ["string"],
            "currency": "CNY|USD|EUR",
            "commitment": "string",
            "upfrontPaymentAmount": "string",
            "recurringPaymentAmount": "string",
            "termDurationInSeconds": "long",
            "tags": {
                "string": "string"
            },
            "returnableUntil": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 1.4 `describe-savings-plan-rates`

Describes the rates for a specific Savings Plan.

**Synopsis:**
```bash
aws savingsplans describe-savings-plan-rates \
    --savings-plan-id <value> \
    [--filters <value>] \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--savings-plan-id` | **Yes** | string | -- | ID of the Savings Plan |
| `--filters` | No | list | None | Filters by `region`, `instanceType`, `productDescription`, `tenancy`, `productType`, `serviceCode`, `usageType`, `operation` |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-1000) |

**Output Schema:**
```json
{
    "savingsPlanId": "string",
    "searchResults": [
        {
            "rate": "string",
            "currency": "CNY|USD|EUR",
            "unit": "Hrs|Lambda-GB-Second|Request",
            "productType": "EC2|Fargate|Lambda|SageMaker|RDS|DSQL|DynamoDB|ElastiCache|DocDB|Neptune|Timestream|Keyspaces|DMS",
            "serviceCode": "string",
            "usageType": "string",
            "operation": "string",
            "properties": [
                {
                    "name": "region|instanceType|instanceFamily",
                    "value": "string"
                }
            ]
        }
    ],
    "nextToken": "string"
}
```

---

### 1.5 `return-savings-plan`

Returns a Savings Plan within the return window (typically 7 days after purchase).

**Synopsis:**
```bash
aws savingsplans return-savings-plan \
    --savings-plan-id <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--savings-plan-id` | **Yes** | string | -- | ID of the Savings Plan to return |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "savingsPlanId": "string"
}
```
