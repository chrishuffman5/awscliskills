# Labeling

## 1. `create-labeling-job`

Creates a data labeling job with human workers.

**Synopsis:**
```bash
aws sagemaker create-labeling-job \
    --labeling-job-name <value> \
    --label-attribute-name <value> \
    --input-config <value> \
    --output-config <value> \
    --role-arn <value> \
    --human-task-config <value> \
    [--label-category-config-s3-uri <value>] \
    [--stopping-conditions <value>] \
    [--labeling-job-algorithms-config <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--labeling-job-name` | **Yes** | string | -- | Unique name (1-63 chars) |
| `--label-attribute-name` | **Yes** | string | -- | Attribute name for labels in output |
| `--input-config` | **Yes** | structure | -- | Input data source (S3 manifest or SNS) |
| `--output-config` | **Yes** | structure | -- | S3 output path |
| `--role-arn` | **Yes** | string | -- | IAM role ARN |
| `--human-task-config` | **Yes** | structure | -- | Worker config, task UI, number of workers |
| `--label-category-config-s3-uri` | No | string | -- | S3 URI for label categories |
| `--stopping-conditions` | No | structure | -- | `MaxHumanLabeledObjectCount`, `MaxPercentageOfInputDatasetLabeled` |
| `--labeling-job-algorithms-config` | No | structure | -- | Auto-labeling algorithm config |
| `--tags` | No | list | -- | Key-value tags |

**Human Task Config:**
```json
{
    "WorkteamArn": "string",
    "UiConfig": {"UiTemplateS3Uri": "string", "HumanTaskUiArn": "string"},
    "PreHumanTaskLambdaArn": "string",
    "TaskKeywords": ["string"],
    "TaskTitle": "string",
    "TaskDescription": "string",
    "NumberOfHumanWorkersPerDataObject": "integer (1-9)",
    "TaskTimeLimitInSeconds": "integer",
    "TaskAvailabilityLifetimeInSeconds": "integer",
    "MaxConcurrentTaskCount": "integer",
    "AnnotationConsolidationConfig": {"AnnotationConsolidationLambdaArn": "string"},
    "PublicWorkforceTaskPrice": {"AmountInUsd": {"Dollars": "integer", "Cents": "integer", "TenthFractionsOfACent": "integer"}}
}
```

**Output Schema:**
```json
{
    "LabelingJobArn": "string"
}
```

---

## 2. `describe-labeling-job`

Returns details about a labeling job.

```bash
aws sagemaker describe-labeling-job --labeling-job-name <value>
```

**Output Schema:**
```json
{
    "LabelingJobStatus": "Initializing|InProgress|Completed|Failed|Stopping|Stopped",
    "LabelCounters": {
        "TotalLabeled": "integer",
        "HumanLabeled": "integer",
        "MachineLabeled": "integer",
        "FailedNonRetryableError": "integer",
        "Unlabeled": "integer"
    },
    "FailureReason": "string",
    "CreationTime": "timestamp",
    "LastModifiedTime": "timestamp",
    "JobReferenceCode": "string",
    "LabelingJobName": "string",
    "LabelingJobArn": "string",
    "LabelAttributeName": "string",
    "InputConfig": {...},
    "OutputConfig": {...},
    "RoleArn": "string",
    "LabelCategoryConfigS3Uri": "string",
    "StoppingConditions": {...},
    "LabelingJobAlgorithmsConfig": {...},
    "HumanTaskConfig": {...},
    "Tags": [...],
    "LabelingJobOutput": {
        "OutputDatasetS3Uri": "string",
        "FinalActiveLearningModelArn": "string"
    }
}
```

---

## 3. `list-labeling-jobs`

Lists labeling jobs. **Paginated operation.**

```bash
aws sagemaker list-labeling-jobs \
    [--creation-time-after <value>] \
    [--creation-time-before <value>] \
    [--last-modified-time-after <value>] \
    [--last-modified-time-before <value>] \
    [--name-contains <value>] \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--status-equals <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

---

## 4. `stop-labeling-job`

Stops a running labeling job.

```bash
aws sagemaker stop-labeling-job --labeling-job-name <value>
```

**Output:** None

---

## 5. `list-labeling-jobs-for-workteam`

Lists labeling jobs assigned to a specific workteam. **Paginated operation.**

```bash
aws sagemaker list-labeling-jobs-for-workteam \
    --workteam-arn <value> \
    [--creation-time-after <value>] \
    [--creation-time-before <value>] \
    [--job-reference-code-contains <value>] \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

---

## Human Review (Augmented AI)

### 6. `create-flow-definition`

Creates a human review workflow definition.

```bash
aws sagemaker create-flow-definition \
    --flow-definition-name <value> \
    --human-loop-config <value> \
    --output-config <value> \
    --role-arn <value> \
    [--human-loop-request-source <value>] \
    [--human-loop-activation-config <value>] \
    [--tags <value>]
```

**Output Schema:**
```json
{
    "FlowDefinitionArn": "string"
}
```

---

### 7. `describe-flow-definition` / `list-flow-definitions` / `delete-flow-definition`

```bash
aws sagemaker describe-flow-definition --flow-definition-name <value>
aws sagemaker list-flow-definitions [--creation-time-after <value>] [--creation-time-before <value>] [--sort-order <value>]
aws sagemaker delete-flow-definition --flow-definition-name <value>
```

---

### 8. `create-human-task-ui`

Creates a worker task UI template.

```bash
aws sagemaker create-human-task-ui \
    --human-task-ui-name <value> \
    --ui-template <value> \
    [--tags <value>]
```

**Output Schema:**
```json
{
    "HumanTaskUiArn": "string"
}
```

---

### 9. `describe-human-task-ui` / `list-human-task-uis` / `delete-human-task-ui`

```bash
aws sagemaker describe-human-task-ui --human-task-ui-name <value>
aws sagemaker list-human-task-uis [--creation-time-after <value>] [--creation-time-before <value>] [--sort-order <value>]
aws sagemaker delete-human-task-ui --human-task-ui-name <value>
```

---

### 10. `render-ui-template`

Renders a worker task UI template with sample data.

```bash
aws sagemaker render-ui-template \
    --task <value> \
    --role-arn <value> \
    [--ui-template <value>] \
    [--human-task-ui-arn <value>]
```

**Output Schema:**
```json
{
    "RenderedContent": "string",
    "Errors": [{"Code": "string", "Message": "string"}]
}
```
