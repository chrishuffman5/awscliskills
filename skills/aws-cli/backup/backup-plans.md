# Backup Plans

### 1.1 `create-backup-plan`

Creates a backup plan with a name, rules (schedule, lifecycle, target vault), and optional advanced settings.

**Synopsis:**
```bash
aws backup create-backup-plan \
    --backup-plan <value> \
    [--backup-plan-tags <value>] \
    [--creator-request-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--backup-plan` | **Yes** | structure | -- | Backup plan body with name, rules, and settings |
| `--backup-plan-tags` | No | map | None | Tags for the backup plan |
| `--creator-request-id` | No | string | None | Idempotency token (1-50 chars) |

**Backup Plan Structure:**
```json
{
    "BackupPlanName": "string",
    "Rules": [
        {
            "RuleName": "string",
            "TargetBackupVaultName": "string",
            "ScheduleExpression": "cron(0 5 ? * * *)",
            "ScheduleExpressionTimezone": "string",
            "StartWindowMinutes": "long",
            "CompletionWindowMinutes": "long",
            "Lifecycle": {
                "MoveToColdStorageAfterDays": "long",
                "DeleteAfterDays": "long",
                "OptInToArchiveForSupportedResources": "boolean"
            },
            "RecoveryPointTags": {"string": "string"},
            "CopyActions": [
                {
                    "DestinationBackupVaultArn": "string",
                    "Lifecycle": {}
                }
            ],
            "EnableContinuousBackup": "boolean"
        }
    ],
    "AdvancedBackupSettings": [
        {
            "ResourceType": "EC2",
            "BackupOptions": {"WindowsVSS": "enabled|disabled"}
        }
    ]
}
```

**Output Schema:**
```json
{
    "BackupPlanId": "string",
    "BackupPlanArn": "string",
    "CreationDate": "timestamp",
    "VersionId": "string",
    "AdvancedBackupSettings": []
}
```

---

### 1.2 `update-backup-plan`

Updates an existing backup plan. Creates a new version.

**Synopsis:**
```bash
aws backup update-backup-plan \
    --backup-plan-id <value> \
    --backup-plan <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--backup-plan-id` | **Yes** | string | -- | Backup plan ID |
| `--backup-plan` | **Yes** | structure | -- | Updated backup plan body |

**Output Schema:**
```json
{
    "BackupPlanId": "string",
    "BackupPlanArn": "string",
    "CreationDate": "timestamp",
    "VersionId": "string",
    "AdvancedBackupSettings": []
}
```

---

### 1.3 `delete-backup-plan`

Deletes a backup plan. Only deletes the plan; existing recovery points are not affected.

**Synopsis:**
```bash
aws backup delete-backup-plan \
    --backup-plan-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--backup-plan-id` | **Yes** | string | -- | Backup plan ID |

**Output Schema:**
```json
{
    "BackupPlanId": "string",
    "BackupPlanArn": "string",
    "DeletionDate": "timestamp",
    "VersionId": "string"
}
```

---

### 1.4 `get-backup-plan`

Returns the body of a backup plan for the specified plan ID.

**Synopsis:**
```bash
aws backup get-backup-plan \
    --backup-plan-id <value> \
    [--version-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--backup-plan-id` | **Yes** | string | -- | Backup plan ID |
| `--version-id` | No | string | None | Specific version ID |

**Output Schema:**
```json
{
    "BackupPlan": {
        "BackupPlanName": "string",
        "Rules": [],
        "AdvancedBackupSettings": []
    },
    "BackupPlanId": "string",
    "BackupPlanArn": "string",
    "VersionId": "string",
    "CreatorRequestId": "string",
    "CreationDate": "timestamp",
    "DeletionDate": "timestamp",
    "LastExecutionDate": "timestamp"
}
```

---

### 1.5 `list-backup-plans`

Lists all active backup plans. **Paginated operation.**

**Synopsis:**
```bash
aws backup list-backup-plans \
    [--include-deleted | --no-include-deleted] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--include-deleted` | No | boolean | false | Include deleted plans |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "NextToken": "string",
    "BackupPlansList": [
        {
            "BackupPlanArn": "string",
            "BackupPlanId": "string",
            "CreationDate": "timestamp",
            "DeletionDate": "timestamp",
            "VersionId": "string",
            "BackupPlanName": "string",
            "CreatorRequestId": "string",
            "LastExecutionDate": "timestamp",
            "AdvancedBackupSettings": []
        }
    ]
}
```

---

### 1.6 `create-backup-selection`

Creates a resource assignment to a backup plan. Specifies which resources are backed up by the plan.

**Synopsis:**
```bash
aws backup create-backup-selection \
    --backup-plan-id <value> \
    --backup-selection <value> \
    [--creator-request-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--backup-plan-id` | **Yes** | string | -- | Backup plan ID |
| `--backup-selection` | **Yes** | structure | -- | Resource selection body |
| `--creator-request-id` | No | string | None | Idempotency token |

**Backup Selection Structure:**
```json
{
    "SelectionName": "string",
    "IamRoleArn": "string",
    "Resources": ["arn:aws:..."],
    "ListOfTags": [
        {
            "ConditionType": "STRINGEQUALS",
            "ConditionKey": "string",
            "ConditionValue": "string"
        }
    ],
    "NotResources": ["arn:aws:..."],
    "Conditions": {
        "StringEquals": [{"ConditionKey": "string", "ConditionValue": "string"}],
        "StringNotEquals": [],
        "StringLike": [],
        "StringNotLike": []
    }
}
```

**Output Schema:**
```json
{
    "SelectionId": "string",
    "BackupPlanId": "string",
    "CreationDate": "timestamp"
}
```

---

### 1.7 `get-backup-selection`

Returns details of a backup selection.

**Synopsis:**
```bash
aws backup get-backup-selection \
    --backup-plan-id <value> \
    --selection-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--backup-plan-id` | **Yes** | string | -- | Backup plan ID |
| `--selection-id` | **Yes** | string | -- | Selection ID |

**Output Schema:**
```json
{
    "BackupSelection": {
        "SelectionName": "string",
        "IamRoleArn": "string",
        "Resources": ["string"],
        "ListOfTags": [],
        "NotResources": ["string"],
        "Conditions": {}
    },
    "SelectionId": "string",
    "BackupPlanId": "string",
    "CreationDate": "timestamp",
    "CreatorRequestId": "string"
}
```

---

### 1.8 `list-backup-selections`

Lists selections for a backup plan. **Paginated operation.**

**Synopsis:**
```bash
aws backup list-backup-selections \
    --backup-plan-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--backup-plan-id` | **Yes** | string | -- | Backup plan ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "NextToken": "string",
    "BackupSelectionsList": [
        {
            "SelectionId": "string",
            "SelectionName": "string",
            "BackupPlanId": "string",
            "CreationDate": "timestamp",
            "CreatorRequestId": "string",
            "IamRoleArn": "string"
        }
    ]
}
```
