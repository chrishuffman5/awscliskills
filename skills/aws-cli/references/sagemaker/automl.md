# AutoML

## 1. `create-auto-ml-job`

Creates an AutoML job that automatically trains and tunes the best machine learning model for classification or regression.

**Synopsis:**
```bash
aws sagemaker create-auto-ml-job \
    --auto-ml-job-name <value> \
    --input-data-config <value> \
    --output-data-config <value> \
    --role-arn <value> \
    [--auto-ml-job-config <value>] \
    [--auto-ml-job-objective <value>] \
    [--problem-type <value>] \
    [--generate-candidate-definitions-only | --no-generate-candidate-definitions-only] \
    [--tags <value>] \
    [--model-deploy-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-ml-job-name` | **Yes** | string | -- | Unique name (1-32 chars) |
| `--input-data-config` | **Yes** | list | -- | Input data channels (1-20) |
| `--output-data-config` | **Yes** | structure | -- | S3 output path |
| `--role-arn` | **Yes** | string | -- | IAM role ARN |
| `--auto-ml-job-config` | No | structure | -- | Completion criteria, security, candidate generation |
| `--auto-ml-job-objective` | No | structure | -- | `MetricName` (e.g., `Accuracy`, `MSE`, `F1`, `AUC`) |
| `--problem-type` | No | string | -- | `BinaryClassification`, `MulticlassClassification`, `Regression` |
| `--generate-candidate-definitions-only` | No | boolean | false | Only generate candidates, do not run them |
| `--model-deploy-config` | No | structure | -- | Auto-deploy best model to endpoint |
| `--tags` | No | list | -- | Key-value tags |

**Output Schema:**
```json
{
    "AutoMLJobArn": "string"
}
```

---

## 2. `create-auto-ml-job-v2`

Creates an AutoML V2 job supporting additional problem types including image classification, text classification, time-series forecasting, and tabular data.

**Synopsis:**
```bash
aws sagemaker create-auto-ml-job-v2 \
    --auto-ml-job-name <value> \
    --auto-ml-job-input-data-config <value> \
    --output-data-config <value> \
    --auto-ml-problem-type-config <value> \
    --role-arn <value> \
    [--auto-ml-job-objective <value>] \
    [--auto-ml-compute-config <value>] \
    [--data-split-config <value>] \
    [--security-config <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-ml-job-name` | **Yes** | string | -- | Unique name (1-32 chars) |
| `--auto-ml-job-input-data-config` | **Yes** | list | -- | Input data config (1-20 channels) |
| `--output-data-config` | **Yes** | structure | -- | S3 output path |
| `--auto-ml-problem-type-config` | **Yes** | structure | -- | Problem type config (see below) |
| `--role-arn` | **Yes** | string | -- | IAM role ARN |
| `--auto-ml-job-objective` | No | structure | -- | Objective metric |
| `--auto-ml-compute-config` | No | structure | -- | Compute resource config |
| `--data-split-config` | No | structure | -- | Validation fraction |
| `--security-config` | No | structure | -- | VPC and encryption |
| `--tags` | No | list | -- | Key-value tags |

**Problem Type Configs (one of):**
```json
{
    "TabularJobConfig": {
        "CandidateGenerationConfig": {...},
        "CompletionCriteria": {...},
        "FeatureSpecificationS3Uri": "string",
        "Mode": "AUTO|ENSEMBLING|HYPERPARAMETER_TUNING",
        "GenerateCandidateDefinitionsOnly": "boolean",
        "ProblemType": "BinaryClassification|MulticlassClassification|Regression",
        "TargetAttributeName": "string",
        "SampleWeightAttributeName": "string"
    },
    "ImageClassificationJobConfig": {
        "CompletionCriteria": {...}
    },
    "TextClassificationJobConfig": {
        "CompletionCriteria": {...},
        "ContentColumn": "string",
        "TargetLabelColumn": "string"
    },
    "TimeSeriesForecastingJobConfig": {
        "ForecastFrequency": "string",
        "ForecastHorizon": "integer",
        "ForecastQuantiles": ["string"],
        "TimeSeriesConfig": {...},
        "Transformations": {...},
        "CompletionCriteria": {...}
    },
    "TextGenerationJobConfig": {
        "CompletionCriteria": {...},
        "BaseModelName": "string",
        "TextGenerationHyperParameters": {"string": "string"},
        "ModelAccessConfig": {"AcceptEula": true}
    }
}
```

**Output Schema:**
```json
{
    "AutoMLJobArn": "string"
}
```

---

## 3. `describe-auto-ml-job`

Returns information about an AutoML job.

**Synopsis:**
```bash
aws sagemaker describe-auto-ml-job \
    --auto-ml-job-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-ml-job-name` | **Yes** | string | -- | Name of the AutoML job |

