# Reviews

### 3.1 `get-lens-review`

Retrieves a lens review for a workload.

**Synopsis:**
```bash
aws wellarchitected get-lens-review \
    --workload-id <value> \
    --lens-alias <value> \
    [--milestone-number <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workload-id` | **Yes** | string | -- | Workload ID (32 hex chars) |
| `--lens-alias` | **Yes** | string | -- | Lens alias or ARN (1-128 chars) |
| `--milestone-number` | No | integer | None | Milestone number (1-100) |

**Output Schema:**
```json
{
    "WorkloadId": "string",
    "MilestoneNumber": "integer",
    "LensReview": {
        "LensAlias": "string",
        "LensArn": "string",
        "LensVersion": "string",
        "LensName": "string",
        "LensStatus": "CURRENT|NOT_CURRENT|DEPRECATED|DELETED|UNSHARED",
        "PillarReviewSummaries": [
            {
                "PillarId": "string",
                "PillarName": "string",
                "Notes": "string",
                "RiskCounts": {
                    "UNANSWERED": "integer",
                    "HIGH": "integer",
                    "MEDIUM": "integer",
                    "NONE": "integer",
                    "NOT_APPLICABLE": "integer"
                },
                "PrioritizedRiskCounts": {}
            }
        ],
        "UpdatedAt": "timestamp",
        "Notes": "string",
        "RiskCounts": {},
        "PrioritizedRiskCounts": {},
        "Profiles": [
            {"ProfileArn": "string", "ProfileVersion": "string"}
        ],
        "JiraConfiguration": {}
    }
}
```

---

### 3.2 `list-lens-reviews`

Lists lens reviews for a workload. **Paginated.**

**Synopsis:**
```bash
aws wellarchitected list-lens-reviews \
    --workload-id <value> \
    [--milestone-number <value>] \
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
| `--milestone-number` | No | integer | None | Milestone number |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "WorkloadId": "string",
    "MilestoneNumber": "integer",
    "LensReviewSummaries": [
        {
            "LensAlias": "string",
            "LensArn": "string",
            "LensVersion": "string",
            "LensName": "string",
            "LensStatus": "string",
            "UpdatedAt": "timestamp",
            "RiskCounts": {},
            "Profiles": [],
            "PrioritizedRiskCounts": {}
        }
    ],
    "NextToken": "string"
}
```

---

### 3.3 `update-lens-review`

Updates a lens review (notes, pillar notes).

**Synopsis:**
```bash
aws wellarchitected update-lens-review \
    --workload-id <value> \
    --lens-alias <value> \
    [--lens-notes <value>] \
    [--pillar-notes <value>] \
    [--jira-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workload-id` | **Yes** | string | -- | Workload ID |
| `--lens-alias` | **Yes** | string | -- | Lens alias or ARN |
| `--lens-notes` | No | string | None | Notes for the lens review (max 2084 chars) |
| `--pillar-notes` | No | map | None | Map of pillar ID to notes |
| `--jira-configuration` | No | structure | None | Jira configuration |

**Output Schema:**
```json
{
    "WorkloadId": "string",
    "LensReview": {
        "LensAlias": "string",
        "LensArn": "string",
        "LensVersion": "string",
        "LensName": "string",
        "Notes": "string",
        "UpdatedAt": "timestamp",
        "RiskCounts": {},
        "PillarReviewSummaries": []
    }
}
```

---

### 3.4 `get-lens-review-report`

Retrieves a lens review report for a workload.

**Synopsis:**
```bash
aws wellarchitected get-lens-review-report \
    --workload-id <value> \
    --lens-alias <value> \
    [--milestone-number <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workload-id` | **Yes** | string | -- | Workload ID |
| `--lens-alias` | **Yes** | string | -- | Lens alias or ARN |
| `--milestone-number` | No | integer | None | Milestone number |

**Output Schema:**
```json
{
    "WorkloadId": "string",
    "MilestoneNumber": "integer",
    "LensReviewReport": {
        "LensAlias": "string",
        "LensArn": "string",
        "Base64String": "string"
    }
}
```

---

### 3.5 `list-lens-review-improvements`

Lists improvement recommendations for a lens review. **Paginated.**

**Synopsis:**
```bash
aws wellarchitected list-lens-review-improvements \
    --workload-id <value> \
    --lens-alias <value> \
    [--pillar-id <value>] \
    [--milestone-number <value>] \
    [--question-priority <value>] \
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
| `--lens-alias` | **Yes** | string | -- | Lens alias or ARN |
| `--pillar-id` | No | string | None | Filter by pillar (1-64 chars) |
| `--milestone-number` | No | integer | None | Milestone number |
| `--question-priority` | No | string | None | `PRIORITIZED` or `NONE` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "WorkloadId": "string",
    "MilestoneNumber": "integer",
    "LensAlias": "string",
    "LensArn": "string",
    "ImprovementSummaries": [
        {
            "QuestionId": "string",
            "PillarId": "string",
            "QuestionTitle": "string",
            "Risk": "UNANSWERED|HIGH|MEDIUM|NONE|NOT_APPLICABLE",
            "ImprovementPlanUrl": "string",
            "ImprovementPlans": [
                {
                    "ChoiceId": "string",
                    "DisplayText": "string",
                    "ImprovementPlanUrl": "string"
                }
            ],
            "JiraConfiguration": {}
        }
    ],
    "NextToken": "string"
}
```

---

### 3.6 `upgrade-lens-review`

Upgrades a lens review to the latest version of the lens.

**Synopsis:**
```bash
aws wellarchitected upgrade-lens-review \
    --workload-id <value> \
    --lens-alias <value> \
    --milestone-name <value> \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workload-id` | **Yes** | string | -- | Workload ID |
| `--lens-alias` | **Yes** | string | -- | Lens alias or ARN |
| `--milestone-name` | **Yes** | string | -- | Name for milestone created during upgrade (3-100 chars) |
| `--client-request-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
None
```
