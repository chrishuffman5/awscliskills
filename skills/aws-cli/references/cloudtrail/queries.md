# Queries

### 4.1 `start-query`

Starts a CloudTrail Lake SQL query against an event data store. The query runs asynchronously. Use `describe-query` to check status and `get-query-results` to retrieve results.

**Synopsis:**
```bash
aws cloudtrail start-query \
    [--query-statement <value>] \
    [--delivery-s3-uri <value>] \
    [--query-alias <value>] \
    [--query-parameters <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--query-statement` | No | string | None | SQL query string. Required unless `--query-alias` is provided |
| `--delivery-s3-uri` | No | string | None | S3 URI for query result delivery (e.g., `s3://bucket/prefix/`) |
| `--query-alias` | No | string | None | Alias of a saved query to run |
| `--query-parameters` | No | list(string) | None | Parameter values for a parameterized query |

**Output Schema:**
```json
{
    "QueryId": "string"
}
```

---

### 4.2 `describe-query`

Returns metadata about a query, including its status, execution statistics, and error message if failed.

**Synopsis:**
```bash
aws cloudtrail describe-query \
    [--event-data-store <value>] \
    [--query-id <value>] \
    [--query-alias <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--event-data-store` | No | string | None | Event data store ARN or ID (deprecated, query ID is sufficient) |
| `--query-id` | No | string | None | Query ID. Required unless `--query-alias` is provided |
| `--query-alias` | No | string | None | Alias of a saved query |

**Output Schema:**
```json
{
    "QueryId": "string",
    "QueryString": "string",
    "QueryStatus": "QUEUED|RUNNING|FINISHED|FAILED|CANCELLED|TIMED_OUT",
    "QueryStatistics": {
        "EventsMatched": "long",
        "EventsScanned": "long",
        "BytesScanned": "long",
        "ExecutionTimeInMillis": "integer",
        "CreationTime": "timestamp"
    },
    "ErrorMessage": "string",
    "DeliveryS3Uri": "string",
    "DeliveryStatus": "SUCCESS|FAILED|FAILED_SIGNING_FILE|PENDING|RESOURCE_NOT_FOUND|ACCESS_DENIED|ACCESS_DENIED_SIGNING_FILE|CANCELLED|UNKNOWN"
}
```

---

### 4.3 `get-query-results`

Returns the results of a completed query. Results are returned in pages. **Paginated operation.**

**Synopsis:**
```bash
aws cloudtrail get-query-results \
    --query-id <value> \
    [--event-data-store <value>] \
    [--next-token <value>] \
    [--max-query-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--query-id` | **Yes** | string | -- | Query ID |
| `--event-data-store` | No | string | None | Event data store ARN or ID (deprecated) |
| `--next-token` | No | string | None | Pagination token |
| `--max-query-results` | No | integer | None | Maximum number of results to return |

**Output Schema:**
```json
{
    "QueryStatus": "QUEUED|RUNNING|FINISHED|FAILED|CANCELLED|TIMED_OUT",
    "QueryStatistics": {
        "ResultsCount": "integer",
        "TotalResultsCount": "integer",
        "BytesScanned": "long"
    },
    "QueryResultRows": [
        [
            {
                "key": "value"
            }
        ]
    ],
    "NextToken": "string",
    "ErrorMessage": "string"
}
```

---

### 4.4 `list-queries`

Lists queries for a specified event data store. **Paginated operation.**

**Synopsis:**
```bash
aws cloudtrail list-queries \
    --event-data-store <value> \
    [--start-time <value>] \
    [--end-time <value>] \
    [--query-status <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--event-data-store` | **Yes** | string | -- | Event data store ARN or ID |
| `--start-time` | No | timestamp | None | Filter queries created after this time |
| `--end-time` | No | timestamp | None | Filter queries created before this time |
| `--query-status` | No | string | None | Filter by status: `QUEUED`, `RUNNING`, `FINISHED`, `FAILED`, `CANCELLED`, `TIMED_OUT` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Queries": [
        {
            "QueryId": "string",
            "QueryStatus": "QUEUED|RUNNING|FINISHED|FAILED|CANCELLED|TIMED_OUT",
            "CreationTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 4.5 `cancel-query`

Cancels a running query. Can only cancel queries in `QUEUED` or `RUNNING` status.

**Synopsis:**
```bash
aws cloudtrail cancel-query \
    --query-id <value> \
    [--event-data-store <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--query-id` | **Yes** | string | -- | Query ID to cancel |
| `--event-data-store` | No | string | None | Event data store ARN or ID (deprecated) |

**Output Schema:**
```json
{
    "QueryId": "string",
    "QueryStatus": "CANCELLED"
}
```
