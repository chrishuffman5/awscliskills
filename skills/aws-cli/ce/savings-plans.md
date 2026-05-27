# Savings Plans

### 5.1 `get-savings-plans-coverage`

Retrieves how much of your cost is covered by Savings Plans.

**Synopsis:**
```bash
aws ce get-savings-plans-coverage \
    --time-period <value> \
    [--group-by <value>] \
    [--granularity <value>] \
    [--filter <value>] \
    [--metrics <value>] \
    [--next-token <value>] \
    [--max-results <value>] \
    [--sort-by <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--time-period` | **Yes** | structure | -- | Time range (max 13 months). Shorthand: `Start=YYYY-MM-DD,End=YYYY-MM-DD` |
| `--group-by` | No | list | None | Group by `INSTANCE_FAMILY`, `REGION`, or `SERVICE` |
| `--granularity` | No | string | None | `DAILY`, `MONTHLY`, or `HOURLY`. Cannot use with `--group-by` |
| `--filter` | No | structure | None | Filter by `LINKED_ACCOUNT`, `REGION`, `SERVICE`, `INSTANCE_FAMILY` |
| `--metrics` | No | list(string) | None | `SpendCoveredBySavingsPlans` |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | 20 | Max results (min 1) |
| `--sort-by` | No | structure | None | Sort key: `SpendCoveredBySavingsPlan`, `OnDemandCost`, `CoveragePercentage`, `TotalCost` |

**Output Schema:**
```json
{
    "SavingsPlansCoverages": [
        {
            "Attributes": {
                "string": "string"
            },
            "Coverage": {
                "SpendCoveredBySavingsPlans": "string",
                "OnDemandCost": "string",
                "TotalCost": "string",
                "CoveragePercentage": "string"
            },
            "TimePeriod": {
                "Start": "string",
                "End": "string"
            }
        }
    ],
    "NextToken": "string"
}
```

---

### 5.2 `get-savings-plans-purchase-recommendation`

Retrieves Savings Plans purchase recommendations.

**Synopsis:**
```bash
aws ce get-savings-plans-purchase-recommendation \
    --savings-plans-type <value> \
    --term-in-years <value> \
    --payment-option <value> \
    --lookback-period-in-days <value> \
    [--account-scope <value>] \
    [--filter <value>] \
    [--next-page-token <value>] \
    [--page-size <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--savings-plans-type` | **Yes** | string | -- | `COMPUTE_SP`, `EC2_INSTANCE_SP`, `SAGEMAKER_SP` |
