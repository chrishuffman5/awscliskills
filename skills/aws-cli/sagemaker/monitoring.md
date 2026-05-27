# Monitoring

## Monitoring Schedules

### 1. `create-monitoring-schedule`

Creates a monitoring schedule for an endpoint.

**Synopsis:**
```bash
aws sagemaker create-monitoring-schedule \
    --monitoring-schedule-name <value> \
    --monitoring-schedule-config <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--monitoring-schedule-name` | **Yes** | string | -- | Unique name (1-63 chars) |
| `--monitoring-schedule-config` | **Yes** | structure | -- | Schedule frequency, job definition, and monitoring type |
| `--tags` | No | list | -- | Key-value tags |

**Monitoring Schedule Config:**
```json
{
    "ScheduleConfig": {
        "ScheduleExpression": "cron(0 * ? * * *)",
        "DataAnalysisStartTime": "string",
        "DataAnalysisEndTime": "string"
    },
    "MonitoringJobDefinition": {
        "BaselineConfig": {...},
        "MonitoringInputs": [...],
        "MonitoringOutputConfig": {...},
        "MonitoringResources": {"ClusterConfig": {"InstanceCount": 1, "InstanceType": "ml.m5.xlarge", "VolumeSizeInGB": 30}},
        "MonitoringAppSpecification": {"ImageUri": "string", "ContainerEntrypoint": [...], "ContainerArguments": [...]},
        "StoppingCondition": {"MaxRuntimeInSeconds": "integer"},
        "Environment": {"string": "string"},
        "NetworkConfig": {...},
        "RoleArn": "string"
    },
    "MonitoringJobDefinitionName": "string",
    "MonitoringType": "DataQuality|ModelQuality|ModelBias|ModelExplainability"
}
```

**Output Schema:**
```json
{
    "MonitoringScheduleArn": "string"
}
```

---

### 2. `describe-monitoring-schedule`

Returns details about a monitoring schedule.

```bash
aws sagemaker describe-monitoring-schedule \
    --monitoring-schedule-name <value>
```

**Output Schema:**
```json
{
    "MonitoringScheduleArn": "string",
    "MonitoringScheduleName": "string",
    "MonitoringScheduleStatus": "Pending|Failed|Scheduled|Stopped",
    "MonitoringType": "DataQuality|ModelQuality|ModelBias|ModelExplainability",
    "FailureReason": "string",
    "CreationTime": "timestamp",
    "LastModifiedTime": "timestamp",
    "MonitoringScheduleConfig": {...},
    "EndpointName": "string",
    "LastMonitoringExecutionSummary": {
        "MonitoringScheduleName": "string",
        "ScheduledTime": "timestamp",
        "CreationTime": "timestamp",
        "LastModifiedTime": "timestamp",
        "MonitoringExecutionStatus": "Pending|Completed|CompletedWithViolations|InProgress|Failed|Stopping|Stopped",
        "ProcessingJobArn": "string",
        "EndpointName": "string",
        "FailureReason": "string",
        "MonitoringJobDefinitionName": "string",
        "MonitoringType": "string"
    }
}
```

---

### 3. `list-monitoring-schedules`

Lists monitoring schedules. **Paginated operation.**

```bash
aws sagemaker list-monitoring-schedules \
    [--endpoint-name <value>] \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--name-contains <value>] \
    [--creation-time-before <value>] \
    [--creation-time-after <value>] \
    [--last-modified-time-before <value>] \
    [--last-modified-time-after <value>] \
    [--status-equals <value>] \
    [--monitoring-job-definition-name <value>] \
    [--monitoring-type-equals <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

---

### 4. `update-monitoring-schedule`

Updates a monitoring schedule.

```bash
aws sagemaker update-monitoring-schedule \
    --monitoring-schedule-name <value> \
    --monitoring-schedule-config <value>
