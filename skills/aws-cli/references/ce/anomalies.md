# Anomalies

### 3.1 `create-anomaly-monitor`

Creates a new cost anomaly detection monitor.

**Synopsis:**
```bash
aws ce create-anomaly-monitor \
    --anomaly-monitor <value> \
    [--resource-tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--anomaly-monitor` | **Yes** | structure | -- | Monitor definition with name, type, and optional specification |
| `--resource-tags` | No | list | None | Tags for IAM access control (max 50) |

**AnomalyMonitor Structure:**
```json
{
    "MonitorName": "string",
    "MonitorType": "DIMENSIONAL|CUSTOM",
    "MonitorDimension": "SERVICE|LINKED_ACCOUNT|TAG|COST_CATEGORY",
    "MonitorSpecification": {
        "Dimensions": {
            "Key": "string",
            "Values": ["string"]
        }
    }
}
```

- `DIMENSIONAL` monitors are AWS-managed and require `MonitorDimension`
- `CUSTOM` monitors require `MonitorSpecification` with an expression filter
- For `TAG` or `COST_CATEGORY` dimensions, `MonitorSpecification` is also required

**Output Schema:**
```json
{
    "MonitorArn": "string"
}
```

---

### 3.2 `delete-anomaly-monitor`

Deletes a cost anomaly monitor.

**Synopsis:**
```bash
aws ce delete-anomaly-monitor \
    --monitor-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--monitor-arn` | **Yes** | string | -- | ARN of the monitor to delete |

**Output Schema:**
```json
{}
```

---

### 3.3 `get-anomaly-monitors`

Retrieves cost anomaly monitors with optional filtering.

**Synopsis:**
```bash
aws ce get-anomaly-monitors \
    [--monitor-arn-list <value>] \
    [--next-page-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--monitor-arn-list` | No | list(string) | None | Specific monitor ARNs to retrieve |
