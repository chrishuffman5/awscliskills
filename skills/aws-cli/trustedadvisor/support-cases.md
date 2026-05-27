# Support Cases

### 3.1 `create-case`

Creates a new AWS Support case. Requires a Business, Enterprise On-Ramp, or Enterprise Support plan.

**Synopsis:**
```bash
aws support create-case \
    --subject <value> \
    --communication-body <value> \
    [--service-code <value>] \
    [--severity-code <value>] \
    [--category-code <value>] \
    [--cc-email-addresses <value>] \
    [--language <value>] \
    [--issue-type <value>] \
    [--attachment-set-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--subject` | **Yes** | string | -- | Title of the support case |
| `--communication-body` | **Yes** | string | -- | Description of the issue (1-8000 chars) |
| `--service-code` | No | string | None | AWS service code (use `describe-services` to list) |
| `--severity-code` | No | string | None | Urgency level (use `describe-severity-levels` to list). Availability depends on support plan |
| `--category-code` | No | string | None | Problem category (use `describe-services` to list) |
| `--cc-email-addresses` | No | list(string) | None | CC email addresses (max 10) |
| `--language` | No | string | None | Language: `zh`, `en`, `ja`, `ko` |
| `--issue-type` | No | string | `technical` | Issue type: `customer-service`, `technical` |
| `--attachment-set-id` | No | string | None | Attachment set ID (from `add-attachments-to-set`) |

**Output Schema:**
```json
{
    "caseId": "string"
}
```

---

### 3.2 `describe-cases`

Describes support cases. Case data is available for 12 months after creation. **Paginated operation.**

**Synopsis:**
```bash
aws support describe-cases \
    [--case-id-list <value>] \
    [--display-id <value>] \
    [--after-time <value>] \
    [--before-time <value>] \
    [--include-resolved-cases | --no-include-resolved-cases] \
    [--include-communications | --no-include-communications] \
    [--language <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--case-id-list` | No | list(string) | None | List of case IDs (max 100) |
