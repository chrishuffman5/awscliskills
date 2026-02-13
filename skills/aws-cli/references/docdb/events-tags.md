# Events & Tags

## Events

### 7.1 `describe-events`

Returns events related to instances, clusters, security groups, and parameter groups. **Paginated operation.**

**Synopsis:**
```bash
aws docdb describe-events \
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
| `--source-identifier` | No | string | All | Identifier of the source resource |
| `--source-type` | No | string | All | Source type: `db-instance`, `db-cluster`, `db-parameter-group`, `db-security-group`, `db-cluster-snapshot` |
| `--start-time` | No | timestamp | None | Start of the time range |
| `--end-time` | No | timestamp | None | End of the time range |
| `--duration` | No | integer | None | Duration in minutes (alternative to start/end time) |
| `--event-categories` | No | list(string) | All | Event categories to filter by |
| `--filters` | No | list | None | Filters |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

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

### 7.2 `describe-event-categories`

Displays a list of categories for all event source types, or for a specified source type.

**Synopsis:**
```bash
aws docdb describe-event-categories \
    [--source-type <value>] \
    [--filters <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-type` | No | string | All | Source type to filter |
| `--filters` | No | list | None | Filters |

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

### 7.3 `create-event-subscription`

Creates an event notification subscription. Events matching the subscription are published to an SNS topic.

**Synopsis:**
```bash
aws docdb create-event-subscription \
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
| `--source-type` | No | string | All | Source type to filter |
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
        "Status": "string",
        "SubscriptionCreationTime": "string",
        "SourceType": "string",
        "SourceIdsList": ["string"],
        "EventCategoriesList": ["string"],
        "Enabled": true|false,
        "EventSubscriptionArn": "string"
    }
}
```

---

### 7.4 `delete-event-subscription`

Deletes an event notification subscription.

**Synopsis:**
```bash
aws docdb delete-event-subscription \
    --subscription-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--subscription-name` | **Yes** | string | -- | Subscription name to delete |

**Output Schema:** Same as `create-event-subscription` output.

---

### 7.5 `describe-event-subscriptions`

Lists all event notification subscriptions. **Paginated operation.**

**Synopsis:**
```bash
aws docdb describe-event-subscriptions \
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
| `--subscription-name` | No | string | All | Subscription name |
| `--filters` | No | list | None | Filters |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

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
            "EventCategoriesList": ["string"],
            "Enabled": true|false,
            "EventSubscriptionArn": "string"
        }
    ],
    "Marker": "string"
}
```

---

### 7.6 `modify-event-subscription`

Modifies an event notification subscription.

**Synopsis:**
```bash
aws docdb modify-event-subscription \
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
| `--subscription-name` | **Yes** | string | -- | Subscription name to modify |
| `--sns-topic-arn` | No | string | -- | New SNS topic ARN |
| `--source-type` | No | string | -- | New source type |
| `--event-categories` | No | list(string) | -- | New event categories |
| `--enabled` | No | boolean | -- | Enable/disable the subscription |

**Output Schema:** Same as `create-event-subscription` output.

---

### 7.7 `add-source-identifier-to-subscription`

Adds a source identifier to an event subscription.

**Synopsis:**
```bash
aws docdb add-source-identifier-to-subscription \
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

**Output Schema:** Same as `create-event-subscription` output.

---

### 7.8 `remove-source-identifier-from-subscription`

Removes a source identifier from an event subscription.

**Synopsis:**
```bash
aws docdb remove-source-identifier-from-subscription \
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

**Output Schema:** Same as `create-event-subscription` output.

---

## Tags

### 7.9 `add-tags-to-resource`

Adds metadata tags to a DocumentDB resource.

**Synopsis:**
```bash
aws docdb add-tags-to-resource \
    --resource-name <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-name` | **Yes** | string | -- | ARN of the resource to tag |
| `--tags` | **Yes** | list | -- | Tags. Shorthand: `Key=string,Value=string ...` |

**Output:** None (HTTP 200 on success)

---

### 7.10 `remove-tags-from-resource`

Removes metadata tags from a DocumentDB resource.

