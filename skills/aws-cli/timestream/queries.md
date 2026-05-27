# Queries

### 3.1 `query`

Executes a Timestream query. Queries time out after 60 seconds. **Paginated operation.**

**Synopsis:**
```bash
aws timestream-query query \
    --query-string <value> \
    [--client-token <value>] \
    [--query-insights <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--query-string` | **Yes** | string | -- | The query to execute (1-262144 chars) |
| `--client-token` | No | string | auto-generated | Idempotency token (32-128 ASCII chars, valid for 5 min) |
| `--query-insights` | No | structure | None | Enable query insights. `Mode`: `ENABLED_WITH_RATE_CONTROL` or `DISABLED` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "QueryId": "string",
    "NextToken": "string",
    "Rows": [
        {
            "Data": [
                {
                    "ScalarValue": "string",
                    "TimeSeriesValue": [
                        {
                            "Time": "string",
                            "Value": {
                                "ScalarValue": "string",
                                "NullValue": "boolean"
                            }
                        }
                    ],
                    "ArrayValue": [],
                    "RowValue": {
                        "Data": []
                    },
                    "NullValue": "boolean"
                }
            ]
        }
    ],
    "ColumnInfo": [
        {
            "Name": "string",
            "Type": {
                "ScalarType": "VARCHAR|BOOLEAN|BIGINT|DOUBLE|TIMESTAMP|DATE|TIME|INTERVAL_DAY_TO_SECOND|INTERVAL_YEAR_TO_MONTH|UNKNOWN|INTEGER",
                "ArrayColumnInfo": {},
                "TimeSeriesMeasureValueColumnInfo": {},
                "RowColumnInfo": []
            }
        }
    ],
    "QueryStatus": {
        "ProgressPercentage": "double",
        "CumulativeBytesScanned": "long",
        "CumulativeBytesMetered": "long"
    },
    "QueryInsightsResponse": {
        "QuerySpatialCoverage": {
            "Max": {
                "Value": "double",
                "TableArn": "string",
                "PartitionKey": ["string"]
            }
        },
        "QueryTemporalRange": {
            "Max": {
                "Value": "long",
                "TableArn": "string"
            }
        },
        "QueryTableCount": "long",
        "OutputRows": "long",
        "OutputBytes": "long"
    }
}
```

**Key Notes:**
- Query timeout: 60 seconds
- Max row size: 1 MB (including metadata)
- QueryInsights rate limit: 1 QPS when enabled
- Use `NextToken` with the same query string and IAM principal for pagination

---

### 3.2 `cancel-query`

Cancels a query that has been issued. Cancellation is guaranteed only if the query has not completed execution before cancellation.

**Synopsis:**
```bash
aws timestream-query cancel-query \
    --query-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--query-id` | **Yes** | string | -- | The ID of the query to cancel |

**Output Schema:**
```json
{
    "CancellationMessage": "string"
}
```

---

### 3.3 `prepare-query`

Validates and returns the query type (SELECT or other), column metadata, and parameters without executing the query.

**Synopsis:**
```bash
aws timestream-query prepare-query \
    --query-string <value> \
    [--validate-only | --no-validate-only] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--query-string` | **Yes** | string | -- | The query string to prepare (1-262144 chars) |
| `--validate-only` | No | boolean | false | If true, only validates without returning column info |

**Output Schema:**
```json
{
    "QueryString": "string",
    "Columns": [
        {
            "Name": "string",
            "Type": {
                "ScalarType": "VARCHAR|BOOLEAN|BIGINT|DOUBLE|TIMESTAMP|DATE|TIME|INTERVAL_DAY_TO_SECOND|INTERVAL_YEAR_TO_MONTH|UNKNOWN|INTEGER",
                "ArrayColumnInfo": {},
                "TimeSeriesMeasureValueColumnInfo": {},
                "RowColumnInfo": []
            },
            "DatabaseName": "string",
            "TableName": "string",
            "Aliased": "boolean"
        }
    ],
    "Parameters": [
        {
            "Name": "string",
            "Type": {}
        }
    ]
}
```

---

### 3.4 `describe-endpoints`

Describes the endpoints for the Timestream service. Available in both `timestream-write` and `timestream-query` namespaces.

**Synopsis:**
```bash
aws timestream-write describe-endpoints \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]

aws timestream-query describe-endpoints \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output Schema:**
```json
{
    "Endpoints": [
        {
            "Address": "string",
            "CachePeriodInMinutes": "long"
        }
    ]
}
```

---

### 3.5 `describe-account-settings`

Describes the account-level settings for the Timestream query service.

**Synopsis:**
```bash
aws timestream-query describe-account-settings \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output Schema:**
```json
{
    "MaxQueryTCU": "integer",
    "QueryPricingModel": "BYTES_SCANNED|COMPUTE_UNITS",
    "QueryCompute": {
        "ComputeMode": "ON_DEMAND|PROVISIONED",
        "ProvisionedCapacity": {
            "ActiveQueryTCU": "integer",
            "NotificationConfiguration": {
                "SnsConfiguration": {
                    "TopicArn": "string"
                },
                "RoleArn": "string"
            },
            "LastUpdate": {
                "TargetQueryTCU": "integer",
                "Status": "PENDING|FAILED|SUCCEEDED",
                "StatusMessage": "string"
            }
        }
    }
}
```

---

### 3.6 `update-account-settings`

Updates the account-level settings for the Timestream query service.

**Synopsis:**
```bash
aws timestream-query update-account-settings \
    [--max-query-tcu <value>] \
    [--query-pricing-model <value>] \
    [--query-compute <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--max-query-tcu` | No | integer | unchanged | Maximum query TCU |
| `--query-pricing-model` | No | string | unchanged | `BYTES_SCANNED` or `COMPUTE_UNITS` |
| `--query-compute` | No | structure | unchanged | Compute mode configuration |

**Output Schema:** Same as `describe-account-settings` output.
