# Events

### 10.1 `create-event-subscription`

Creates a DMS event notification subscription.

**Synopsis:**
```bash
aws dms create-event-subscription \
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
| `--subscription-name` | **Yes** | string | -- | Subscription name (max 255 chars) |
| `--sns-topic-arn` | **Yes** | string | -- | SNS topic ARN for notifications |
| `--source-type` | No | string | -- | Source type: `replication-instance` or `replication-task` |
| `--event-categories` | No | list(string) | -- | Event categories to subscribe to |
| `--source-ids` | No | list(string) | -- | Source identifiers to filter |
| `--enabled` | No | boolean | true | Activate the subscription |
| `--tags` | No | list | -- | Tags |

**Output Schema:**
```json
{
    "EventSubscription": {
        "CustomerAwsId": "string",
        "CustSubscriptionId": "string",
        "SnsTopicArn": "string",
        "Status": "creating|modifying|deleting|active|no-permission|topic-not-exist",
        "SubscriptionCreationTime": "string",
        "SourceType": "string",
        "SourceIdsList": ["string"],
        "EventCategoriesList": ["string"],
        "Enabled": "boolean"
    }
}
```

---

### 10.2 `delete-event-subscription`

Deletes a DMS event subscription.

**Synopsis:**
```bash
aws dms delete-event-subscription \
    --subscription-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--subscription-name` | **Yes** | string | -- | Name of the subscription to delete |

**Output Schema:** Same as `create-event-subscription`.

---

### 10.3 `describe-event-subscriptions`

Lists all the event subscriptions for an account. **Paginated operation.**

**Synopsis:**
```bash
aws dms describe-event-subscriptions \
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
| `--subscription-name` | No | string | -- | Specific subscription name |
| `--filters` | No | list | -- | Filters: `event-subscription-arn` |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "Marker": "string",
    "EventSubscriptionsList": [
        {
            "CustomerAwsId": "string",
            "CustSubscriptionId": "string",
            "SnsTopicArn": "string",
            "Status": "string",
            "SubscriptionCreationTime": "string",
            "SourceType": "string",
            "SourceIdsList": ["string"],
            "EventCategoriesList": ["string"],
            "Enabled": "boolean"
        }
    ]
}
```

---

### 10.4 `modify-event-subscription`

Modifies an existing DMS event notification subscription.

**Synopsis:**
```bash
aws dms modify-event-subscription \
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
| `--source-type` | No | string | -- | New source type |
| `--event-categories` | No | list(string) | -- | New event categories |
| `--enabled` | No | boolean | -- | Enable/disable subscription |

**Output Schema:** Same as `create-event-subscription`.

---

### 10.5 `describe-event-categories`

Lists categories for all event source types, or for a specified source type.

**Synopsis:**
```bash
aws dms describe-event-categories \
    [--source-type <value>] \
    [--filters <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-type` | No | string | -- | Source type to filter by |
| `--filters` | No | list | -- | Filters: `source-type` |

**Output Schema:**
```json
{
    "EventCategoryGroupList": [
        {
            "SourceType": "string",
            "EventCategories": ["string"]
        }
    ]
}
```

---

### 10.6 `describe-events`

Lists events for a given source identifier and source type. **Paginated operation.**

**Synopsis:**
```bash
aws dms describe-events \
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
| `--source-identifier` | No | string | -- | Source identifier (instance or task ID) |
| `--source-type` | No | string | -- | `replication-instance` or `replication-task` |
| `--start-time` | No | timestamp | -- | Start time for events |
| `--end-time` | No | timestamp | -- | End time for events |
| `--duration` | No | integer | -- | Duration in minutes (alternative to start/end time) |
| `--event-categories` | No | list(string) | -- | Filter by event categories |
| `--filters` | No | list | -- | Filters: `event-source-arn` |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "Marker": "string",
    "Events": [
        {
            "SourceIdentifier": "string",
            "SourceType": "replication-instance|replication-task",
            "Message": "string",
            "EventCategories": ["string"],
            "Date": "timestamp"
        }
    ]
}
```

---

### 10.7 `update-subscriptions-to-event-bridge`

Migrates DMS subscriptions to EventBridge.

**Synopsis:**
```bash
aws dms update-subscriptions-to-event-bridge \
    [--force-move | --no-force-move] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--force-move` | No | boolean | false | Force migration even if some subscriptions cannot be moved |

**Output Schema:**
```json
{
    "Result": "string"
}
```
