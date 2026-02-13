# Service Graph

### 2.1 `get-service-graph`

Retrieves a document describing the services that process incoming requests and downstream services they call. **Paginated operation.**

**Synopsis:**
```bash
aws xray get-service-graph \
    --start-time <value> \
    --end-time <value> \
    [--group-name <value>] \
    [--group-arn <value>] \
    [--starting-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--start-time` | **Yes** | timestamp | -- | Start of the time range (Unix epoch or ISO 8601) |
| `--end-time` | **Yes** | timestamp | -- | End of the time range |
| `--group-name` | No | string | None | Name of a group to filter the service graph |
| `--group-arn` | No | string | None | ARN of a group to filter the service graph |
| `--starting-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "StartTime": "timestamp",
    "EndTime": "timestamp",
    "Services": [
        {
            "ReferenceId": "integer",
            "Name": "string",
            "Names": ["string"],
            "Root": "boolean",
            "AccountId": "string",
            "Type": "string",
            "State": "string",
            "StartTime": "timestamp",
            "EndTime": "timestamp",
            "Edges": [
                {
                    "ReferenceId": "integer",
                    "StartTime": "timestamp",
                    "EndTime": "timestamp",
                    "SummaryStatistics": {
                        "OkCount": "long",
                        "ErrorStatistics": {
                            "ThrottleCount": "long",
                            "OtherCount": "long",
                            "TotalCount": "long"
                        },
                        "FaultStatistics": {
                            "OtherCount": "long",
                            "TotalCount": "long"
                        },
                        "TotalCount": "long",
                        "TotalResponseTime": "double"
                    },
                    "ResponseTimeHistogram": [
                        {
                            "Value": "double",
                            "Count": "integer"
                        }
                    ],
                    "Aliases": [
                        {
                            "Name": "string",
                            "Names": ["string"],
                            "Type": "string"
                        }
                    ]
                }
            ],
            "SummaryStatistics": {
                "OkCount": "long",
                "ErrorStatistics": {
                    "ThrottleCount": "long",
                    "OtherCount": "long",
                    "TotalCount": "long"
                },
                "FaultStatistics": {
                    "OtherCount": "long",
                    "TotalCount": "long"
                },
                "TotalCount": "long",
                "TotalResponseTime": "double"
            },
            "DurationHistogram": [],
            "ResponseTimeHistogram": []
        }
    ],
    "ContainsOldGroupVersions": "boolean",
    "NextToken": "string"
}
```

---

### 2.2 `get-time-series-service-statistics`

Returns time series service statistics for a time range. **Paginated operation.**

**Synopsis:**
```bash
aws xray get-time-series-service-statistics \
    --start-time <value> \
    --end-time <value> \
    [--group-name <value>] \
    [--group-arn <value>] \
    [--entity-selector-expression <value>] \
    [--period <value>] \
    [--forecast-statistics | --no-forecast-statistics] \
    [--starting-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--start-time` | **Yes** | timestamp | -- | Start of the time range |
| `--end-time` | **Yes** | timestamp | -- | End of the time range |
| `--group-name` | No | string | None | Name of a group |
| `--group-arn` | No | string | None | ARN of a group |
| `--entity-selector-expression` | No | string | None | Entity selector expression (e.g., `service("my-service")`) |
| `--period` | No | integer | None | Aggregation period in seconds |
| `--forecast-statistics` | No | boolean | false | Include forecast statistics |
| `--starting-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "TimeSeriesServiceStatistics": [
        {
            "Timestamp": "timestamp",
            "EdgeSummaryStatistics": {
                "OkCount": "long",
                "ErrorStatistics": {
                    "ThrottleCount": "long",
                    "OtherCount": "long",
                    "TotalCount": "long"
                },
                "FaultStatistics": {
                    "OtherCount": "long",
                    "TotalCount": "long"
                },
                "TotalCount": "long",
                "TotalResponseTime": "double"
            },
            "ServiceSummaryStatistics": {
                "OkCount": "long",
                "ErrorStatistics": {},
                "FaultStatistics": {},
                "TotalCount": "long",
                "TotalResponseTime": "double"
            },
            "ServiceForecastStatistics": {
                "FaultCountHigh": "long",
                "FaultCountLow": "long"
            },
            "ResponseTimeHistogram": []
        }
    ],
    "ContainsOldGroupVersions": "boolean",
    "NextToken": "string"
}
```
