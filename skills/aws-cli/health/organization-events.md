# Organization Events

> Organization commands require Health to be enabled for Organizations via `enable-health-service-access-for-organization`.

### 3.1 `describe-events-for-organization`

Returns Health events across the organization. **Paginated operation.** Results sorted by `lastModifiedTime` (most recent first).

**Synopsis:**
```bash
aws health describe-events-for-organization \
    [--filter <value>] \
    [--locale <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filter` | No | structure | None | Filter criteria including `awsAccountIds` |
| `--locale` | No | string | `en` | Language for results |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Filter Structure:**
```json
{
    "actionabilities": ["ACTION_REQUIRED|ACTION_MAY_BE_REQUIRED|INFORMATIONAL"],
    "eventTypeCodes": ["string"],
    "awsAccountIds": ["string"],
    "services": ["string"],
    "regions": ["string"],
    "startTime": {"from": "timestamp", "to": "timestamp"},
    "endTime": {"from": "timestamp", "to": "timestamp"},
    "lastUpdatedTime": {"from": "timestamp", "to": "timestamp"},
    "entityArns": ["string"],
    "entityValues": ["string"],
    "eventTypeCategories": ["issue|accountNotification|scheduledChange|investigation"],
    "eventStatusCodes": ["open|closed|upcoming"],
    "personas": ["OPERATIONS|SECURITY|BILLING"]
}
```

**Output Schema:**
```json
{
    "events": [
        {
            "arn": "string",
            "service": "string",
            "eventTypeCode": "string",
            "eventTypeCategory": "issue|accountNotification|scheduledChange|investigation",
            "eventScopeCode": "PUBLIC|ACCOUNT_SPECIFIC|NONE",
            "region": "string",
            "startTime": "timestamp",
            "endTime": "timestamp",
            "lastUpdatedTime": "timestamp",
            "statusCode": "open|closed|upcoming",
            "actionability": "string",
            "personas": ["string"]
        }
    ],
    "nextToken": "string"
}
```

---

### 3.2 `describe-event-details-for-organization`

Returns detailed information about Health events across the organization. Batch operation (up to 10 events).

**Synopsis:**
```bash
aws health describe-event-details-for-organization \
    --organization-event-detail-filters <value> \
    [--locale <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-event-detail-filters` | **Yes** | list | -- | Event ARN and optional account ID pairs (1-10 items) |
| `--locale` | No | string | `en` | Language for results |

**Filter Structure:**
```json
[
    {
        "eventArn": "string",
        "awsAccountId": "string"
    }
]
```

> For public events, omit `awsAccountId`. For account-specific events, provide a valid account ID.

**Output Schema:**
```json
{
    "successfulSet": [
        {
            "awsAccountId": "string",
            "event": {
                "arn": "string",
                "service": "string",
                "eventTypeCode": "string",
                "eventTypeCategory": "string",
                "region": "string",
                "startTime": "timestamp",
                "endTime": "timestamp",
                "lastUpdatedTime": "timestamp",
                "statusCode": "open|closed|upcoming",
                "eventScopeCode": "string",
                "actionability": "string",
                "personas": ["string"]
            },
            "eventDescription": {
                "latestDescription": "string"
            },
            "eventMetadata": {
                "key": "value"
            }
        }
    ],
    "failedSet": [
        {
            "awsAccountId": "string",
            "eventArn": "string",
            "errorName": "string",
            "errorMessage": "string"
        }
    ]
}
```

---

### 3.3 `describe-affected-entities-for-organization`

Returns entities affected by Health events across the organization. **Paginated operation.**

**Synopsis:**
```bash
aws health describe-affected-entities-for-organization \
    [--organization-entity-filters <value>] \
    [--organization-entity-account-filters <value>] \
    [--locale <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-entity-filters` | No | list | None | Event ARN and account ID pairs (1-10 items) |
| `--organization-entity-account-filters` | No | list | None | Event ARN, account ID, and status code filters (1-10 items) |
| `--locale` | No | string | `en` | Language for results |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Organization Entity Filter:**
```json
[
    {
        "eventArn": "string",
        "awsAccountId": "string"
    }
]
```

**Organization Entity Account Filter:**
```json
[
    {
        "eventArn": "string",
        "awsAccountId": "string",
        "statusCodes": ["IMPAIRED|UNIMPAIRED|UNKNOWN|PENDING|RESOLVED"]
    }
]
```

**Output Schema:**
```json
{
    "entities": [
        {
            "entityArn": "string",
            "eventArn": "string",
            "entityValue": "string",
            "entityUrl": "string",
            "awsAccountId": "string",
            "lastUpdatedTime": "timestamp",
            "statusCode": "IMPAIRED|UNIMPAIRED|UNKNOWN|PENDING|RESOLVED",
            "tags": {},
            "entityMetadata": {}
        }
    ],
    "failedSet": [
        {
            "awsAccountId": "string",
            "eventArn": "string",
            "errorName": "string",
            "errorMessage": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 3.4 `describe-affected-accounts-for-organization`

Returns a list of accounts affected by a Health event within the organization. **Paginated operation.**

**Synopsis:**
```bash
aws health describe-affected-accounts-for-organization \
    --event-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--event-arn` | **Yes** | string | -- | The unique identifier for the event (max 1600 chars) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "affectedAccounts": ["string"],
    "eventScopeCode": "PUBLIC|ACCOUNT_SPECIFIC|NONE",
    "nextToken": "string"
}
```

---

### 3.5 `describe-entity-aggregates-for-organization`

Returns aggregate entity counts for Health events across the organization.

**Synopsis:**
```bash
aws health describe-entity-aggregates-for-organization \
    --event-arns <value> \
    [--aws-account-ids <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--event-arns` | **Yes** | list(string) | -- | Event ARNs (1-50 items) |
| `--aws-account-ids` | No | list(string) | None | Account IDs to filter by (1-50 items) |

**Output Schema:**
```json
{
    "organizationEntityAggregates": [
        {
            "eventArn": "string",
            "count": "integer",
            "statuses": {
                "IMPAIRED": "integer",
                "UNIMPAIRED": "integer",
                "UNKNOWN": "integer",
                "PENDING": "integer",
                "RESOLVED": "integer"
            },
            "accounts": [
                {
                    "accountId": "string",
                    "count": "integer",
                    "statuses": {
                        "IMPAIRED": "integer",
                        "UNIMPAIRED": "integer",
                        "UNKNOWN": "integer",
                        "PENDING": "integer",
                        "RESOLVED": "integer"
                    }
                }
            ]
        }
    ]
}
```
