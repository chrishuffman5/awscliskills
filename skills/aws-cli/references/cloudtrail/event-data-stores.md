# Event Data Stores

### 3.1 `create-event-data-store`

Creates a new event data store for CloudTrail Lake. Event data stores collect and retain events for querying.

**Synopsis:**
```bash
aws cloudtrail create-event-data-store \
    --name <value> \
    [--advanced-event-selectors <value>] \
    [--multi-region-enabled | --no-multi-region-enabled] \
    [--organization-enabled | --no-organization-enabled] \
    [--retention-period <value>] \
    [--termination-protection-enabled | --no-termination-protection-enabled] \
    [--tags-list <value>] \
    [--kms-key-id <value>] \
    [--start-ingestion | --no-start-ingestion] \
    [--billing-mode <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Event data store name (3-128 chars) |
| `--advanced-event-selectors` | No | list | None | Advanced event selectors for filtering events |
| `--multi-region-enabled` | No | boolean | true | Collect events from all regions |
| `--organization-enabled` | No | boolean | false | Collect events for all accounts in the organization |
| `--retention-period` | No | integer | 2557 | Retention period in days (7-3653) |
| `--termination-protection-enabled` | No | boolean | true | Prevent deletion without disabling first |
| `--tags-list` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |
| `--kms-key-id` | No | string | None | KMS key ID for encryption |
| `--start-ingestion` | No | boolean | true | Start ingesting events immediately |
| `--billing-mode` | No | string | `EXTENDABLE_RETENTION_PRICING` | Billing mode: `EXTENDABLE_RETENTION_PRICING` or `FIXED_RETENTION_PRICING` |

**Output Schema:**
```json
{
    "EventDataStoreArn": "string",
    "Name": "string",
    "Status": "CREATED|ENABLED|PENDING_DELETION|STARTING_INGESTION|STOPPING_INGESTION|STOPPED_INGESTION",
    "AdvancedEventSelectors": [
        {
            "Name": "string",
            "FieldSelectors": [
                {
                    "Field": "string",
                    "Equals": ["string"],
                    "StartsWith": ["string"],
                    "EndsWith": ["string"],
                    "NotEquals": ["string"],
                    "NotStartsWith": ["string"],
                    "NotEndsWith": ["string"]
                }
            ]
        }
    ],
    "MultiRegionEnabled": true|false,
    "OrganizationEnabled": true|false,
    "RetentionPeriod": "integer",
    "TerminationProtectionEnabled": true|false,
    "CreatedTimestamp": "timestamp",
    "UpdatedTimestamp": "timestamp",
    "KmsKeyId": "string",
    "BillingMode": "string"
}
```

---

### 3.2 `delete-event-data-store`

Marks an event data store for deletion. The store is placed in `PENDING_DELETION` status and can be restored within the retention period using `restore-event-data-store`. Termination protection must be disabled first.

**Synopsis:**
```bash
aws cloudtrail delete-event-data-store \
    --event-data-store <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--event-data-store` | **Yes** | string | -- | Event data store ARN or ID |

**Output:** None (HTTP 200 on success)

---

### 3.3 `describe-event-data-store`

Returns configuration and status information for an event data store. Deprecated in favor of `get-event-data-store`.

**Synopsis:**
```bash
aws cloudtrail describe-event-data-store \
    --event-data-store <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--event-data-store` | **Yes** | string | -- | Event data store ARN or ID |

**Output Schema:** Same as `get-event-data-store`.

---

### 3.4 `get-event-data-store`

Returns configuration and status information for an event data store.

**Synopsis:**
```bash
aws cloudtrail get-event-data-store \
    --event-data-store <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--event-data-store` | **Yes** | string | -- | Event data store ARN or ID |

**Output Schema:**
```json
{
    "EventDataStoreArn": "string",
    "Name": "string",
    "Status": "CREATED|ENABLED|PENDING_DELETION|STARTING_INGESTION|STOPPING_INGESTION|STOPPED_INGESTION",
    "AdvancedEventSelectors": [
        {
            "Name": "string",
            "FieldSelectors": [
                {
                    "Field": "string",
                    "Equals": ["string"],
                    "StartsWith": ["string"],
                    "EndsWith": ["string"],
                    "NotEquals": ["string"],
                    "NotStartsWith": ["string"],
                    "NotEndsWith": ["string"]
                }
            ]
        }
    ],
    "MultiRegionEnabled": true|false,
    "OrganizationEnabled": true|false,
    "RetentionPeriod": "integer",
    "TerminationProtectionEnabled": true|false,
    "CreatedTimestamp": "timestamp",
    "UpdatedTimestamp": "timestamp",
    "KmsKeyId": "string",
    "BillingMode": "string",
    "FederationStatus": "ENABLING|ENABLED|DISABLING|DISABLED",
    "FederationRoleArn": "string",
    "PartitionKeys": [
        {
            "Name": "string",
            "Type": "string"
        }
    ]
}
```

---

### 3.5 `list-event-data-stores`

Lists event data stores in the current account. **Paginated operation.**

**Synopsis:**
```bash
aws cloudtrail list-event-data-stores \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "EventDataStores": [
        {
            "EventDataStoreArn": "string",
            "Name": "string",
            "Status": "CREATED|ENABLED|PENDING_DELETION|STARTING_INGESTION|STOPPING_INGESTION|STOPPED_INGESTION",
            "AdvancedEventSelectors": [],
            "MultiRegionEnabled": true|false,
            "OrganizationEnabled": true|false,
            "RetentionPeriod": "integer",
            "CreatedTimestamp": "timestamp",
            "UpdatedTimestamp": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.6 `update-event-data-store`

Updates an event data store's configuration, including event selectors, retention period, and multi-region settings.

**Synopsis:**
```bash
aws cloudtrail update-event-data-store \
    --event-data-store <value> \
    [--name <value>] \
    [--advanced-event-selectors <value>] \
    [--multi-region-enabled | --no-multi-region-enabled] \
    [--organization-enabled | --no-organization-enabled] \
    [--retention-period <value>] \
    [--termination-protection-enabled | --no-termination-protection-enabled] \
    [--kms-key-id <value>] \
    [--billing-mode <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--event-data-store` | **Yes** | string | -- | Event data store ARN or ID |
| `--name` | No | string | unchanged | New name |
| `--advanced-event-selectors` | No | list | unchanged | Updated event selectors |
| `--multi-region-enabled` | No | boolean | unchanged | Multi-region collection |
| `--organization-enabled` | No | boolean | unchanged | Organization-wide collection |
| `--retention-period` | No | integer | unchanged | Retention period in days (7-3653) |
| `--termination-protection-enabled` | No | boolean | unchanged | Termination protection |
| `--kms-key-id` | No | string | unchanged | KMS key ID |
| `--billing-mode` | No | string | unchanged | Billing mode |

**Output Schema:**
```json
{
    "EventDataStoreArn": "string",
    "Name": "string",
    "Status": "string",
    "AdvancedEventSelectors": [],
    "MultiRegionEnabled": true|false,
    "OrganizationEnabled": true|false,
    "RetentionPeriod": "integer",
    "TerminationProtectionEnabled": true|false,
    "CreatedTimestamp": "timestamp",
    "UpdatedTimestamp": "timestamp",
    "KmsKeyId": "string",
    "BillingMode": "string"
}
```

---

### 3.7 `restore-event-data-store`

Restores a previously deleted event data store that is in `PENDING_DELETION` status. Can only be restored within the retention period.

**Synopsis:**
```bash
aws cloudtrail restore-event-data-store \
    --event-data-store <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--event-data-store` | **Yes** | string | -- | Event data store ARN or ID |

**Output Schema:**
```json
{
    "EventDataStoreArn": "string",
    "Name": "string",
    "Status": "string",
    "AdvancedEventSelectors": [],
    "MultiRegionEnabled": true|false,
    "OrganizationEnabled": true|false,
    "RetentionPeriod": "integer",
    "TerminationProtectionEnabled": true|false,
    "CreatedTimestamp": "timestamp",
    "UpdatedTimestamp": "timestamp",
    "KmsKeyId": "string",
    "BillingMode": "string"
}
```

---

### 3.8 `enable-federation`

Enables AWS Lake Formation federation on an event data store, allowing you to query it using Athena or other Lake Formation consumers.

**Synopsis:**
```bash
aws cloudtrail enable-federation \
    --event-data-store <value> \
    --federation-role-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--event-data-store` | **Yes** | string | -- | Event data store ARN or ID |
| `--federation-role-arn` | **Yes** | string | -- | IAM role ARN used for federation |

**Output Schema:**
```json
{
    "EventDataStoreArn": "string",
    "FederationStatus": "ENABLING|ENABLED|DISABLING|DISABLED",
    "FederationRoleArn": "string"
}
```

---

### 3.9 `disable-federation`

Disables Lake Formation federation on an event data store.

**Synopsis:**
```bash
aws cloudtrail disable-federation \
    --event-data-store <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--event-data-store` | **Yes** | string | -- | Event data store ARN or ID |

**Output Schema:**
```json
{
    "EventDataStoreArn": "string",
    "FederationStatus": "ENABLING|ENABLED|DISABLING|DISABLED"
}
```