**Synopsis:**
```bash
aws docdb remove-tags-from-resource \
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

**Output:** None (HTTP 200 on success)

---

### 7.11 `list-tags-for-resource`

Lists all tags on a DocumentDB resource.

**Synopsis:**
```bash
aws docdb list-tags-for-resource \
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

## Maintenance & Info

### 7.12 `apply-pending-maintenance-action`

Applies a pending maintenance action to a resource.

**Synopsis:**
```bash
aws docdb apply-pending-maintenance-action \
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
| `--apply-action` | **Yes** | string | -- | Action to apply (e.g., `system-update`, `db-upgrade`) |
| `--opt-in-type` | **Yes** | string | -- | Opt-in type: `immediate`, `next-maintenance`, `undo-opt-in` |

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

### 7.13 `describe-pending-maintenance-actions`

Returns a list of pending maintenance actions. **Paginated operation.**

**Synopsis:**
```bash
aws docdb describe-pending-maintenance-actions \
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
| `--resource-identifier` | No | string | All | ARN of the resource |
| `--filters` | No | list | None | Filters |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

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
    ],
    "Marker": "string"
}
```

---

### 7.14 `describe-certificates`

Returns a list of certificate authority (CA) certificates provided by Amazon DocumentDB. **Paginated operation.**

**Synopsis:**
```bash
aws docdb describe-certificates \
    [--certificate-identifier <value>] \
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
| `--certificate-identifier` | No | string | All | Certificate identifier |
| `--filters` | No | list | None | Filters |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Certificates": [
        {
            "CertificateIdentifier": "string",
            "CertificateType": "string",
            "Thumbprint": "string",
            "ValidFrom": "timestamp",
            "ValidTill": "timestamp",
            "CertificateArn": "string"
        }
    ],
    "Marker": "string"
}
```

---

### 7.15 `describe-db-engine-versions`

Returns a list of available engine versions. **Paginated operation.**

**Synopsis:**
```bash
aws docdb describe-db-engine-versions \
    [--engine <value>] \
    [--engine-version <value>] \
    [--db-parameter-group-family <value>] \
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
| `--engine` | No | string | All | Engine name: `docdb` |
| `--engine-version` | No | string | All | Specific version |
| `--db-parameter-group-family` | No | string | All | Parameter group family |
| `--filters` | No | list | None | Filters |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "DBEngineVersions": [
        {
            "Engine": "string",
            "EngineVersion": "string",
            "DBParameterGroupFamily": "string",
            "DBEngineDescription": "string",
            "DBEngineVersionDescription": "string",
            "ValidUpgradeTarget": [
                {
                    "Engine": "string",
                    "EngineVersion": "string",
                    "Description": "string",
                    "AutoUpgrade": true|false,
                    "IsMajorVersionUpgrade": true|false
                }
            ],
            "ExportableLogTypes": ["string"],
            "SupportsLogExportsToCloudwatchLogs": true|false,
            "SupportedCACertificateIdentifiers": ["string"],
            "SupportsCertificateRotationWithoutRestart": true|false
        }
    ],
    "Marker": "string"
}
```

---

### 7.16 `describe-orderable-db-instance-options`

Returns a list of orderable instance options for the specified engine. **Paginated operation.**

**Synopsis:**
```bash
aws docdb describe-orderable-db-instance-options \
    --engine <value> \
    [--engine-version <value>] \
    [--db-instance-class <value>] \
    [--license-model <value>] \
    [--vpc | --no-vpc] \
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
| `--engine` | **Yes** | string | -- | Engine: `docdb` |
| `--engine-version` | No | string | All | Engine version |
| `--db-instance-class` | No | string | All | Instance class |
| `--license-model` | No | string | All | License model |
| `--vpc` | No | boolean | -- | Filter for VPC instances |
| `--filters` | No | list | None | Filters |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "OrderableDBInstanceOptions": [
        {
            "Engine": "string",
            "EngineVersion": "string",
            "DBInstanceClass": "string",
            "LicenseModel": "string",
            "AvailabilityZones": [
                {
                    "Name": "string"
                }
            ],
            "Vpc": true|false,
            "StorageType": "string"
        }
    ],
    "Marker": "string"
}
```
