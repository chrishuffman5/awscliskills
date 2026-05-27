# Audit

## 9.1 `describe-account-audit-configuration`

Describes the account-level audit configuration.

**Synopsis:**
```bash
aws iot describe-account-audit-configuration \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output Schema:**
```json
{
    "roleArn": "string",
    "auditNotificationTargetConfigurations": {
        "SNS": {"targetArn": "string", "roleArn": "string", "enabled": "boolean"}
    },
    "auditCheckConfigurations": {
        "LOGGING_DISABLED_CHECK|REVOKED_CA_CERTIFICATE_STILL_ACTIVE_CHECK|...": {
            "enabled": "boolean"
        }
    }
}
```

---

## 9.2 `update-account-audit-configuration`

Updates the account-level audit configuration.

**Synopsis:**
```bash
aws iot update-account-audit-configuration \
    [--role-arn <value>] \
    [--audit-notification-target-configurations <value>] \
    [--audit-check-configurations <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--role-arn` | No | string | None | IAM role ARN for audit |
| `--audit-notification-target-configurations` | No | map | None | SNS notification targets |
| `--audit-check-configurations` | No | map | None | Enable/disable audit checks |

**Output:** None

---

## 9.3 `delete-account-audit-configuration`

Deletes the account-level audit configuration.

**Synopsis:**
```bash
aws iot delete-account-audit-configuration \
    [--delete-scheduled-audits | --no-delete-scheduled-audits] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--delete-scheduled-audits` | No | boolean | false | Also delete scheduled audits |

**Output:** None

---

## 9.4 `create-scheduled-audit`

Creates a scheduled audit.

**Synopsis:**
```bash
aws iot create-scheduled-audit \
    --frequency <value> \
    --target-check-names <value> \
    --scheduled-audit-name <value> \
    [--day-of-month <value>] \
    [--day-of-week <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--frequency` | **Yes** | string | -- | `DAILY`, `WEEKLY`, `BIWEEKLY`, `MONTHLY` |
| `--target-check-names` | **Yes** | list | -- | Audit check names to perform |
| `--scheduled-audit-name` | **Yes** | string | -- | Audit name (1-128 chars) |
| `--day-of-month` | No | string | None | Day of month (1-31 or LAST). Required if MONTHLY |
| `--day-of-week` | No | string | None | `SUN`-`SAT`. Required if WEEKLY/BIWEEKLY |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "scheduledAuditArn": "string"
}
```

---

## 9.5 `describe-scheduled-audit`

Describes a scheduled audit.

**Synopsis:**
```bash
aws iot describe-scheduled-audit \
    --scheduled-audit-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--scheduled-audit-name` | **Yes** | string | -- | Scheduled audit name |

**Output Schema:**
```json
{
    "frequency": "DAILY|WEEKLY|BIWEEKLY|MONTHLY",
    "dayOfMonth": "string",
    "dayOfWeek": "SUN|MON|TUE|WED|THU|FRI|SAT",
    "targetCheckNames": ["string"],
    "scheduledAuditName": "string",
    "scheduledAuditArn": "string"
}
```

---

## 9.6 `list-scheduled-audits`

Lists scheduled audits. **Paginated operation.**

**Synopsis:**
```bash
aws iot list-scheduled-audits \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-250) |

**Output Schema:**
```json
{
    "scheduledAudits": [
        {
            "scheduledAuditName": "string",
            "scheduledAuditArn": "string",
            "frequency": "string",
            "dayOfMonth": "string",
            "dayOfWeek": "string"
        }
    ],
    "nextToken": "string"
}
```

---

## 9.7 `update-scheduled-audit`

Updates a scheduled audit.

**Synopsis:**
```bash
aws iot update-scheduled-audit \
    --scheduled-audit-name <value> \
    [--frequency <value>] \
    [--day-of-month <value>] \
    [--day-of-week <value>] \
    [--target-check-names <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--scheduled-audit-name` | **Yes** | string | -- | Scheduled audit name |
| `--frequency` | No | string | None | Updated frequency |
| `--day-of-month` | No | string | None | Updated day of month |
| `--day-of-week` | No | string | None | Updated day of week |
| `--target-check-names` | No | list | None | Updated check names |

**Output Schema:**
```json
{
    "scheduledAuditArn": "string"
}
```

---

## 9.8 `delete-scheduled-audit`

Deletes a scheduled audit.

**Synopsis:**
```bash
aws iot delete-scheduled-audit \
    --scheduled-audit-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--scheduled-audit-name` | **Yes** | string | -- | Scheduled audit name |

**Output:** None

---

## 9.9 `start-on-demand-audit-task`

Starts an on-demand audit.

**Synopsis:**
```bash
aws iot start-on-demand-audit-task \
    --target-check-names <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--target-check-names` | **Yes** | list | -- | Audit check names to run |

**Output Schema:**
```json
{
    "taskId": "string"
}
```

---

## 9.10 `describe-audit-task`

Describes an audit task.

**Synopsis:**
```bash
aws iot describe-audit-task \
    --task-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--task-id` | **Yes** | string | -- | Audit task ID |

**Output Schema:**
```json
{
    "taskStatus": "IN_PROGRESS|COMPLETED|FAILED|CANCELED",
    "taskType": "ON_DEMAND_AUDIT_TASK|SCHEDULED_AUDIT_TASK",
    "taskStartTime": "timestamp",
    "taskStatistics": {
        "totalChecks": "integer",
        "inProgressChecks": "integer",
        "waitingForDataCollectionChecks": "integer",
        "compliantChecks": "integer",
        "nonCompliantChecks": "integer",
        "failedChecks": "integer",
        "canceledChecks": "integer"
    },
    "scheduledAuditName": "string",
    "auditDetails": {}
}
```

---

## 9.11 `list-audit-tasks`

Lists audit tasks. **Paginated operation.**

**Synopsis:**
```bash
aws iot list-audit-tasks \
    --start-time <value> \
    --end-time <value> \
    [--task-type <value>] \
    [--task-status <value>] \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--start-time` | **Yes** | timestamp | -- | Start of time range |
| `--end-time` | **Yes** | timestamp | -- | End of time range |
| `--task-type` | No | string | None | `ON_DEMAND_AUDIT_TASK` or `SCHEDULED_AUDIT_TASK` |
| `--task-status` | No | string | None | `IN_PROGRESS`, `COMPLETED`, `FAILED`, `CANCELED` |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-250) |

**Output Schema:**
```json
{
    "tasks": [
        {
            "taskId": "string",
            "taskStatus": "string",
            "taskType": "string"
        }
    ],
    "nextToken": "string"
}
```

---

## 9.12 `describe-audit-finding`

Describes an audit finding.

**Synopsis:**
```bash
aws iot describe-audit-finding \
    --finding-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--finding-id` | **Yes** | string | -- | Finding ID |

**Output Schema:**
```json
{
    "finding": {
        "findingId": "string",
        "taskId": "string",
        "checkName": "string",
        "taskStartTime": "timestamp",
        "findingTime": "timestamp",
        "severity": "CRITICAL|HIGH|MEDIUM|LOW",
        "nonCompliantResource": {
            "resourceType": "DEVICE_CERTIFICATE|CA_CERTIFICATE|IOT_POLICY|COGNITO_IDENTITY_POOL|CLIENT_ID|ACCOUNT_SETTINGS|ROLE_ALIAS|IAM_ROLE|ISSUER_CERTIFICATE",
            "resourceIdentifier": {},
            "additionalInfo": {}
        },
        "relatedResources": [],
        "reasonForNonCompliance": "string",
        "reasonForNonComplianceCode": "string",
        "isSuppressed": "boolean"
    }
}
```

---

## 9.13 `list-audit-findings`

Lists audit findings. **Paginated operation.**

**Synopsis:**
```bash
aws iot list-audit-findings \
    [--task-id <value>] \
    [--check-name <value>] \
    [--resource-identifier <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--start-time <value>] \
    [--end-time <value>] \
    [--list-suppressed-findings | --no-list-suppressed-findings] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--task-id` | No | string | None | Filter by task ID |
| `--check-name` | No | string | None | Filter by check name |
| `--resource-identifier` | No | structure | None | Filter by resource |
| `--max-results` | No | integer | None | Max results (1-250) |
| `--next-token` | No | string | None | Pagination token |
| `--start-time` | No | timestamp | None | Start of time range |
| `--end-time` | No | timestamp | None | End of time range |
| `--list-suppressed-findings` | No | boolean | false | Include suppressed findings |

**Output Schema:**
```json
{
    "findings": [
        {
            "findingId": "string",
            "taskId": "string",
            "checkName": "string",
            "findingTime": "timestamp",
            "severity": "string",
            "nonCompliantResource": {},
            "isSuppressed": "boolean"
        }
    ],
    "nextToken": "string"
}
```

---

## 9.14 `list-related-resources-for-audit-finding`

Lists resources related to an audit finding.

**Synopsis:**
```bash
aws iot list-related-resources-for-audit-finding \
    --finding-id <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--finding-id` | **Yes** | string | -- | Finding ID |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results |

**Output Schema:**
```json
{
    "relatedResources": [
        {
            "resourceType": "string",
            "resourceIdentifier": {},
            "additionalInfo": {}
        }
    ],
    "nextToken": "string"
}
```

---

## 9.15 `create-audit-suppression`

Creates an audit finding suppression.

**Synopsis:**
```bash
aws iot create-audit-suppression \
    --check-name <value> \
    --resource-identifier <value> \
    --client-request-token <value> \
    [--expiration-date <value>] \
    [--suppress-indefinitely | --no-suppress-indefinitely] \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--check-name` | **Yes** | string | -- | Audit check name |
| `--resource-identifier` | **Yes** | structure | -- | Resource to suppress |
| `--client-request-token` | **Yes** | string | -- | Idempotency token |
| `--expiration-date` | No | timestamp | None | Suppression expiration |
| `--suppress-indefinitely` | No | boolean | false | Suppress indefinitely |
| `--description` | No | string | None | Description |

**Output:** None

---

## 9.16 `describe-audit-suppression`

Describes an audit suppression.

**Synopsis:**
```bash
aws iot describe-audit-suppression \
    --check-name <value> \
    --resource-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--check-name` | **Yes** | string | -- | Audit check name |
| `--resource-identifier` | **Yes** | structure | -- | Resource identifier |

**Output Schema:**
```json
{
    "checkName": "string",
    "resourceIdentifier": {},
    "expirationDate": "timestamp",
    "suppressIndefinitely": "boolean",
    "description": "string"
}
```

---

## 9.17 `list-audit-suppressions`

Lists audit suppressions. **Paginated operation.**

**Synopsis:**
```bash
aws iot list-audit-suppressions \
    [--check-name <value>] \
    [--resource-identifier <value>] \
    [--ascending-order | --no-ascending-order] \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--check-name` | No | string | None | Filter by check name |
| `--resource-identifier` | No | structure | None | Filter by resource |
| `--ascending-order` | No | boolean | false | Sort ascending |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-250) |

**Output Schema:**
```json
{
    "suppressions": [
        {
            "checkName": "string",
            "resourceIdentifier": {},
            "expirationDate": "timestamp",
            "suppressIndefinitely": "boolean",
            "description": "string"
        }
    ],
    "nextToken": "string"
}
```

---

## 9.18 `update-audit-suppression`

Updates an audit suppression.

**Synopsis:**
```bash
aws iot update-audit-suppression \
    --check-name <value> \
    --resource-identifier <value> \
    [--expiration-date <value>] \
    [--suppress-indefinitely | --no-suppress-indefinitely] \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--check-name` | **Yes** | string | -- | Audit check name |
| `--resource-identifier` | **Yes** | structure | -- | Resource identifier |
| `--expiration-date` | No | timestamp | None | Updated expiration |
| `--suppress-indefinitely` | No | boolean | None | Suppress indefinitely |
| `--description` | No | string | None | Updated description |

**Output:** None

---

## 9.19 `delete-audit-suppression`

Deletes an audit suppression.

**Synopsis:**
```bash
aws iot delete-audit-suppression \
    --check-name <value> \
    --resource-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--check-name` | **Yes** | string | -- | Audit check name |
| `--resource-identifier` | **Yes** | structure | -- | Resource identifier |

**Output:** None

---

## 9.20 `create-mitigation-action`

Creates a mitigation action for audit findings.

**Synopsis:**
```bash
aws iot create-mitigation-action \
    --action-name <value> \
    --role-arn <value> \
    --action-params <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--action-name` | **Yes** | string | -- | Action name (1-128 chars) |
| `--role-arn` | **Yes** | string | -- | IAM role ARN |
| `--action-params` | **Yes** | structure | -- | Action parameters (one of the types below) |
| `--tags` | No | list | None | Tags |

**ActionParams (one of):**
- `updateDeviceCertificateParams`: `{action: "DEACTIVATE"}`
- `updateCACertificateParams`: `{action: "DEACTIVATE"}`
- `addThingsToThingGroupParams`: `{thingGroupNames: [], overrideDynamicGroups: boolean}`
- `replaceDefaultPolicyVersionParams`: `{templateName: "BLANK_POLICY"}`
- `enableIoTLoggingParams`: `{roleArnForLogging: "string", logLevel: "DEBUG|INFO|ERROR|WARN|DISABLED"}`
- `publishFindingToSnsParams`: `{topicArn: "string"}`

**Output Schema:**
```json
{
    "actionArn": "string",
    "actionId": "string"
}
```

---

## 9.21 `describe-mitigation-action`

Describes a mitigation action.

**Synopsis:**
```bash
aws iot describe-mitigation-action \
    --action-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--action-name` | **Yes** | string | -- | Action name |

**Output Schema:**
```json
{
    "actionName": "string",
    "actionType": "UPDATE_DEVICE_CERTIFICATE|UPDATE_CA_CERTIFICATE|ADD_THINGS_TO_THING_GROUP|REPLACE_DEFAULT_POLICY_VERSION|ENABLE_IOT_LOGGING|PUBLISH_FINDING_TO_SNS",
    "actionArn": "string",
    "actionId": "string",
    "roleArn": "string",
    "actionParams": {},
    "creationDate": "timestamp",
    "lastModifiedDate": "timestamp"
}
```

---

## 9.22 `list-mitigation-actions`

Lists mitigation actions. **Paginated operation.**

**Synopsis:**
```bash
aws iot list-mitigation-actions \
    [--action-type <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--action-type` | No | string | None | Filter by action type |
| `--max-results` | No | integer | None | Max results (1-250) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "actionIdentifiers": [
        {
            "actionName": "string",
            "actionArn": "string",
            "creationDate": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

## 9.23 `update-mitigation-action`

Updates a mitigation action.

**Synopsis:**
```bash
aws iot update-mitigation-action \
    --action-name <value> \
    [--role-arn <value>] \
    [--action-params <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--action-name` | **Yes** | string | -- | Action name |
| `--role-arn` | No | string | None | Updated IAM role ARN |
| `--action-params` | No | structure | None | Updated action parameters |

**Output Schema:**
```json
{
    "actionArn": "string",
    "actionId": "string"
}
```

---

## 9.24 `delete-mitigation-action`

Deletes a mitigation action.

**Synopsis:**
```bash
aws iot delete-mitigation-action \
    --action-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--action-name` | **Yes** | string | -- | Action name |

**Output:** None

---

## 9.25 `start-audit-mitigation-actions-task`

Starts applying mitigation actions to audit findings.

**Synopsis:**
```bash
aws iot start-audit-mitigation-actions-task \
    --task-id <value> \
    --target <value> \
    --audit-check-to-actions-mapping <value> \
    --client-request-token <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--task-id` | **Yes** | string | -- | Task ID (1-128 chars) |
| `--target` | **Yes** | structure | -- | Target: auditTaskId, findingIds, or auditCheckToReasonCodeFilter |
| `--audit-check-to-actions-mapping` | **Yes** | map | -- | Map of check names to action name lists |
| `--client-request-token` | **Yes** | string | -- | Idempotency token |

**Output Schema:**
```json
{
    "taskId": "string"
}
```

---

## 9.26 `describe-audit-mitigation-actions-task`

Describes an audit mitigation actions task.

**Synopsis:**
```bash
aws iot describe-audit-mitigation-actions-task \
    --task-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--task-id` | **Yes** | string | -- | Task ID |

**Output Schema:**
```json
{
    "taskStatus": "IN_PROGRESS|COMPLETED|FAILED|CANCELED",
    "startTime": "timestamp",
    "endTime": "timestamp",
    "taskStatistics": {},
    "target": {},
    "auditCheckToActionsMapping": {},
    "actionsDefinition": []
}
```

---

## 9.27 `list-audit-mitigation-actions-tasks`

Lists audit mitigation actions tasks. **Paginated operation.**

**Synopsis:**
```bash
aws iot list-audit-mitigation-actions-tasks \
    --start-time <value> \
    --end-time <value> \
    [--audit-task-id <value>] \
    [--finding-id <value>] \
    [--task-status <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--start-time` | **Yes** | timestamp | -- | Start of time range |
| `--end-time` | **Yes** | timestamp | -- | End of time range |
| `--audit-task-id` | No | string | None | Filter by audit task ID |
| `--finding-id` | No | string | None | Filter by finding ID |
| `--task-status` | No | string | None | Filter by status |
| `--max-results` | No | integer | None | Max results |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "tasks": [
        {
            "taskId": "string",
            "startTime": "timestamp",
            "taskStatus": "string"
        }
    ],
    "nextToken": "string"
}
```

---

## 9.28 `list-audit-mitigation-actions-executions`

Lists executions of audit mitigation actions. **Paginated operation.**

**Synopsis:**
```bash
aws iot list-audit-mitigation-actions-executions \
    --task-id <value> \
    --finding-id <value> \
    [--action-status <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--task-id` | **Yes** | string | -- | Task ID |
| `--finding-id` | **Yes** | string | -- | Finding ID |
| `--action-status` | No | string | None | Filter: `IN_PROGRESS`, `COMPLETED`, `FAILED`, `CANCELED`, `SKIPPED`, `PENDING` |
| `--max-results` | No | integer | None | Max results |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "actionsExecutions": [
        {
            "taskId": "string",
            "findingId": "string",
            "actionName": "string",
            "actionId": "string",
            "status": "string",
            "startTime": "timestamp",
            "endTime": "timestamp",
            "errorCode": "string",
            "message": "string"
        }
    ],
    "nextToken": "string"
}
```

---

## 9.29 `cancel-audit-mitigation-actions-task`

Cancels an audit mitigation actions task.

**Synopsis:**
```bash
aws iot cancel-audit-mitigation-actions-task \
    --task-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--task-id` | **Yes** | string | -- | Task ID |

**Output:** None
