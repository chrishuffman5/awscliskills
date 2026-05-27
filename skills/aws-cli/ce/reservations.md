# Reservations

### 4.1 `get-reservation-coverage`

Retrieves the reservation coverage for your account, showing how much of your usage is covered by reservations.

**Synopsis:**
```bash
aws ce get-reservation-coverage \
    --time-period <value> \
    [--group-by <value>] \
    [--granularity <value>] \
    [--filter <value>] \
    [--metrics <value>] \
    [--next-page-token <value>] \
    [--sort-by <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--time-period` | **Yes** | structure | -- | Time range (max 13 months). Shorthand: `Start=YYYY-MM-DD,End=YYYY-MM-DD` |
| `--group-by` | No | list | None | Group by `AZ`, `CACHE_ENGINE`, `DATABASE_ENGINE`, `DEPLOYMENT_OPTION`, `INSTANCE_TYPE`, `INVOICING_ENTITY`, `LINKED_ACCOUNT`, `OPERATING_SYSTEM`, `PLATFORM`, `REGION`, `TENANCY` |
| `--granularity` | No | string | None | `DAILY`, `MONTHLY`, or `HOURLY`. Cannot use with `--group-by` |
| `--filter` | No | structure | None | Expression filter |
| `--metrics` | No | list(string) | None | `Hour`, `Unit`, `Cost` |
| `--next-page-token` | No | string | None | Pagination token |
| `--sort-by` | No | structure | None | Sort key and order. Keys: `OnDemandCost`, `CoverageHoursPercentage`, `OnDemandHours`, `ReservedHours`, `TotalRunningHours`, `Time` |
| `--max-results` | No | integer | None | Max results (min 1) |

**Output Schema:**
```json
{
    "CoveragesByTime": [
        {
            "TimePeriod": {
                "Start": "string",
                "End": "string"
            },
            "Groups": [
                {
                    "Attributes": {
                        "string": "string"
                    },
                    "Coverage": {
                        "CoverageHours": {
                            "OnDemandHours": "string",
                            "ReservedHours": "string",
                            "TotalRunningHours": "string",
                            "CoverageHoursPercentage": "string"
                        },
                        "CoverageNormalizedUnits": {
                            "OnDemandNormalizedUnits": "string",
                            "ReservedNormalizedUnits": "string",
                            "TotalRunningNormalizedUnits": "string",
                            "CoverageNormalizedUnitsPercentage": "string"
                        },
                        "CoverageCost": {
                            "OnDemandCost": "string"
                        }
                    }
                }
            ],
            "Total": {
                "CoverageHours": {},
                "CoverageNormalizedUnits": {},
                "CoverageCost": {}
            }
        }
    ],
    "Total": {
        "CoverageHours": {
            "OnDemandHours": "string",
            "ReservedHours": "string",
            "TotalRunningHours": "string",
            "CoverageHoursPercentage": "string"
        },
        "CoverageNormalizedUnits": {
            "OnDemandNormalizedUnits": "string",
            "ReservedNormalizedUnits": "string",
            "TotalRunningNormalizedUnits": "string",
            "CoverageNormalizedUnitsPercentage": "string"
        },
        "CoverageCost": {
            "OnDemandCost": "string"
        }
    },
    "NextPageToken": "string"
}
```

---

### 4.2 `get-reservation-purchase-recommendation`

Gets recommendations for Reserved Instance purchases based on your usage.

**Synopsis:**
```bash
aws ce get-reservation-purchase-recommendation \
    --service <value> \
    [--account-id <value>] \
    [--account-scope <value>] \
    [--lookback-period-in-days <value>] \
    [--term-in-years <value>] \
    [--payment-option <value>] \
    [--service-specification <value>] \
    [--filter <value>] \
    [--page-size <value>] \
    [--next-page-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service` | **Yes** | string | -- | Service for recommendations (e.g., `Amazon Elastic Compute Cloud - Compute`, `Amazon RDS`, `Amazon ElastiCache`, `Amazon Redshift`, `Amazon OpenSearch Service`) |
