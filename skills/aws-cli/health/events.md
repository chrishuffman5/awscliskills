# Events

### 1.1 `describe-events`

Returns Health events matching optional filter criteria. **Paginated operation.** Results sorted by `lastModifiedTime` (most recent first).

**Synopsis:**
```bash
aws health describe-events \
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
| `--filter` | No | structure | None | Filter criteria (see structure below) |
| `--locale` | No | string | `en` | Language for results (2-256 chars) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Filter Structure:**
```json
{
    "actionabilities": ["ACTION_REQUIRED|ACTION_MAY_BE_REQUIRED|INFORMATIONAL"],
    "eventArns": ["string"],
    "eventTypeCodes": ["string"],
    "services": ["string"],
    "regions": ["string"],
    "availabilityZones": ["string"],
    "startTimes": [{"from": "timestamp", "to": "timestamp"}],
    "endTimes": [{"from": "timestamp", "to": "timestamp"}],
    "lastUpdatedTimes": [{"from": "timestamp", "to": "timestamp"}],
    "entityArns": ["string"],
    "entityValues": ["string"],
    "eventTypeCategories": ["issue|accountNotification|scheduledChange|investigation"],
    "tags": [{"key": "value"}],
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
            "region": "string",
            "availabilityZone": "string",
            "startTime": "timestamp",
            "endTime": "timestamp",
            "lastUpdatedTime": "timestamp",
            "statusCode": "open|closed|upcoming",
            "eventScopeCode": "PUBLIC|ACCOUNT_SPECIFIC|NONE",
            "actionability": "ACTION_REQUIRED|ACTION_MAY_BE_REQUIRED|INFORMATIONAL",
            "personas": ["string"]
        }
    ],
    "nextToken": "string"
}
```

---

### 1.2 `describe-event-details`

Returns detailed information about one or more Health events. Batch operation (up to 10 events).

**Synopsis:**
```bash
aws health describe-event-details \
    --event-arns <value> \
    [--locale <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--event-arns` | **Yes** | list(string) | -- | Event ARNs to describe (1-10 items) |
| `--locale` | No | string | `en` | Language for results |

**Output Schema:**
```json
{
    "successfulSet": [
        {
            "event": {
                "arn": "string",
                "service": "string",
                "eventTypeCode": "string",
                "eventTypeCategory": "issue|accountNotification|scheduledChange|investigation",
                "region": "string",
                "availabilityZone": "string",
                "startTime": "timestamp",
                "endTime": "timestamp",
                "lastUpdatedTime": "timestamp",
                "statusCode": "open|closed|upcoming",
                "eventScopeCode": "PUBLIC|ACCOUNT_SPECIFIC|NONE",
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
            "eventArn": "string",
            "errorName": "string",
            "errorMessage": "string"
        }
    ]
}
```

---

### 1.3 `describe-event-types`

Returns event types matching optional filter criteria. **Paginated operation.**

**Synopsis:**
```bash
aws health describe-event-types \
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
| `--filter` | No | structure | None | Filter: `eventTypeCodes` (1-10), `services` (1-10), `eventTypeCategories` (1-10), `actionabilities` (1-3), `personas` (1-3) |
| `--locale` | No | string | `en` | Language for results |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Filter Structure:**
```json
{
    "eventTypeCodes": ["string"],
    "services": ["string"],
    "eventTypeCategories": ["issue|accountNotification|scheduledChange|investigation"],
    "actionabilities": ["ACTION_REQUIRED|ACTION_MAY_BE_REQUIRED|INFORMATIONAL"],
    "personas": ["OPERATIONS|SECURITY|BILLING"]
}
```

**Output Schema:**
```json
{
    "eventTypes": [
        {
            "service": "string",
            "code": "string",
            "category": "issue|accountNotification|scheduledChange|investigation",
            "actionability": "ACTION_REQUIRED|ACTION_MAY_BE_REQUIRED|INFORMATIONAL",
            "personas": ["string"]
        }
    ],
    "nextToken": "string"
}
```

---

### 1.4 `describe-event-aggregates`

Returns aggregate counts of events by event type category. **Paginated operation.**

**Synopsis:**
```bash
aws health describe-event-aggregates \
    --aggregate-field <value> \
    [--filter <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aggregate-field` | **Yes** | string | -- | Aggregation field. Only supported value: `eventTypeCategory` |
| `--filter` | No | structure | None | Same filter structure as `describe-events` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "eventAggregates": [
        {
            "aggregateValue": "string",
            "count": "integer"
        }
    ],
    "nextToken": "string"
}
```
