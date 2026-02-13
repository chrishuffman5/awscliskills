# Maintenance Windows

### 5.1 `create-maintenance-window`

Creates a maintenance window for scheduling tasks on managed instances.

**Synopsis:**
```bash
aws ssm create-maintenance-window \
    --name <value> \
    --schedule <value> \
    --duration <value> \
    --cutoff <value> \
    --allow-unassociated-targets \
    [--description <value>] \
    [--start-date <value>] \
    [--end-date <value>] \
    [--schedule-timezone <value>] \
    [--schedule-offset <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Maintenance window name |
| `--schedule` | **Yes** | string | -- | Schedule expression: cron or rate (e.g. `cron(0 2 ? * SUN *)`, `rate(7 days)`) |
| `--duration` | **Yes** | integer | -- | Duration in hours (1-24) |
| `--cutoff` | **Yes** | integer | -- | Hours before end to stop scheduling new tasks |
| `--allow-unassociated-targets` | **Yes** | boolean | -- | Allow tasks without targets (for Run Command) |
| `--description` | No | string | None | Description (max 128 chars) |
| `--start-date` | No | string | None | Start date (ISO 8601) |
| `--end-date` | No | string | None | End date (ISO 8601) |
| `--schedule-timezone` | No | string | `UTC` | IANA timezone for the schedule |
| `--schedule-offset` | No | integer | None | Days offset for cron schedules (1-6) |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "WindowId": "string"
}
```

---

### 5.2 `delete-maintenance-window`

Deletes a maintenance window.

**Synopsis:**
```bash
aws ssm delete-maintenance-window \
    --window-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--window-id` | **Yes** | string | -- | Maintenance window ID |

**Output Schema:**
```json
{
    "WindowId": "string"
}
```

---

### 5.3 `describe-maintenance-windows`

Lists maintenance windows. **Paginated operation.**

