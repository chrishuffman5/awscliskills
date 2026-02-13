# Response Plans

### 1.1 `create-response-plan`

Creates a response plan that automates the initial response to incidents.

**Synopsis:**
```bash
aws ssm-incidents create-response-plan \
    --name <value> \
    --incident-template <value> \
    [--display-name <value>] \
    [--chat-channel <value>] \
    [--engagements <value>] \
    [--actions <value>] \
    [--integrations <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Response plan name |
| `--incident-template` | **Yes** | structure | -- | Incident template with title and impact |
| `--display-name` | No | string | None | Human-readable display name |
| `--chat-channel` | No | structure | None | Chat channel (AWS Chatbot SNS topic ARNs) |
| `--engagements` | No | list(string) | None | Contact and escalation plan ARNs to engage |
| `--actions` | No | list | None | Actions to run when incident starts |
| `--integrations` | No | list | None | Service integrations (PagerDuty) |
| `--tags` | No | map | None | Tags |

**Incident Template Structure:**
```json
{
    "title": "string",
    "impact": 1|2|3|4|5,
    "summary": "string",
    "dedupeString": "string",
    "notificationTargets": [
        {
            "snsTopicArn": "string"
        }
    ],
    "incidentTags": {
        "string": "string"
    }
}
```

**Output Schema:**
```json
{
    "arn": "string"
}
```

---

### 1.2 `delete-response-plan`

Deletes the specified response plan. Deleting a response plan stops all linked CloudWatch alarms and EventBridge rules from creating an incident.

**Synopsis:**
```bash
aws ssm-incidents delete-response-plan \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | Response plan ARN |

**Output Schema:**
```json
{}
```

---

### 1.3 `get-response-plan`

Retrieves the details of the specified response plan.

**Synopsis:**
```bash
aws ssm-incidents get-response-plan \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | Response plan ARN |

**Output Schema:**
```json
{
    "arn": "string",
    "name": "string",
    "displayName": "string",
    "incidentTemplate": {
        "title": "string",
        "impact": "integer",
        "summary": "string",
        "dedupeString": "string",
        "notificationTargets": [],
        "incidentTags": {}
    },
    "chatChannel": {
        "chatbotSns": ["string"],
        "empty": {}
    },
    "engagements": ["string"],
    "actions": [
        {
            "ssmAutomation": {
                "roleArn": "string",
                "documentName": "string",
                "documentVersion": "string",
                "targetAccount": "RESPONSE_PLAN_OWNER_ACCOUNT|IMPACTED_ACCOUNT",
                "parameters": {},
                "dynamicParameters": {}
            }
        }
    ],
    "integrations": [
        {
            "pagerDutyConfiguration": {
                "name": "string",
                "secretId": "string",
                "pagerDutyIncidentConfiguration": {
                    "serviceId": "string"
                }
            }
        }
    ]
}
```

---

### 1.4 `list-response-plans`

Lists all response plans in your account. **Paginated operation.**

**Synopsis:**
```bash
aws ssm-incidents list-response-plans \
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
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Maximum items |

**Output Schema:**
```json
{
    "responsePlanSummaries": [
        {
            "arn": "string",
            "name": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 1.5 `update-response-plan`

Updates the specified response plan.

**Synopsis:**
```bash
aws ssm-incidents update-response-plan \
    --arn <value> \
    [--display-name <value>] \
    [--incident-template-title <value>] \
    [--incident-template-impact <value>] \
    [--incident-template-summary <value>] \
    [--incident-template-dedupe-string <value>] \
    [--incident-template-notification-targets <value>] \
    [--incident-template-tags <value>] \
    [--chat-channel <value>] \
    [--engagements <value>] \
    [--actions <value>] \
    [--integrations <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | Response plan ARN |
| `--display-name` | No | string | None | Updated display name |
| `--incident-template-title` | No | string | None | Updated incident title |
| `--incident-template-impact` | No | integer | None | Updated impact (1-5) |
| `--incident-template-summary` | No | string | None | Updated summary |
| `--incident-template-dedupe-string` | No | string | None | Updated dedup string |
| `--incident-template-notification-targets` | No | list | None | Updated notification targets |
| `--incident-template-tags` | No | map | None | Updated incident tags |
| `--chat-channel` | No | structure | None | Updated chat channel |
| `--engagements` | No | list(string) | None | Updated engagements |
| `--actions` | No | list | None | Updated actions |
| `--integrations` | No | list | None | Updated integrations |

**Output Schema:**
```json
{}
```
