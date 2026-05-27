# Queries

### 3.1 `start-query`

Starts a query for Internet Monitor data. Specify the query type, time period, and filter parameters.

**Synopsis:**
```bash
aws internetmonitor start-query \
    --monitor-name <value> \
    --start-time <value> \
    --end-time <value> \
    --query-type <value> \
    [--filter-parameters <value>] \
    [--linked-account-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--monitor-name` | **Yes** | string | -- | Monitor name (1-255 chars) |
| `--start-time` | **Yes** | timestamp | -- | Beginning of the time period |
| `--end-time` | **Yes** | timestamp | -- | End of the time period |
| `--query-type` | **Yes** | string | -- | Query type (see Query Types below) |
| `--filter-parameters` | No | list | -- | Filters to scope results |
| `--linked-account-id` | No | string | -- | Cross-account ID (12 digits) |

**Query Types:**
- `MEASUREMENTS` — Availability, performance, traffic, RTT at 5-minute intervals
- `TOP_LOCATIONS` — Top location/ASN combinations by traffic volume
- `TOP_LOCATION_DETAILS` — TTFB for CloudFront, current, and best EC2 config at 1-hour intervals
- `OVERALL_TRAFFIC_SUGGESTIONS` — TTFB using 30-day weighted average across AWS locations
- `OVERALL_TRAFFIC_SUGGESTIONS_DETAILS` — TTFB for top locations in proposed AWS location
- `ROUTING_SUGGESTIONS` — Predicted RTT from IP prefix to AWS location at 1-hour intervals

**Filter Parameters Structure:**
```json
[
    {
        "Field": "string",
        "Operator": "EQUALS|NOT_EQUALS",
        "Values": ["string"]
    }
]
```

**Output Schema:**
```json
{
    "QueryId": "string"
}
```

---

### 3.2 `get-query-results`

Retrieves the results of a query. Use the `QueryId` returned by `start-query`.

**Synopsis:**
```bash
aws internetmonitor get-query-results \
    --monitor-name <value> \
    --query-id <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--monitor-name` | **Yes** | string | -- | Monitor name |
| `--query-id` | **Yes** | string | -- | Query ID from `start-query` |
| `--next-token` | No | string | -- | Token for next page of results |
| `--max-results` | No | integer | -- | Max results to return (1-1000) |

**Output Schema:**
```json
{
    "Fields": [
        {
            "Name": "string",
            "Type": "string"
        }
    ],
    "Data": [
        ["string"]
    ],
    "NextToken": "string"
}
```

---

### 3.3 `get-query-status`

Returns the current status of a query.

**Synopsis:**
```bash
aws internetmonitor get-query-status \
    --monitor-name <value> \
    --query-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--monitor-name` | **Yes** | string | -- | Monitor name |
| `--query-id` | **Yes** | string | -- | Query ID from `start-query` |

**Output Schema:**
```json
{
    "Status": "QUEUED|RUNNING|SUCCEEDED|FAILED|CANCELED"
}
```

---

### 3.4 `stop-query`

Stops a query that is in progress.

**Synopsis:**
```bash
aws internetmonitor stop-query \
    --monitor-name <value> \
    --query-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--monitor-name` | **Yes** | string | -- | Monitor name |
| `--query-id` | **Yes** | string | -- | Query ID to stop |

**Output Schema:** None (HTTP 200 on success).
