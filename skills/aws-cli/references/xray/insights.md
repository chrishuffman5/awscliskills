# Insights

### 5.1 `get-insight`

Returns the details of a specific insight.

**Synopsis:**
```bash
aws xray get-insight \
    --insight-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--insight-id` | **Yes** | string | -- | ID of the insight |

**Output Schema:**
```json
{
    "Insight": {
        "InsightId": "string",
        "GroupARN": "string",
        "GroupName": "string",
        "RootCauseServiceId": {
            "Name": "string",
            "Names": ["string"],
            "AccountId": "string",
            "Type": "string"
        },
        "Categories": ["FAULT"],
        "State": "ACTIVE|CLOSED",
        "StartTime": "timestamp",
        "EndTime": "timestamp",
        "Summary": "string",
        "ClientRequestImpactStatistics": {
            "FaultCount": "long",
            "OkCount": "long",
            "TotalCount": "long"
        },
        "RootCauseServiceRequestImpactStatistics": {
            "FaultCount": "long",
            "OkCount": "long",
            "TotalCount": "long"
        },
        "TopAnomalousServices": [
            {
                "ServiceId": {
                    "Name": "string",
                    "Names": ["string"],
                    "AccountId": "string",
                    "Type": "string"
                }
            }
        ]
    }
}
```

---

### 5.2 `get-insight-events`

Returns events associated with an insight. **Paginated operation.**

**Synopsis:**
```bash
aws xray get-insight-events \
    --insight-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--insight-id` | **Yes** | string | -- | ID of the insight |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "InsightEvents": [
        {
            "Summary": "string",
            "EventTime": "timestamp",
            "ClientRequestImpactStatistics": {
                "FaultCount": "long",
                "OkCount": "long",
                "TotalCount": "long"
            },
            "RootCauseServiceRequestImpactStatistics": {
                "FaultCount": "long",
                "OkCount": "long",
                "TotalCount": "long"
            },
            "TopAnomalousServices": [
                {
                    "ServiceId": {
                        "Name": "string",
                        "Names": ["string"],
                        "AccountId": "string",
                        "Type": "string"
                    }
                }
            ]
        }
    ],
    "NextToken": "string"
}
```

---

### 5.3 `get-insight-impact-graph`

Returns the impact graph for an insight, showing affected services and their statistics.

**Synopsis:**
```bash
aws xray get-insight-impact-graph \
    --insight-id <value> \
    --start-time <value> \
    --end-time <value> \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--insight-id` | **Yes** | string | -- | ID of the insight |
| `--start-time` | **Yes** | timestamp | -- | Start of the time range |
| `--end-time` | **Yes** | timestamp | -- | End of the time range |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "InsightId": "string",
    "StartTime": "timestamp",
    "EndTime": "timestamp",
    "ServiceGraphStartTime": "timestamp",
    "ServiceGraphEndTime": "timestamp",
    "Services": [
        {
            "ReferenceId": "integer",
            "Type": "string",
            "Name": "string",
            "Names": ["string"],
            "AccountId": "string",
            "Edges": [
                {
                    "ReferenceId": "integer"
                }
            ]
        }
    ],
    "NextToken": "string"
}
```

---

### 5.4 `get-insight-summaries`

Returns a list of insight summaries for a group over a time range. **Paginated operation.**

**Synopsis:**
```bash
aws xray get-insight-summaries \
    --start-time <value> \
    --end-time <value> \
    [--group-name <value>] \
    [--group-arn <value>] \
    [--states <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--start-time` | **Yes** | timestamp | -- | Start of the time range |
| `--end-time` | **Yes** | timestamp | -- | End of the time range |
| `--group-name` | No | string | None | Name of the group |
| `--group-arn` | No | string | None | ARN of the group |
| `--states` | No | list(string) | None | Filter by state: `ACTIVE`, `CLOSED` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "InsightSummaries": [
        {
            "InsightId": "string",
            "GroupARN": "string",
            "GroupName": "string",
            "RootCauseServiceId": {
                "Name": "string",
                "Names": ["string"],
                "AccountId": "string",
                "Type": "string"
            },
            "Categories": ["FAULT"],
            "State": "ACTIVE|CLOSED",
            "StartTime": "timestamp",
            "EndTime": "timestamp",
            "Summary": "string",
            "ClientRequestImpactStatistics": {
                "FaultCount": "long",
                "OkCount": "long",
                "TotalCount": "long"
            },
            "RootCauseServiceRequestImpactStatistics": {
                "FaultCount": "long",
                "OkCount": "long",
                "TotalCount": "long"
            },
            "TopAnomalousServices": [],
            "LastUpdateTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```
