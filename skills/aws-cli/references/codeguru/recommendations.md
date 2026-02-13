# Recommendations

### 3.1 `list-recommendations`

Returns the list of all recommendations for a completed code review. Uses `aws codeguru-reviewer`. **Paginated operation.**

**Synopsis:**
```bash
aws codeguru-reviewer list-recommendations \
    --code-review-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--code-review-arn` | **Yes** | string | -- | ARN of the code review |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "RecommendationSummaries": [
        {
            "FilePath": "string",
            "RecommendationId": "string",
            "StartLine": "integer",
            "EndLine": "integer",
            "Description": "string",
            "RecommendationCategory": "AWSBestPractices|AWSCloudFormationIssues|DuplicateCode|CodeMaintenanceIssues|ConcurrencyIssues|InputValidations|PythonBestPractices|JavaBestPractices|ResourceLeaks|SecurityIssues|CodeInconsistencies",
            "RuleMetadata": {
                "RuleId": "string",
                "RuleName": "string",
                "ShortDescription": "string",
                "LongDescription": "string",
                "RuleTags": ["string"]
            },
            "Severity": "Info|Low|Medium|High|Critical"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.2 `list-recommendation-feedback`

Returns a list of recommendation feedback objects for a given code review. Uses `aws codeguru-reviewer`. **Paginated operation.**

**Synopsis:**
```bash
aws codeguru-reviewer list-recommendation-feedback \
    --code-review-arn <value> \
    [--recommendation-ids <value>] \
    [--user-ids <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--code-review-arn` | **Yes** | string | -- | ARN of the code review |
| `--recommendation-ids` | No | list(string) | None | Filter by recommendation IDs |
| `--user-ids` | No | list(string) | None | Filter by user IDs who gave feedback |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "RecommendationFeedbackSummaries": [
        {
            "RecommendationId": "string",
            "Reactions": ["ThumbsUp|ThumbsDown"],
            "UserId": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.3 `describe-recommendation-feedback`

Describes the feedback on a recommendation for a given code review. Uses `aws codeguru-reviewer`.

**Synopsis:**
```bash
aws codeguru-reviewer describe-recommendation-feedback \
    --code-review-arn <value> \
    --recommendation-id <value> \
    [--user-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--code-review-arn` | **Yes** | string | -- | ARN of the code review |
| `--recommendation-id` | **Yes** | string | -- | ID of the recommendation |
| `--user-id` | No | string | None | Optional user ID to filter feedback by |

**Output Schema:**
```json
{
    "RecommendationFeedback": {
        "CodeReviewArn": "string",
        "RecommendationId": "string",
        "Reactions": ["ThumbsUp|ThumbsDown"],
        "UserId": "string",
        "CreatedTimeStamp": "timestamp",
        "LastUpdatedTimeStamp": "timestamp"
    }
}
```

---

### 3.4 `put-recommendation-feedback`

Stores customer feedback for a CodeGuru Reviewer recommendation. Uses `aws codeguru-reviewer`.

**Synopsis:**
```bash
aws codeguru-reviewer put-recommendation-feedback \
    --code-review-arn <value> \
    --recommendation-id <value> \
    --reactions <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--code-review-arn` | **Yes** | string | -- | ARN of the code review |
| `--recommendation-id` | **Yes** | string | -- | ID of the recommendation to provide feedback on |
| `--reactions` | **Yes** | list(string) | -- | Feedback reactions: `ThumbsUp`, `ThumbsDown` |

**Output Schema:**
```json
{}
```