| `--next-page-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results to return |

**Output Schema:**
```json
{
    "AnomalyMonitors": [
        {
            "MonitorArn": "string",
            "MonitorName": "string",
            "CreationDate": "string",
            "LastUpdatedDate": "string",
            "LastEvaluatedDate": "string",
            "MonitorType": "DIMENSIONAL|CUSTOM",
            "MonitorDimension": "SERVICE|LINKED_ACCOUNT|TAG|COST_CATEGORY",
            "MonitorSpecification": {},
            "DimensionalValueCount": "integer"
        }
    ],
    "NextPageToken": "string"
}
```

---

### 3.4 `update-anomaly-monitor`

Updates an existing anomaly monitor name or specification.

**Synopsis:**
```bash
aws ce update-anomaly-monitor \
    --monitor-arn <value> \
    [--monitor-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--monitor-arn` | **Yes** | string | -- | ARN of the monitor to update |
| `--monitor-name` | No | string | None | New name for the monitor |

**Output Schema:**
```json
{
    "MonitorArn": "string"
}
```

---

### 3.5 `create-anomaly-subscription`

Creates a notification subscription for anomaly alerts.

**Synopsis:**
```bash
aws ce create-anomaly-subscription \
    --anomaly-subscription <value> \
    [--resource-tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--anomaly-subscription` | **Yes** | structure | -- | Subscription definition |
| `--resource-tags` | No | list | None | Tags for IAM access control (max 50) |

**AnomalySubscription Structure:**
```json
{
    "SubscriptionName": "string",
    "MonitorArnList": ["string"],
    "Subscribers": [
        {
            "Address": "string",
            "Type": "EMAIL|SNS",
            "Status": "CONFIRMED|DECLINED"
        }
    ],
    "Frequency": "DAILY|IMMEDIATE|WEEKLY",
    "ThresholdExpression": {
        "Dimensions": {
            "Key": "ANOMALY_TOTAL_IMPACT_ABSOLUTE|ANOMALY_TOTAL_IMPACT_PERCENTAGE",
            "MatchOptions": ["GREATER_THAN_OR_EQUAL"],
            "Values": ["100"]
        }
    }
}
```

**Output Schema:**
```json
{
    "SubscriptionArn": "string"
}
```

---

### 3.6 `delete-anomaly-subscription`

Deletes an anomaly subscription.

**Synopsis:**
```bash
aws ce delete-anomaly-subscription \
    --subscription-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--subscription-arn` | **Yes** | string | -- | ARN of the subscription to delete |

**Output Schema:**
```json
{}
```

---

### 3.7 `get-anomaly-subscriptions`

Retrieves anomaly subscriptions with optional filtering.

**Synopsis:**
```bash
aws ce get-anomaly-subscriptions \
    [--subscription-arn-list <value>] \
    [--monitor-arn <value>] \
    [--next-page-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--subscription-arn-list` | No | list(string) | None | Specific subscription ARNs |
| `--monitor-arn` | No | string | None | Filter by monitor ARN |
| `--next-page-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results |

**Output Schema:**
```json
{
    "AnomalySubscriptions": [
        {
            "SubscriptionArn": "string",
            "AccountId": "string",
            "MonitorArnList": ["string"],
            "Subscribers": [
                {
                    "Address": "string",
                    "Type": "EMAIL|SNS",
                    "Status": "CONFIRMED|DECLINED"
                }
            ],
            "Frequency": "DAILY|IMMEDIATE|WEEKLY",
            "SubscriptionName": "string",
            "ThresholdExpression": {}
        }
    ],
    "NextPageToken": "string"
}
```

---

### 3.8 `update-anomaly-subscription`

Updates an existing anomaly subscription.

**Synopsis:**
```bash
aws ce update-anomaly-subscription \
    --subscription-arn <value> \
    [--subscription-name <value>] \
    [--monitor-arn-list <value>] \
    [--subscribers <value>] \
    [--frequency <value>] \
    [--threshold-expression <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--subscription-arn` | **Yes** | string | -- | ARN of the subscription to update |
| `--subscription-name` | No | string | None | Updated name |
| `--monitor-arn-list` | No | list(string) | None | Updated monitor ARN list |
| `--subscribers` | No | list | None | Updated subscriber list |
| `--frequency` | No | string | None | `DAILY`, `IMMEDIATE`, or `WEEKLY` |
| `--threshold-expression` | No | structure | None | Updated threshold expression |

**Output Schema:**
```json
{
    "SubscriptionArn": "string"
}
```

---

### 3.9 `get-anomalies`

Retrieves cost anomalies with optional filtering by monitor, date, feedback, or impact. **Paginated.**

**Synopsis:**
```bash
aws ce get-anomalies \
    --date-interval <value> \
    [--monitor-arn <value>] \
    [--feedback <value>] \
    [--total-impact <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--date-interval` | **Yes** | structure | -- | Date range. Shorthand: `StartDate=YYYY-MM-DD,EndDate=YYYY-MM-DD` |
| `--monitor-arn` | No | string | None | Filter by specific monitor ARN |
| `--feedback` | No | string | None | `YES`, `NO`, or `PLANNED_ACTIVITY` |
| `--total-impact` | No | structure | None | Filter by impact. Shorthand: `NumericOperator=GREATER_THAN,StartValue=100` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**TotalImpact Structure:**
```json
{
    "NumericOperator": "EQUAL|GREATER_THAN_OR_EQUAL|LESS_THAN_OR_EQUAL|GREATER_THAN|LESS_THAN|BETWEEN",
    "StartValue": "double",
    "EndValue": "double"
}
```

**Output Schema:**
```json
{
    "Anomalies": [
        {
            "AnomalyId": "string",
            "AnomalyStartDate": "string",
            "AnomalyEndDate": "string",
            "DimensionValue": "string",
            "RootCauses": [
                {
                    "Service": "string",
                    "Region": "string",
                    "LinkedAccount": "string",
                    "LinkedAccountName": "string",
                    "UsageType": "string"
                }
            ],
            "AnomalyScore": {
                "MaxScore": "double",
                "CurrentScore": "double"
            },
            "Impact": {
                "MaxImpact": "double",
                "TotalImpact": "double",
                "TotalActualSpend": "double",
                "TotalExpectedSpend": "double",
                "TotalImpactPercentage": "double"
            },
            "MonitorArn": "string",
            "Feedback": "YES|NO|PLANNED_ACTIVITY"
        }
    ],
    "NextPageToken": "string"
}
```

---

### 3.10 `provide-anomaly-feedback`

Provides feedback on a detected anomaly to improve future detection accuracy.

**Synopsis:**
```bash
aws ce provide-anomaly-feedback \
    --anomaly-id <value> \
    --feedback <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--anomaly-id` | **Yes** | string | -- | ID of the anomaly |
| `--feedback` | **Yes** | string | -- | `YES` (expected), `NO` (unexpected), or `PLANNED_ACTIVITY` |

**Output Schema:**
```json
{
    "AnomalyId": "string"
}
```
