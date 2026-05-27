# Metrics

### 8.1 `start-metrics-export`

Starts a metrics export task from Resilience Hub.

**Synopsis:**
```bash
aws resiliencehub start-metrics-export \
    [--bucket-name <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bucket-name` | No | string | None | S3 bucket name for exported metrics |
| `--client-token` | No | string | Auto | Idempotency token (1-63 chars) |

**Output Schema:**
```json
{
    "metricsExportId": "string",
    "status": "Pending|InProgress|Failed|Success"
}
```

---

### 8.2 `describe-metrics-export`

Describes a metrics export task.

**Synopsis:**
```bash
aws resiliencehub describe-metrics-export \
    --metrics-export-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--metrics-export-id` | **Yes** | string | -- | Metrics export task ID (1-255 chars) |

**Output Schema:**
```json
{
    "errorMessage": "string",
    "exportLocation": {
        "bucket": "string",
        "prefix": "string"
    },
    "metricsExportId": "string",
    "status": "Pending|InProgress|Failed|Success"
}
```

---

### 8.3 `list-metrics`

Lists metrics from Resilience Hub. **Paginated operation.**

**Synopsis:**
```bash
aws resiliencehub list-metrics \
    [--conditions <value>] \
    [--data-source <value>] \
    [--fields <value>] \
    [--sorts <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--conditions` | No | list | None | Filter conditions (0-50). Each: `field`, `operator`, `value` |
| `--data-source` | No | string | None | Data source name (1-255 chars) |
| `--fields` | No | list | None | Fields to return (0-50). Each: `name`, optional `aggregation` |
| `--sorts` | No | list | None | Sort order (0-50). Each: `field`, optional `ascending` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Condition Operators:** `Equals`, `NotEquals`, `GreaterThen`, `GreaterOrEquals`, `LessThen`, `LessOrEquals`

**Field Aggregations:** `Min`, `Max`, `Sum`, `Avg`, `Count`

**Output Schema:**
```json
{
    "rows": [
        ["string"]
    ],
    "nextToken": "string"
}
```
