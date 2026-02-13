# Budgets

### 1.1 `create-budget`

Creates a new budget. You can create budgets for cost, usage, RI utilization/coverage, or Savings Plans utilization/coverage.

**Synopsis:**
```bash
aws budgets create-budget \
    --account-id <value> \
    --budget <value> \
    [--notifications-with-subscribers <value>] \
    [--resource-tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | 12-digit AWS account ID |
| `--budget` | **Yes** | structure | -- | Budget object (JSON or `file://`). See structure below |
| `--notifications-with-subscribers` | No | list | None | Up to 10 notifications with subscribers |
| `--resource-tags` | No | list | None | Tags (max 200) |

**Budget Structure:**
```json
{
    "BudgetName": "string",
    "BudgetType": "COST|USAGE|RI_UTILIZATION|RI_COVERAGE|SAVINGS_PLANS_UTILIZATION|SAVINGS_PLANS_COVERAGE",
    "TimeUnit": "DAILY|MONTHLY|QUARTERLY|ANNUALLY|CUSTOM",
    "BudgetLimit": {
        "Amount": "string",
        "Unit": "string"
    },
    "TimePeriod": {
        "Start": "timestamp",
        "End": "timestamp"
    },
    "CostFilters": {
        "string": ["string"]
    },
    "CostTypes": {
        "IncludeTax": true,
        "IncludeSubscription": true,
        "UseBlended": false,
        "IncludeRefund": true,
        "IncludeCredit": true,
        "IncludeUpfront": true,
        "IncludeRecurring": true,
        "IncludeOtherSubscription": true,
        "IncludeSupport": true,
        "IncludeDiscount": true,
        "UseAmortized": false
    },
    "AutoAdjustData": {
        "AutoAdjustType": "HISTORICAL|FORECAST",
        "HistoricalOptions": {
            "BudgetAdjustmentPeriod": "integer"
        }
    }
}
```

**Notification Structure:**
```json
[
    {
        "Notification": {
            "NotificationType": "ACTUAL|FORECASTED",
            "ComparisonOperator": "GREATER_THAN|LESS_THAN|EQUAL_TO",
            "Threshold": "double",
            "ThresholdType": "PERCENTAGE|ABSOLUTE_VALUE"
        },
        "Subscribers": [
            {
                "SubscriptionType": "SNS|EMAIL",
                "Address": "string"
            }
        ]
    }
]
```

**Output Schema:**
```json
{}
```

---

### 1.2 `delete-budget`

Deletes a budget and all related notifications and subscribers.

**Synopsis:**
```bash
aws budgets delete-budget \
    --account-id <value> \
    --budget-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | 12-digit AWS account ID |
| `--budget-name` | **Yes** | string | -- | Name of the budget to delete |

**Output Schema:**
```json
{}
```

---

### 1.3 `describe-budget`

Describes a single budget for an account.

**Synopsis:**
```bash
aws budgets describe-budget \
    --account-id <value> \
    --budget-name <value> \
    [--show-filter-expression | --no-show-filter-expression] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | 12-digit AWS account ID |
| `--budget-name` | **Yes** | string | -- | Name of the budget |
| `--show-filter-expression` | No | boolean | false | Include filter expression in response |

**Output Schema:**
```json
{
    "Budget": {
        "BudgetName": "string",
        "BudgetType": "COST|USAGE|RI_UTILIZATION|RI_COVERAGE|SAVINGS_PLANS_UTILIZATION|SAVINGS_PLANS_COVERAGE",
        "TimeUnit": "DAILY|MONTHLY|QUARTERLY|ANNUALLY|CUSTOM",
        "BudgetLimit": {
            "Amount": "string",
            "Unit": "string"
        },
        "PlannedBudgetLimits": {},
        "CostFilters": {},
        "CostTypes": {
            "IncludeTax": "boolean",
            "IncludeSubscription": "boolean",
            "UseBlended": "boolean",
            "IncludeRefund": "boolean",
            "IncludeCredit": "boolean",
            "IncludeUpfront": "boolean",
            "IncludeRecurring": "boolean",
            "IncludeOtherSubscription": "boolean",
            "IncludeSupport": "boolean",
            "IncludeDiscount": "boolean",
            "UseAmortized": "boolean"
        },
        "TimePeriod": {
            "Start": "timestamp",
            "End": "timestamp"
        },
        "CalculatedSpend": {
            "ActualSpend": {
                "Amount": "string",
                "Unit": "string"
            },
            "ForecastedSpend": {
                "Amount": "string",
                "Unit": "string"
            }
        },
        "LastUpdatedTime": "timestamp",
        "AutoAdjustData": {
            "AutoAdjustType": "HISTORICAL|FORECAST",
            "HistoricalOptions": {
                "BudgetAdjustmentPeriod": "integer",
                "LookBackAvailablePeriods": "integer"
            },
            "LastAutoAdjustTime": "timestamp"
        },
        "FilterExpression": {},
        "Metrics": ["string"],
        "BillingViewArn": "string",
        "HealthStatus": {
            "Status": "HEALTHY|UNHEALTHY",
            "StatusReason": "string"
        }
    }
}
```

---

### 1.4 `describe-budgets`

Lists all budgets for an account. **Paginated.**

**Synopsis:**
```bash
aws budgets describe-budgets \
    --account-id <value> \
    [--show-filter-expression | --no-show-filter-expression] \
    [--cli-input-json | --cli-input-yaml] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | 12-digit AWS account ID |
| `--show-filter-expression` | No | boolean | false | Include filter expressions |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call (max 100) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Budgets": [
        {
            "BudgetName": "string",
            "BudgetType": "string",
            "TimeUnit": "string",
            "BudgetLimit": {},
            "CostFilters": {},
            "CostTypes": {},
            "TimePeriod": {},
            "CalculatedSpend": {},
            "LastUpdatedTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.5 `update-budget`

Updates an existing budget. You must provide the entire budget object.

**Synopsis:**
```bash
aws budgets update-budget \
    --account-id <value> \
    --new-budget <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | 12-digit AWS account ID |
| `--new-budget` | **Yes** | structure | -- | Complete updated budget object |

**Output Schema:**
```json
{}
```

---

### 1.6 `describe-budget-performance-history`

Describes the history of a budget's performance against its cost or usage amount. **Paginated.**

**Synopsis:**
```bash
aws budgets describe-budget-performance-history \
    --account-id <value> \
    --budget-name <value> \
    [--time-period <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | 12-digit AWS account ID |
| `--budget-name` | **Yes** | string | -- | Name of the budget |
| `--time-period` | No | structure | None | Filter by time range. Shorthand: `Start=timestamp,End=timestamp` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "BudgetPerformanceHistory": {
        "BudgetName": "string",
        "BudgetType": "string",
        "CostFilters": {},
        "CostTypes": {},
        "TimeUnit": "string",
        "BudgetedAndActualAmountsList": [
            {
                "BudgetedAmount": {
                    "Amount": "string",
                    "Unit": "string"
                },
                "ActualAmount": {
                    "Amount": "string",
                    "Unit": "string"
                },
                "TimePeriod": {
                    "Start": "timestamp",
                    "End": "timestamp"
                }
            }
        ]
    },
    "NextToken": "string"
}
```
