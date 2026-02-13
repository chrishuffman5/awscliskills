# Event Subscriptions

### 7.1 `create-event-subscription`

Creates an RDS event subscription using SNS.

```bash
aws rds create-event-subscription \
    --subscription-name <value> \
    --sns-topic-arn <value> \
    [--source-type <value>] \
    [--event-categories <value>] \
    [--source-ids <value>] \
    [--enabled | --no-enabled] \
    [--tags <value>]
```

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--subscription-name` | **Yes** | string | -- | Subscription name (1-255 chars) |
| `--sns-topic-arn` | **Yes** | string | -- | SNS topic ARN |
| `--source-type` | No | string | all | `db-instance`, `db-cluster`, `db-parameter-group`, `db-security-group`, `db-snapshot`, `db-cluster-snapshot` |
| `--event-categories` | No | list | all | Event categories to subscribe to |
| `--source-ids` | No | list | all | Source identifiers to monitor |
| `--enabled` / `--no-enabled` | No | boolean | true | Enable the subscription |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "EventSubscription": {
        "CustomerAwsId": "string",
        "CustSubscriptionId": "string",
        "SnsTopicArn": "string",
        "Status": "string",
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

### 7.2 `delete-event-subscription`

Deletes an event subscription.

```bash
aws rds delete-event-subscription \
    --subscription-name <value>
```

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--subscription-name` | **Yes** | string | Subscription name |

**Output Schema:** Same `EventSubscription` structure.

---

### 7.3 `describe-event-subscriptions`

Describes event subscriptions. **Paginated.**

```bash
aws rds describe-event-subscriptions \
    [--subscription-name <value>] \
    [--filters <value>] \
    [--max-items <value>] \
    [--starting-token <value>]
```

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--subscription-name` | No | string | all | Specific subscription |
| `--filters` | No | list | None | Filters |

**Output Schema:**
```json
{
    "EventSubscriptionsList": [
        { "...same EventSubscription structure..." }
    ],
    "Marker": "string"
}
```

---

### 7.4 `modify-event-subscription`

Modifies an event subscription.

```bash
aws rds modify-event-subscription \
    --subscription-name <value> \
    [--sns-topic-arn <value>] \
    [--source-type <value>] \
    [--event-categories <value>] \
    [--enabled | --no-enabled]
```

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--subscription-name` | **Yes** | string | -- | Subscription name |
| `--sns-topic-arn` | No | string | no change | SNS topic ARN |
| `--source-type` | No | string | no change | Source type |
| `--event-categories` | No | list | no change | Event categories |
| `--enabled` / `--no-enabled` | No | boolean | no change | Enable/disable |

**Output Schema:** Same `EventSubscription` structure.

---

### 7.5 `describe-events`

Lists RDS events for the past 14 days. **Paginated.**

```bash
aws rds describe-events \
    [--source-identifier <value>] \
    [--source-type <value>] \
    [--start-time <value>] \
    [--end-time <value>] \
    [--duration <value>] \
    [--event-categories <value>] \
    [--filters <value>] \
    [--max-items <value>] \
    [--starting-token <value>]
```

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-identifier` | No | string | all | Source identifier |
| `--source-type` | No | string | all | `db-instance`, `db-cluster`, `db-parameter-group`, `db-security-group`, `db-snapshot`, `db-cluster-snapshot` |
| `--start-time` | No | timestamp | None | Start of time range |
| `--end-time` | No | timestamp | None | End of time range |
| `--duration` | No | integer | None | Minutes to retrieve events for |
| `--event-categories` | No | list | all | Filter by categories |

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
    ],
    "Marker": "string"
}
```

---

### 7.6 `describe-event-categories`

Lists all event categories for a source type.

```bash
aws rds describe-event-categories \
    [--source-type <value>] \
    [--filters <value>]
```

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-type` | No | string | all | Source type filter |

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
