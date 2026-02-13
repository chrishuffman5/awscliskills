# Events & Tags

### 8.1 `create-event-subscription`

Creates a Neptune event notification subscription using SNS.

**Synopsis:**
```bash
aws neptune create-event-subscription \
    --subscription-name <value> \
    --sns-topic-arn <value> \
    [--source-type <value>] \
    [--event-categories <value>] \
    [--source-ids <value>] \
    [--enabled | --no-enabled] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--subscription-name` | **Yes** | string | -- | Subscription name |
| `--sns-topic-arn` | **Yes** | string | -- | SNS topic ARN |
| `--source-type` | No | string | -- | Source type: `db-instance`, `db-cluster`, `db-parameter-group`, `db-security-group`, `db-cluster-snapshot` |
| `--event-categories` | No | list(string) | All | Event categories to subscribe to |
| `--source-ids` | No | list(string) | All | Source identifiers to filter |
| `--enabled` | No | boolean | true | Enable the subscription |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "EventSubscription": {
        "CustomerAwsId": "string",
        "CustSubscriptionId": "string",
        "SnsTopicArn": "string",
        "Status": "creating",
        "SubscriptionCreationTime": "string",
        "SourceType": "string",
        "SourceIdsList": ["string"],
        "EventCategoriesList": ["string"],
        "Enabled": "boolean",
        "EventSubscriptionArn": "string"
    }
}
```

---

### 8.2 `modify-event-subscription`

Modifies a Neptune event notification subscription.

**Synopsis:**
```bash
aws neptune modify-event-subscription \
    --subscription-name <value> \
    [--sns-topic-arn <value>] \
    [--source-type <value>] \
    [--event-categories <value>] \
    [--enabled | --no-enabled] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--subscription-name` | **Yes** | string | -- | Subscription name |
| `--sns-topic-arn` | No | string | -- | New SNS topic ARN |
| `--source-type` | No | string | -- | Updated source type |
| `--event-categories` | No | list(string) | -- | Updated event categories |
| `--enabled` | No | boolean | -- | Enable or disable |

**Output Schema:**
```json
{
    "EventSubscription": {
        "CustSubscriptionId": "string",
        "SnsTopicArn": "string",
        "Status": "string",
        "SourceType": "string",
        "EventCategoriesList": ["string"],
        "Enabled": "boolean",
        "EventSubscriptionArn": "string"
    }
}
```

---

### 8.3 `delete-event-subscription`

Deletes a Neptune event notification subscription.

**Synopsis:**
```bash
aws neptune delete-event-subscription \
    --subscription-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--subscription-name` | **Yes** | string | -- | Subscription name |

**Output Schema:**
```json
{
    "EventSubscription": {
        "CustSubscriptionId": "string",
        "SnsTopicArn": "string",
        "Status": "deleting",
        "EventSubscriptionArn": "string"
    }
}
```

---

### 8.4 `describe-event-subscriptions`

Describes Neptune event notification subscriptions. **Paginated operation.**

**Synopsis:**
```bash
aws neptune describe-event-subscriptions \
    [--subscription-name <value>] \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--subscription-name` | No | string | -- | Specific subscription to describe |
| `--filters` | No | list | None | Filters |

**Output Schema:**
```json
{
    "EventSubscriptionsList": [
        {
            "CustomerAwsId": "string",
            "CustSubscriptionId": "string",
            "SnsTopicArn": "string",
            "Status": "string",
            "SourceType": "string",
            "SourceIdsList": ["string"],
            "EventCategoriesList": ["string"],
            "Enabled": "boolean",
            "EventSubscriptionArn": "string"
        }
    ]
}
```

---

### 8.5 `describe-events`

Describes Neptune events. **Paginated operation.**

**Synopsis:**
```bash
aws neptune describe-events \
    [--source-identifier <value>] \
    [--source-type <value>] \
    [--start-time <value>] \
    [--end-time <value>] \
    [--duration <value>] \
    [--event-categories <value>] \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-identifier` | No | string | -- | Source identifier |
| `--source-type` | No | string | -- | Source type |
| `--start-time` | No | timestamp | -- | Start time (ISO 8601) |
| `--end-time` | No | timestamp | -- | End time (ISO 8601) |
| `--duration` | No | integer | -- | Duration in minutes (past events) |
| `--event-categories` | No | list(string) | -- | Filter by event categories |

**Output Schema:**
```json
{
    "Events": [
        {
            "SourceIdentifier": "string",
            "SourceType": "string",
            "Message": "string",
            "EventCategories": ["string"],
            "Date": "timestamp",
            "SourceArn": "string"
        }
    ]
}
```

---

### 8.6 `describe-event-categories`

Lists all event categories for Neptune.

**Synopsis:**
```bash
aws neptune describe-event-categories \
    [--source-type <value>] \
    [--filters <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-type` | No | string | -- | Filter by source type |

**Output Schema:**
```json
{
    "EventCategoriesMapList": [
        {
            "SourceType": "string",
            "EventCategories": ["string"]
        }
    ]
}
```

---

### 8.7 `add-source-identifier-to-subscription`

Adds a source identifier to a Neptune event subscription.

**Synopsis:**
```bash
aws neptune add-source-identifier-to-subscription \
    --subscription-name <value> \
    --source-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--subscription-name` | **Yes** | string | -- | Subscription name |
| `--source-identifier` | **Yes** | string | -- | Source identifier to add |

**Output Schema:**
```json
{
    "EventSubscription": {
        "CustSubscriptionId": "string",
        "SourceIdsList": ["string"],
        "EventSubscriptionArn": "string"
    }
}
```

---

### 8.8 `remove-source-identifier-from-subscription`

Removes a source identifier from a Neptune event subscription.

**Synopsis:**
```bash
aws neptune remove-source-identifier-from-subscription \
    --subscription-name <value> \
    --source-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--subscription-name` | **Yes** | string | -- | Subscription name |
| `--source-identifier` | **Yes** | string | -- | Source identifier to remove |

**Output Schema:**
```json
{
    "EventSubscription": {
        "CustSubscriptionId": "string",
        "SourceIdsList": ["string"],
        "EventSubscriptionArn": "string"
    }
}
```

---

### 8.9 `add-tags-to-resource`

Adds tags to a Neptune resource.

**Synopsis:**
```bash
aws neptune add-tags-to-resource \
    --resource-name <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-name` | **Yes** | string | -- | ARN of the resource |
| `--tags` | **Yes** | list | -- | Tags. Shorthand: `Key=string,Value=string ...` |

**Output:** None

---

### 8.10 `remove-tags-from-resource`

Removes tags from a Neptune resource.

**Synopsis:**
```bash
aws neptune remove-tags-from-resource \
    --resource-name <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-name` | **Yes** | string | -- | ARN of the resource |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output:** None

---

### 8.11 `list-tags-for-resource`

Lists tags for a Neptune resource.

**Synopsis:**
```bash
aws neptune list-tags-for-resource \
    --resource-name <value> \
    [--filters <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-name` | **Yes** | string | -- | ARN of the resource |
| `--filters` | No | list | None | Filters |

**Output Schema:**
```json
{
    "TagList": [
        {
            "Key": "string",
            "Value": "string"
        }
    ]
}
```

---

### 8.12 `apply-pending-maintenance-action`

Applies a pending maintenance action to a Neptune resource.

**Synopsis:**
```bash
aws neptune apply-pending-maintenance-action \
    --resource-identifier <value> \
    --apply-action <value> \
    --opt-in-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-identifier` | **Yes** | string | -- | ARN of the resource |
| `--apply-action` | **Yes** | string | -- | Action (e.g., `system-update`, `db-upgrade`) |
| `--opt-in-type` | **Yes** | string | -- | `immediate`, `next-maintenance`, `undo-opt-in` |

**Output Schema:**
```json
{
    "ResourcePendingMaintenanceActions": {
        "ResourceIdentifier": "string",
        "PendingMaintenanceActionDetails": [
            {
                "Action": "string",
                "AutoAppliedAfterDate": "timestamp",
                "ForcedApplyDate": "timestamp",
                "OptInStatus": "string",
                "CurrentApplyDate": "timestamp",
                "Description": "string"
            }
        ]
    }
}
```

---

### 8.13 `describe-pending-maintenance-actions`

Lists pending maintenance actions for Neptune resources. **Paginated operation.**

**Synopsis:**
```bash
aws neptune describe-pending-maintenance-actions \
    [--resource-identifier <value>] \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-identifier` | No | string | -- | Filter by resource ARN |
| `--filters` | No | list | None | Filters |

**Output Schema:**
```json
{
    "PendingMaintenanceActions": [
        {
            "ResourceIdentifier": "string",
            "PendingMaintenanceActionDetails": [
                {
                    "Action": "string",
                    "AutoAppliedAfterDate": "timestamp",
                    "ForcedApplyDate": "timestamp",
                    "OptInStatus": "string",
                    "CurrentApplyDate": "timestamp",
                    "Description": "string"
                }
            ]
        }
    ]
}
```
