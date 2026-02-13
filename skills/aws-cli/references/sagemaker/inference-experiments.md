# Inference Experiments

## 1. `create-inference-experiment`

Creates an inference experiment for A/B testing models on an endpoint.

**Synopsis:**
```bash
aws sagemaker create-inference-experiment \
    --name <value> \
    --type <value> \
    --endpoint-name <value> \
    --model-variants <value> \
    [--schedule <value>] \
    [--description <value>] \
    [--role-arn <value>] \
    [--data-storage-config <value>] \
    [--shadow-mode-config <value>] \
    [--kms-key <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Experiment name (1-120 chars) |
| `--type` | **Yes** | string | -- | `ShadowMode` |
| `--endpoint-name` | **Yes** | string | -- | Endpoint name |
| `--model-variants` | **Yes** | list | -- | Model variant configurations |
| `--schedule` | No | structure | -- | `StartTime`, `EndTime` |
| `--description` | No | string | -- | Description |
| `--role-arn` | No | string | -- | IAM role ARN |
| `--data-storage-config` | No | structure | -- | Data capture S3 config |
| `--shadow-mode-config` | No | structure | -- | Shadow variant traffic config |
| `--kms-key` | No | string | -- | KMS key for encryption |
| `--tags` | No | list | -- | Key-value tags |

**Model Variants:**
```json
[
    {
        "ModelName": "string",
        "VariantName": "string",
        "InfrastructureConfig": {
            "InfrastructureType": "RealTimeInference",
            "RealTimeInferenceConfig": {
                "InstanceType": "ml.m5.xlarge|...",
                "InstanceCount": "integer"
            }
        }
    }
]
```

**Output Schema:**
```json
{
    "InferenceExperimentArn": "string"
}
```

---

## 2. `describe-inference-experiment`

Returns details about an inference experiment.

```bash
aws sagemaker describe-inference-experiment --name <value>
```

**Output Schema:**
```json
{
    "Arn": "string",
    "Name": "string",
    "Type": "ShadowMode",
    "Schedule": {"StartTime": "timestamp", "EndTime": "timestamp"},
    "Status": "Creating|Created|Updating|Running|Starting|Stopping|Completed|Cancelled",
    "StatusReason": "string",
    "Description": "string",
    "CreationTime": "timestamp",
    "CompletionTime": "timestamp",
    "LastModifiedTime": "timestamp",
    "RoleArn": "string",
    "EndpointMetadata": {
        "EndpointName": "string",
        "EndpointConfigName": "string",
        "EndpointStatus": "string",
        "FailureReason": "string"
    },
    "ModelVariants": [
        {
            "ModelName": "string",
            "VariantName": "string",
            "InfrastructureConfig": {...}
        }
    ],
    "DataStorageConfig": {"Destination": "string", "KmsKey": "string", "ContentType": {...}},
    "ShadowModeConfig": {
        "SourceModelVariantName": "string",
        "ShadowModelVariants": [{"ShadowModelVariantName": "string", "SamplingPercentage": "integer"}]
    },
    "KmsKey": "string"
}
```

---

## 3. `list-inference-experiments`

Lists inference experiments. **Paginated operation.**

```bash
aws sagemaker list-inference-experiments \
    [--name-contains <value>] \
    [--type <value>] \
    [--status-equals <value>] \
    [--creation-time-after <value>] \
    [--creation-time-before <value>] \
    [--last-modified-time-after <value>] \
    [--last-modified-time-before <value>] \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

---

## 4. `update-inference-experiment`

Updates an inference experiment.

```bash
aws sagemaker update-inference-experiment \
    --name <value> \
    [--schedule <value>] \
    [--description <value>] \
    [--model-variants <value>] \
    [--data-storage-config <value>] \
    [--shadow-mode-config <value>]
```

**Output Schema:**
```json
{
    "InferenceExperimentArn": "string"
}
```

---

## 5. `start-inference-experiment` / `stop-inference-experiment` / `delete-inference-experiment`

```bash
aws sagemaker start-inference-experiment --name <value>
aws sagemaker stop-inference-experiment --name <value> --model-variant-actions <value> [--desired-model-variants <value>] [--desired-state <value>] [--reason <value>]
aws sagemaker delete-inference-experiment --name <value>
```

