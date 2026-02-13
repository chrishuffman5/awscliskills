# Map Runs

### 4.1 `describe-map-run`

Gets information about a Map Run, including item counts, progress, and configuration.

**Synopsis:**
```bash
aws stepfunctions describe-map-run \
    --map-run-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--map-run-arn` | **Yes** | string | -- | ARN of the Map Run |

**Output Schema:**
```json
{
    "mapRunArn": "string",
    "executionArn": "string",
    "status": "RUNNING|SUCCEEDED|FAILED|ABORTED",
    "startDate": "timestamp",
    "stopDate": "timestamp",
    "maxConcurrency": "integer",
    "toleratedFailurePercentage": "float",
    "toleratedFailureCount": "long",
    "itemCounts": {
        "pending": "long",
        "running": "long",
        "succeeded": "long",
        "failed": "long",
        "timedOut": "long",
        "aborted": "long",
        "total": "long",
        "resultsWritten": "long",
        "failuresNotRedrivable": "long",
        "pendingRedrive": "long"
    },
    "executionCounts": {
        "pending": "long",
        "running": "long",
        "succeeded": "long",
        "failed": "long",
        "timedOut": "long",
        "aborted": "long",
        "total": "long",
        "resultsWritten": "long",
        "failuresNotRedrivable": "long",
        "pendingRedrive": "long"
    },
    "redriveCount": "integer",
    "redriveDate": "timestamp"
}
```

---

### 4.2 `list-map-runs`

Lists Map Runs started by a child execution of a Distributed Map state. **Paginated operation.**

**Synopsis:**
```bash
aws stepfunctions list-map-runs \
    --execution-arn <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--execution-arn` | **Yes** | string | -- | ARN of the execution |
| `--max-results` | No | integer | None | Maximum items (1-1000) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "mapRuns": [
        {
            "executionArn": "string",
            "mapRunArn": "string",
            "stateMachineArn": "string",
            "startDate": "timestamp",
            "stopDate": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 4.3 `update-map-run`

Updates the configuration of a Map Run (concurrency and failure tolerance).

**Synopsis:**
```bash
aws stepfunctions update-map-run \
    --map-run-arn <value> \
    [--max-concurrency <value>] \
    [--tolerated-failure-percentage <value>] \
    [--tolerated-failure-count <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--map-run-arn` | **Yes** | string | -- | ARN of the Map Run |
| `--max-concurrency` | No | integer | None | Maximum number of concurrent child executions (0 = unlimited) |
| `--tolerated-failure-percentage` | No | float | None | Maximum percentage of failed items before the Map Run fails (0.0-100.0) |
| `--tolerated-failure-count` | No | long | None | Maximum number of failed items before the Map Run fails (0 = no tolerance) |

**Output:** None
