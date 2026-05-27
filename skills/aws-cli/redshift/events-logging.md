# Events & Logging

### 7.1 `create-event-subscription`

Creates an event notification subscription.

**Synopsis:**
```bash
aws redshift create-event-subscription \
    --subscription-name <value> \
    --sns-topic-arn <value> \
    [--source-type <value>] \
    [--source-ids <value>] \
    [--event-categories <value>] \
    [--severity <value>] \
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
| `--source-type` | No | string | -- | Source type: `cluster`, `cluster-parameter-group`, `cluster-security-group`, `cluster-snapshot`, `scheduled-action` |
| `--source-ids` | No | list(string) | -- | Source identifiers to filter |
| `--event-categories` | No | list(string) | -- | Event categories to filter (e.g., `configuration`, `management`, `monitoring`, `security`, `pending`) |
| `--severity` | No | string | -- | Severity: `ERROR`, `INFO` |
| `--enabled` | No | boolean | true | Whether the subscription is enabled |
| `--tags` | No | list | -- | Tags |

**Output Schema:**
```json
{
    "EventSubscription": {
        "CustomerAwsId": "string",
        "CustSubscriptionId": "string",
        "SnsTopicArn": "string",
        "Status": "active|no-permission|topic-not-exist",
        "SubscriptionCreationTime": "timestamp",
        "SourceType": "string",
        "SourceIdsList": ["string"],
        "EventCategoriesList": ["string"],
        "Severity": "string",
        "Enabled": "boolean",
        "Tags": [{"Key": "string", "Value": "string"}]
    }
}
```

---

### 7.2 `delete-event-subscription`

Deletes an event notification subscription.

**Synopsis:**
```bash
aws redshift delete-event-subscription \
    --subscription-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--subscription-name` | **Yes** | string | -- | Subscription to delete |

No output on success.

---

### 7.3 `describe-event-subscriptions`

Lists event notification subscriptions. **Paginated operation.**

**Synopsis:**
```bash
aws redshift describe-event-subscriptions \
    [--subscription-name <value>] \
    [--tag-keys <value>] \
    [--tag-values <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--subscription-name` | No | string | -- | Specific subscription |
| `--tag-keys` | No | list(string) | -- | Filter by tag keys |
| `--tag-values` | No | list(string) | -- | Filter by tag values |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "EventSubscriptionsList": [
        {
            "CustomerAwsId": "string",
            "CustSubscriptionId": "string",
            "SnsTopicArn": "string",
            "Status": "string",
            "SubscriptionCreationTime": "timestamp",
            "SourceType": "string",
            "SourceIdsList": ["string"],
            "EventCategoriesList": ["string"],
            "Severity": "string",
            "Enabled": "boolean",
            "Tags": []
        }
    ],
    "Marker": "string"
}
```

---

### 7.4 `modify-event-subscription`

Modifies an event notification subscription.

**Synopsis:**
```bash
aws redshift modify-event-subscription \
    --subscription-name <value> \
    [--sns-topic-arn <value>] \
    [--source-type <value>] \
    [--source-ids <value>] \
    [--event-categories <value>] \
    [--severity <value>] \
    [--enabled | --no-enabled] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--subscription-name` | **Yes** | string | -- | Subscription to modify |
| `--sns-topic-arn` | No | string | -- | New SNS topic ARN |
| `--source-type` | No | string | -- | New source type |
| `--source-ids` | No | list(string) | -- | New source IDs |
| `--event-categories` | No | list(string) | -- | New event categories |
| `--severity` | No | string | -- | New severity filter |
| `--enabled` | No | boolean | -- | Enable or disable |

**Output Schema:**
```json
{
    "EventSubscription": {
        "CustSubscriptionId": "string",
        "SnsTopicArn": "string",
        "Status": "string",
        "SourceType": "string",
        "SourceIdsList": ["string"],
        "EventCategoriesList": ["string"],
        "Severity": "string",
        "Enabled": "boolean"
    }
}
```

---

### 7.5 `describe-events`

Returns events related to clusters, security groups, snapshots, and parameter groups. **Paginated operation.**

**Synopsis:**
```bash
aws redshift describe-events \
    [--source-identifier <value>] \
    [--source-type <value>] \
    [--start-time <value>] \
    [--end-time <value>] \
    [--duration <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-identifier` | No | string | -- | Source identifier (cluster name, etc.) |
| `--source-type` | No | string | -- | Source type: `cluster`, `cluster-parameter-group`, `cluster-security-group`, `cluster-snapshot`, `scheduled-action` |
| `--start-time` | No | timestamp | -- | Start of the time range |
| `--end-time` | No | timestamp | -- | End of the time range |
| `--duration` | No | integer | -- | Duration in minutes (alternative to start/end) |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "Events": [
        {
            "SourceIdentifier": "string",
            "SourceType": "cluster|cluster-parameter-group|cluster-security-group|cluster-snapshot|scheduled-action",
            "Message": "string",
            "EventCategories": ["string"],
            "Severity": "ERROR|INFO",
            "Date": "timestamp",
            "EventId": "string"
        }
    ],
    "Marker": "string"
}
```

---

### 7.6 `describe-event-categories`

Returns information about event categories for a given source type.

**Synopsis:**
```bash
aws redshift describe-event-categories \
    [--source-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-type` | No | string | -- | Source type filter |

**Output Schema:**
```json
{
    "EventCategoriesMapList": [
        {
            "SourceType": "string",
            "Events": [
                {
                    "EventId": "string",
                    "EventCategories": ["string"],
                    "EventDescription": "string",
                    "Severity": "string"
                }
            ]
        }
    ]
}
```

---

### 7.7 `enable-logging`

Starts logging audit information to Amazon S3 or CloudWatch Logs.

**Synopsis:**
```bash
aws redshift enable-logging \
    --cluster-identifier <value> \
    [--bucket-name <value>] \
    [--s3-key-prefix <value>] \
    [--log-destination-type <value>] \
    [--log-exports <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-identifier` | **Yes** | string | -- | Cluster to enable logging for |
| `--bucket-name` | No | string | -- | S3 bucket name for log delivery |
| `--s3-key-prefix` | No | string | -- | S3 key prefix for log files |
| `--log-destination-type` | No | string | -- | Destination: `s3`, `cloudwatch` |
| `--log-exports` | No | list(string) | -- | Log types: `connectionlog`, `useractivitylog`, `userlog` |

**Output Schema:**
```json
{
    "LoggingEnabled": "boolean",
    "BucketName": "string",
    "S3KeyPrefix": "string",
    "LastSuccessfulDeliveryTime": "timestamp",
    "LastFailureTime": "timestamp",
    "LastFailureMessage": "string",
    "LogDestinationType": "s3|cloudwatch",
    "LogExports": ["string"]
}
```

---

### 7.8 `disable-logging`

Stops audit logging for a cluster.

**Synopsis:**
```bash
aws redshift disable-logging \
    --cluster-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-identifier` | **Yes** | string | -- | Cluster to disable logging for |

**Output Schema:**
```json
{
    "LoggingEnabled": false,
    "BucketName": "string",
    "S3KeyPrefix": "string"
}
```

---

### 7.9 `describe-logging-status`

Returns the logging status of a cluster.

**Synopsis:**
```bash
aws redshift describe-logging-status \
    --cluster-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--cluster-identifier` | **Yes** | string | -- | Cluster to describe logging for |

**Output Schema:**
```json
{
    "LoggingEnabled": "boolean",
    "BucketName": "string",
    "S3KeyPrefix": "string",
    "LastSuccessfulDeliveryTime": "timestamp",
    "LastFailureTime": "timestamp",
    "LastFailureMessage": "string",
    "LogDestinationType": "s3|cloudwatch",
    "LogExports": ["string"]
}
```
