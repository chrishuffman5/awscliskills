# Traces

### 1.1 `batch-get-traces`

Retrieves a list of traces specified by ID. Each trace is a collection of segment documents from a single request. **Paginated operation.**

**Synopsis:**
```bash
aws xray batch-get-traces \
    --trace-ids <value> \
    [--starting-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--trace-ids` | **Yes** | list(string) | -- | Trace IDs to retrieve (max 5) |
| `--starting-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "Traces": [
        {
            "Id": "string",
            "Duration": "double",
            "LimitExceeded": "boolean",
            "Segments": [
                {
                    "Id": "string",
                    "Document": "string"
                }
            ]
        }
    ],
    "UnprocessedTraceIds": ["string"],
    "NextToken": "string"
}
```

---

### 1.2 `get-trace-summaries`

Retrieves IDs and annotations for traces available for a specified time frame using an optional filter. **Paginated operation.**

**Synopsis:**
```bash
aws xray get-trace-summaries \
    --start-time <value> \
    --end-time <value> \
    [--time-range-type <value>] \
    [--sampling | --no-sampling] \
    [--sampling-strategy <value>] \
    [--filter-expression <value>] \
    [--starting-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--start-time` | **Yes** | timestamp | -- | Start of the time range (Unix epoch or ISO 8601) |
| `--end-time` | **Yes** | timestamp | -- | End of the time range |
| `--time-range-type` | No | string | `TraceId` | Time range type: `TraceId`, `Event` |
| `--sampling` | No | boolean | true | Enable sampling of trace summaries |
| `--sampling-strategy` | No | structure | None | Sampling strategy. Shorthand: `Name=PartialScan\|FixedRate,Value=double` |
| `--filter-expression` | No | string | None | Filter expression (e.g., `service("my-service")`) |
| `--starting-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "TraceSummaries": [
        {
            "Id": "string",
            "Duration": "double",
            "ResponseTime": "double",
            "HasFault": "boolean",
            "HasError": "boolean",
            "HasThrottle": "boolean",
            "IsPartial": "boolean",
            "Http": {
                "HttpURL": "string",
                "HttpStatus": "integer",
                "HttpMethod": "string",
                "UserAgent": "string",
                "ClientIp": "string"
            },
            "Annotations": {
                "string": [
                    {
                        "AnnotationValue": {
                            "NumberValue": "double",
                            "BooleanValue": "boolean",
                            "StringValue": "string"
                        },
                        "ServiceIds": [
                            {
                                "Name": "string",
                                "Names": ["string"],
                                "AccountId": "string",
                                "Type": "string"
                            }
                        ]
                    }
                ]
            },
            "Users": [
                {
                    "UserName": "string",
                    "ServiceIds": []
                }
            ],
            "ServiceIds": [],
            "ResourceARNs": [
                {
                    "ARN": "string"
                }
            ],
            "InstanceIds": [
                {
                    "Id": "string"
                }
            ],
            "AvailabilityZones": [
                {
                    "Name": "string"
                }
            ],
            "EntryPoint": {},
            "FaultRootCauses": [],
            "ErrorRootCauses": [],
            "ResponseTimeRootCauses": [],
            "Revision": "integer",
            "MatchedEventTime": "timestamp"
        }
    ],
    "ApproximateTime": "timestamp",
    "TracesProcessedCount": "long",
    "NextToken": "string"
}
```

---

### 1.3 `get-trace-graph`

Retrieves a service graph for one or more specific trace IDs. **Paginated operation.**

**Synopsis:**
```bash
aws xray get-trace-graph \
    --trace-ids <value> \
    [--starting-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--trace-ids` | **Yes** | list(string) | -- | Trace IDs for the service graph |
| `--starting-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
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
                    "ResponseTimeHistogram": [],
                    "Aliases": []
                }
            ],
            "SummaryStatistics": {
                "OkCount": "long",
                "ErrorStatistics": {},
                "FaultStatistics": {},
                "TotalCount": "long",
                "TotalResponseTime": "double"
            },
            "DurationHistogram": [],
            "ResponseTimeHistogram": []
        }
    ],
    "NextToken": "string"
}
```

