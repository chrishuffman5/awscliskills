# Affected Entities

### 2.1 `describe-affected-entities`

Returns entities (resources) affected by a Health event. **Paginated operation.** At least one event ARN is required in the filter.

**Synopsis:**
```bash
aws health describe-affected-entities \
    --filter <value> \
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
| `--filter` | **Yes** | structure | -- | Filter with required `eventArns` (1-10) and optional `entityArns`, `entityValues`, `lastUpdatedTimes`, `tags`, `statusCodes` |
| `--locale` | No | string | `en` | Language for results |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Filter Structure:**
```json
{
    "eventArns": ["string"],
    "entityArns": ["string"],
    "entityValues": ["string"],
    "lastUpdatedTimes": [
        {
            "from": "timestamp",
            "to": "timestamp"
        }
    ],
    "tags": [{"key": "value"}],
    "statusCodes": ["IMPAIRED|UNIMPAIRED|UNKNOWN|PENDING|RESOLVED"]
}
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
            "tags": {
                "key": "value"
            },
            "entityMetadata": {
                "key": "value"
            }
        }
    ],
    "nextToken": "string"
}
```

---

### 2.2 `describe-entity-aggregates`

Returns aggregate entity counts for specified Health events.

**Synopsis:**
```bash
aws health describe-entity-aggregates \
    [--event-arns <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--event-arns` | No | list(string) | None | Event ARNs to get aggregate counts for (1-50 items) |

**Output Schema:**
```json
{
    "entityAggregates": [
        {
            "eventArn": "string",
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
```