**stop-inference-experiment Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Experiment name |
| `--model-variant-actions` | **Yes** | map | -- | Actions per variant: `Promote`, `Remove`, `Retain` |
| `--desired-model-variants` | No | list | -- | Desired model variant configs |
| `--desired-state` | No | string | -- | `Completed`, `Cancelled` |
| `--reason` | No | string | -- | Reason for stopping |

---

## Inference Recommendations

### 6. `create-inference-recommendations-job`

Creates a job that recommends instance types and configurations for deploying a model.

**Synopsis:**
```bash
aws sagemaker create-inference-recommendations-job \
    --job-name <value> \
    --job-type <value> \
    --role-arn <value> \
    --input-config <value> \
    [--job-description <value>] \
    [--stopping-conditions <value>] \
    [--output-config <value>] \
    [--tags <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-name` | **Yes** | string | -- | Unique name (1-64 chars) |
| `--job-type` | **Yes** | string | -- | `Default` or `Advanced` |
| `--role-arn` | **Yes** | string | -- | IAM role ARN |
| `--input-config` | **Yes** | structure | -- | Model package ARN or container config, traffic pattern, endpoint configs |
| `--stopping-conditions` | No | structure | -- | Max invocations, model latency thresholds |
| `--output-config` | No | structure | -- | Compilation config |
| `--tags` | No | list | -- | Key-value tags |

**Output Schema:**
```json
{
    "JobArn": "string"
}
```

---

### 7. `describe-inference-recommendations-job`

Returns details about an inference recommendations job.

```bash
aws sagemaker describe-inference-recommendations-job --job-name <value>
```

**Output Schema:**
```json
{
    "JobName": "string",
    "JobDescription": "string",
    "JobType": "Default|Advanced",
    "JobArn": "string",
    "RoleArn": "string",
    "Status": "PENDING|IN_PROGRESS|COMPLETED|FAILED|STOPPING|STOPPED|DELETING",
    "CreationTime": "timestamp",
    "CompletionTime": "timestamp",
    "LastModifiedTime": "timestamp",
    "FailureReason": "string",
    "InputConfig": {...},
    "StoppingConditions": {...},
    "InferenceRecommendations": [
        {
            "RecommendationId": "string",
            "Metrics": {
                "CostPerHour": "float",
                "CostPerInference": "float",
                "MaxInvocations": "integer",
                "ModelLatency": "integer",
                "CpuUtilization": "float",
                "MemoryUtilization": "float",
                "ModelSetupTime": "integer"
            },
            "EndpointConfiguration": {
                "EndpointName": "string",
                "VariantName": "string",
                "InstanceType": "string",
                "InitialInstanceCount": "integer",
                "ServerlessConfig": {...}
            },
            "ModelConfiguration": {
                "InferenceSpecificationName": "string",
                "EnvironmentParameters": [{"Key": "string", "ValueType": "string", "Value": "string"}],
                "CompilationJobName": "string"
            },
            "InvocationEndTime": "timestamp",
            "InvocationStartTime": "timestamp"
        }
    ],
    "EndpointPerformances": [...]
}
```

---

### 8. `list-inference-recommendations-jobs`

Lists inference recommendations jobs. **Paginated operation.**

```bash
aws sagemaker list-inference-recommendations-jobs \
    [--creation-time-after <value>] \
    [--creation-time-before <value>] \
    [--last-modified-time-after <value>] \
    [--last-modified-time-before <value>] \
    [--name-contains <value>] \
    [--status-equals <value>] \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--model-name-equals <value>] \
    [--model-package-version-arn-equals <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

---

### 9. `stop-inference-recommendations-job`

Stops an inference recommendations job.

```bash
aws sagemaker stop-inference-recommendations-job --job-name <value>
```

**Output:** None

---

### 10. `get-scaling-configuration-recommendation`

Gets auto scaling configuration recommendations for an inference component.

```bash
aws sagemaker get-scaling-configuration-recommendation \
    --inference-recommendations-job-name <value> \
    [--recommendation-id <value>] \
    [--endpoint-name <value>] \
    [--target-cpu-utilization-per-core <value>] \
    [--scaling-policy-objective <value>]
```
