# Budget Actions

### 2.1 `create-budget-action`

Creates a budget action that triggers auto-remediation when a budget threshold is breached.

**Synopsis:**
```bash
aws budgets create-budget-action \
    --account-id <value> \
    --budget-name <value> \
    --notification-type <value> \
    --action-type <value> \
    --action-threshold <value> \
    --definition <value> \
    --execution-role-arn <value> \
    --approval-model <value> \
    --subscribers <value> \
    [--resource-tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | 12-digit AWS account ID |
| `--budget-name` | **Yes** | string | -- | Budget name (1-100 chars) |
| `--notification-type` | **Yes** | string | -- | `ACTUAL` or `FORECASTED` |
| `--action-type` | **Yes** | string | -- | `APPLY_IAM_POLICY`, `APPLY_SCP_POLICY`, or `RUN_SSM_DOCUMENTS` |
| `--action-threshold` | **Yes** | structure | -- | Threshold trigger. Shorthand: `ActionThresholdValue=double,ActionThresholdType=PERCENTAGE\|ABSOLUTE_VALUE` |
| `--definition` | **Yes** | structure | -- | Action definition (IAM, SCP, or SSM). See structures below |
| `--execution-role-arn` | **Yes** | string | -- | IAM role ARN for action execution |
| `--approval-model` | **Yes** | string | -- | `AUTOMATIC` or `MANUAL` |
| `--subscribers` | **Yes** | list | -- | Notification subscribers (1-11). Shorthand: `SubscriptionType=EMAIL,Address=user@example.com` |
| `--resource-tags` | No | list | None | Tags (max 200) |

**IAM Action Definition:**
```json
{
    "IamActionDefinition": {
        "PolicyArn": "string",
        "Roles": ["string"],
        "Groups": ["string"],
        "Users": ["string"]
    }
}
```

**SCP Action Definition:**
```json
{
    "ScpActionDefinition": {
        "PolicyId": "string",
        "TargetIds": ["string"]
    }
}
```

**SSM Action Definition:**
```json
{
    "SsmActionDefinition": {
        "ActionSubType": "STOP_EC2_INSTANCES|STOP_RDS_INSTANCES",
        "Region": "string",
        "InstanceIds": ["string"]
    }
}
```

**Output Schema:**
```json
{
    "AccountId": "string",
    "BudgetName": "string",
    "ActionId": "string"
}
```

---

### 2.2 `delete-budget-action`

Deletes a budget action.

**Synopsis:**
```bash
aws budgets delete-budget-action \
    --account-id <value> \
    --budget-name <value> \
    --action-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | 12-digit AWS account ID |
| `--budget-name` | **Yes** | string | -- | Budget name |
| `--action-id` | **Yes** | string | -- | Action ID (UUID, 36 chars) |

**Output Schema:**
```json
{
    "AccountId": "string",
    "BudgetName": "string",
    "Action": {
        "ActionId": "string",
        "BudgetName": "string",
        "NotificationType": "ACTUAL|FORECASTED",
        "ActionType": "APPLY_IAM_POLICY|APPLY_SCP_POLICY|RUN_SSM_DOCUMENTS",
        "ActionThreshold": {
            "ActionThresholdValue": "double",
            "ActionThresholdType": "PERCENTAGE|ABSOLUTE_VALUE"
        },
        "Definition": {},
        "ExecutionRoleArn": "string",
        "ApprovalModel": "AUTOMATIC|MANUAL",
        "Status": "STANDBY|PENDING|EXECUTION_IN_PROGRESS|EXECUTION_SUCCESS|EXECUTION_FAILURE|REVERSE_IN_PROGRESS|REVERSE_SUCCESS|REVERSE_FAILURE|RESET_IN_PROGRESS|RESET_FAILURE",
        "Subscribers": []
    }
}
```

---

### 2.3 `describe-budget-action`

Describes a budget action detail.

