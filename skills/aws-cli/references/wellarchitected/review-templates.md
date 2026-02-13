# Review Templates

### 7.1 `create-review-template`

Creates a review template for standardized workload reviews.

**Synopsis:**
```bash
aws wellarchitected create-review-template \
    --template-name <value> \
    --description <value> \
    --lenses <value> \
    [--notes <value>] \
    [--tags <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--template-name` | **Yes** | string | -- | Template name (3-100 chars) |
| `--description` | **Yes** | string | -- | Description (3-250 chars) |
| `--lenses` | **Yes** | list(string) | -- | Lens aliases or ARNs |
| `--notes` | No | string | None | Notes (max 2084 chars) |
| `--tags` | No | map | None | Tags (1-50 tags) |
| `--client-request-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "ReviewTemplate": {
        "Description": "string",
        "Lenses": ["string"],
        "Notes": "string",
        "QuestionCounts": {"string": "integer"},
        "Owner": "string",
        "UpdatedAt": "timestamp",
        "TemplateArn": "string",
        "TemplateName": "string",
        "Tags": {"string": "string"},
        "UpdateStatus": "CURRENT|LENS_NOT_CURRENT",
        "ShareInvitationId": "string"
    }
}
```

---

### 7.2 `delete-review-template`

Deletes a review template.

**Synopsis:**
```bash
aws wellarchitected delete-review-template \
    --template-arn <value> \
    --client-request-token <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--template-arn` | **Yes** | string | -- | Template ARN |
| `--client-request-token` | **Yes** | string | -- | Idempotency token |

**Output Schema:**
```json
None
```

---

### 7.3 `get-review-template`

Retrieves a review template.

**Synopsis:**
```bash
aws wellarchitected get-review-template \
    --template-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--template-arn` | **Yes** | string | -- | Template ARN |

**Output Schema:**
```json
{
    "ReviewTemplate": {
        "Description": "string",
        "Lenses": ["string"],
        "Notes": "string",
        "QuestionCounts": {"string": "integer"},
        "Owner": "string",
        "UpdatedAt": "timestamp",
        "TemplateArn": "string",
        "TemplateName": "string",
        "Tags": {"string": "string"},
        "UpdateStatus": "CURRENT|LENS_NOT_CURRENT",
        "ShareInvitationId": "string"
    }
}
```

---

### 7.4 `list-review-templates`

Lists all review templates. **Paginated.**

