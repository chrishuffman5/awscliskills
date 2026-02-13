# Report Plans

### 9.1 `create-report-plan`

Creates a report plan for generating backup compliance and job reports.

**Synopsis:**
```bash
aws backup create-report-plan \
    --report-plan-name <value> \
    --report-delivery-channel <value> \
    --report-setting <value> \
    [--report-plan-description <value>] \
    [--report-plan-tags <value>] \
    [--idempotency-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--report-plan-name` | **Yes** | string | -- | Plan name (1-256 chars, `[a-zA-Z][_a-zA-Z0-9]*`) |
| `--report-delivery-channel` | **Yes** | structure | -- | S3 delivery config |
| `--report-setting` | **Yes** | structure | -- | Report template and scope |
| `--report-plan-description` | No | string | None | Description (max 1024 chars) |
| `--report-plan-tags` | No | map | None | Tags |
| `--idempotency-token` | No | string | None | Idempotency token |

**Report Delivery Channel:**
```json
{
    "S3BucketName": "string",
    "S3KeyPrefix": "string",
    "Formats": ["CSV", "JSON"]
}
```

**Report Setting:**
```json
{
    "ReportTemplate": "RESOURCE_COMPLIANCE_REPORT|CONTROL_COMPLIANCE_REPORT|BACKUP_JOB_REPORT|COPY_JOB_REPORT|RESTORE_JOB_REPORT|SCAN_JOB_REPORT",
    "FrameworkArns": ["string"],
    "Accounts": ["string"],
    "OrganizationUnits": ["string"],
    "Regions": ["string"]
}
```

**Output Schema:**
```json
{
    "ReportPlanName": "string",
    "ReportPlanArn": "string",
    "CreationTime": "timestamp"
}
```

---

### 9.2 `describe-report-plan`

Returns details of a report plan.

**Synopsis:**
```bash
aws backup describe-report-plan \
    --report-plan-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--report-plan-name` | **Yes** | string | -- | Report plan name |

**Output Schema:**
```json
{
    "ReportPlan": {
        "ReportPlanArn": "string",
        "ReportPlanName": "string",
        "ReportPlanDescription": "string",
        "ReportSetting": {},
        "ReportDeliveryChannel": {},
        "DeploymentStatus": "CREATE_IN_PROGRESS|UPDATE_IN_PROGRESS|DELETE_IN_PROGRESS|COMPLETED",
        "CreationTime": "timestamp",
        "LastAttemptedExecutionTime": "timestamp",
        "LastSuccessfulExecutionTime": "timestamp"
    }
}
```

---

### 9.3 `list-report-plans`

Lists report plans. **Paginated operation.**

**Synopsis:**
```bash
aws backup list-report-plans \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Output Schema:**
```json
{
    "ReportPlans": [
        {
            "ReportPlanArn": "string",
            "ReportPlanName": "string",
            "ReportPlanDescription": "string",
            "ReportSetting": {},
            "ReportDeliveryChannel": {},
            "DeploymentStatus": "string",
            "CreationTime": "timestamp",
            "LastAttemptedExecutionTime": "timestamp",
            "LastSuccessfulExecutionTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 9.4 `start-report-job`

Starts generating a report.

**Synopsis:**
```bash
aws backup start-report-job \
    --report-plan-name <value> \
    [--idempotency-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--report-plan-name` | **Yes** | string | -- | Report plan name |
| `--idempotency-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "ReportJobId": "string"
}
```

---

### 9.5 `list-report-jobs`

Lists report jobs. **Paginated operation.**

**Synopsis:**
```bash
aws backup list-report-jobs \
    [--by-report-plan-name <value>] \
    [--by-creation-before <value>] \
    [--by-creation-after <value>] \
    [--by-status <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Output Schema:**
```json
{
    "ReportJobs": [
        {
            "ReportJobId": "string",
            "ReportPlanArn": "string",
            "ReportTemplate": "string",
            "CreationTime": "timestamp",
            "CompletionTime": "timestamp",
            "Status": "COMPLETED|RUNNING|FAILED",
            "StatusMessage": "string",
            "ReportDestination": {
                "S3BucketName": "string",
                "S3Keys": ["string"]
            }
        }
    ],
    "NextToken": "string"
}
```
