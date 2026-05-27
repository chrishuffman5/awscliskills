# Logs Insights

### 14.1 `start-query`

Starts a CloudWatch Logs Insights query. Results are available via `get-query-results`.

**Synopsis:**
```bash
aws logs start-query \
    --start-time <value> \
    --end-time <value> \
    --query-string <value> \
    [--log-group-name <value>] \
    [--log-group-names <value>] \
    [--log-group-identifiers <value>] \
    [--query-language <value>] \
    [--limit <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--start-time` | **Yes** | long | -- | Start of time range (epoch seconds) |
| `--end-time` | **Yes** | long | -- | End of time range (epoch seconds) |
| `--query-string` | **Yes** | string | -- | Logs Insights query (max 10,000 chars) |
| `--log-group-name` | No* | string | -- | Single log group (1-512 chars). *Must specify one of the three log group params |
| `--log-group-names` | No* | list | -- | Log group names (max 50) |
| `--log-group-identifiers` | No* | list | -- | Log group names or ARNs (max 50) |
| `--query-language` | No | string | `CWLI` | `CWLI`, `SQL`, or `PPL` |
| `--limit` | No | integer | 10000 | Max events to return (1-10,000) |

**Output Schema:**
```json
{
    "queryId": "string"
}
```

---

### 14.2 `get-query-results`

Retrieves results of a Logs Insights query.

**Synopsis:**
```bash
aws logs get-query-results \
    --query-id <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--query-id` | **Yes** | string | -- | Query ID from `start-query` (1-256 chars) |

**Output Schema:**
```json
{
    "queryLanguage": "CWLI|SQL|PPL",
    "results": [
        [
            {
                "field": "string",
                "value": "string"
            }
        ]
    ],
    "statistics": {
        "recordsMatched": double,
        "recordsScanned": double,
        "estimatedRecordsSkipped": double,
        "bytesScanned": double,
        "estimatedBytesSkipped": double,
        "logGroupsScanned": double
    },
    "status": "Scheduled|Running|Complete|Failed|Cancelled|Timeout|Unknown",
    "encryptionKey": "string"
}
```

---

### 14.3 `stop-query`

Stops a running Logs Insights query.

**Synopsis:**
```bash
aws logs stop-query \
    --query-id <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--query-id` | **Yes** | string | -- | Query ID to stop (1-256 chars) |

**Output Schema:**
```json
{
    "success": true|false
}
```

---

### 14.4 `describe-queries`

Lists Logs Insights queries that are scheduled, running, or recently completed. **Paginated.**

**Synopsis:**
```bash
aws logs describe-queries \
    [--log-group-name <value>] \
    [--status <value>] \
    [--max-items <value>] \
    [--starting-token <value>] \
    [--page-size <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--log-group-name` | No | string | -- | Filter by log group name (1-512 chars) |
| `--status` | No | string | -- | `Scheduled`, `Running`, `Complete`, `Failed`, `Cancelled`, `Timeout`, `Unknown` |
| `--max-items` | No | integer | -- | Total items to return |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |

**Output Schema:**
```json
{
    "queries": [
        {
            "queryId": "string",
            "queryString": "string",
            "status": "Scheduled|Running|Complete|Failed|Cancelled|Timeout|Unknown",
            "createTime": long,
            "logGroupName": "string"
        }
    ],
    "nextToken": "string"
}
```

---
