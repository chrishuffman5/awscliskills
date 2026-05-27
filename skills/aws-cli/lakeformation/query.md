# Query

Lake Formation query planning enables optimized data access for engines like Amazon Athena and Amazon Redshift Spectrum by splitting queries into work units.

### 9.1 `start-query-planning`

Submits a query for planning. Returns a query ID for tracking.

**Synopsis:**
```bash
aws lakeformation start-query-planning \
    --query-planning-context <value> \
    --query-string <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--query-planning-context` | **Yes** | structure | -- | Context including database, catalog, and transaction |
| `--query-string` | **Yes** | string | -- | SQL query string |

**Query Planning Context:**
```json
{
    "CatalogId": "string",
    "DatabaseName": "string",
    "QueryAsOfTime": "timestamp",
    "QueryParameters": {
        "key": "string"
    },
    "TransactionId": "string"
}
```

**Output Schema:**
```json
{
    "QueryId": "string"
}
```

---

### 9.2 `get-query-state`

Returns the state of a query planning request.

**Synopsis:**
```bash
aws lakeformation get-query-state \
    --query-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--query-id` | **Yes** | string | -- | Query ID from start-query-planning |

**Output Schema:**
```json
{
    "Error": "string",
    "State": "PENDING|WORKUNITS_AVAILABLE|ERROR|FINISHED|EXPIRED"
}
```

---

### 9.3 `get-query-statistics`

Returns execution statistics for a query.

**Synopsis:**
```bash
aws lakeformation get-query-statistics \
    --query-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--query-id` | **Yes** | string | -- | Query ID |

**Output Schema:**
```json
{
    "ExecutionStatistics": {
        "AverageExecutionTimeMillis": "long",
        "DataScannedBytes": "long",
        "WorkUnitsExecutedCount": "long"
    },
    "PlanningStatistics": {
        "EstimatedDataToScanBytes": "long",
        "PlanningTimeMillis": "long",
        "QueueTimeMillis": "long",
        "WorkUnitsGeneratedCount": "long"
    },
    "QuerySubmissionTime": "timestamp"
}
```

---

### 9.4 `get-work-units`

Returns the work units for a completed query plan. **Paginated operation.**

**Synopsis:**
```bash
aws lakeformation get-work-units \
    --query-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--query-id` | **Yes** | string | -- | Query ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items |

**Output Schema:**
```json
{
    "QueryId": "string",
    "WorkUnitRanges": [
        {
            "WorkUnitIdMax": "long",
            "WorkUnitIdMin": "long",
            "WorkUnitToken": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 9.5 `get-work-unit-results`

Returns the results for a specific work unit.

**Synopsis:**
```bash
aws lakeformation get-work-unit-results \
    --query-id <value> \
    --work-unit-id <value> \
    --work-unit-token <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--query-id` | **Yes** | string | -- | Query ID |
| `--work-unit-id` | **Yes** | long | -- | Work unit ID |
| `--work-unit-token` | **Yes** | string | -- | Work unit token from get-work-units |

**Output Schema:**
```json
{
    "ResultStream": "streaming blob"
}
```

The result stream contains Apache Arrow format data.
