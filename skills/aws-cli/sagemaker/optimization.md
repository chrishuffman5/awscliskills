# Optimization

## 1. `create-optimization-job`

Creates a model optimization job (quantization, compilation, distillation).

**Synopsis:**
```bash
aws sagemaker create-optimization-job \
    --optimization-job-name <value> \
    --role-arn <value> \
    --model-source <value> \
    --deployment-instance-type <value> \
    --optimization-configs <value> \
    --output-config <value> \
    --stopping-condition <value> \
    [--optimization-environment <value>] \
    [--vpc-config <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--optimization-job-name` | **Yes** | string | -- | Unique name (1-63 chars) |
| `--role-arn` | **Yes** | string | -- | IAM role ARN |
| `--model-source` | **Yes** | structure | -- | `S3` (`S3Uri`, `ModelAccessConfig`) |
| `--deployment-instance-type` | **Yes** | string | -- | Target instance type for deployment |
| `--optimization-configs` | **Yes** | list | -- | Optimization techniques |
| `--output-config` | **Yes** | structure | -- | `S3OutputLocation`, `KmsKeyId` |
| `--stopping-condition` | **Yes** | structure | -- | `MaxRuntimeInSeconds`, `MaxWaitTimeInSeconds`, `MaxPendingTimeInSeconds` |
| `--optimization-environment` | No | map | -- | Environment variables |
| `--vpc-config` | No | structure | -- | VPC config |
| `--tags` | No | list | -- | Key-value tags |

**Optimization Configs (one of per entry):**
```json
[
    {
        "ModelQuantizationConfig": {
            "Image": "string",
            "OverrideEnvironment": {"string": "string"}
        }
    },
    {
        "ModelCompilationConfig": {
            "Image": "string",
            "OverrideEnvironment": {"string": "string"}
        }
    }
]
```

**Output Schema:**
```json
{
    "OptimizationJobArn": "string"
}
```

---

## 2. `describe-optimization-job`

Returns details about an optimization job.

```bash
aws sagemaker describe-optimization-job --optimization-job-name <value>
```

**Output Schema:**
```json
{
    "OptimizationJobArn": "string",
    "OptimizationJobStatus": "INPROGRESS|COMPLETED|FAILED|STARTING|STOPPING|STOPPED",
    "OptimizationStartTime": "timestamp",
    "OptimizationEndTime": "timestamp",
    "CreationTime": "timestamp",
    "LastModifiedTime": "timestamp",
    "FailureReason": "string",
    "OptimizationJobName": "string",
    "ModelSource": {"S3": {"S3Uri": "string"}},
    "OptimizationEnvironment": {"string": "string"},
    "DeploymentInstanceType": "string",
    "OptimizationConfigs": [...],
    "OutputConfig": {"S3OutputLocation": "string", "KmsKeyId": "string"},
    "OptimizationOutput": {"RecommendedInferenceImage": "string"},
    "RoleArn": "string",
    "StoppingCondition": {...},
    "VpcConfig": {...}
}
```

---

## 3. `list-optimization-jobs`

Lists optimization jobs. **Paginated operation.**

```bash
aws sagemaker list-optimization-jobs \
    [--creation-time-after <value>] \
    [--creation-time-before <value>] \
    [--last-modified-time-after <value>] \
    [--last-modified-time-before <value>] \
    [--optimization-contains <value>] \
    [--name-contains <value>] \
    [--status-equals <value>] \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

---

## 4. `stop-optimization-job`

Stops a running optimization job.

```bash
aws sagemaker stop-optimization-job --optimization-job-name <value>
```

**Output:** None

---

## 5. `delete-optimization-job`

Deletes an optimization job.

```bash
aws sagemaker delete-optimization-job --optimization-job-name <value>
```

**Output:** None