---

### 1.4 `put-trace-segments`

Uploads trace segment documents to X-Ray. Used by the X-Ray daemon and SDK.

**Synopsis:**
```bash
aws xray put-trace-segments \
    --trace-segment-documents <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--trace-segment-documents` | **Yes** | list(string) | -- | JSON segment documents to upload |

**Output Schema:**
```json
{
    "UnprocessedTraceSegments": [
        {
            "Id": "string",
            "ErrorCode": "string",
            "Message": "string"
        }
    ]
}
```

---

### 1.5 `start-trace-retrieval`

Initiates a trace retrieval process. Retrieves traces matching a specified time range and optional filter expression.

**Synopsis:**
```bash
aws xray start-trace-retrieval \
    --start-time <value> \
    --end-time <value> \
    [--filter-expression <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--start-time` | **Yes** | timestamp | -- | Start of the retrieval time range |
| `--end-time` | **Yes** | timestamp | -- | End of the retrieval time range |
| `--filter-expression` | No | string | None | Filter expression for trace retrieval |

**Output Schema:**
```json
{
    "RetrievalToken": "string"
}
```

---

### 1.6 `cancel-trace-retrieval`

Cancels an ongoing trace retrieval operation.

**Synopsis:**
```bash
aws xray cancel-trace-retrieval \
    --retrieval-token <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--retrieval-token` | **Yes** | string | -- | Retrieval token from start-trace-retrieval |

**Output Schema:**
```json
{}
```

---

### 1.7 `list-retrieved-traces`

Lists traces retrieved by a previous `start-trace-retrieval` call. **Paginated operation.**

**Synopsis:**
```bash
aws xray list-retrieved-traces \
    --retrieval-token <value> \
    [--trace-format <value>] \
    [--starting-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--retrieval-token` | **Yes** | string | -- | Retrieval token from start-trace-retrieval |
| `--trace-format` | No | string | `XRAY` | Trace format: `XRAY`, `OTEL` |
| `--starting-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "RetrievalStatus": "SCHEDULED|RUNNING|COMPLETE|FAILED|CANCELLED|TIMEOUT",
    "TraceFormat": "XRAY|OTEL",
    "Traces": [
        {
            "Id": "string",
            "Duration": "double",
            "Spans": [
                {
                    "Id": "string",
                    "Document": "string"
                }
            ]
        }
    ],
    "NextToken": "string"
}
```

---

### 1.8 `get-retrieved-traces-graph`

Gets the service graph for traces retrieved by a previous retrieval operation. **Paginated operation.**

**Synopsis:**
```bash
aws xray get-retrieved-traces-graph \
    --retrieval-token <value> \
    [--starting-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--retrieval-token` | **Yes** | string | -- | Retrieval token from start-trace-retrieval |
| `--starting-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "RetrievalStatus": "SCHEDULED|RUNNING|COMPLETE|FAILED|CANCELLED|TIMEOUT",
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
            "Edges": [],
            "SummaryStatistics": {},
            "DurationHistogram": [],
            "ResponseTimeHistogram": []
        }
    ],
    "NextToken": "string"
}
```

---

### 1.9 `get-trace-segment-destination`

Returns the current trace segment destination configuration.

**Synopsis:**
```bash
aws xray get-trace-segment-destination \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

No required parameters.

**Output Schema:**
```json
{
    "Destination": "XRay|CloudWatchLogs",
    "Status": "PENDING|ACTIVE"
}
```

---

### 1.10 `update-trace-segment-destination`

Updates the trace segment destination configuration.

**Synopsis:**
```bash
aws xray update-trace-segment-destination \
    [--destination <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--destination` | No | string | None | Destination: `XRay`, `CloudWatchLogs` |

**Output Schema:**
```json
{
    "Destination": "XRay|CloudWatchLogs",
    "Status": "PENDING|ACTIVE"
}
```