| `--display-id` | No | string | None | Display ID shown in AWS Support Center |
| `--after-time` | No | string | None | Start date for filtering (ISO-8601) |
| `--before-time` | No | string | None | End date for filtering (ISO-8601) |
| `--include-resolved-cases` | No | boolean | false | Include resolved cases |
| `--include-communications` | No | boolean | true | Include case communications |
| `--language` | No | string | None | Language: `zh`, `en`, `ja`, `ko` |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "cases": [
        {
            "caseId": "string",
            "displayId": "string",
            "subject": "string",
            "status": "all-open|customer-action-completed|opened|pending-customer-action|reopened|resolved|unassigned|work-in-progress",
            "serviceCode": "string",
            "categoryCode": "string",
            "severityCode": "low|normal|high|urgent|critical",
            "submittedBy": "string",
            "timeCreated": "string",
            "language": "string",
            "ccEmailAddresses": ["string"],
            "recentCommunications": {
                "communications": [
                    {
                        "caseId": "string",
                        "body": "string",
                        "submittedBy": "string",
                        "timeCreated": "string",
                        "attachmentSet": [
                            {
                                "attachmentId": "string",
                                "fileName": "string"
                            }
                        ]
                    }
                ],
                "nextToken": "string"
            }
        }
    ],
    "nextToken": "string"
}
```

---

### 3.3 `add-communication-to-case`

Adds a communication to a support case.

**Synopsis:**
```bash
aws support add-communication-to-case \
    --communication-body <value> \
    [--case-id <value>] \
    [--cc-email-addresses <value>] \
    [--attachment-set-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--communication-body` | **Yes** | string | -- | Communication body text (1-8000 chars) |
| `--case-id` | No | string | None | The support case ID |
| `--cc-email-addresses` | No | list(string) | None | CC email addresses (max 10) |
| `--attachment-set-id` | No | string | None | Attachment set ID |

**Output Schema:**
```json
{
    "result": true|false
}
```

---

### 3.4 `describe-communications`

Returns communications and attachments for a support case. **Paginated operation.**

**Synopsis:**
```bash
aws support describe-communications \
    --case-id <value> \
    [--before-time <value>] \
    [--after-time <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--case-id` | **Yes** | string | -- | The support case ID |
| `--before-time` | No | string | None | End date for filtering (ISO-8601) |
| `--after-time` | No | string | None | Start date for filtering (ISO-8601) |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "communications": [
        {
            "caseId": "string",
            "body": "string",
            "submittedBy": "string",
            "timeCreated": "string",
            "attachmentSet": [
                {
                    "attachmentId": "string",
                    "fileName": "string"
                }
            ]
        }
    ],
    "nextToken": "string"
}
```

---

### 3.5 `resolve-case`

Resolves a support case.

**Synopsis:**
```bash
aws support resolve-case \
    [--case-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--case-id` | No | string | None | The support case ID to resolve |

**Output Schema:**
```json
{
    "initialCaseStatus": "string",
    "finalCaseStatus": "string"
}
```

---

### 3.6 `describe-services`

Returns the list of AWS service codes and categories for support cases.

**Synopsis:**
```bash
aws support describe-services \
    [--service-code-list <value>] \
    [--language <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-code-list` | No | list(string) | None | List of service codes to filter |
| `--language` | No | string | None | Language: `zh`, `en`, `ja`, `ko` |

**Output Schema:**
```json
{
    "services": [
        {
            "code": "string",
            "name": "string",
            "categories": [
                {
                    "code": "string",
                    "name": "string"
                }
            ]
        }
    ]
}
```

---

### 3.7 `describe-severity-levels`

Returns the list of severity levels for support cases.

**Synopsis:**
```bash
aws support describe-severity-levels \
    [--language <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--language` | No | string | None | Language: `zh`, `en`, `ja`, `ko` |

**Output Schema:**
```json
{
    "severityLevels": [
        {
            "code": "string",
            "name": "string"
        }
    ]
}
```

---

### 3.8 `describe-create-case-options`

Returns options for creating a support case.

**Synopsis:**
```bash
aws support describe-create-case-options \
    --issue-type <value> \
    --service-code <value> \
    --language <value> \
    --category-code <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--issue-type` | **Yes** | string | -- | Issue type: `customer-service`, `technical` |
| `--service-code` | **Yes** | string | -- | AWS service code |
| `--language` | **Yes** | string | -- | Language code |
| `--category-code` | **Yes** | string | -- | Category code |

**Output Schema:**
```json
{
    "languageAvailability": "string",
    "communicationTypes": [
        {
            "type": "string",
            "supportedHours": [
                {
                    "startTime": "string",
                    "endTime": "string"
                }
            ],
            "datesWithoutSupport": [
                {
                    "startDateTime": "string",
                    "endDateTime": "string"
                }
            ]
        }
    ]
}
```

---

### 3.9 `describe-supported-languages`

Returns supported languages for a given service, category, and issue type.

**Synopsis:**
```bash
aws support describe-supported-languages \
    --issue-type <value> \
    --service-code <value> \
    --category-code <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--issue-type` | **Yes** | string | -- | Issue type: `customer-service`, `technical` |
| `--service-code` | **Yes** | string | -- | AWS service code |
| `--category-code` | **Yes** | string | -- | Category code |

**Output Schema:**
```json
{
    "supportedLanguages": [
        {
            "code": "string",
            "language": "string",
            "display": "string"
        }
    ]
}
```

---

### 3.10 `add-attachments-to-set`

Adds one or more attachments to an attachment set for a support case.

**Synopsis:**
```bash
aws support add-attachments-to-set \
    --attachments <value> \
    [--attachment-set-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--attachments` | **Yes** | list | -- | List of attachments. Structure: `fileName=string,data=blob` |
| `--attachment-set-id` | No | string | None | Existing attachment set ID to add to. If omitted, a new set is created |

**Output Schema:**
```json
{
    "attachmentSetId": "string",
    "expiryTime": "string"
}
```

---

### 3.11 `describe-attachment`

Returns the attachment for a support case.

**Synopsis:**
```bash
aws support describe-attachment \
    --attachment-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--attachment-id` | **Yes** | string | -- | The ID of the attachment to retrieve |

**Output Schema:**
```json
{
    "attachment": {
        "fileName": "string",
        "data": "blob"
    }
}
```