**Synopsis:**
```bash
aws ssm describe-maintenance-windows \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | list | None | Filters: `Name`, `Enabled` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "WindowIdentities": [
        {
            "WindowId": "string",
            "Name": "string",
            "Description": "string",
            "Enabled": true,
            "Duration": "integer",
            "Cutoff": "integer",
            "Schedule": "string",
            "ScheduleTimezone": "string",
            "ScheduleOffset": "integer",
            "EndDate": "string",
            "StartDate": "string",
            "NextExecutionTime": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 5.4 `get-maintenance-window`

Gets details about a specific maintenance window.

**Synopsis:**
```bash
aws ssm get-maintenance-window \
    --window-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--window-id` | **Yes** | string | -- | Maintenance window ID |

**Output Schema:**
```json
{
    "WindowId": "string",
    "Name": "string",
    "Description": "string",
    "StartDate": "string",
    "EndDate": "string",
    "Schedule": "string",
    "ScheduleTimezone": "string",
    "ScheduleOffset": "integer",
    "NextExecutionTime": "string",
    "Duration": "integer",
    "Cutoff": "integer",
    "AllowUnassociatedTargets": true,
    "Enabled": true,
    "CreatedDate": "timestamp",
    "ModifiedDate": "timestamp"
}
```

---

### 5.5 `update-maintenance-window`

Updates a maintenance window configuration.

**Synopsis:**
```bash
aws ssm update-maintenance-window \
    --window-id <value> \
    [--name <value>] \
    [--description <value>] \
    [--start-date <value>] \
    [--end-date <value>] \
    [--schedule <value>] \
    [--schedule-timezone <value>] \
    [--schedule-offset <value>] \
    [--duration <value>] \
    [--cutoff <value>] \
    [--allow-unassociated-targets | --no-allow-unassociated-targets] \
    [--enabled | --no-enabled] \
    [--replace | --no-replace] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--window-id` | **Yes** | string | -- | Maintenance window ID |
| `--name` | No | string | None | Updated name |
| `--description` | No | string | None | Updated description |
| `--schedule` | No | string | None | Updated schedule expression |
| `--schedule-timezone` | No | string | None | Updated timezone |
| `--duration` | No | integer | None | Updated duration |
| `--cutoff` | No | integer | None | Updated cutoff |
| `--enabled` | No | boolean | None | Enable the window |
| `--no-enabled` | No | boolean | None | Disable the window |
| `--replace` | No | boolean | false | Replace all optional fields with provided values |

**Output Schema:**
```json
{
    "WindowId": "string",
    "Name": "string",
    "Description": "string",
    "StartDate": "string",
    "EndDate": "string",
    "Schedule": "string",
    "ScheduleTimezone": "string",
    "ScheduleOffset": "integer",
    "Duration": "integer",
    "Cutoff": "integer",
    "AllowUnassociatedTargets": true,
    "Enabled": true
}
```

---

### 5.6 `register-target-with-maintenance-window`

Registers a target (instances) with a maintenance window.

**Synopsis:**
```bash
aws ssm register-target-with-maintenance-window \
    --window-id <value> \
    --resource-type <value> \
    --targets <value> \
    [--owner-information <value>] \
    [--name <value>] \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--window-id` | **Yes** | string | -- | Maintenance window ID |
| `--resource-type` | **Yes** | string | -- | Resource type: `INSTANCE` or `RESOURCE_GROUP` |
| `--targets` | **Yes** | list | -- | Targets. Shorthand: `Key=InstanceIds\|tag:TagName,Values=string ...` |
| `--owner-information` | No | string | None | Owner information |
| `--name` | No | string | None | Target registration name |
| `--description` | No | string | None | Description |

**Output Schema:**
```json
{
    "WindowTargetId": "string"
}
```

---

### 5.7 `deregister-target-from-maintenance-window`

Removes a target from a maintenance window.

**Synopsis:**
```bash
aws ssm deregister-target-from-maintenance-window \
    --window-id <value> \
    --window-target-id <value> \
    [--safe | --no-safe] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--window-id` | **Yes** | string | -- | Maintenance window ID |
| `--window-target-id` | **Yes** | string | -- | Target ID to deregister |
| `--safe` | No | boolean | true | Check if target is referenced by tasks before removing |

**Output Schema:**
```json
{
    "WindowId": "string",
    "WindowTargetId": "string"
}
```

---

### 5.8 `describe-maintenance-window-targets`

Lists the targets registered with a maintenance window. **Paginated operation.**

**Synopsis:**
```bash
aws ssm describe-maintenance-window-targets \
    --window-id <value> \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--window-id` | **Yes** | string | -- | Maintenance window ID |
| `--filters` | No | list | None | Filters |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Targets": [
        {
            "WindowId": "string",
            "WindowTargetId": "string",
            "ResourceType": "INSTANCE|RESOURCE_GROUP",
            "Targets": [],
            "OwnerInformation": "string",
            "Name": "string",
            "Description": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 5.9 `register-task-with-maintenance-window`

Registers a task (Run Command, Automation, Step Functions, or Lambda) with a maintenance window.

**Synopsis:**
```bash
aws ssm register-task-with-maintenance-window \
    --window-id <value> \
    --task-arn <value> \
    --task-type <value> \
    [--targets <value>] \
    [--service-role-arn <value>] \
    [--task-parameters <value>] \
    [--task-invocation-parameters <value>] \
    [--priority <value>] \
    [--max-concurrency <value>] \
    [--max-errors <value>] \
    [--logging-info <value>] \
    [--name <value>] \
    [--description <value>] \
    [--cutoff-behavior <value>] \
    [--alarm-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--window-id` | **Yes** | string | -- | Maintenance window ID |
| `--task-arn` | **Yes** | string | -- | Task ARN (document name for Run Command, ARN for others) |
| `--task-type` | **Yes** | string | -- | Task type: `RUN_COMMAND`, `AUTOMATION`, `STEP_FUNCTIONS`, `LAMBDA` |
| `--targets` | No | list | None | Targets for the task |
| `--service-role-arn` | No | string | None | IAM service role ARN |
| `--task-invocation-parameters` | No | structure | None | Task-specific invocation parameters |
| `--priority` | No | integer | 0 | Task priority (0 = highest) |
| `--max-concurrency` | No | string | None | Max concurrent targets |
| `--max-errors` | No | string | None | Max errors before stopping |
| `--name` | No | string | None | Task name |
| `--description` | No | string | None | Task description |
| `--cutoff-behavior` | No | string | None | Behavior at window cutoff: `CONTINUE_TASK` or `CANCEL_TASK` |

**Output Schema:**
```json
{
    "WindowTaskId": "string"
}
```

---

### 5.10 `deregister-task-from-maintenance-window`

Removes a task from a maintenance window.

**Synopsis:**
```bash
aws ssm deregister-task-from-maintenance-window \
    --window-id <value> \
    --window-task-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--window-id` | **Yes** | string | -- | Maintenance window ID |
| `--window-task-id` | **Yes** | string | -- | Task ID to deregister |

**Output Schema:**
```json
{
    "WindowId": "string",
    "WindowTaskId": "string"
}
```

---

### 5.11 `describe-maintenance-window-tasks`

Lists the tasks registered with a maintenance window. **Paginated operation.**

**Synopsis:**
```bash
aws ssm describe-maintenance-window-tasks \
    --window-id <value> \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--window-id` | **Yes** | string | -- | Maintenance window ID |
| `--filters` | No | list | None | Filters |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Tasks": [
        {
            "WindowId": "string",
            "WindowTaskId": "string",
            "TaskArn": "string",
            "Type": "RUN_COMMAND|AUTOMATION|STEP_FUNCTIONS|LAMBDA",
            "Targets": [],
            "TaskParameters": {},
            "Priority": "integer",
            "LoggingInfo": {},
            "ServiceRoleArn": "string",
            "MaxConcurrency": "string",
            "MaxErrors": "string",
            "Name": "string",
            "Description": "string",
            "CutoffBehavior": "CONTINUE_TASK|CANCEL_TASK",
            "AlarmConfiguration": {}
        }
    ],
    "NextToken": "string"
}
```

---

### 5.12 `describe-maintenance-window-executions`

Lists executions of a maintenance window. **Paginated operation.**

**Synopsis:**
```bash
aws ssm describe-maintenance-window-executions \
    --window-id <value> \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--window-id` | **Yes** | string | -- | Maintenance window ID |
| `--filters` | No | list | None | Filters: `ExecutedBefore`, `ExecutedAfter`, `Status` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "WindowExecutions": [
        {
            "WindowId": "string",
            "WindowExecutionId": "string",
            "Status": "PENDING|IN_PROGRESS|SUCCESS|FAILED|TIMED_OUT|CANCELLING|CANCELLED|SKIPPED_OVERLAPPING",
            "StatusDetails": "string",
            "StartTime": "timestamp",
            "EndTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 5.13 `get-maintenance-window-execution`

Gets details about a specific maintenance window execution.

**Synopsis:**
```bash
aws ssm get-maintenance-window-execution \
    --window-execution-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--window-execution-id` | **Yes** | string | -- | Window execution ID |

**Output Schema:**
```json
{
    "WindowExecutionId": "string",
    "TaskIds": ["string"],
    "Status": "PENDING|IN_PROGRESS|SUCCESS|FAILED|TIMED_OUT|CANCELLING|CANCELLED|SKIPPED_OVERLAPPING",
    "StatusDetails": "string",
    "StartTime": "timestamp",
    "EndTime": "timestamp"
}
```

---

### 5.14 `get-maintenance-window-execution-task`

Gets details about a specific task execution within a maintenance window execution.

**Synopsis:**
```bash
aws ssm get-maintenance-window-execution-task \
    --window-execution-id <value> \
    --task-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--window-execution-id` | **Yes** | string | -- | Window execution ID |
| `--task-id` | **Yes** | string | -- | Task ID |

**Output Schema:**
```json
{
    "WindowExecutionId": "string",
    "TaskExecutionId": "string",
    "TaskArn": "string",
    "ServiceRole": "string",
    "Type": "RUN_COMMAND|AUTOMATION|STEP_FUNCTIONS|LAMBDA",
    "TaskParameters": [],
    "Priority": "integer",
    "MaxConcurrency": "string",
    "MaxErrors": "string",
    "Status": "PENDING|IN_PROGRESS|SUCCESS|FAILED|TIMED_OUT|CANCELLING|CANCELLED|SKIPPED_OVERLAPPING",
    "StatusDetails": "string",
    "StartTime": "timestamp",
    "EndTime": "timestamp",
    "AlarmConfiguration": {},
    "TriggeredAlarms": []
}
```
