# State Manager

### 7.1 `create-association`

Creates a State Manager association that applies a document to targets on a schedule.

**Synopsis:**
```bash
aws ssm create-association \
    --name <value> \
    [--document-version <value>] \
    [--instance-id <value>] \
    [--parameters <value>] \
    [--targets <value>] \
    [--schedule-expression <value>] \
    [--output-location <value>] \
    [--association-name <value>] \
    [--automation-target-parameter-name <value>] \
    [--max-errors <value>] \
    [--max-concurrency <value>] \
    [--compliance-severity <value>] \
    [--sync-compliance <value>] \
    [--apply-only-at-cron-interval | --no-apply-only-at-cron-interval] \
    [--calendar-names <value>] \
    [--target-locations <value>] \
    [--tags <value>] \
    [--alarm-configuration <value>] \
    [--target-maps <value>] \
    [--duration <value>] \
    [--schedule-offset <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Document name to associate |
| `--document-version` | No | string | None | Document version |
| `--instance-id` | No | string | None | Instance ID (use this OR `--targets`) |
| `--parameters` | No | map | None | Document parameters |
| `--targets` | No | list | None | Targets. Shorthand: `Key=InstanceIds\|tag:TagName,Values=string ...` |
| `--schedule-expression` | No | string | None | Cron or rate expression (e.g. `cron(0 2 ? * SUN *)`) |
| `--output-location` | No | structure | None | S3 output location |
| `--association-name` | No | string | None | Friendly name for the association |
| `--max-errors` | No | string | None | Max errors before stopping |
| `--max-concurrency` | No | string | None | Max concurrent targets |
| `--compliance-severity` | No | string | `UNSPECIFIED` | Compliance severity: `CRITICAL`, `HIGH`, `MEDIUM`, `LOW`, `UNSPECIFIED` |
| `--sync-compliance` | No | string | None | Sync compliance: `AUTO` or `MANUAL` |
| `--apply-only-at-cron-interval` | No | boolean | false | Only apply at scheduled intervals, not on creation |
| `--calendar-names` | No | list(string) | None | Change Calendar document names |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |
| `--duration` | No | integer | None | Max duration in hours (1-24) |
| `--schedule-offset` | No | integer | None | Days offset for cron schedules (1-6) |

**Output Schema:**
```json
{
    "AssociationDescription": {
        "Name": "string",
        "InstanceId": "string",
        "AssociationVersion": "string",
        "Date": "timestamp",
        "LastUpdateAssociationDate": "timestamp",
        "Status": {
            "Date": "timestamp",
            "Name": "Pending|Success|Failed",
            "Message": "string",
            "AdditionalInfo": "string"
        },
        "Overview": {
            "Status": "string",
            "DetailedStatus": "string",
            "AssociationStatusAggregatedCount": {}
        },
        "DocumentVersion": "string",
        "AutomationTargetParameterName": "string",
        "Parameters": {},
        "AssociationId": "string",
        "Targets": [],
        "ScheduleExpression": "string",
        "OutputLocation": {},
        "LastExecutionDate": "timestamp",
        "LastSuccessfulExecutionDate": "timestamp",
        "AssociationName": "string",
        "MaxErrors": "string",
        "MaxConcurrency": "string",
        "ComplianceSeverity": "string",
        "SyncCompliance": "string",
        "ApplyOnlyAtCronInterval": true,
        "CalendarNames": [],
        "TargetLocations": [],
        "ScheduleOffset": "integer",
        "Duration": "integer",
        "TargetMaps": [],
        "AlarmConfiguration": {},
        "TriggeredAlarms": []
    }
}
```

---

### 7.2 `delete-association`

Deletes a State Manager association.

**Synopsis:**
```bash
aws ssm delete-association \
    [--name <value>] \
    [--instance-id <value>] \
    [--association-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | No | string | None | Document name (requires `--instance-id`) |
| `--instance-id` | No | string | None | Instance ID (requires `--name`) |
| `--association-id` | No | string | None | Association ID (alternative to name+instance-id) |

**Output Schema:**
```json
{}
```

---

### 7.3 `describe-association`

Describes a State Manager association.

**Synopsis:**
```bash
aws ssm describe-association \
    [--name <value>] \
    [--instance-id <value>] \
    [--association-id <value>] \
    [--association-version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | No | string | None | Document name |
| `--instance-id` | No | string | None | Instance ID |
| `--association-id` | No | string | None | Association ID |
| `--association-version` | No | string | None | Specific version |

**Output Schema:**
```json
{
    "AssociationDescription": {
        "Name": "string",
        "InstanceId": "string",
        "AssociationVersion": "string",
        "Date": "timestamp",
        "Status": {},
        "Overview": {},
        "DocumentVersion": "string",
        "Parameters": {},
        "AssociationId": "string",
        "Targets": [],
        "ScheduleExpression": "string",
        "OutputLocation": {},
        "LastExecutionDate": "timestamp",
        "LastSuccessfulExecutionDate": "timestamp",
        "AssociationName": "string",
        "MaxErrors": "string",
        "MaxConcurrency": "string",
        "ComplianceSeverity": "string",
        "SyncCompliance": "string",
        "ApplyOnlyAtCronInterval": true,
        "CalendarNames": [],
        "TargetLocations": [],
        "ScheduleOffset": "integer",
        "Duration": "integer",
        "TargetMaps": [],
        "AlarmConfiguration": {},
        "TriggeredAlarms": []
    }
}
```

---

### 7.4 `list-associations`

Lists State Manager associations. **Paginated operation.**

**Synopsis:**
```bash
aws ssm list-associations \
    [--association-filter-list <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--association-filter-list` | No | list | None | Filters: `InstanceId`, `Name`, `AssociationId`, `AssociationStatusName`, `LastExecutedBefore`, `LastExecutedAfter`, `AssociationName`, `ResourceGroupName` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Associations": [
        {
            "Name": "string",
            "InstanceId": "string",
            "AssociationId": "string",
            "AssociationVersion": "string",
            "DocumentVersion": "string",
            "Targets": [],
            "LastExecutionDate": "timestamp",
            "Overview": {
                "Status": "string",
                "DetailedStatus": "string",
                "AssociationStatusAggregatedCount": {}
            },
            "ScheduleExpression": "string",
            "AssociationName": "string",
            "ScheduleOffset": "integer",
            "Duration": "integer",
            "TargetMaps": []
        }
    ],
    "NextToken": "string"
}
```

---

### 7.5 `update-association`

Updates a State Manager association.

**Synopsis:**
```bash
aws ssm update-association \
    --association-id <value> \
    [--parameters <value>] \
    [--document-version <value>] \
    [--schedule-expression <value>] \
    [--output-location <value>] \
    [--name <value>] \
    [--targets <value>] \
    [--association-name <value>] \
    [--association-version <value>] \
    [--automation-target-parameter-name <value>] \
    [--max-errors <value>] \
    [--max-concurrency <value>] \
    [--compliance-severity <value>] \
    [--sync-compliance <value>] \
    [--apply-only-at-cron-interval | --no-apply-only-at-cron-interval] \
    [--calendar-names <value>] \
    [--target-locations <value>] \
    [--alarm-configuration <value>] \
    [--target-maps <value>] \
    [--duration <value>] \
    [--schedule-offset <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--association-id` | **Yes** | string | -- | Association ID |
| `--parameters` | No | map | None | Updated parameters |
| `--document-version` | No | string | None | Updated document version |
| `--schedule-expression` | No | string | None | Updated schedule |
| `--output-location` | No | structure | None | Updated output location |
| `--name` | No | string | None | Updated document name |
| `--targets` | No | list | None | Updated targets |
| `--association-name` | No | string | None | Updated association name |
| `--max-errors` | No | string | None | Updated max errors |
| `--max-concurrency` | No | string | None | Updated max concurrency |
| `--compliance-severity` | No | string | None | Updated compliance severity |
| `--sync-compliance` | No | string | None | Updated sync compliance |
| `--duration` | No | integer | None | Updated duration |
| `--schedule-offset` | No | integer | None | Updated schedule offset |

**Output Schema:**
```json
{
    "AssociationDescription": {
        "Name": "string",
        "AssociationVersion": "string",
        "AssociationId": "string",
        "Targets": [],
        "ScheduleExpression": "string",
        "Parameters": {},
        "MaxErrors": "string",
        "MaxConcurrency": "string"
    }
}
```

---

### 7.6 `describe-association-executions`

Lists the executions of a State Manager association. **Paginated operation.**

**Synopsis:**
```bash
aws ssm describe-association-executions \
    --association-id <value> \
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
| `--association-id` | **Yes** | string | -- | Association ID |
| `--filters` | No | list | None | Filters: `ExecutionId`, `Status`, `CreatedTime` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "AssociationExecutions": [
        {
            "AssociationId": "string",
            "AssociationVersion": "string",
            "ExecutionId": "string",
            "Status": "string",
            "DetailedStatus": "string",
            "CreatedTime": "timestamp",
            "LastExecutionDate": "timestamp",
            "ResourceCountByStatus": "string",
            "AlarmConfiguration": {},
            "TriggeredAlarms": []
        }
    ],
    "NextToken": "string"
}
```

---

### 7.7 `describe-association-execution-targets`

Lists the targets for a specific association execution. **Paginated operation.**

**Synopsis:**
```bash
aws ssm describe-association-execution-targets \
    --association-id <value> \
    --execution-id <value> \
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
| `--association-id` | **Yes** | string | -- | Association ID |
| `--execution-id` | **Yes** | string | -- | Execution ID |
| `--filters` | No | list | None | Filters: `Status`, `ResourceId`, `ResourceType` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "AssociationExecutionTargets": [
        {
            "AssociationId": "string",
            "AssociationVersion": "string",
            "ExecutionId": "string",
            "ResourceId": "string",
            "ResourceType": "string",
            "Status": "string",
            "DetailedStatus": "string",
            "LastExecutionDate": "timestamp",
            "OutputSource": {
                "OutputSourceId": "string",
                "OutputSourceType": "string"
            }
        }
    ],
    "NextToken": "string"
}
```
