# Restore Testing

### 10.1 `create-restore-testing-plan`

Creates a restore testing plan that automatically tests recovery points.

**Synopsis:**
```bash
aws backup create-restore-testing-plan \
    --restore-testing-plan <value> \
    [--creator-request-id <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--restore-testing-plan` | **Yes** | structure | -- | Restore testing plan configuration |
| `--creator-request-id` | No | string | None | Idempotency token |
| `--tags` | No | map | None | Tags |

**Restore Testing Plan Structure:**
```json
{
    "RestoreTestingPlanName": "string",
    "ScheduleExpression": "cron(...)",
    "ScheduleExpressionTimezone": "string",
    "StartWindowHours": "integer",
    "RecoveryPointSelection": {
        "Algorithm": "LATEST_WITHIN_WINDOW|RANDOM_WITHIN_WINDOW",
        "IncludeVaults": ["string"],
        "ExcludeVaults": ["string"],
        "RecoveryPointTypes": ["CONTINUOUS", "SNAPSHOT"],
        "SelectionWindowDays": "integer"
    }
}
```

**Output Schema:**
```json
{
    "CreationTime": "timestamp",
    "RestoreTestingPlanArn": "string",
    "RestoreTestingPlanName": "string"
}
```

---

### 10.2 `create-restore-testing-selection`

Creates a resource selection for a restore testing plan.

**Synopsis:**
```bash
aws backup create-restore-testing-selection \
    --restore-testing-plan-name <value> \
    --restore-testing-selection <value> \
    [--creator-request-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--restore-testing-plan-name` | **Yes** | string | -- | Plan name |
| `--restore-testing-selection` | **Yes** | structure | -- | Selection configuration |

**Output Schema:**
```json
{
    "CreationTime": "timestamp",
    "RestoreTestingPlanArn": "string",
    "RestoreTestingPlanName": "string",
    "RestoreTestingSelectionName": "string"
}
```

---

### 10.3 `list-restore-testing-plans`

Lists restore testing plans. **Paginated operation.**

**Synopsis:**
```bash
aws backup list-restore-testing-plans \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Output Schema:**
```json
{
    "NextToken": "string",
    "RestoreTestingPlans": [
        {
            "CreationTime": "timestamp",
            "LastExecutionTime": "timestamp",
            "LastUpdateTime": "timestamp",
            "RestoreTestingPlanArn": "string",
            "RestoreTestingPlanName": "string",
            "ScheduleExpression": "string",
            "StartWindowHours": "integer"
        }
    ]
}
```

---

### 10.4 `get-restore-testing-plan`

Returns details of a restore testing plan.

**Synopsis:**
```bash
aws backup get-restore-testing-plan \
    --restore-testing-plan-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--restore-testing-plan-name` | **Yes** | string | -- | Plan name |

**Output Schema:**
```json
{
    "RestoreTestingPlan": {
        "CreationTime": "timestamp",
        "CreatorRequestId": "string",
        "LastExecutionTime": "timestamp",
        "LastUpdateTime": "timestamp",
        "RecoveryPointSelection": {},
        "RestoreTestingPlanArn": "string",
        "RestoreTestingPlanName": "string",
        "ScheduleExpression": "string",
        "ScheduleExpressionTimezone": "string",
        "StartWindowHours": "integer"
    }
}
```