| `--term-in-years` | **Yes** | string | -- | `ONE_YEAR` or `THREE_YEARS` |
| `--payment-option` | **Yes** | string | -- | `NO_UPFRONT`, `PARTIAL_UPFRONT`, `ALL_UPFRONT` |
| `--lookback-period-in-days` | **Yes** | string | -- | `SEVEN_DAYS`, `THIRTY_DAYS`, or `SIXTY_DAYS` |
| `--account-scope` | No | string | None | `PAYER` or `LINKED` |
| `--filter` | No | structure | None | Expression filter by `LINKED_ACCOUNT`, `REGION`, `INSTANCE_FAMILY` |
| `--next-page-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |

**Output Schema:**
```json
{
    "Metadata": {
        "RecommendationId": "string",
        "GenerationTimestamp": "string",
        "AdditionalMetadata": "string"
    },
    "SavingsPlansPurchaseRecommendation": {
        "AccountScope": "PAYER|LINKED",
        "SavingsPlansType": "COMPUTE_SP|EC2_INSTANCE_SP|SAGEMAKER_SP",
        "TermInYears": "ONE_YEAR|THREE_YEARS",
        "PaymentOption": "NO_UPFRONT|PARTIAL_UPFRONT|ALL_UPFRONT",
        "LookbackPeriodInDays": "SEVEN_DAYS|THIRTY_DAYS|SIXTY_DAYS",
        "SavingsPlansPurchaseRecommendationDetails": [
            {
                "SavingsPlansDetails": {
                    "Region": "string",
                    "InstanceFamily": "string",
                    "OfferingId": "string"
                },
                "AccountId": "string",
                "UpfrontCost": "string",
                "EstimatedROI": "string",
                "CurrencyCode": "string",
                "EstimatedSPCost": "string",
                "EstimatedOnDemandCost": "string",
                "EstimatedOnDemandCostWithCurrentCommitment": "string",
                "EstimatedSavingsAmount": "string",
                "EstimatedSavingsPercentage": "string",
                "HourlyCommitmentToPurchase": "string",
                "EstimatedAverageUtilization": "string",
                "CurrentMinimumHourlyOnDemandSpend": "string",
                "CurrentMaximumHourlyOnDemandSpend": "string",
                "CurrentAverageHourlyOnDemandSpend": "string",
                "RecommendationDetailId": "string"
            }
        ],
        "SavingsPlansPurchaseRecommendationSummary": {
            "EstimatedROI": "string",
            "CurrencyCode": "string",
            "EstimatedTotalCost": "string",
            "CurrentOnDemandSpend": "string",
            "EstimatedSavingsAmount": "string",
            "TotalRecommendationCount": "string",
            "DailyCommitmentToPurchase": "string",
            "HourlyCommitmentToPurchase": "string",
            "EstimatedSavingsPercentage": "string",
            "EstimatedMonthlySavingsAmount": "string",
            "EstimatedOnDemandCostWithCurrentCommitment": "string"
        }
    },
    "NextPageToken": "string"
}
```

---

### 5.3 `get-savings-plans-utilization`

Retrieves the Savings Plans utilization for your account.

**Synopsis:**
```bash
aws ce get-savings-plans-utilization \
    --time-period <value> \
    [--granularity <value>] \
    [--filter <value>] \
    [--sort-by <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--time-period` | **Yes** | structure | -- | Time range for utilization data |
| `--granularity` | No | string | None | `DAILY` or `MONTHLY` |
| `--filter` | No | structure | None | Expression filter |
| `--sort-by` | No | structure | None | Sort key and order |

**Output Schema:**
```json
{
    "SavingsPlansUtilizationsByTime": [
        {
            "TimePeriod": {
                "Start": "string",
                "End": "string"
            },
            "Utilization": {
                "TotalCommitment": "string",
                "UsedCommitment": "string",
                "UnusedCommitment": "string",
                "UtilizationPercentage": "string"
            },
            "Savings": {
                "NetSavings": "string",
                "OnDemandCostEquivalent": "string"
            },
            "AmortizedCommitment": {
                "AmortizedRecurringCommitment": "string",
                "AmortizedUpfrontCommitment": "string",
                "TotalAmortizedCommitment": "string"
            }
        }
    ],
    "Total": {
        "Utilization": {},
        "Savings": {},
        "AmortizedCommitment": {}
    }
}
```

---

### 5.4 `get-savings-plans-utilization-details`

Retrieves attribute information and detailed Savings Plans utilization at the member account level.

**Synopsis:**
```bash
aws ce get-savings-plans-utilization-details \
    --time-period <value> \
    [--filter <value>] \
    [--data-type <value>] \
    [--sort-by <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--time-period` | **Yes** | structure | -- | Time range |
| `--filter` | No | structure | None | Expression filter |
| `--data-type` | No | list(string) | None | `ATTRIBUTES`, `UTILIZATION`, `AMORTIZED_COMMITMENT`, `SAVINGS` |
| `--sort-by` | No | structure | None | Sort key and order |
| `--max-results` | No | integer | None | Max results |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "SavingsPlansUtilizationDetails": [
        {
            "SavingsPlanArn": "string",
            "Attributes": {
                "string": "string"
            },
            "Utilization": {
                "TotalCommitment": "string",
                "UsedCommitment": "string",
                "UnusedCommitment": "string",
                "UtilizationPercentage": "string"
            },
            "Savings": {
                "NetSavings": "string",
                "OnDemandCostEquivalent": "string"
            },
            "AmortizedCommitment": {
                "AmortizedRecurringCommitment": "string",
                "AmortizedUpfrontCommitment": "string",
                "TotalAmortizedCommitment": "string"
            }
        }
    ],
    "Total": {},
    "TimePeriod": {
        "Start": "string",
        "End": "string"
    },
    "NextToken": "string"
}
```

---

### 5.5 `get-savings-plan-purchase-recommendation-details`

Retrieves details for a specific Savings Plans purchase recommendation.

**Synopsis:**
```bash
aws ce get-savings-plan-purchase-recommendation-details \
    --recommendation-detail-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--recommendation-detail-id` | **Yes** | string | -- | ID of the recommendation detail |

**Output Schema:**
```json
{
    "RecommendationDetailId": "string",
    "RecommendationDetailData": {
        "AccountScope": "PAYER|LINKED",
        "LookbackPeriodInDays": "SEVEN_DAYS|THIRTY_DAYS|SIXTY_DAYS",
        "SavingsPlansType": "COMPUTE_SP|EC2_INSTANCE_SP|SAGEMAKER_SP",
        "TermInYears": "ONE_YEAR|THREE_YEARS",
        "PaymentOption": "string",
        "AccountId": "string",
        "CurrencyCode": "string",
        "InstanceFamily": "string",
        "Region": "string",
        "OfferingId": "string",
        "GenerationTimestamp": "string",
        "LatestUsageTimestamp": "string",
        "CurrentAverageHourlyOnDemandSpend": "string",
        "CurrentMaximumHourlyOnDemandSpend": "string",
        "CurrentMinimumHourlyOnDemandSpend": "string",
        "EstimatedAverageUtilization": "string",
        "EstimatedMonthlySavingsAmount": "string",
        "EstimatedOnDemandCost": "string",
        "EstimatedOnDemandCostWithCurrentCommitment": "string",
        "EstimatedROI": "string",
        "EstimatedSPCost": "string",
        "EstimatedSavingsAmount": "string",
        "EstimatedSavingsPercentage": "string",
        "ExistingHourlyCommitment": "string",
        "HourlyCommitmentToPurchase": "string",
        "UpfrontCost": "string",
        "CurrentAverageCoverage": "string",
        "EstimatedAverageCoverage": "string",
        "MetricsOverLookbackPeriod": [
            {
                "StartTime": "string",
                "EstimatedOnDemandCost": "string",
                "CurrentCoverage": "string",
                "EstimatedCoverage": "string",
                "EstimatedNewCommitmentUtilization": "string"
            }
        ]
    }
}
```

---

### 5.6 `list-savings-plans-purchase-recommendation-generation`

Lists Savings Plans recommendation generation jobs. **Paginated.**

**Synopsis:**
```bash
aws ce list-savings-plans-purchase-recommendation-generation \
    [--generation-status <value>] \
    [--recommendation-ids <value>] \
    [--page-size <value>] \
    [--next-page-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--generation-status` | No | string | None | `SUCCEEDED`, `PROCESSING`, or `FAILED` |
| `--recommendation-ids` | No | list(string) | None | Specific recommendation IDs |
| `--page-size` | No | integer | None | Items per page |
| `--next-page-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "GenerationSummaryList": [
        {
            "RecommendationId": "string",
            "GenerationStatus": "SUCCEEDED|PROCESSING|FAILED",
            "GenerationStartedTime": "string",
            "GenerationCompletionTime": "string",
            "EstimatedCompletionTime": "string"
        }
    ],
    "NextPageToken": "string"
}
```

---

### 5.7 `start-savings-plans-purchase-recommendation-generation`

Starts a Savings Plans purchase recommendation generation job.

**Synopsis:**
```bash
aws ce start-savings-plans-purchase-recommendation-generation \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| (none) | -- | -- | -- | No command-specific parameters |

**Output Schema:**
```json
{
    "RecommendationId": "string",
    "GenerationStartedTime": "string",
    "EstimatedCompletionTime": "string"
}
```
