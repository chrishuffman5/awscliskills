# Hyperparameter Tuning

## 1. `create-hyper-parameter-tuning-job`

Creates a hyperparameter tuning job that uses a search strategy to find optimal hyperparameters.

**Synopsis:**
```bash
aws sagemaker create-hyper-parameter-tuning-job \
    --hyper-parameter-tuning-job-name <value> \
    --hyper-parameter-tuning-job-config <value> \
    [--training-job-definition <value>] \
    [--training-job-definitions <value>] \
    [--warm-start-config <value>] \
    [--autotune <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--hyper-parameter-tuning-job-name` | **Yes** | string | -- | Unique name (1-32 chars) |
| `--hyper-parameter-tuning-job-config` | **Yes** | structure | -- | Tuning strategy, objective, and resource limits |
| `--training-job-definition` | No | structure | -- | Single training job definition |
| `--training-job-definitions` | No | list | -- | Multiple training job definitions |
| `--warm-start-config` | No | structure | -- | Warm start from previous tuning jobs |
| `--autotune` | No | structure | -- | `Mode`: `Enabled` or `Disabled` |
| `--tags` | No | list | -- | Key-value tags |

**Tuning Job Config:**
```json
{
    "Strategy": "Bayesian|Random|Hyperband|Grid",
    "HyperParameterTuningJobObjective": {
        "Type": "Maximize|Minimize",
        "MetricName": "string"
    },
    "ResourceLimits": {
        "MaxNumberOfTrainingJobs": "integer",
        "MaxParallelTrainingJobs": "integer",
        "MaxRuntimeInSeconds": "integer"
    },
    "ParameterRanges": {
        "IntegerParameterRanges": [
            {"Name": "string", "MinValue": "string", "MaxValue": "string", "ScalingType": "Auto|Linear|Logarithmic|ReverseLogarithmic"}
        ],
        "ContinuousParameterRanges": [
            {"Name": "string", "MinValue": "string", "MaxValue": "string", "ScalingType": "Auto|Linear|Logarithmic|ReverseLogarithmic"}
        ],
        "CategoricalParameterRanges": [
            {"Name": "string", "Values": ["string"]}
        ],
        "AutoParameters": [
            {"Name": "string", "ValueHint": "string"}
        ]
    },
    "TrainingJobEarlyStoppingType": "Off|Auto",
    "TuningJobCompletionCriteria": {
        "TargetObjectiveMetricValue": "float",
        "BestObjectiveNotImproving": {"MaxNumberOfTrainingJobsNotImproving": "integer"},
        "ConvergenceDetected": {"CompleteOnConvergence": "Disabled|Enabled"}
    },
    "RandomSeed": "integer"
}
```

**Warm Start Config:**
```json
{
    "ParentHyperParameterTuningJobs": [
        {"HyperParameterTuningJobName": "string"}
    ],
    "WarmStartType": "IdenticalDataAndAlgorithm|TransferLearning"
}
```

**Output Schema:**
```json
{
    "HyperParameterTuningJobArn": "string"
}
```

---

## 2. `describe-hyper-parameter-tuning-job`

Returns details about a hyperparameter tuning job.

**Synopsis:**
```bash
aws sagemaker describe-hyper-parameter-tuning-job \
    --hyper-parameter-tuning-job-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--hyper-parameter-tuning-job-name` | **Yes** | string | -- | Name of the tuning job |

**Output Schema:**
```json
{
    "HyperParameterTuningJobName": "string",
    "HyperParameterTuningJobArn": "string",
    "HyperParameterTuningJobConfig": {...},
    "TrainingJobDefinition": {...},
    "TrainingJobDefinitions": [...],
    "HyperParameterTuningJobStatus": "Completed|InProgress|Failed|Stopped|Stopping|Deleting|DeleteFailed",
    "CreationTime": "timestamp",
    "HyperParameterTuningEndTime": "timestamp",
    "LastModifiedTime": "timestamp",
    "TrainingJobStatusCounters": {
        "Completed": "integer",
        "InProgress": "integer",
        "RetryableError": "integer",
        "NonRetryableError": "integer",
        "Stopped": "integer"
    },
    "ObjectiveStatusCounters": {
        "Succeeded": "integer",
        "Pending": "integer",
        "Failed": "integer"
    },
    "BestTrainingJob": {
        "TrainingJobDefinitionName": "string",
        "TrainingJobName": "string",
        "TrainingJobArn": "string",
        "TuningJobName": "string",
        "CreationTime": "timestamp",
        "TrainingStartTime": "timestamp",
        "TrainingEndTime": "timestamp",
        "TrainingJobStatus": "string",
        "TunedHyperParameters": {"string": "string"},
        "FailureReason": "string",
        "FinalHyperParameterTuningJobObjectiveMetric": {
            "Type": "Maximize|Minimize",
            "MetricName": "string",
            "Value": "float"
        },
        "ObjectiveStatus": "Succeeded|Pending|Failed"
    },
    "OverallBestTrainingJob": {...},
    "WarmStartConfig": {...},
    "Autotune": {"Mode": "Enabled|Disabled"},
    "FailureReason": "string",
    "TuningJobCompletionDetails": {
        "NumberOfTrainingJobsObjectiveNotImproving": "integer",
        "ConvergenceDetectedTime": "timestamp"
    },
    "ConsumedResources": {"RuntimeInSeconds": "integer"}
}
```

