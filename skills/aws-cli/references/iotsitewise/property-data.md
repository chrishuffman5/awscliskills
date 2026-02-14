# Property Data

### 3.1 `get-asset-property-value`

Gets the current value of an asset property.

**Synopsis:**
```bash
aws iotsitewise get-asset-property-value \
    [--asset-id <value>] \
    [--property-id <value>] \
    [--property-alias <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--asset-id` | Conditional | string | -- | Asset ID (required with `--property-id`) |
| `--property-id` | Conditional | string | -- | Property ID (required with `--asset-id`) |
| `--property-alias` | Conditional | string | -- | Property alias (alternative to asset-id + property-id) |

**Output Schema:**
```json
{
    "propertyValue": {
        "value": {
            "stringValue": "string",
            "integerValue": "integer",
            "doubleValue": "double",
            "booleanValue": "boolean"
        },
        "timestamp": {
            "timeInSeconds": "long",
            "offsetInNanos": "integer"
        },
        "quality": "GOOD|BAD|UNCERTAIN"
    }
}
```

---

### 3.2 `get-asset-property-value-history`

Gets historical values of an asset property. **Paginated operation.**

**Synopsis:**
```bash
aws iotsitewise get-asset-property-value-history \
    [--asset-id <value>] \
    [--property-id <value>] \
    [--property-alias <value>] \
    [--start-date <value>] \
    [--end-date <value>] \
    [--qualities <value>] \
    [--time-ordering <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--asset-id` | Conditional | string | -- | Asset ID (required with `--property-id`) |
