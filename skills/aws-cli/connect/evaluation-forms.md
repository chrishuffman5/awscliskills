# Evaluation Forms

### 12.1 `create-evaluation-form`

Creates an evaluation form for the specified instance.

**Synopsis:**
```bash
aws connect create-evaluation-form \
    --instance-id <value> \
    --title <value> \
    --items <value> \
    [--description <value>] \
    [--scoring-strategy <value>] \
    [--client-token <value>] \
    [--as-draft | --no-as-draft] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--title` | **Yes** | string | -- | Form title |
| `--items` | **Yes** | list | -- | Sections and questions (max 100 each) |
| `--description` | No | string | None | Form description |
| `--scoring-strategy` | No | structure | None | `Mode`: `QUESTION_ONLY`/`SECTION_ONLY`, `Status`: `ENABLED`/`DISABLED` |
| `--client-token` | No | string | Auto | Idempotency token |
| `--as-draft` | No | boolean | None | Create as draft |
| `--tags` | No | map | None | Tags (max 50) |

**Items Structure (Section):**
```json
{
    "Section": {
        "Title": "string",
        "RefId": "string",
        "Instructions": "string",
        "Items": [],
        "Weight": "double"
    }
}
```

**Items Structure (Question):**
```json
{
    "Question": {
        "Title": "string",
        "RefId": "string",
        "QuestionType": "TEXT|SINGLESELECT|NUMERIC|MULTISELECT|DATETIME",
        "QuestionTypeProperties": {},
        "Weight": "double"
    }
}
```

**Output Schema:**
```json
{
    "EvaluationFormId": "string",
    "EvaluationFormArn": "string"
}
```

---

### 12.2 `describe-evaluation-form`

Describes an evaluation form.

**Synopsis:**
```bash
aws connect describe-evaluation-form \
    --instance-id <value> \
    --evaluation-form-id <value> \
    [--evaluation-form-version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--evaluation-form-id` | **Yes** | string | -- | Evaluation form ID |
| `--evaluation-form-version` | No | integer | None | Specific version |

**Output Schema:**
```json
{
    "EvaluationForm": {
        "EvaluationFormId": "string",
        "EvaluationFormVersion": "integer",
        "Locked": "boolean",
        "EvaluationFormArn": "string",
        "Title": "string",
        "Description": "string",
        "Status": "DRAFT|ACTIVE",
        "Items": [],
        "ScoringStrategy": {},
        "CreatedTime": "timestamp",
        "CreatedBy": "string",
        "LastModifiedTime": "timestamp",
        "LastModifiedBy": "string",
        "Tags": { "key": "value" }
    }
}
```

---

### 12.3 `list-evaluation-forms`

Lists evaluation forms. **Paginated operation.**

**Synopsis:**
```bash
aws connect list-evaluation-forms \
    --instance-id <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-100) |

**Output Schema:**
```json
{
    "EvaluationFormSummaryList": [ { "EvaluationFormId": "string", "EvaluationFormArn": "string", "Title": "string", "CreatedTime": "timestamp", "CreatedBy": "string", "LastModifiedTime": "timestamp", "LastModifiedBy": "string", "LastActivatedTime": "timestamp", "LastActivatedBy": "string", "LatestVersion": "integer", "ActiveVersion": "integer" } ],
    "NextToken": "string"
}
```

---

### 12.4 `list-evaluation-form-versions`

Lists evaluation form versions. **Paginated operation.**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--evaluation-form-id` | **Yes** | string | -- | Evaluation form ID |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results |

---

### 12.5 `update-evaluation-form`

Updates an evaluation form.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--evaluation-form-id` | **Yes** | string | -- | Form ID |
| `--evaluation-form-version` | **Yes** | integer | -- | Version to update |
| `--title` | **Yes** | string | -- | Updated title |
| `--items` | **Yes** | list | -- | Updated items |
| `--description` | No | string | None | Updated description |
| `--scoring-strategy` | No | structure | None | Updated scoring |
| `--create-new-version` | No | boolean | None | Create new version |

**Output Schema:**
```json
{
    "EvaluationFormId": "string",
    "EvaluationFormArn": "string",
    "EvaluationFormVersion": "integer"
}
```

---

### 12.6 `activate-evaluation-form`

Activates an evaluation form version.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--evaluation-form-id` | **Yes** | string | -- | Form ID |
| `--evaluation-form-version` | **Yes** | integer | -- | Version to activate |

**Output Schema:**
```json
{
    "EvaluationFormId": "string",
    "EvaluationFormArn": "string",
    "EvaluationFormVersion": "integer"
}
```

---

### 12.7 `deactivate-evaluation-form`

Deactivates an evaluation form.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--evaluation-form-id` | **Yes** | string | -- | Form ID |
| `--evaluation-form-version` | **Yes** | integer | -- | Version to deactivate |

**Output Schema:**
```json
{
    "EvaluationFormId": "string",
    "EvaluationFormArn": "string",
    "EvaluationFormVersion": "integer"
}
```

---

### 12.8 `delete-evaluation-form`

Deletes an evaluation form.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--evaluation-form-id` | **Yes** | string | -- | Form ID |
| `--evaluation-form-version` | No | integer | None | Specific version to delete |

**Output:** None

---

### 12.9 `start-contact-evaluation`

Starts an evaluation for a contact.

**Synopsis:**
```bash
aws connect start-contact-evaluation \
    --instance-id <value> \
    --contact-id <value> \
    --evaluation-form-id <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--contact-id` | **Yes** | string | -- | Contact ID |
| `--evaluation-form-id` | **Yes** | string | -- | Evaluation form ID |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "EvaluationId": "string",
    "EvaluationArn": "string"
}
```

---

### 12.10 `describe-contact-evaluation`

Describes a contact evaluation.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--evaluation-id` | **Yes** | string | -- | Evaluation ID |

**Output Schema:**
```json
{
    "Evaluation": {
        "EvaluationId": "string",
        "EvaluationArn": "string",
        "Metadata": { "ContactId": "string", "EvaluatorArn": "string", "ContactAgentId": "string", "Score": {} },
        "Answers": {},
        "Notes": {},
        "Status": "DRAFT|SUBMITTED",
        "Scores": {},
        "CreatedTime": "timestamp",
        "LastModifiedTime": "timestamp",
        "Tags": {}
    },
    "EvaluationForm": {}
}
```

---

### 12.11-12.16 Additional Evaluation Commands

`list-contact-evaluations`, `update-contact-evaluation`, `submit-contact-evaluation`, `delete-contact-evaluation`, `search-contact-evaluations`, `search-evaluation-forms` provide listing, updating, submitting, deleting, and searching capabilities for evaluations and forms. All require `--instance-id`.
