# Subscribers

### 4.1 `create-subscriber`

Creates a subscriber for a budget notification. You can have up to 11 subscribers per notification.

**Synopsis:**
```bash
aws budgets create-subscriber \
    --account-id <value> \
    --budget-name <value> \
    --notification <value> \
    --subscriber <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | 12-digit AWS account ID |
| `--budget-name` | **Yes** | string | -- | Budget name |
| `--notification` | **Yes** | structure | -- | Notification to add subscriber to |
| `--subscriber` | **Yes** | structure | -- | Subscriber to add. Shorthand: `SubscriptionType=EMAIL,Address=user@example.com` |

**Subscriber Structure:**
```json
{
    "SubscriptionType": "SNS|EMAIL",
    "Address": "string"
}
```

**Output Schema:**
```json
{}
```

---

### 4.2 `delete-subscriber`

Removes a subscriber from a budget notification.

**Synopsis:**
```bash
aws budgets delete-subscriber \
    --account-id <value> \
    --budget-name <value> \
    --notification <value> \
    --subscriber <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | 12-digit AWS account ID |
| `--budget-name` | **Yes** | string | -- | Budget name |
| `--notification` | **Yes** | structure | -- | Notification the subscriber belongs to |
| `--subscriber` | **Yes** | structure | -- | Subscriber to remove |

**Output Schema:**
```json
{}
```

---

### 4.3 `update-subscriber`

Replaces a subscriber on a budget notification.

**Synopsis:**
```bash
aws budgets update-subscriber \
    --account-id <value> \
    --budget-name <value> \
    --notification <value> \
    --old-subscriber <value> \
    --new-subscriber <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | 12-digit AWS account ID |
| `--budget-name` | **Yes** | string | -- | Budget name |
| `--notification` | **Yes** | structure | -- | Notification the subscriber belongs to |
| `--old-subscriber` | **Yes** | structure | -- | Current subscriber to replace |
| `--new-subscriber` | **Yes** | structure | -- | Replacement subscriber |

**Output Schema:**
```json
{}
```

---

### 4.4 `describe-subscribers-for-notification`

Lists the subscribers associated with a budget notification. **Paginated.**

**Synopsis:**
```bash
aws budgets describe-subscribers-for-notification \
    --account-id <value> \
    --budget-name <value> \
    --notification <value> \
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
| `--notification` | **Yes** | structure | -- | Notification to list subscribers for |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Subscribers": [
        {
            "SubscriptionType": "SNS|EMAIL",
            "Address": "string"
        }
    ],
    "NextToken": "string"
}
```