| `--property-id` | Conditional | string | -- | Property ID (required with `--asset-id`) |
| `--property-alias` | Conditional | string | -- | Property alias |
| `--start-date` | No | timestamp | None | Exclusive start time (epoch seconds) |
| `--end-date` | No | timestamp | None | Inclusive end time (epoch seconds) |
| `--qualities` | No | list | None | Filter: `GOOD`, `BAD`, `UNCERTAIN` |
| `--time-ordering` | No | string | `ASCENDING` | `ASCENDING` or `DESCENDING` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "assetPropertyValueHistory": [
        {
            "value": {
                "stringValue": "string",
                "integerValue": "integer",
                "doubleValue": "double",
                "booleanValue": "boolean"
            },
            "timestamp": {
                "timeInSeconds": "long",
                "offsetInNanos": "integer"
            },
            "quality": "GOOD|BAD|UNCERTAIN"
        }
    ],
    "nextToken": "string"
}
```

---

### 3.3 `get-asset-property-aggregates`

Gets aggregated values for an asset property. **Paginated operation.**

**Synopsis:**
```bash
aws iotsitewise get-asset-property-aggregates \
    --aggregate-types <value> \
    --resolution <value> \
    --start-date <value> \
    --end-date <value> \
    [--asset-id <value>] \
    [--property-id <value>] \
    [--property-alias <value>] \
    [--qualities <value>] \
    [--time-ordering <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aggregate-types` | **Yes** | list | -- | `AVERAGE`, `COUNT`, `MAXIMUM`, `MINIMUM`, `SUM`, `STANDARD_DEVIATION` |
| `--resolution` | **Yes** | string | -- | `1m`, `15m`, `1h`, `1d` |
| `--start-date` | **Yes** | timestamp | -- | Exclusive start time (epoch seconds) |
| `--end-date` | **Yes** | timestamp | -- | Inclusive end time (epoch seconds) |
| `--asset-id` | Conditional | string | -- | Asset ID |
| `--property-id` | Conditional | string | -- | Property ID |
| `--property-alias` | Conditional | string | -- | Property alias |
| `--qualities` | No | list | None | Filter: `GOOD`, `BAD`, `UNCERTAIN` |
| `--time-ordering` | No | string | `ASCENDING` | `ASCENDING` or `DESCENDING` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "aggregatedValues": [
        {
            "timestamp": "double",
            "quality": "GOOD|BAD|UNCERTAIN",
            "value": {
                "average": "double",
                "count": "double",
                "maximum": "double",
                "minimum": "double",
                "sum": "double",
                "standardDeviation": "double"
            }
        }
    ],
    "nextToken": "string"
}
```

---

### 3.4 `get-interpolated-asset-property-values`

Gets interpolated values for an asset property. **Paginated operation.**

**Synopsis:**
```bash
aws iotsitewise get-interpolated-asset-property-values \
    --start-time-in-seconds <value> \
    --end-time-in-seconds <value> \
    --quality <value> \
    --interval-in-seconds <value> \
    --type <value> \
    [--asset-id <value>] \
    [--property-id <value>] \
    [--property-alias <value>] \
    [--start-time-offset-in-nanos <value>] \
    [--end-time-offset-in-nanos <value>] \
    [--interval-window-in-seconds <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--start-time-in-seconds` | **Yes** | long | -- | Start time (epoch seconds) |
| `--end-time-in-seconds` | **Yes** | long | -- | End time (epoch seconds) |
| `--quality` | **Yes** | string | -- | `GOOD`, `BAD`, `UNCERTAIN` |
| `--interval-in-seconds` | **Yes** | long | -- | Interval between interpolated values |
| `--type` | **Yes** | string | -- | `LINEAR_INTERPOLATION`, `LOCF_INTERPOLATION` |
| `--asset-id` | Conditional | string | -- | Asset ID |
| `--property-id` | Conditional | string | -- | Property ID |
| `--property-alias` | Conditional | string | -- | Property alias |
| `--start-time-offset-in-nanos` | No | integer | 0 | Start time nanosecond offset |
| `--end-time-offset-in-nanos` | No | integer | 0 | End time nanosecond offset |
| `--interval-window-in-seconds` | No | long | None | Window for LOCF interpolation |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "interpolatedAssetPropertyValues": [
        {
            "timestamp": {
                "timeInSeconds": "long",
                "offsetInNanos": "integer"
            },
            "value": {
                "stringValue": "string",
                "integerValue": "integer",
                "doubleValue": "double",
                "booleanValue": "boolean"
            }
        }
    ],
    "nextToken": "string"
}
```

---

### 3.5 `batch-put-asset-property-value`

Sends asset property values to IoT SiteWise (max 10 entries per request).

**Synopsis:**
```bash
aws iotsitewise batch-put-asset-property-value \
    --entries <value> \
    [--enable-partial-entry-processing | --no-enable-partial-entry-processing] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--entries` | **Yes** | list | -- | List of property value entries (max 10) |
| `--enable-partial-entry-processing` | No | boolean | false | Ingest valid TQVs even if some fail |

**Entry Structure:**
```json
{
    "entryId": "string",
    "assetId": "string",
    "propertyId": "string",
    "propertyAlias": "string",
    "propertyValues": [
        {
            "value": {
                "stringValue": "string",
                "integerValue": "integer",
                "doubleValue": "double",
                "booleanValue": "boolean"
            },
            "timestamp": {
                "timeInSeconds": "long",
                "offsetInNanos": "integer"
            },
            "quality": "GOOD|BAD|UNCERTAIN"
        }
    ]
}
```

**Output Schema:**
```json
{
    "errorEntries": [
        {
            "entryId": "string",
            "errors": [
                {
                    "errorCode": "string",
                    "errorMessage": "string",
                    "timestamps": [
                        {"timeInSeconds": "long", "offsetInNanos": "integer"}
                    ]
                }
            ]
        }
    ]
}
```

---

### 3.6 `batch-get-asset-property-value`

Gets current property values for multiple assets in batch.

**Synopsis:**
```bash
aws iotsitewise batch-get-asset-property-value \
    --entries <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--entries` | **Yes** | list | -- | List of entries (max 128) |

**Entry Structure:**
```json
{
    "entryId": "string",
    "assetId": "string",
    "propertyId": "string",
    "propertyAlias": "string"
}
```

**Output Schema:**
```json
{
    "successEntries": [
        {
            "entryId": "string",
            "propertyValue": {
                "value": {},
                "timestamp": {"timeInSeconds": "long", "offsetInNanos": "integer"},
                "quality": "GOOD|BAD|UNCERTAIN"
            }
        }
    ],
    "errorEntries": [
        {
            "entryId": "string",
            "errorCode": "ResourceNotFoundException|InvalidRequestException|AccessDeniedException",
            "errorMessage": "string"
        }
    ],
    "skippedEntries": [
        {
            "entryId": "string",
            "completionStatus": "SUCCESS|ERROR",
            "errorInfo": {"errorCode": "string", "errorTimestamp": "timestamp"}
        }
    ],
    "nextToken": "string"
}
```

---

### 3.7 `batch-get-asset-property-value-history`

Gets historical property values for multiple assets in batch. **Paginated operation.**

**Synopsis:**
```bash
aws iotsitewise batch-get-asset-property-value-history \
    --entries <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--entries` | **Yes** | list | -- | List of entries (max 128) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Max total items |

**Entry Structure:**
```json
{
    "entryId": "string",
    "assetId": "string",
    "propertyId": "string",
    "propertyAlias": "string",
    "startDate": "timestamp",
    "endDate": "timestamp",
    "qualities": ["GOOD|BAD|UNCERTAIN"],
    "timeOrdering": "ASCENDING|DESCENDING"
}
```

**Output Schema:**
```json
{
    "successEntries": [
        {
            "entryId": "string",
            "assetPropertyValueHistory": [
                {
                    "value": {},
                    "timestamp": {"timeInSeconds": "long", "offsetInNanos": "integer"},
                    "quality": "GOOD|BAD|UNCERTAIN"
                }
            ]
        }
    ],
    "errorEntries": [
        {
            "entryId": "string",
            "errorCode": "string",
            "errorMessage": "string"
        }
    ],
    "skippedEntries": [],
    "nextToken": "string"
}
```

---

### 3.8 `batch-get-asset-property-aggregates`

Gets aggregated property values for multiple assets in batch. **Paginated operation.**

**Synopsis:**
```bash
aws iotsitewise batch-get-asset-property-aggregates \
    --entries <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--entries` | **Yes** | list | -- | List of entries (max 128) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Max total items |

**Entry Structure:**
```json
{
    "entryId": "string",
    "assetId": "string",
    "propertyId": "string",
    "propertyAlias": "string",
    "aggregateTypes": ["AVERAGE|COUNT|MAXIMUM|MINIMUM|SUM|STANDARD_DEVIATION"],
    "resolution": "1m|15m|1h|1d",
    "startDate": "timestamp",
    "endDate": "timestamp",
    "qualities": ["GOOD|BAD|UNCERTAIN"],
    "timeOrdering": "ASCENDING|DESCENDING"
}
```

**Output Schema:**
```json
{
    "successEntries": [
        {
            "entryId": "string",
            "aggregatedValues": [
                {
                    "timestamp": "double",
                    "quality": "GOOD|BAD|UNCERTAIN",
                    "value": {
                        "average": "double",
                        "count": "double",
                        "maximum": "double",
                        "minimum": "double",
                        "sum": "double",
                        "standardDeviation": "double"
                    }
                }
            ]
        }
    ],
    "errorEntries": [],
    "skippedEntries": [],
    "nextToken": "string"
}
```
