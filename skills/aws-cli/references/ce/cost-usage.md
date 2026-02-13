# Cost & Usage

### 1.1 `get-cost-and-usage`

Retrieves cost and usage metrics for your account. You can filter and group results by dimensions, tags, or cost categories.

**Synopsis:**
```bash
aws ce get-cost-and-usage \
    --time-period <value> \
    --granularity <value> \
    --metrics <value> \
    [--filter <value>] \
    [--group-by <value>] \
    [--billing-view-arn <value>] \
    [--next-page-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--time-period` | **Yes** | structure | -- | Start (inclusive) and end (exclusive) dates. Shorthand: `Start=YYYY-MM-DD,End=YYYY-MM-DD` |
| `--granularity` | **Yes** | string | -- | `DAILY`, `MONTHLY`, or `HOURLY` |
| `--metrics` | **Yes** | list(string) | -- | Metrics to return: `AmortizedCost`, `BlendedCost`, `NetAmortizedCost`, `NetUnblendedCost`, `NormalizedUsageAmount`, `UnblendedCost`, `UsageQuantity` |
| `--filter` | No | structure | None | Expression to filter by dimensions, tags, or cost categories. Supports `And`/`Or`/`Not` |
| `--group-by` | No | list | None | Group by up to 2 groups. Shorthand: `Type=DIMENSION,Key=SERVICE` |
| `--billing-view-arn` | No | string | None | ARN of a specific billing view |
| `--next-page-token` | No | string | None | Pagination token from previous response |

**Output Schema:**
```json
{
    "NextPageToken": "string",
    "GroupDefinitions": [
        {
            "Type": "DIMENSION|TAG|COST_CATEGORY",
            "Key": "string"
        }
    ],
    "ResultsByTime": [
        {
            "TimePeriod": {
                "Start": "string",
                "End": "string"
            },
            "Total": {
                "MetricName": {
                    "Amount": "string",
                    "Unit": "string"
                }
            },
            "Groups": [
                {
                    "Keys": ["string"],
                    "Metrics": {
                        "MetricName": {
                            "Amount": "string",
                            "Unit": "string"
                        }
                    }
                }
            ],
            "Estimated": "boolean"
        }
    ],
    "DimensionValueAttributes": [
        {
            "Value": "string",
            "Attributes": {
                "string": "string"
            }
        }
    ]
}
```

---

### 1.2 `get-cost-and-usage-with-resources`

Retrieves cost and usage metrics with resource-level detail. Limited to the last 14 days and requires filtering by `RESOURCE_ID` or `SERVICE`.

**Synopsis:**
```bash
aws ce get-cost-and-usage-with-resources \
    --time-period <value> \
    --granularity <value> \
    --filter <value> \
    [--metrics <value>] \
    [--group-by <value>] \
    [--billing-view-arn <value>] \
    [--next-page-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--time-period` | **Yes** | structure | -- | Time range within last 14 days. Shorthand: `Start=YYYY-MM-DD,End=YYYY-MM-DD` |
| `--granularity` | **Yes** | string | -- | `DAILY`, `MONTHLY`, or `HOURLY` (hourly only for EC2) |
| `--filter` | **Yes** | structure | -- | Must filter by `RESOURCE_ID` or include `SERVICE` dimension |
| `--metrics` | No | list(string) | None | Metrics: `AmortizedCost`, `BlendedCost`, `NetAmortizedCost`, `NetUnblendedCost`, `NormalizedUsageAmount`, `UnblendedCost`, `UsageQuantity` |
| `--group-by` | No | list | None | Group by up to 2 groups |
| `--billing-view-arn` | No | string | None | ARN of a specific billing view |
| `--next-page-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "NextPageToken": "string",
    "GroupDefinitions": [
        {
            "Type": "DIMENSION|TAG|COST_CATEGORY",
            "Key": "string"
        }
    ],
    "ResultsByTime": [
        {
            "TimePeriod": {
                "Start": "string",
                "End": "string"
            },
            "Total": {
                "MetricName": {
                    "Amount": "string",
                    "Unit": "string"
                }
            },
            "Groups": [
                {
                    "Keys": ["string"],
                    "Metrics": {
                        "MetricName": {
                            "Amount": "string",
                            "Unit": "string"
                        }
                    }
                }
            ],
            "Estimated": "boolean"
        }
    ],
    "DimensionValueAttributes": [
        {
            "Value": "string",
            "Attributes": {
                "string": "string"
            }
        }
    ]
}
```

---

