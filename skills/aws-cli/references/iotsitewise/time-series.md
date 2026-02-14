# Time Series

### 4.1 `describe-time-series`

Describes a time series associated with an asset property or alias.

**Synopsis:**
```bash
aws iotsitewise describe-time-series \
    [--alias <value>] \
    [--asset-id <value>] \
    [--property-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--alias` | Conditional | string | -- | Time series alias (alternative to asset-id + property-id) |
| `--asset-id` | Conditional | string | -- | Asset ID |
| `--property-id` | Conditional | string | -- | Property ID |

**Output Schema:**
```json
{
    "assetId": "string",
    "propertyId": "string",
    "alias": "string",
    "timeSeriesId": "string",
    "dataType": "STRING|INTEGER|DOUBLE|BOOLEAN|STRUCT",
    "dataTypeSpec": "string",
    "timeSeriesCreationDate": "timestamp",
    "timeSeriesLastUpdateDate": "timestamp",
    "timeSeriesArn": "string"
}
```

---

### 4.2 `list-time-series`

Lists time series. **Paginated operation.**

**Synopsis:**
```bash
aws iotsitewise list-time-series \
    [--asset-id <value>] \
    [--alias-prefix <value>] \
    [--time-series-type <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--asset-id` | No | string | None | Filter by asset ID |
| `--alias-prefix` | No | string | None | Filter by alias prefix |
| `--time-series-type` | No | string | None | `ASSOCIATED` or `DISASSOCIATED` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "TimeSeriesSummaries": [
        {
            "timeSeriesId": "string",
            "dataType": "STRING|INTEGER|DOUBLE|BOOLEAN|STRUCT",
            "dataTypeSpec": "string",
            "timeSeriesCreationDate": "timestamp",
            "timeSeriesLastUpdateDate": "timestamp",
            "timeSeriesArn": "string",
            "assetId": "string",
            "propertyId": "string",
            "alias": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 4.3 `delete-time-series`

Deletes a time series. Identify by alias or by asset-id + property-id.

**Synopsis:**
```bash
aws iotsitewise delete-time-series \
    [--alias <value>] \
    [--asset-id <value>] \
    [--property-id <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--alias` | Conditional | string | -- | Time series alias |
| `--asset-id` | Conditional | string | -- | Asset ID |
| `--property-id` | Conditional | string | -- | Property ID |
| `--client-token` | No | string | Auto | Idempotency token |

**Output:** None
