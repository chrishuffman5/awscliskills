# Queries

These commands use `aws forecastquery` (not `aws forecast`).

### 9.1 `query-forecast`

Queries a forecast for specific items within a time range.

**Synopsis:**
```bash
aws forecastquery query-forecast \
    --forecast-arn <value> \
    --filters <value> \
    [--start-date <value>] \
    [--end-date <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--forecast-arn` | **Yes** | string | -- | Forecast ARN (max 256 chars) |
| `--filters` | **Yes** | map | -- | Key-value filters (1-50 entries). Example: `item_id=product_123` |
| `--start-date` | No | string | None | Start date: `yyyy-MM-ddTHH:mm:ss` |
| `--end-date` | No | string | None | End date: `yyyy-MM-ddTHH:mm:ss` |
| `--next-token` | No | string | None | Pagination token (1-3000 chars, expires after 24h) |

**Output Schema:**
```json
{
    "Forecast": {
        "Predictions": {
            "p10": [
                {"Timestamp": "string", "Value": "double"}
            ],
            "p50": [
                {"Timestamp": "string", "Value": "double"}
            ],
            "p90": [
                {"Timestamp": "string", "Value": "double"}
            ]
        }
    }
}
```

**Notes:**
- Prediction keys depend on forecast types configured in `create-forecast` (default: `p10`, `p50`, `p90`)
- Can also include `mean` if configured
- Forecast must be ACTIVE before querying

---

### 9.2 `query-what-if-forecast`

Queries a what-if forecast for specific items within a time range.

**Synopsis:**
```bash
aws forecastquery query-what-if-forecast \
    --what-if-forecast-arn <value> \
    --filters <value> \
    [--start-date <value>] \
    [--end-date <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--what-if-forecast-arn` | **Yes** | string | -- | What-if forecast ARN (max 300 chars) |
| `--filters` | **Yes** | map | -- | Key-value filters (1-50 entries) |
| `--start-date` | No | string | None | Start date: `yyyy-MM-ddTHH:mm:ss` |
| `--end-date` | No | string | None | End date: `yyyy-MM-ddTHH:mm:ss` |
| `--next-token` | No | string | None | Pagination token (1-3000 chars, expires after 24h) |

**Output Schema:**
```json
{
    "Forecast": {
        "Predictions": {
            "p10": [
                {"Timestamp": "string", "Value": "double"}
            ],
            "p50": [
                {"Timestamp": "string", "Value": "double"}
            ],
            "p90": [
                {"Timestamp": "string", "Value": "double"}
            ]
        }
    }
}
```
