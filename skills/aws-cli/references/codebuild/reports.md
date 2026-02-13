# Reports

### 5.1 `batch-get-reports`

Returns information about one or more reports.

**Synopsis:**
```bash
aws codebuild batch-get-reports \
    --report-arns <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--report-arns` | **Yes** | list(string) | -- | Report ARNs (max 100) |

**Output Schema:**
```json
{
    "reports": [
        {
            "arn": "string",
            "type": "TEST|CODE_COVERAGE",
            "name": "string",
            "reportGroupArn": "string",
            "executionId": "string",
            "status": "GENERATING|SUCCEEDED|FAILED|INCOMPLETE|DELETING",
            "created": "timestamp",
            "expired": "timestamp",
            "exportConfig": {
                "exportConfigType": "S3|NO_EXPORT",
                "s3Destination": { }
            },
            "truncated": true|false,
            "testSummary": {
                "total": "integer",
                "statusCounts": {
                    "string": "integer"
                },
                "durationInNanoSeconds": "long"
            },
            "codeCoverageSummary": {
                "lineCoveragePercentage": "double",
                "linesCovered": "integer",
                "linesMissed": "integer",
                "branchCoveragePercentage": "double",
                "branchesCovered": "integer",
                "branchesMissed": "integer"
            }
        }
    ],
    "reportsNotFound": ["string"]
}
```

---

### 5.2 `delete-report`

Deletes a report.

**Synopsis:**
```bash
aws codebuild delete-report \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | Report ARN |

**Output Schema:**
```json
{}
```

---

### 5.3 `describe-test-cases`

Returns a list of test cases for a report. **Paginated operation.**

**Synopsis:**
```bash
aws codebuild describe-test-cases \
    --report-arn <value> \
    [--filter <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--report-arn` | **Yes** | string | -- | Report ARN |
| `--filter` | No | structure | None | Filter by status. Shorthand: `status=SUCCEEDED\|FAILED\|ERROR\|SKIPPED\|UNKNOWN` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "testCases": [
        {
            "reportArn": "string",
            "testRawDataPath": "string",
            "prefix": "string",
            "name": "string",
            "status": "string",
            "durationInNanoSeconds": "long",
            "message": "string",
            "expired": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 5.4 `list-reports`

Returns a list of report ARNs. **Paginated operation.**

**Synopsis:**
```bash
aws codebuild list-reports \
    [--sort-order <value>] \
    [--filter <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--sort-order` | No | string | `ASCENDING` | Sort order: `ASCENDING`, `DESCENDING` |
| `--filter` | No | structure | None | Filter by status. Shorthand: `status=GENERATING\|SUCCEEDED\|FAILED\|INCOMPLETE\|DELETING` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "reports": ["string"],
    "nextToken": "string"
}
```

---

### 5.5 `list-reports-for-report-group`

Returns a list of report ARNs belonging to a report group. **Paginated operation.**

**Synopsis:**
```bash
aws codebuild list-reports-for-report-group \
    --report-group-arn <value> \
    [--sort-order <value>] \
    [--filter <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--report-group-arn` | **Yes** | string | -- | Report group ARN |
| `--sort-order` | No | string | `ASCENDING` | Sort order: `ASCENDING`, `DESCENDING` |
| `--filter` | No | structure | None | Filter by status |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "reports": ["string"],
    "nextToken": "string"
}
```
