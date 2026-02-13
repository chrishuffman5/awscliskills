# Answers

### 4.1 `get-answer`

Gets the answer to a specific question in a workload review.

**Synopsis:**
```bash
aws wellarchitected get-answer \
    --workload-id <value> \
    --lens-alias <value> \
    --question-id <value> \
    [--milestone-number <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workload-id` | **Yes** | string | -- | Workload ID (32 hex chars) |
| `--lens-alias` | **Yes** | string | -- | Lens alias or ARN (1-128 chars) |
| `--question-id` | **Yes** | string | -- | Question ID (1-128 chars) |
| `--milestone-number` | No | integer | None | Milestone number (1-100) |

**Output Schema:**
```json
{
    "WorkloadId": "string",
    "MilestoneNumber": "integer",
    "LensAlias": "string",
    "LensArn": "string",
    "Answer": {
        "QuestionId": "string",
        "PillarId": "string",
        "QuestionTitle": "string",
        "QuestionDescription": "string",
        "ImprovementPlanUrl": "string",
        "HelpfulResourceUrl": "string",
        "HelpfulResourceDisplayText": "string",
        "Choices": [
            {
                "ChoiceId": "string",
                "Title": "string",
                "Description": "string",
                "HelpfulResource": {
                    "DisplayText": "string",
                    "Url": "string"
                },
                "ImprovementPlan": {
                    "DisplayText": "string",
                    "Url": "string"
                },
                "AdditionalResources": [
                    {
                        "Type": "HELPFUL_RESOURCE|IMPROVEMENT_PLAN",
                        "Content": [{"DisplayText": "string", "Url": "string"}]
                    }
                ]
            }
        ],
        "SelectedChoices": ["string"],
        "ChoiceAnswers": [
            {
                "ChoiceId": "string",
                "Status": "SELECTED|NOT_APPLICABLE|UNSELECTED",
                "Reason": "OUT_OF_SCOPE|BUSINESS_PRIORITIES|ARCHITECTURE_CONSTRAINTS|OTHER|NONE",
                "Notes": "string"
            }
        ],
        "IsApplicable": "boolean",
        "Risk": "UNANSWERED|HIGH|MEDIUM|NONE|NOT_APPLICABLE",
        "Notes": "string",
        "Reason": "OUT_OF_SCOPE|BUSINESS_PRIORITIES|ARCHITECTURE_CONSTRAINTS|OTHER|NONE",
        "JiraConfiguration": {
            "JiraIssueUrl": "string",
            "LastSyncedTime": "timestamp"
        }
    }
}
```

---

### 4.2 `list-answers`

Lists answers for a lens review. **Paginated.**

**Synopsis:**
```bash
aws wellarchitected list-answers \
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
    "AnswerSummaries": [
        {
            "QuestionId": "string",
            "PillarId": "string",
            "QuestionTitle": "string",
            "Choices": [],
            "SelectedChoices": ["string"],
            "ChoiceAnswerSummaries": [
                {"ChoiceId": "string", "Status": "string", "Reason": "string"}
            ],
            "IsApplicable": "boolean",
            "Risk": "UNANSWERED|HIGH|MEDIUM|NONE|NOT_APPLICABLE",
            "Reason": "string",
            "QuestionType": "PRIORITIZED|NON_PRIORITIZED",
            "JiraConfiguration": {}
        }
    ],
    "NextToken": "string"
}
```

---

### 4.3 `update-answer`

Updates an answer to a question in a workload review.

**Synopsis:**
```bash
aws wellarchitected update-answer \
    --workload-id <value> \
    --lens-alias <value> \
    --question-id <value> \
    [--selected-choices <value>] \
    [--choice-updates <value>] \
    [--notes <value>] \
    [--is-applicable | --no-is-applicable] \
    [--reason <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workload-id` | **Yes** | string | -- | Workload ID |
| `--lens-alias` | **Yes** | string | -- | Lens alias or ARN |
| `--question-id` | **Yes** | string | -- | Question ID |
| `--selected-choices` | No | list(string) | None | Selected choice IDs |
| `--choice-updates` | No | map | None | Map of choice ID to update. JSON: `{"choiceId": {"Status": "SELECTED|NOT_APPLICABLE|UNSELECTED", "Reason": "string", "Notes": "string"}}` |
| `--notes` | No | string | None | Notes (max 2084 chars) |
| `--is-applicable` | No | boolean | None | Whether the question is applicable |
| `--reason` | No | string | None | `OUT_OF_SCOPE`, `BUSINESS_PRIORITIES`, `ARCHITECTURE_CONSTRAINTS`, `OTHER`, `NONE` |

**Output Schema:**
```json
{
    "WorkloadId": "string",
    "LensAlias": "string",
    "LensArn": "string",
    "Answer": {
        "QuestionId": "string",
        "PillarId": "string",
        "QuestionTitle": "string",
        "SelectedChoices": ["string"],
        "ChoiceAnswers": [],
        "IsApplicable": "boolean",
        "Risk": "string",
        "Notes": "string",
        "Reason": "string"
    }
}
```