### 1.3 `get-cost-and-usage-comparisons`

Compares cost and usage across two time periods.

**Synopsis:**
```bash
aws ce get-cost-and-usage-comparisons \
    --time-period <value> \
    --comparison-time-period <value> \
    --granularity <value> \
    --metrics <value> \
    [--filter <value>] \
    [--group-by <value>] \
    [--billing-view-arn <value>] \
    [--next-page-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--time-period` | **Yes** | structure | -- | Base time period. Shorthand: `Start=YYYY-MM-DD,End=YYYY-MM-DD` |
| `--comparison-time-period` | **Yes** | structure | -- | Time period to compare against |
| `--granularity` | **Yes** | string | -- | `DAILY` or `MONTHLY` |
| `--metrics` | **Yes** | string | -- | Metric for comparison |
| `--filter` | No | structure | None | Expression filter |
| `--group-by` | No | list | None | Group by dimensions, tags, or cost categories |
| `--billing-view-arn` | No | string | None | ARN of billing view |
| `--next-page-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Maximum results to return |

**Output Schema:**
```json
{
    "NextPageToken": "string",
    "CostAndUsageComparisons": [
        {
            "TimePeriod": {
                "Start": "string",
                "End": "string"
            },
            "BaselineMetricValue": {
                "Amount": "string",
                "Unit": "string"
            },
            "ComparisonMetricValue": {
                "Amount": "string",
                "Unit": "string"
            },
            "Difference": {
                "Amount": "string",
                "Unit": "string"
            },
            "Keys": ["string"]
        }
    ]
}
```

---

### 1.4 `get-cost-comparison-drivers`

Identifies the main drivers of cost differences between two time periods.

**Synopsis:**
```bash
aws ce get-cost-comparison-drivers \
    --time-period <value> \
    --comparison-time-period <value> \
    --metrics <value> \
    [--filter <value>] \
    [--billing-view-arn <value>] \
    [--next-page-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--time-period` | **Yes** | structure | -- | Base time period |
| `--comparison-time-period` | **Yes** | structure | -- | Comparison time period |
| `--metrics` | **Yes** | string | -- | Cost metric to analyze |
| `--filter` | No | structure | None | Expression filter |
| `--billing-view-arn` | No | string | None | ARN of billing view |
| `--next-page-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Maximum results to return |

**Output Schema:**
```json
{
    "NextPageToken": "string",
    "Drivers": [
        {
            "Service": "string",
            "Region": "string",
            "UsageType": "string",
            "Operation": "string",
            "BaselineSpend": {
                "Amount": "string",
                "Unit": "string"
            },
            "ComparisonSpend": {
                "Amount": "string",
                "Unit": "string"
            },
            "Difference": {
                "Amount": "string",
                "Unit": "string"
            }
        }
    ]
}
```

---

### 1.5 `get-cost-forecast`

Retrieves a forecast for how much AWS predicts you will spend over a forecast period based on historical costs.

**Synopsis:**
```bash
aws ce get-cost-forecast \
    --time-period <value> \
    --metric <value> \
    --granularity <value> \
    [--filter <value>] \
    [--billing-view-arn <value>] \
    [--prediction-interval-level <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--time-period` | **Yes** | structure | -- | Forecast period. Start must be today or later |
| `--metric` | **Yes** | string | -- | `BLENDED_COST`, `UNBLENDED_COST`, `AMORTIZED_COST`, `NET_UNBLENDED_COST`, `NET_AMORTIZED_COST`, `USAGE_QUANTITY`, `NORMALIZED_USAGE_AMOUNT` |
| `--granularity` | **Yes** | string | -- | `DAILY` (up to 3 months) or `MONTHLY` (up to 18 months) |
| `--filter` | No | structure | None | Expression filter by dimensions, tags, or cost categories |
| `--billing-view-arn` | No | string | None | ARN of billing view |
| `--prediction-interval-level` | No | integer | None | Confidence level 51-99. Higher = wider prediction interval |

**Output Schema:**
```json
{
    "Total": {
        "Amount": "string",
        "Unit": "string"
    },
    "ForecastResultsByTime": [
        {
            "TimePeriod": {
                "Start": "string",
                "End": "string"
            },
            "MeanValue": "string",
            "PredictionIntervalLowerBound": "string",
            "PredictionIntervalUpperBound": "string"
        }
    ]
}
```

---

### 1.6 `get-usage-forecast`

Retrieves a forecast for how much AWS predicts you will use over a forecast period based on historical usage.

**Synopsis:**
```bash
aws ce get-usage-forecast \
    --time-period <value> \
    --metric <value> \
    --granularity <value> \
    [--filter <value>] \
    [--billing-view-arn <value>] \
    [--prediction-interval-level <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--time-period` | **Yes** | structure | -- | Forecast period. Start must be today or later |
| `--metric` | **Yes** | string | -- | `USAGE_QUANTITY` or `NORMALIZED_USAGE_AMOUNT` |
| `--granularity` | **Yes** | string | -- | `DAILY` (up to 3 months) or `MONTHLY` (up to 18 months) |
| `--filter` | No | structure | None | Expression filter |
| `--billing-view-arn` | No | string | None | ARN of billing view |
| `--prediction-interval-level` | No | integer | None | Confidence level 51-99 |

**Output Schema:**
```json
{
    "Total": {
        "Amount": "string",
        "Unit": "string"
    },
    "ForecastResultsByTime": [
        {
            "TimePeriod": {
                "Start": "string",
                "End": "string"
            },
            "MeanValue": "string",
            "PredictionIntervalLowerBound": "string",
            "PredictionIntervalUpperBound": "string"
        }
    ]
}
```

---

### 1.7 `get-dimension-values`

Retrieves all available filter values for a specified dimension over a time period. You can search values with an arbitrary string.

**Synopsis:**
```bash
aws ce get-dimension-values \
    --time-period <value> \
    --dimension <value> \
    [--search-string <value>] \
    [--context <value>] \
    [--filter <value>] \
    [--sort-by <value>] \
    [--billing-view-arn <value>] \
    [--max-results <value>] \
    [--next-page-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--time-period` | **Yes** | structure | -- | Start/end dates for retrieving dimension values |
| `--dimension` | **Yes** | string | -- | Dimension name (e.g., `SERVICE`, `REGION`, `LINKED_ACCOUNT`, `INSTANCE_TYPE`) |
| `--search-string` | No | string | None | String to search within dimension values (max 1024) |
| `--context` | No | string | `COST_AND_USAGE` | `COST_AND_USAGE`, `RESERVATIONS`, or `SAVINGS_PLANS` |
| `--filter` | No | structure | None | Expression filter |
| `--sort-by` | No | list | None | Sort by metric key and order (`ASCENDING`/`DESCENDING`) |
| `--billing-view-arn` | No | string | None | ARN of billing view |
| `--max-results` | No | integer | 1000 | Max objects returned (min 1, max 1000) |
| `--next-page-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "DimensionValues": [
        {
            "Value": "string",
            "Attributes": {
                "string": "string"
            }
        }
    ],
    "ReturnSize": "integer",
    "TotalSize": "integer",
    "NextPageToken": "string"
}
```

---

### 1.8 `get-tags`

Queries for available tag keys and tag values for a specified time period.

**Synopsis:**
```bash
aws ce get-tags \
    --time-period <value> \
    [--search-string <value>] \
    [--tag-key <value>] \
    [--filter <value>] \
    [--sort-by <value>] \
    [--billing-view-arn <value>] \
    [--max-results <value>] \
    [--next-page-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--time-period` | **Yes** | structure | -- | Start/end dates for retrieving tag values |
| `--search-string` | No | string | None | String to search tag values (max 1024) |
| `--tag-key` | No | string | None | Specific tag key to return values for (max 1024) |
| `--filter` | No | structure | None | Expression filter |
| `--sort-by` | No | list | None | Sort by metric key and order. Cannot use with pagination or search |
| `--billing-view-arn` | No | string | None | ARN of billing view |
| `--max-results` | No | integer | 1000 | Max results (only with `--sort-by`) |
| `--next-page-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "NextPageToken": "string",
    "Tags": ["string"],
    "ReturnSize": "integer",
    "TotalSize": "integer"
}
```

---

### 1.9 `get-approximate-usage-records`

Retrieves the approximate count of usage records for a given time period and granularity.

**Synopsis:**
```bash
aws ce get-approximate-usage-records \
    --granularity <value> \
    --approximation-dimension <value> \
    [--services <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--granularity` | **Yes** | string | -- | `DAILY` or `MONTHLY` |
| `--approximation-dimension` | **Yes** | string | -- | `SERVICE` or `RESOURCE` |
| `--services` | No | list(string) | None | Specific services to include |

**Output Schema:**
```json
{
    "Services": {
        "string": "long"
    },
    "TotalRecords": "long",
    "LookbackPeriod": {
        "Start": "string",
        "End": "string"
    }
}
```
