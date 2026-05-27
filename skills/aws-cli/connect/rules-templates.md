# Rules & Templates

### 15.1 `create-rule`

Creates a rule for the specified instance.

**Synopsis:**
```bash
aws connect create-rule \
    --instance-id <value> \
    --name <value> \
    --trigger-event-source <value> \
    --function <value> \
    --actions <value> \
    --publish-status <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--name` | **Yes** | string | -- | Rule name (1-200 chars) |
| `--trigger-event-source` | **Yes** | structure | -- | Event source trigger |
| `--function` | **Yes** | string | -- | Rule conditions in Rules Function language |
| `--actions` | **Yes** | list | -- | Actions to execute |
| `--publish-status` | **Yes** | string | -- | `DRAFT` or `PUBLISHED` |
| `--client-token` | No | string | Auto | Idempotency token |

**TriggerEventSource:**
```json
{
    "EventSourceName": "OnPostCallAnalysisAvailable|OnRealTimeCallAnalysisAvailable|OnRealTimeChatAnalysisAvailable|OnPostChatAnalysisAvailable|OnZendeskTicketCreate|OnZendeskTicketStatusUpdate|OnSalesforceCaseCreate|OnContactEvaluationSubmit|OnMetricDataUpdate|OnCaseCreate|OnCaseUpdate|OnSlaBreach",
    "IntegrationAssociationId": "string"
}
```

**Actions (ActionType values):** `CREATE_TASK`, `ASSIGN_CONTACT_CATEGORY`, `GENERATE_EVENTBRIDGE_EVENT`, `SEND_NOTIFICATION`, `CREATE_CASE`, `UPDATE_CASE`, `ASSIGN_SLA`, `END_ASSOCIATED_TASKS`, `SUBMIT_AUTO_EVALUATION`

**Output Schema:**
```json
{
    "RuleArn": "string",
    "RuleId": "string"
}
```

---

### 15.2 `describe-rule`

Describes a rule.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--rule-id` | **Yes** | string | -- | Rule ID |

**Output Schema:**
```json
{
    "Rule": {
        "Name": "string",
        "RuleId": "string",
        "RuleArn": "string",
        "TriggerEventSource": {},
        "Function": "string",
        "Actions": [],
        "PublishStatus": "DRAFT|PUBLISHED",
        "CreatedTime": "timestamp",
        "LastUpdatedTime": "timestamp",
        "LastUpdatedBy": "string",
        "Tags": { "key": "value" }
    }
}
```

---

### 15.3 `list-rules`

Lists rules. **Paginated operation.**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--publish-status` | No | string | None | Filter: `DRAFT` or `PUBLISHED` |
| `--event-source-name` | No | string | None | Filter by event source |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-200) |

**Output Schema:**
```json
{
    "RuleSummaryList": [ { "Name": "string", "RuleId": "string", "RuleArn": "string", "EventSourceName": "string", "PublishStatus": "string", "ActionSummaries": [], "CreatedTime": "timestamp", "LastUpdatedTime": "timestamp" } ],
    "NextToken": "string"
}
```

---

### 15.4 `update-rule`

Updates a rule.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rule-id` | **Yes** | string | -- | Rule ID |
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--name` | **Yes** | string | -- | Updated name |
| `--function` | **Yes** | string | -- | Updated conditions |
| `--actions` | **Yes** | list | -- | Updated actions |
| `--publish-status` | **Yes** | string | -- | `DRAFT` or `PUBLISHED` |

**Output:** None

---

### 15.5 `delete-rule`

Deletes a rule.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--rule-id` | **Yes** | string | -- | Rule ID |

**Output:** None

---

### 15.6 `create-task-template`

Creates a task template.

**Synopsis:**
```bash
aws connect create-task-template \
    --instance-id <value> \
    --name <value> \
    --fields <value> \
    [--description <value>] \
    [--contact-flow-id <value>] \
    [--self-assign-flow-id <value>] \
    [--constraints <value>] \
    [--defaults <value>] \
    [--status <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--name` | **Yes** | string | -- | Template name (1-100 chars) |
| `--fields` | **Yes** | list | -- | Field definitions |
| `--description` | No | string | None | Description |
| `--contact-flow-id` | No | string | None | Associated flow |
| `--self-assign-flow-id` | No | string | None | Self-assign flow |
| `--constraints` | No | structure | None | Field constraints (required/readonly/invisible) |
| `--defaults` | No | structure | None | Default field values |
| `--status` | No | string | None | `ACTIVE` or `INACTIVE` |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "Id": "string",
    "Arn": "string"
}
```

---

### 15.7 `get-task-template`

Gets a task template.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--task-template-id` | **Yes** | string | -- | Task template ID |
| `--snapshot-version` | No | string | None | Specific version |

**Output Schema:**
```json
{
    "InstanceId": "string",
    "Id": "string",
    "Arn": "string",
    "Name": "string",
    "Description": "string",
    "ContactFlowId": "string",
    "SelfAssignFlowId": "string",
    "Constraints": {},
    "Defaults": {},
    "Fields": [],
    "Status": "ACTIVE|INACTIVE",
    "LastModifiedTime": "timestamp",
    "CreatedTime": "timestamp",
    "Tags": { "key": "value" }
}
```

---

### 15.8 `list-task-templates`

Lists task templates. **Paginated operation.**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-100) |
| `--status` | No | string | None | Filter: `ACTIVE` or `INACTIVE` |
| `--name` | No | string | None | Filter by name prefix |

---

### 15.9 `update-task-template`

Updates a task template.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--task-template-id` | **Yes** | string | -- | Task template ID |
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--name` | No | string | None | Updated name |
| `--description` | No | string | None | Updated description |
| `--contact-flow-id` | No | string | None | Updated flow |
| `--constraints` | No | structure | None | Updated constraints |
| `--defaults` | No | structure | None | Updated defaults |
| `--status` | No | string | None | Updated status |
| `--fields` | No | list | None | Updated fields |

---

### 15.10 `delete-task-template`

Deletes a task template.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--task-template-id` | **Yes** | string | -- | Task template ID |

**Output:** None
