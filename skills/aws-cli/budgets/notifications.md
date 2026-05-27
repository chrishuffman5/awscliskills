# Notifications

### 3.1 `create-notification`

Creates a notification on a budget. You can have up to 10 notifications per budget.

**Synopsis:**
```bash
aws budgets create-notification \
    --account-id <value> \
    --budget-name <value> \
    --notification <value> \
    --subscribers <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | 12-digit AWS account ID |
| `--budget-name` | **Yes** | string | -- | Budget name |
| `--notification` | **Yes** | structure | -- | Notification definition. Shorthand: `NotificationType=ACTUAL,ComparisonOperator=GREATER_THAN,Threshold=80,ThresholdType=PERCENTAGE` |
| `--subscribers` | **Yes** | list | -- | Subscribers (1-11). Shorthand: `SubscriptionType=EMAIL,Address=user@example.com` |

**Notification Structure:**
```json
{
    "NotificationType": "ACTUAL|FORECASTED",
    "ComparisonOperator": "GREATER_THAN|LESS_THAN|EQUAL_TO",
    "Threshold": "double",
    "ThresholdType": "PERCENTAGE|ABSOLUTE_VALUE",
    "NotificationState": "OK|ALARM"
}
```

**Output Schema:**
```json
{}
```

---

### 3.2 `delete-notification`

Deletes a notification from a budget. Deleting a notification also deletes its subscribers.

**Synopsis:**
```bash
aws budgets delete-notification \
    --account-id <value> \
    --budget-name <value> \
    --notification <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | 12-digit AWS account ID |
| `--budget-name` | **Yes** | string | -- | Budget name |
| `--notification` | **Yes** | structure | -- | Notification to delete (must match exactly) |

**Output Schema:**
```json
{}
```

---

### 3.3 `update-notification`

Updates a notification on a budget.

**Synopsis:**
```bash
aws budgets update-notification \
    --account-id <value> \
    --budget-name <value> \
    --old-notification <value> \
    --new-notification <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | 12-digit AWS account ID |
| `--budget-name` | **Yes** | string | -- | Budget name |
| `--old-notification` | **Yes** | structure | -- | Current notification to replace |
| `--new-notification` | **Yes** | structure | -- | Updated notification |

**Output Schema:**
```json
{}
```

---

### 3.4 `describe-notifications-for-budget`

Lists the notifications associated with a budget. **Paginated.**

**Synopsis:**
```bash
aws budgets describe-notifications-for-budget \
    --account-id <value> \
    --budget-name <value> \
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
| `--budget-name` | **Yes** | string | -- | Budget name |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Notifications": [
        {
            "NotificationType": "ACTUAL|FORECASTED",
            "ComparisonOperator": "GREATER_THAN|LESS_THAN|EQUAL_TO",
            "Threshold": "double",
            "ThresholdType": "PERCENTAGE|ABSOLUTE_VALUE",
            "NotificationState": "OK|ALARM"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.5 `describe-budget-notifications-for-account`

Lists all budget notifications across all budgets for an account. **Paginated.**

**Synopsis:**
```bash
aws budgets describe-budget-notifications-for-account \
    --account-id <value> \
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
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "BudgetNotificationsForAccount": [
        {
            "Notifications": [
                {
                    "NotificationType": "string",
                    "ComparisonOperator": "string",
                    "Threshold": "double",
                    "ThresholdType": "string",
                    "NotificationState": "string"
                }
            ],
            "BudgetName": "string"
        }
    ],
    "NextToken": "string"
}
```