**Synopsis:**
```bash
aws budgets describe-budget-action \
    --account-id <value> \
    --budget-name <value> \
    --action-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | 12-digit AWS account ID |
| `--budget-name` | **Yes** | string | -- | Budget name |
| `--action-id` | **Yes** | string | -- | Action ID (UUID) |

**Output Schema:**
```json
{
    "AccountId": "string",
    "BudgetName": "string",
    "Action": {
        "ActionId": "string",
        "BudgetName": "string",
        "NotificationType": "ACTUAL|FORECASTED",
        "ActionType": "string",
        "ActionThreshold": {},
        "Definition": {},
        "ExecutionRoleArn": "string",
        "ApprovalModel": "AUTOMATIC|MANUAL",
        "Status": "string",
        "Subscribers": []
    }
}
```

---

### 2.4 `update-budget-action`

Updates a budget action.

**Synopsis:**
```bash
aws budgets update-budget-action \
    --account-id <value> \
    --budget-name <value> \
    --action-id <value> \
    [--notification-type <value>] \
    [--action-threshold <value>] \
    [--definition <value>] \
    [--execution-role-arn <value>] \
    [--approval-model <value>] \
    [--subscribers <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | 12-digit AWS account ID |
| `--budget-name` | **Yes** | string | -- | Budget name |
| `--action-id` | **Yes** | string | -- | Action ID (UUID) |
| `--notification-type` | No | string | None | `ACTUAL` or `FORECASTED` |
| `--action-threshold` | No | structure | None | Updated threshold |
| `--definition` | No | structure | None | Updated action definition |
| `--execution-role-arn` | No | string | None | Updated execution role ARN |
| `--approval-model` | No | string | None | `AUTOMATIC` or `MANUAL` |
| `--subscribers` | No | list | None | Updated subscribers |

**Output Schema:**
```json
{
    "AccountId": "string",
    "BudgetName": "string",
    "OldAction": {},
    "NewAction": {}
}
```

---

### 2.5 `execute-budget-action`

Manually executes a budget action.

**Synopsis:**
```bash
aws budgets execute-budget-action \
    --account-id <value> \
    --budget-name <value> \
    --action-id <value> \
    --execution-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | 12-digit AWS account ID |
| `--budget-name` | **Yes** | string | -- | Budget name |
| `--action-id` | **Yes** | string | -- | Action ID (UUID) |
| `--execution-type` | **Yes** | string | -- | `APPROVE_BUDGET_ACTION`, `RETRY_BUDGET_ACTION`, `REVERSE_BUDGET_ACTION`, or `RESET_BUDGET_ACTION` |

**Output Schema:**
```json
{
    "AccountId": "string",
    "BudgetName": "string",
    "ActionId": "string",
    "ExecutionType": "APPROVE_BUDGET_ACTION|RETRY_BUDGET_ACTION|REVERSE_BUDGET_ACTION|RESET_BUDGET_ACTION"
}
```

---

### 2.6 `describe-budget-action-histories`

Describes the history of the status changes for a budget action. **Paginated.**

**Synopsis:**
```bash
aws budgets describe-budget-action-histories \
    --account-id <value> \
    --budget-name <value> \
    --action-id <value> \
    [--time-period <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | 12-digit AWS account ID |
| `--budget-name` | **Yes** | string | -- | Budget name |
| `--action-id` | **Yes** | string | -- | Action ID (UUID) |
| `--time-period` | No | structure | None | Filter by time range |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ActionHistories": [
        {
            "Timestamp": "timestamp",
            "Status": "STANDBY|PENDING|EXECUTION_IN_PROGRESS|EXECUTION_SUCCESS|EXECUTION_FAILURE|REVERSE_IN_PROGRESS|REVERSE_SUCCESS|REVERSE_FAILURE|RESET_IN_PROGRESS|RESET_FAILURE",
            "EventType": "SYSTEM|CREATE_ACTION|DELETE_ACTION|UPDATE_ACTION|EXECUTE_ACTION",
            "ActionHistoryDetails": {
                "Message": "string",
                "Action": {}
            }
        }
    ],
    "NextToken": "string"
}
```

---

### 2.7 `describe-budget-actions-for-account`

Lists all budget actions for an account. **Paginated.**

**Synopsis:**
```bash
aws budgets describe-budget-actions-for-account \
    --account-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | 12-digit AWS account ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Actions": [
        {
            "ActionId": "string",
            "BudgetName": "string",
            "NotificationType": "string",
            "ActionType": "string",
            "ActionThreshold": {},
            "Definition": {},
            "ExecutionRoleArn": "string",
            "ApprovalModel": "string",
            "Status": "string",
            "Subscribers": []
        }
    ],
    "NextToken": "string"
}
```

---

### 2.8 `describe-budget-actions-for-budget`

Lists all budget actions for a specific budget. **Paginated.**

**Synopsis:**
```bash
aws budgets describe-budget-actions-for-budget \
    --account-id <value> \
    --budget-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | 12-digit AWS account ID |
| `--budget-name` | **Yes** | string | -- | Budget name |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Actions": [
        {
            "ActionId": "string",
            "BudgetName": "string",
            "NotificationType": "string",
            "ActionType": "string",
            "ActionThreshold": {},
            "Definition": {},
            "ExecutionRoleArn": "string",
            "ApprovalModel": "string",
            "Status": "string",
            "Subscribers": []
        }
    ],
    "NextToken": "string"
}
```
