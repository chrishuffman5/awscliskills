# Schedules

### 1.1 `create-schedule`

Creates a new schedule with a target, schedule expression, and optional retry/DLQ configuration.

**Synopsis:**
```bash
aws scheduler create-schedule \
    --name <value> \
    --schedule-expression <value> \
    --flexible-time-window <value> \
    --target <value> \
    [--action-after-completion <value>] \
    [--client-token <value>] \
    [--description <value>] \
    [--end-date <value>] \
    [--group-name <value>] \
    [--kms-key-arn <value>] \
    [--schedule-expression-timezone <value>] \
    [--start-date <value>] \
    [--state <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Schedule name (1-64 chars, alphanumeric, `-`, `_`, `.`) |
| `--schedule-expression` | **Yes** | string | -- | `at()`, `rate()`, or `cron()` expression (1-256 chars) |
| `--flexible-time-window` | **Yes** | structure | -- | Invocation time window (Mode: OFF or FLEXIBLE) |
| `--target` | **Yes** | structure | -- | Target configuration (Arn + RoleArn required) |
| `--action-after-completion` | No | string | NONE | Action after one-time schedule completes: `NONE` or `DELETE` |
| `--client-token` | No | string | Auto | Idempotency token |
| `--description` | No | string | None | Description (0-512 chars) |
| `--end-date` | No | timestamp | None | UTC end date for recurring schedule |
| `--group-name` | No | string | default | Schedule group name |
| `--kms-key-arn` | No | string | None | KMS key for encryption |
| `--schedule-expression-timezone` | No | string | UTC | IANA time zone (e.g., `America/New_York`) |
| `--start-date` | No | timestamp | None | UTC start date |
| `--state` | No | string | ENABLED | `ENABLED` or `DISABLED` |

**FlexibleTimeWindow structure:**
```json
{
    "Mode": "OFF|FLEXIBLE",
    "MaximumWindowInMinutes": 15
}
```

**Target structure:**
```json
{
    "Arn": "string",
    "RoleArn": "string",
    "Input": "string",
    "RetryPolicy": {
        "MaximumEventAgeInSeconds": 3600,
        "MaximumRetryAttempts": 3
    },
    "DeadLetterConfig": {
        "Arn": "string"
    },
    "EcsParameters": {
        "TaskDefinitionArn": "string",
        "TaskCount": 1,
        "LaunchType": "EC2|FARGATE|EXTERNAL",
        "NetworkConfiguration": {
            "awsvpcConfiguration": {
                "Subnets": ["string"],
                "SecurityGroups": ["string"],
                "AssignPublicIp": "ENABLED|DISABLED"
            }
        },
        "PlatformVersion": "string",
        "Group": "string",
        "CapacityProviderStrategy": [],
        "EnableECSManagedTags": true,
        "EnableExecuteCommand": false,
        "PlacementConstraints": [],
        "PlacementStrategy": [],
        "PropagateTags": "TASK_DEFINITION",
        "ReferenceId": "string",
        "Tags": []
    },
    "EventBridgeParameters": {
        "DetailType": "string",
        "Source": "string"
    },
    "KinesisParameters": {
        "PartitionKey": "string"
    },
    "SageMakerPipelineParameters": {
        "PipelineParameterList": [
            {"Name": "string", "Value": "string"}
        ]
    },
    "SqsParameters": {
        "MessageGroupId": "string"
    }
}
```

**Output Schema:**
```json
{
    "ScheduleArn": "string"
}
```

---

### 1.2 `get-schedule`

Gets details about a schedule.

**Synopsis:**
```bash
aws scheduler get-schedule \
    --name <value> \
    [--group-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Schedule name |
| `--group-name` | No | string | default | Schedule group name |

**Output Schema:**
```json
{
    "Arn": "string",
    "Name": "string",
    "GroupName": "string",
    "Description": "string",
    "ScheduleExpression": "string",
    "ScheduleExpressionTimezone": "string",
    "FlexibleTimeWindow": {
        "Mode": "OFF|FLEXIBLE",
        "MaximumWindowInMinutes": "integer"
    },
    "Target": {
        "Arn": "string",
        "RoleArn": "string",
        "Input": "string",
        "RetryPolicy": {},
        "DeadLetterConfig": {},
        "EcsParameters": {},
        "EventBridgeParameters": {},
        "KinesisParameters": {},
        "SageMakerPipelineParameters": {},
        "SqsParameters": {}
    },
    "State": "ENABLED|DISABLED",
    "ActionAfterCompletion": "NONE|DELETE",
    "StartDate": "timestamp",
    "EndDate": "timestamp",
    "KmsKeyArn": "string",
    "CreationDate": "timestamp",
    "LastModificationDate": "timestamp"
}
```

---

### 1.3 `list-schedules`

Lists schedules with optional filters. **Paginated operation.**

**Synopsis:**
```bash
aws scheduler list-schedules \
    [--group-name <value>] \
    [--name-prefix <value>] \
    [--state <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--group-name` | No | string | None | Filter by schedule group |
| `--name-prefix` | No | string | None | Filter by name prefix |
| `--state` | No | string | None | Filter: `ENABLED` or `DISABLED` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Size of each page |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "Schedules": [
        {
            "Arn": "string",
            "Name": "string",
            "GroupName": "string",
            "State": "ENABLED|DISABLED",
            "CreationDate": "timestamp",
            "LastModificationDate": "timestamp",
            "Target": {
                "Arn": "string"
            }
        }
    ],
    "NextToken": "string"
}
```

---

### 1.4 `update-schedule`

Updates an existing schedule. All parameters from create-schedule apply; you must provide the full schedule configuration.

**Synopsis:**
```bash
aws scheduler update-schedule \
    --name <value> \
    --schedule-expression <value> \
    --flexible-time-window <value> \
    --target <value> \
    [--action-after-completion <value>] \
    [--client-token <value>] \
    [--description <value>] \
    [--end-date <value>] \
    [--group-name <value>] \
    [--kms-key-arn <value>] \
    [--schedule-expression-timezone <value>] \
    [--start-date <value>] \
    [--state <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Schedule name |
| `--schedule-expression` | **Yes** | string | -- | Updated schedule expression |
| `--flexible-time-window` | **Yes** | structure | -- | Updated time window |
| `--target` | **Yes** | structure | -- | Updated target configuration |
| `--action-after-completion` | No | string | None | `NONE` or `DELETE` |
| `--client-token` | No | string | Auto | Idempotency token |
| `--description` | No | string | None | Updated description |
| `--end-date` | No | timestamp | None | Updated end date |
| `--group-name` | No | string | default | Schedule group |
| `--kms-key-arn` | No | string | None | KMS key ARN |
| `--schedule-expression-timezone` | No | string | UTC | Updated time zone |
| `--start-date` | No | timestamp | None | Updated start date |
| `--state` | No | string | None | `ENABLED` or `DISABLED` |

**Output Schema:**
```json
{
    "ScheduleArn": "string"
}
```

---

### 1.5 `delete-schedule`

Deletes a schedule.

**Synopsis:**
```bash
aws scheduler delete-schedule \
    --name <value> \
    [--client-token <value>] \
    [--group-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Schedule name to delete |
| `--client-token` | No | string | Auto | Idempotency token |
| `--group-name` | No | string | default | Schedule group name |

**Output:** None