**Output Schema:**
```json
{
    "AutoMLJobName": "string",
    "AutoMLJobArn": "string",
    "InputDataConfig": [...],
    "OutputDataConfig": {...},
    "RoleArn": "string",
    "AutoMLJobObjective": {"MetricName": "string"},
    "ProblemType": "BinaryClassification|MulticlassClassification|Regression",
    "AutoMLJobConfig": {...},
    "CreationTime": "timestamp",
    "EndTime": "timestamp",
    "LastModifiedTime": "timestamp",
    "FailureReason": "string",
    "AutoMLJobStatus": "Completed|InProgress|Failed|Stopped|Stopping",
    "AutoMLJobSecondaryStatus": "Starting|MaxCandidatesReached|Failed|Stopped|MaxAutoMLJobRuntimeReached|Stopping|CandidateDefinitionsGenerated|Completed|...",
    "BestCandidate": {
        "CandidateName": "string",
        "FinalAutoMLJobObjectiveMetric": {
            "Type": "Maximize|Minimize",
            "MetricName": "string",
            "Value": "float",
            "StandardMetricName": "string"
        },
        "ObjectiveStatus": "Succeeded|Pending|Failed",
        "CandidateSteps": [...],
        "CandidateStatus": "Completed|InProgress|Failed|Stopped|Stopping",
        "InferenceContainers": [
            {"Image": "string", "ModelDataUrl": "string", "Environment": {"string": "string"}}
        ],
        "CandidateProperties": {...}
    },
    "GenerateCandidateDefinitionsOnly": "boolean",
    "ModelDeployConfig": {...},
    "ModelDeployResult": {"EndpointName": "string"}
}
```

---

## 4. `describe-auto-ml-job-v2`

Returns information about an AutoML V2 job.

**Synopsis:**
```bash
aws sagemaker describe-auto-ml-job-v2 \
    --auto-ml-job-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-ml-job-name` | **Yes** | string | -- | Name of the AutoML V2 job |

**Output Schema:** Same structure as `describe-auto-ml-job` with additional `AutoMLProblemTypeConfig` and `AutoMLProblemTypeConfigName` fields.

---

## 5. `list-auto-ml-jobs`

Lists AutoML jobs. **Paginated operation.**

**Synopsis:**
```bash
aws sagemaker list-auto-ml-jobs \
    [--creation-time-after <value>] \
    [--creation-time-before <value>] \
    [--last-modified-time-after <value>] \
    [--last-modified-time-before <value>] \
    [--name-contains <value>] \
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
| `--creation-time-after` | No | timestamp | -- | Filter by creation time |
| `--creation-time-before` | No | timestamp | -- | Filter by creation time |
| `--name-contains` | No | string | -- | Filter by name substring |
| `--status-equals` | No | string | -- | `Completed`, `InProgress`, `Failed`, `Stopped`, `Stopping` |
| `--sort-by` | No | string | `Name` | `Name`, `CreationTime`, `Status` |
| `--sort-order` | No | string | `Ascending` | `Ascending`, `Descending` |

**Output Schema:**
```json
{
    "AutoMLJobSummaries": [
        {
            "AutoMLJobName": "string",
            "AutoMLJobArn": "string",
            "AutoMLJobStatus": "string",
            "AutoMLJobSecondaryStatus": "string",
            "CreationTime": "timestamp",
            "EndTime": "timestamp",
            "LastModifiedTime": "timestamp",
            "FailureReason": "string"
        }
    ],
    "NextToken": "string"
}
```

---

## 6. `stop-auto-ml-job`

Stops an AutoML job.

**Synopsis:**
```bash
aws sagemaker stop-auto-ml-job \
    --auto-ml-job-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--auto-ml-job-name` | **Yes** | string | -- | Name of the AutoML job to stop |

**Output:** None

---

## 7. `list-candidates-for-auto-ml-job`

Lists candidates generated by an AutoML job. **Paginated operation.**

**Synopsis:**
```bash
aws sagemaker list-candidates-for-auto-ml-job \
    --auto-ml-job-name <value> \
    [--status-equals <value>] \
    [--candidate-name-equals <value>] \
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
| `--auto-ml-job-name` | **Yes** | string | -- | AutoML job name |
| `--status-equals` | No | string | -- | `Completed`, `InProgress`, `Failed`, `Stopped`, `Stopping` |
| `--candidate-name-equals` | No | string | -- | Filter by candidate name |
| `--sort-by` | No | string | `CreationTime` | `CreationTime`, `Status`, `FinalObjectiveMetricValue` |
| `--sort-order` | No | string | `Ascending` | `Ascending`, `Descending` |

**Output Schema:**
```json
{
    "Candidates": [
        {
            "CandidateName": "string",
            "FinalAutoMLJobObjectiveMetric": {
                "Type": "Maximize|Minimize",
                "MetricName": "string",
                "Value": "float"
            },
            "ObjectiveStatus": "Succeeded|Pending|Failed",
            "CandidateSteps": [
                {
                    "CandidateStepType": "AWS::SageMaker::TrainingJob|AWS::SageMaker::TransformJob|AWS::SageMaker::ProcessingJob",
                    "CandidateStepArn": "string",
                    "CandidateStepName": "string"
                }
            ],
            "CandidateStatus": "Completed|InProgress|Failed|Stopped|Stopping",
            "InferenceContainers": [
                {"Image": "string", "ModelDataUrl": "string", "Environment": {"string": "string"}}
            ],
            "CreationTime": "timestamp",
            "EndTime": "timestamp",
            "LastModifiedTime": "timestamp",
            "FailureReason": "string"
        }
    ],
    "NextToken": "string"
}
```