```

**Output Schema:**
```json
{
    "MonitoringScheduleArn": "string"
}
```

---

### 5. `delete-monitoring-schedule` / `start-monitoring-schedule` / `stop-monitoring-schedule`

```bash
aws sagemaker delete-monitoring-schedule --monitoring-schedule-name <value>
aws sagemaker start-monitoring-schedule --monitoring-schedule-name <value>
aws sagemaker stop-monitoring-schedule --monitoring-schedule-name <value>
```

**Output:** None

---

### 6. `list-monitoring-executions`

Lists monitoring executions. **Paginated operation.**

```bash
aws sagemaker list-monitoring-executions \
    --monitoring-schedule-name <value> \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--scheduled-time-before <value>] \
    [--scheduled-time-after <value>] \
    [--creation-time-before <value>] \
    [--creation-time-after <value>] \
    [--last-modified-time-before <value>] \
    [--last-modified-time-after <value>] \
    [--status-equals <value>] \
    [--monitoring-job-definition-name <value>] \
    [--monitoring-type-equals <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

---

## Data Quality Job Definitions

### 7. `create-data-quality-job-definition`

Creates a definition for a data quality monitoring job.

**Synopsis:**
```bash
aws sagemaker create-data-quality-job-definition \
    --job-definition-name <value> \
    --data-quality-app-specification <value> \
    --data-quality-job-input <value> \
    --data-quality-job-output-config <value> \
    --job-resources <value> \
    --role-arn <value> \
    [--data-quality-baseline-config <value>] \
    [--network-config <value>] \
    [--stopping-condition <value>] \
    [--tags <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-definition-name` | **Yes** | string | -- | Unique name (1-63 chars) |
| `--data-quality-app-specification` | **Yes** | structure | -- | `ImageUri`, `ContainerEntrypoint`, `ContainerArguments`, `Environment`, `PostAnalyticsProcessorSourceUri`, `RecordPreprocessorSourceUri` |
| `--data-quality-job-input` | **Yes** | structure | -- | Endpoint input or batch transform input |
| `--data-quality-job-output-config` | **Yes** | structure | -- | S3 output config |
| `--job-resources` | **Yes** | structure | -- | Cluster config |
| `--role-arn` | **Yes** | string | -- | IAM role ARN |
| `--data-quality-baseline-config` | No | structure | -- | Baseline constraints and statistics URIs |
| `--network-config` | No | structure | -- | VPC config |
| `--stopping-condition` | No | structure | -- | `MaxRuntimeInSeconds` |
| `--tags` | No | list | -- | Key-value tags |

**Output Schema:**
```json
{
    "JobDefinitionArn": "string"
}
```

---

### 8. `describe-data-quality-job-definition` / `list-data-quality-job-definitions` / `delete-data-quality-job-definition`

```bash
aws sagemaker describe-data-quality-job-definition --job-definition-name <value>
aws sagemaker list-data-quality-job-definitions [--sort-by <value>] [--sort-order <value>] [--name-contains <value>] [--creation-time-before <value>] [--creation-time-after <value>] [--endpoint-name <value>]
aws sagemaker delete-data-quality-job-definition --job-definition-name <value>
```

---

## Model Quality Job Definitions

### 9. `create-model-quality-job-definition`

Creates a definition for a model quality monitoring job.

**Synopsis:**
```bash
aws sagemaker create-model-quality-job-definition \
    --job-definition-name <value> \
    --model-quality-app-specification <value> \
    --model-quality-job-input <value> \
    --model-quality-job-output-config <value> \
    --job-resources <value> \
    --role-arn <value> \
    [--model-quality-baseline-config <value>] \
    [--network-config <value>] \
    [--stopping-condition <value>] \
    [--tags <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-definition-name` | **Yes** | string | -- | Unique name |
| `--model-quality-app-specification` | **Yes** | structure | -- | `ImageUri`, `ProblemType` (`BinaryClassification`/`MulticlassClassification`/`Regression`) |
| `--model-quality-job-input` | **Yes** | structure | -- | Ground truth and endpoint input |
| `--model-quality-job-output-config` | **Yes** | structure | -- | S3 output |
| `--job-resources` | **Yes** | structure | -- | Cluster config |
| `--role-arn` | **Yes** | string | -- | IAM role ARN |

**Output Schema:**
```json
{
    "JobDefinitionArn": "string"
}
```

---

### 10. `describe-model-quality-job-definition` / `list-model-quality-job-definitions` / `delete-model-quality-job-definition`

Same pattern as data quality job definitions.

---

## Model Bias Job Definitions

### 11. `create-model-bias-job-definition`

Creates a definition for a model bias monitoring job.

```bash
aws sagemaker create-model-bias-job-definition \
    --job-definition-name <value> \
    --model-bias-app-specification <value> \
    --model-bias-job-input <value> \
    --model-bias-job-output-config <value> \
    --job-resources <value> \
    --role-arn <value> \
    [--model-bias-baseline-config <value>] \
    [--network-config <value>] \
    [--stopping-condition <value>] \
    [--tags <value>]
```

Same structure as model quality with `--model-bias-app-specification` containing `ImageUri` and `ConfigUri`.

---

### 12. `describe-model-bias-job-definition` / `list-model-bias-job-definitions` / `delete-model-bias-job-definition`

Same pattern as other monitoring job definitions.

---

## Model Explainability Job Definitions

### 13. `create-model-explainability-job-definition`

Creates a definition for a model explainability monitoring job.

```bash
aws sagemaker create-model-explainability-job-definition \
    --job-definition-name <value> \
    --model-explainability-app-specification <value> \
    --model-explainability-job-input <value> \
    --model-explainability-job-output-config <value> \
    --job-resources <value> \
    --role-arn <value> \
    [--model-explainability-baseline-config <value>] \
    [--network-config <value>] \
    [--stopping-condition <value>] \
    [--tags <value>]
```

Same structure as model bias with `--model-explainability-app-specification` containing `ImageUri` and `ConfigUri`.

---

### 14. `describe-model-explainability-job-definition` / `list-model-explainability-job-definitions` / `delete-model-explainability-job-definition`

Same pattern as other monitoring job definitions.

---

## Monitoring Alerts

### 15. `list-monitoring-alerts`

Lists monitoring alerts for a schedule.

```bash
aws sagemaker list-monitoring-alerts \
    --monitoring-schedule-name <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

---

### 16. `list-monitoring-alert-history`

Lists alert history.

```bash
aws sagemaker list-monitoring-alert-history \
    [--monitoring-schedule-name <value>] \
    [--monitoring-alert-name <value>] \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--creation-time-before <value>] \
    [--creation-time-after <value>] \
    [--status-equals <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

---

### 17. `update-monitoring-alert`

Updates a monitoring alert.

```bash
aws sagemaker update-monitoring-alert \
    --monitoring-schedule-name <value> \
    --monitoring-alert-name <value> \
    --data-points-to-alert <value> \
    --evaluation-period <value>
```

**Output Schema:**
```json
{
    "MonitoringScheduleArn": "string",
    "MonitoringAlertName": "string"
}
```