| `--account-id` | No | string | None | Specific account ID for linked account recommendations |
| `--account-scope` | No | string | None | `PAYER` or `LINKED` |
| `--lookback-period-in-days` | No | string | None | `SEVEN_DAYS`, `THIRTY_DAYS`, or `SIXTY_DAYS` |
| `--term-in-years` | No | string | None | `ONE_YEAR` or `THREE_YEARS` |
| `--payment-option` | No | string | None | `NO_UPFRONT`, `PARTIAL_UPFRONT`, `ALL_UPFRONT`, `LIGHT_UTILIZATION`, `MEDIUM_UTILIZATION`, `HEAVY_UTILIZATION` |
| `--service-specification` | No | structure | None | EC2-specific configuration |
| `--filter` | No | structure | None | Expression filter |
| `--page-size` | No | integer | None | Items per page |
| `--next-page-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "Metadata": {
        "RecommendationId": "string",
        "GenerationTimestamp": "string"
    },
    "Recommendations": [
        {
            "AccountScope": "PAYER|LINKED",
            "LookbackPeriodInDays": "SEVEN_DAYS|THIRTY_DAYS|SIXTY_DAYS",
            "TermInYears": "ONE_YEAR|THREE_YEARS",
            "PaymentOption": "string",
            "ServiceSpecification": {},
            "RecommendationDetails": [
                {
                    "AccountId": "string",
                    "InstanceDetails": {},
                    "RecommendedNumberOfInstancesToPurchase": "string",
                    "RecommendedNormalizedUnitsToPurchase": "string",
                    "MinimumNumberOfInstancesUsedPerHour": "string",
                    "MaximumNumberOfInstancesUsedPerHour": "string",
                    "AverageNumberOfInstancesUsedPerHour": "string",
                    "MinimumNormalizedUnitsUsedPerHour": "string",
                    "MaximumNormalizedUnitsUsedPerHour": "string",
                    "AverageNormalizedUnitsUsedPerHour": "string",
                    "AverageUtilization": "string",
                    "EstimatedBreakEvenInMonths": "string",
                    "CurrencyCode": "string",
                    "EstimatedMonthlySavingsAmount": "string",
                    "EstimatedMonthlySavingsPercentage": "string",
                    "EstimatedMonthlyOnDemandCost": "string",
                    "EstimatedReservationCostForLookbackPeriod": "string",
                    "UpfrontCost": "string",
                    "RecurringStandardMonthlyCost": "string"
                }
            ],
            "RecommendationSummary": {
                "TotalEstimatedMonthlySavingsAmount": "string",
                "TotalEstimatedMonthlySavingsPercentage": "string",
                "CurrencyCode": "string"
            }
        }
    ],
    "NextPageToken": "string"
}
```

---

### 4.3 `get-reservation-utilization`

Retrieves the reservation utilization for your account, showing how much of your reservations are being used.

**Synopsis:**
```bash
aws ce get-reservation-utilization \
    --time-period <value> \
    [--group-by <value>] \
    [--granularity <value>] \
    [--filter <value>] \
    [--next-page-token <value>] \
    [--sort-by <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--time-period` | **Yes** | structure | -- | Time range (max 13 months) |
| `--group-by` | No | list | None | Group by `SUBSCRIPTION_ID`, `INSTANCE_TYPE`, `LINKED_ACCOUNT`, `PLATFORM`, `REGION`, `TENANCY`, `AZ` |
| `--granularity` | No | string | None | `DAILY` or `MONTHLY` |
| `--filter` | No | structure | None | Expression filter |
| `--next-page-token` | No | string | None | Pagination token |
| `--sort-by` | No | structure | None | Sort key and order |
| `--max-results` | No | integer | None | Max results |

**Output Schema:**
```json
{
    "UtilizationsByTime": [
        {
            "TimePeriod": {
                "Start": "string",
                "End": "string"
            },
            "Groups": [
                {
                    "Key": "string",
                    "Value": "string",
                    "Attributes": {
                        "string": "string"
                    },
                    "Utilization": {
                        "UtilizationPercentage": "string",
                        "UtilizationPercentageInUnits": "string",
                        "PurchasedHours": "string",
                        "PurchasedUnits": "string",
                        "TotalActualHours": "string",
                        "TotalActualUnits": "string",
                        "UnusedHours": "string",
                        "UnusedUnits": "string",
                        "OnDemandCostOfRIHoursUsed": "string",
                        "NetRISavings": "string",
                        "TotalPotentialRISavings": "string",
                        "AmortizedUpfrontFee": "string",
                        "AmortizedRecurringFee": "string",
                        "TotalAmortizedFee": "string",
                        "RICostForUnusedHours": "string",
                        "RealizedSavings": "string",
                        "UnrealizedSavings": "string"
                    }
                }
            ],
            "Total": {}
        }
    ],
    "Total": {
        "UtilizationPercentage": "string",
        "PurchasedHours": "string",
        "TotalActualHours": "string",
        "UnusedHours": "string",
        "OnDemandCostOfRIHoursUsed": "string",
        "NetRISavings": "string",
        "TotalPotentialRISavings": "string",
        "AmortizedUpfrontFee": "string",
        "AmortizedRecurringFee": "string",
        "TotalAmortizedFee": "string"
    },
    "NextPageToken": "string"
}
```