**Synopsis:**
```bash
aws wellarchitected list-review-templates \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ReviewTemplates": [
        {
            "Description": "string",
            "Lenses": ["string"],
            "Owner": "string",
            "UpdatedAt": "timestamp",
            "TemplateArn": "string",
            "TemplateName": "string",
            "UpdateStatus": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 7.5 `update-review-template`

Updates a review template.

**Synopsis:**
```bash
aws wellarchitected update-review-template \
    --template-arn <value> \
    [--template-name <value>] \
    [--description <value>] \
    [--notes <value>] \
    [--lenses-to-associate <value>] \
    [--lenses-to-disassociate <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--template-arn` | **Yes** | string | -- | Template ARN |
| `--template-name` | No | string | None | New name |
| `--description` | No | string | None | New description |
| `--notes` | No | string | None | New notes |
| `--lenses-to-associate` | No | list(string) | None | Lenses to add |
| `--lenses-to-disassociate` | No | list(string) | None | Lenses to remove |

**Output Schema:**
```json
{
    "ReviewTemplate": {
        "TemplateArn": "string",
        "TemplateName": "string",
        "Description": "string",
        "Lenses": ["string"],
        "Notes": "string",
        "UpdateStatus": "string"
    }
}
```

---

### 7.6 `get-review-template-answer`

Gets an answer from a review template.

**Synopsis:**
```bash
aws wellarchitected get-review-template-answer \
    --template-arn <value> \
    --lens-alias <value> \
    --question-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--template-arn` | **Yes** | string | -- | Template ARN |
| `--lens-alias` | **Yes** | string | -- | Lens alias or ARN |
| `--question-id` | **Yes** | string | -- | Question ID |

**Output Schema:**
```json
{
    "TemplateArn": "string",
    "LensAlias": "string",
    "Answer": {
        "QuestionId": "string",
        "PillarId": "string",
        "QuestionTitle": "string",
        "QuestionDescription": "string",
        "Choices": [],
        "SelectedChoices": ["string"],
        "ChoiceAnswers": [],
        "IsApplicable": "boolean",
        "AnswerStatus": "UNANSWERED|ANSWERED",
        "Notes": "string",
        "Reason": "string",
        "HelpfulResourceUrl": "string"
    }
}
```

---

### 7.7 `list-review-template-answers`

Lists answers in a review template. **Paginated.**

**Synopsis:**
```bash
aws wellarchitected list-review-template-answers \
    --template-arn <value> \
    --lens-alias <value> \
    [--pillar-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--template-arn` | **Yes** | string | -- | Template ARN |
| `--lens-alias` | **Yes** | string | -- | Lens alias or ARN |
| `--pillar-id` | No | string | None | Filter by pillar |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "TemplateArn": "string",
    "LensAlias": "string",
    "AnswerSummaries": [
        {
            "QuestionId": "string",
            "PillarId": "string",
            "QuestionTitle": "string",
            "Choices": [],
            "SelectedChoices": ["string"],
            "ChoiceAnswerSummaries": [],
            "IsApplicable": "boolean",
            "AnswerStatus": "string",
            "Reason": "string",
            "QuestionType": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 7.8 `update-review-template-answer`

Updates an answer in a review template.

**Synopsis:**
```bash
aws wellarchitected update-review-template-answer \
    --template-arn <value> \
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
| `--template-arn` | **Yes** | string | -- | Template ARN |
| `--lens-alias` | **Yes** | string | -- | Lens alias or ARN |
| `--question-id` | **Yes** | string | -- | Question ID |
| `--selected-choices` | No | list(string) | None | Selected choice IDs |
| `--choice-updates` | No | map | None | Choice updates (JSON) |
| `--notes` | No | string | None | Notes |
| `--is-applicable` | No | boolean | None | Whether applicable |
| `--reason` | No | string | None | Reason for non-applicability |

**Output Schema:**
```json
{
    "TemplateArn": "string",
    "LensAlias": "string",
    "Answer": {
        "QuestionId": "string",
        "SelectedChoices": ["string"],
        "ChoiceAnswers": [],
        "IsApplicable": "boolean",
        "AnswerStatus": "string",
        "Notes": "string"
    }
}
```

---

### 7.9 `get-review-template-lens-review`

Gets a lens review from a review template.

**Synopsis:**
```bash
aws wellarchitected get-review-template-lens-review \
    --template-arn <value> \
    --lens-alias <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--template-arn` | **Yes** | string | -- | Template ARN |
| `--lens-alias` | **Yes** | string | -- | Lens alias or ARN |

**Output Schema:**
```json
{
    "TemplateArn": "string",
    "LensReview": {
        "LensAlias": "string",
        "LensArn": "string",
        "LensVersion": "string",
        "LensName": "string",
        "LensStatus": "string",
        "PillarReviewSummaries": [],
        "UpdatedAt": "timestamp",
        "Notes": "string",
        "QuestionCounts": {"string": "integer"}
    }
}
```

---

### 7.10 `update-review-template-lens-review`

Updates a lens review in a review template.

**Synopsis:**
```bash
aws wellarchitected update-review-template-lens-review \
    --template-arn <value> \
    --lens-alias <value> \
    [--lens-notes <value>] \
    [--pillar-notes <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--template-arn` | **Yes** | string | -- | Template ARN |
| `--lens-alias` | **Yes** | string | -- | Lens alias or ARN |
| `--lens-notes` | No | string | None | Notes for the lens review |
| `--pillar-notes` | No | map | None | Map of pillar ID to notes |

**Output Schema:**
```json
{
    "TemplateArn": "string",
    "LensReview": {
        "LensAlias": "string",
        "LensArn": "string",
        "LensVersion": "string",
        "LensName": "string",
        "Notes": "string"
    }
}
```

---

### 7.11 `upgrade-review-template-lens-review`

Upgrades a review template lens review to the latest version.

**Synopsis:**
```bash
aws wellarchitected upgrade-review-template-lens-review \
    --template-arn <value> \
    --lens-alias <value> \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--template-arn` | **Yes** | string | -- | Template ARN |
| `--lens-alias` | **Yes** | string | -- | Lens alias or ARN |
| `--client-request-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
None
```

---

### 7.12 `create-template-share`

Shares a review template with another account.

**Synopsis:**
```bash
aws wellarchitected create-template-share \
    --template-arn <value> \
    --shared-with <value> \
    --client-request-token <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--template-arn` | **Yes** | string | -- | Template ARN |
| `--shared-with` | **Yes** | string | -- | Account ID, org ID, or OU ID |
| `--client-request-token` | **Yes** | string | -- | Idempotency token |

**Output Schema:**
```json
{
    "TemplateArn": "string",
    "ShareId": "string"
}
```

---

### 7.13 `delete-template-share`

Deletes a template share.

**Synopsis:**
```bash
aws wellarchitected delete-template-share \
    --share-id <value> \
    --template-arn <value> \
    --client-request-token <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--share-id` | **Yes** | string | -- | Share ID |
| `--template-arn` | **Yes** | string | -- | Template ARN |
| `--client-request-token` | **Yes** | string | -- | Idempotency token |

**Output Schema:**
```json
None
```

---

### 7.14 `list-template-shares`

Lists shares for a review template. **Paginated.**

**Synopsis:**
```bash
aws wellarchitected list-template-shares \
    --template-arn <value> \
    [--shared-with-prefix <value>] \
    [--status <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--template-arn` | **Yes** | string | -- | Template ARN |
| `--shared-with-prefix` | No | string | None | Filter by shared-with prefix |
| `--status` | No | string | None | Filter by share status |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "TemplateShareSummaries": [
        {
            "ShareId": "string",
            "SharedWith": "string",
            "Status": "string",
            "StatusMessage": "string"
        }
    ],
    "NextToken": "string"
}
```
