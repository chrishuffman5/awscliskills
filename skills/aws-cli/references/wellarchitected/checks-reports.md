# Checks & Reports

### 9.1 `list-check-details`

Lists Trusted Advisor check details for a workload. **Paginated.**

**Synopsis:**
```bash
aws wellarchitected list-check-details \
    --workload-id <value> \
    --lens-arn <value> \
    --pillar-id <value> \
    --question-id <value> \
    --choice-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workload-id` | **Yes** | string | -- | Workload ID |
| `--lens-arn` | **Yes** | string | -- | Lens ARN |
| `--pillar-id` | **Yes** | string | -- | Pillar ID |
| `--question-id` | **Yes** | string | -- | Question ID |
| `--choice-id` | **Yes** | string | -- | Choice ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call (max 100) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "CheckDetails": [
        {
            "Id": "string",
            "Name": "string",
            "Description": "string",
            "Provider": "TRUSTED_ADVISOR",
            "LensArn": "string",
            "PillarId": "string",
            "QuestionId": "string",
            "ChoiceId": "string",
            "Status": "FETCH_FAILED|WARNING|ERROR|OK|NOT_AVAILABLE",
            "AccountId": "string",
            "FlaggedResources": "integer",
            "Reason": "ASSUME_ROLE_ERROR|ACCESS_DENIED|UNKNOWN_ERROR|PREMIUM_SUPPORT_REQUIRED",
            "UpdatedAt": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 9.2 `list-check-summaries`

Lists Trusted Advisor check summaries for a workload. **Paginated.**

**Synopsis:**
```bash
aws wellarchitected list-check-summaries \
    --workload-id <value> \
    --lens-arn <value> \
    --pillar-id <value> \
    --question-id <value> \
    --choice-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workload-id` | **Yes** | string | -- | Workload ID |
| `--lens-arn` | **Yes** | string | -- | Lens ARN |
| `--pillar-id` | **Yes** | string | -- | Pillar ID |
| `--question-id` | **Yes** | string | -- | Question ID |
| `--choice-id` | **Yes** | string | -- | Choice ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "CheckSummaries": [
        {
            "Id": "string",
            "Name": "string",
            "Provider": "TRUSTED_ADVISOR",
            "Description": "string",
            "UpdatedAt": "timestamp",
            "LensArn": "string",
            "PillarId": "string",
            "QuestionId": "string",
            "ChoiceId": "string",
            "Status": "FETCH_FAILED|WARNING|ERROR|OK|NOT_AVAILABLE",
            "AccountSummary": {
                "string": "integer"
            }
        }
    ],
    "NextToken": "string"
}
```

---

### 9.3 `get-consolidated-report`

Retrieves a consolidated report across all workloads. **Paginated.**

**Synopsis:**
```bash
aws wellarchitected get-consolidated-report \
    --format <value> \
    [--include-shared-resources | --no-include-shared-resources] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--format` | **Yes** | string | -- | Report format: `PDF` or `JSON` |
| `--include-shared-resources` | No | boolean | false | Include shared workloads |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Metrics": [
        {
            "MetricType": "WORKLOAD",
            "RiskCounts": {
                "UNANSWERED": "integer",
                "HIGH": "integer",
                "MEDIUM": "integer",
                "NONE": "integer",
                "NOT_APPLICABLE": "integer"
            },
            "WorkloadId": "string",
            "WorkloadName": "string",
            "WorkloadArn": "string",
            "UpdatedAt": "timestamp",
            "Lenses": [
                {
                    "LensArn": "string",
                    "Pillars": [
                        {
                            "PillarId": "string",
                            "RiskCounts": {}
                        }
                    ],
                    "RiskCounts": {}
                }
            ],
            "LensesAppliedCount": "integer"
        }
    ],
    "NextToken": "string",
    "Base64String": "string"
}
```

---

### 9.4 `list-notifications`

Lists notifications for a workload. **Paginated.**

**Synopsis:**
```bash
aws wellarchitected list-notifications \
    [--workload-id <value>] \
    [--resource-arn <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workload-id` | No | string | None | Filter by workload |
| `--resource-arn` | No | string | None | Filter by resource ARN |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "NotificationSummaries": [
        {
            "Type": "LENS_VERSION_UPGRADED|LENS_VERSION_DEPRECATED",
            "LensUpgradeSummary": {
                "WorkloadId": "string",
                "WorkloadName": "string",
                "LensAlias": "string",
                "LensArn": "string",
                "CurrentLensVersion": "string",
                "LatestLensVersion": "string",
                "ResourceArn": "string",
                "ResourceName": "string"
            }
        }
    ],
    "NextToken": "string"
}
```