---

## 3. `list-hyper-parameter-tuning-jobs`

Lists hyperparameter tuning jobs. **Paginated operation.**

**Synopsis:**
```bash
aws sagemaker list-hyper-parameter-tuning-jobs \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--name-contains <value>] \
    [--creation-time-after <value>] \
    [--creation-time-before <value>] \
    [--last-modified-time-after <value>] \
    [--last-modified-time-before <value>] \
    [--status-equals <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--sort-by` | No | string | `Name` | `Name`, `Status`, `CreationTime` |
| `--sort-order` | No | string | `Ascending` | `Ascending`, `Descending` |
| `--name-contains` | No | string | -- | Filter by name substring |
| `--status-equals` | No | string | -- | `Completed`, `InProgress`, `Failed`, `Stopped`, `Stopping` |

**Output Schema:**
```json
{
    "HyperParameterTuningJobSummaries": [
        {
            "HyperParameterTuningJobName": "string",
            "HyperParameterTuningJobArn": "string",
            "HyperParameterTuningJobStatus": "string",
            "Strategy": "Bayesian|Random|Hyperband|Grid",
            "CreationTime": "timestamp",
            "HyperParameterTuningEndTime": "timestamp",
            "LastModifiedTime": "timestamp",
            "TrainingJobStatusCounters": {...},
            "ObjectiveStatusCounters": {...},
            "ResourceLimits": {"MaxNumberOfTrainingJobs": "integer", "MaxParallelTrainingJobs": "integer"}
        }
    ],
    "NextToken": "string"
}
```

---

## 4. `stop-hyper-parameter-tuning-job`

Stops a running hyperparameter tuning job and all running training jobs launched by that job.

**Synopsis:**
```bash
aws sagemaker stop-hyper-parameter-tuning-job \
    --hyper-parameter-tuning-job-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--hyper-parameter-tuning-job-name` | **Yes** | string | -- | Name of the tuning job to stop |

**Output:** None

---

## 5. `delete-hyper-parameter-tuning-job`

Deletes a hyperparameter tuning job.

**Synopsis:**
```bash
aws sagemaker delete-hyper-parameter-tuning-job \
    --hyper-parameter-tuning-job-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--hyper-parameter-tuning-job-name` | **Yes** | string | -- | Name of the tuning job to delete |

**Output:** None

---

## 6. `list-training-jobs-for-hyper-parameter-tuning-job`

Lists training jobs launched by a hyperparameter tuning job. **Paginated operation.**

**Synopsis:**
```bash
aws sagemaker list-training-jobs-for-hyper-parameter-tuning-job \
    --hyper-parameter-tuning-job-name <value> \
    [--status-equals <value>] \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--hyper-parameter-tuning-job-name` | **Yes** | string | -- | Tuning job name |
| `--status-equals` | No | string | -- | `InProgress`, `Completed`, `Failed`, `Stopping`, `Stopped` |
| `--sort-by` | No | string | `Name` | `Name`, `CreationTime`, `Status`, `FinalObjectiveMetricValue` |
| `--sort-order` | No | string | `Ascending` | `Ascending`, `Descending` |

**Output Schema:**
```json
{
    "TrainingJobSummaries": [
        {
            "TrainingJobDefinitionName": "string",
            "TrainingJobName": "string",
            "TrainingJobArn": "string",
            "TuningJobName": "string",
            "CreationTime": "timestamp",
            "TrainingStartTime": "timestamp",
            "TrainingEndTime": "timestamp",
            "TrainingJobStatus": "InProgress|Completed|Failed|Stopping|Stopped",
            "TunedHyperParameters": {"string": "string"},
            "FailureReason": "string",
            "FinalHyperParameterTuningJobObjectiveMetric": {
                "Type": "Maximize|Minimize",
                "MetricName": "string",
                "Value": "float"
            },
            "ObjectiveStatus": "Succeeded|Pending|Failed"
        }
    ],
    "NextToken": "string"
}
```
