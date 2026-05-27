# AWS CLI v2 -- Amazon SageMaker Command Reference Index

> Based on AWS CLI v2 documentation. Sources: https://docs.aws.amazon.com/cli/latest/reference/sagemaker/ , https://docs.aws.amazon.com/cli/latest/reference/sagemaker-runtime/

---

## Quick Reference

### Training & Processing

| Command | Description |
|---------|-------------|
| `create-training-job` | Create a training job |
| `describe-training-job` | Get training job details |
| `list-training-jobs` | List training jobs |
| `stop-training-job` | Stop a training job |
| `update-training-job` | Update a training job |
| `delete-training-job` | Delete a training job |
| `create-processing-job` | Create a processing job |
| `describe-processing-job` | Get processing job details |
| `list-processing-jobs` | List processing jobs |
| `stop-processing-job` | Stop a processing job |
| `delete-processing-job` | Delete a processing job |
| `create-hyper-parameter-tuning-job` | Create a hyperparameter tuning job |
| `describe-hyper-parameter-tuning-job` | Get tuning job details |
| `list-hyper-parameter-tuning-jobs` | List tuning jobs |
| `stop-hyper-parameter-tuning-job` | Stop a tuning job |
| `delete-hyper-parameter-tuning-job` | Delete a tuning job |
| `list-training-jobs-for-hyper-parameter-tuning-job` | List training jobs for a tuning job |
| `create-auto-ml-job` | Create an AutoML job |
| `create-auto-ml-job-v2` | Create an AutoML v2 job |
| `describe-auto-ml-job` | Get AutoML job details |
| `describe-auto-ml-job-v2` | Get AutoML v2 job details |
| `list-auto-ml-jobs` | List AutoML jobs |
| `stop-auto-ml-job` | Stop an AutoML job |
| `list-candidates-for-auto-ml-job` | List candidates for an AutoML job |

### Models & Endpoints

| Command | Description |
|---------|-------------|
| `create-model` | Create a model |
| `describe-model` | Get model details |
| `list-models` | List models |
| `delete-model` | Delete a model |
| `create-endpoint-config` | Create an endpoint configuration |
| `describe-endpoint-config` | Get endpoint config details |
| `list-endpoint-configs` | List endpoint configurations |
| `delete-endpoint-config` | Delete an endpoint configuration |
| `create-endpoint` | Create an endpoint |
| `describe-endpoint` | Get endpoint details |
| `list-endpoints` | List endpoints |
| `update-endpoint` | Update an endpoint |
| `update-endpoint-weights-and-capacities` | Update variant weights |
| `delete-endpoint` | Delete an endpoint |
| `create-inference-component` | Create an inference component |
| `describe-inference-component` | Get inference component details |
| `list-inference-components` | List inference components |
| `update-inference-component` | Update an inference component |
| `delete-inference-component` | Delete an inference component |
| `create-compilation-job` | Compile a model for edge devices |
| `describe-compilation-job` | Get compilation job details |
| `list-compilation-jobs` | List compilation jobs |
| `stop-compilation-job` | Stop a compilation job |

### Pipelines

| Command | Description |
|---------|-------------|
| `create-pipeline` | Create a pipeline |
| `describe-pipeline` | Get pipeline details |
| `list-pipelines` | List pipelines |
| `update-pipeline` | Update a pipeline |
| `delete-pipeline` | Delete a pipeline |
| `start-pipeline-execution` | Start a pipeline execution |
| `describe-pipeline-execution` | Get execution details |
| `list-pipeline-executions` | List pipeline executions |
| `stop-pipeline-execution` | Stop a pipeline execution |
| `retry-pipeline-execution` | Retry a failed execution |
| `list-pipeline-execution-steps` | List execution steps |

### Experiments & Lineage

| Command | Description |
|---------|-------------|
| `create-experiment` | Create an experiment |
| `create-trial` | Create a trial |
| `create-trial-component` | Create a trial component |
| `associate-trial-component` | Associate a component with a trial |
| `create-action` | Create a lineage action |
| `create-artifact` | Create a lineage artifact |
| `create-context` | Create a lineage context |
| `add-association` | Add a lineage association |
| `query-lineage` | Query lineage graph |

### Feature Store & Model Registry

| Command | Description |
|---------|-------------|
| `create-feature-group` | Create a feature group |
| `describe-feature-group` | Get feature group details |
| `list-feature-groups` | List feature groups |
| `create-model-package-group` | Create a model package group |
| `create-model-package` | Create a model package |
| `describe-model-package` | Get model package details |
| `list-model-packages` | List model packages |
| `update-model-package` | Update a model package |

### Monitoring

| Command | Description |
|---------|-------------|
| `create-monitoring-schedule` | Create a monitoring schedule |
| `list-monitoring-schedules` | List monitoring schedules |
| `create-data-quality-job-definition` | Create a data quality job definition |
| `create-model-quality-job-definition` | Create a model quality job definition |
| `create-model-bias-job-definition` | Create a model bias job definition |
| `create-model-explainability-job-definition` | Create an explainability job definition |

### Infrastructure

| Command | Description |
|---------|-------------|
| `create-notebook-instance` | Create a notebook instance |
| `start-notebook-instance` | Start a notebook instance |
| `stop-notebook-instance` | Stop a notebook instance |
| `create-cluster` | Create a HyperPod cluster |
| `create-domain` | Create a Studio domain |
| `create-user-profile` | Create a Studio user profile |
| `create-space` | Create a Studio space |

### MLflow & Optimization

| Command | Description |
|---------|-------------|
| `create-mlflow-tracking-server` | Create an MLflow tracking server |
| `start-mlflow-tracking-server` | Start an MLflow server |
| `create-optimization-job` | Create a model optimization job |

### Other

| Command | Description |
|---------|-------------|
| `create-transform-job` | Create a batch transform job |
| `create-labeling-job` | Create a labeling job |
| `create-algorithm` | Create a custom algorithm |
| `create-project` | Create a project |
| `search` | Search SageMaker resources |

### Runtime (`aws sagemaker-runtime`)

| Command | Description |
|---------|-------------|
| `invoke-endpoint` | Invoke an endpoint for real-time inference |
| `invoke-endpoint-async` | Invoke an endpoint asynchronously |

---

## Global Options

These options are available on ALL `aws sagemaker` and `aws sagemaker-runtime` commands.

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `--debug` | boolean | false | Enable debug logging to stderr |
| `--endpoint-url` | string | -- | Override the default service endpoint URL |
| `--no-verify-ssl` | boolean | false | Disable SSL certificate verification |
| `--no-paginate` | boolean | false | Disable automatic pagination |
| `--output` | string | `json` | Output format: `json`, `text`, `table`, `yaml`, `yaml-stream` |
| `--query` | string | -- | JMESPath query to filter output |
| `--profile` | string | `default` | Named AWS credential profile |
| `--region` | string | from config | AWS region to send requests to |
| `--version` | string | -- | Display the CLI version |
| `--color` | string | `auto` | Toggle color output: `on`, `off`, `auto` |
| `--no-sign-request` | boolean | false | Do not sign requests |
| `--ca-bundle` | string | -- | Path to custom CA certificate bundle |
| `--cli-read-timeout` | integer | 60 | Socket read timeout in seconds |
| `--cli-connect-timeout` | integer | 60 | Socket connect timeout in seconds |
| `--cli-binary-format` | string | `base64` | Format for binary blob input: `base64`, `raw-in-base64-out` |
| `--no-cli-pager` | boolean | false | Disable the output pager |
| `--cli-auto-prompt` | boolean | false | Auto-prompt for missing parameters |
| `--no-cli-auto-prompt` | boolean | false | Disable auto-prompt |
| `--cli-input-json` | string | -- | Read arguments from a JSON string or `file://` path |
| `--cli-input-yaml` | string | -- | Read arguments from a YAML string or `file://` path |
| `--generate-cli-skeleton` | string | -- | Print input/output skeleton: `input`, `yaml-input`, `output` |

---

## Common Patterns

### Instance Types
SageMaker uses `ml.*` instance types (e.g., `ml.m5.xlarge`, `ml.p3.2xlarge`, `ml.g5.xlarge`). Available types vary by feature (training, inference, processing, notebooks).

### Job Status Values
| Status | Description |
|--------|-------------|
| `InProgress` | Job is running |
| `Completed` | Job finished successfully |
| `Failed` | Job failed |
| `Stopping` | Job is being stopped |
| `Stopped` | Job was stopped |

### Endpoint Status Values
| Status | Description |
|--------|-------------|
| `Creating` | Endpoint is being created |
| `Updating` | Endpoint is being updated |
| `InService` | Endpoint is available |
| `Deleting` | Endpoint is being deleted |
| `Failed` | Endpoint creation/update failed |
| `RollingBack` | Endpoint update is rolling back |

### Name Constraints
Most SageMaker resource names follow: pattern `[a-zA-Z0-9](-*[a-zA-Z0-9]){0,62}`, max 63 characters.

### Wait Commands
```bash
aws sagemaker wait endpoint-in-service --endpoint-name my-endpoint
aws sagemaker wait training-job-completed-or-stopped --training-job-name my-job
aws sagemaker wait notebook-instance-in-service --notebook-instance-name my-nb
aws sagemaker wait processing-job-completed-or-stopped --processing-job-name my-job
aws sagemaker wait transform-job-completed-or-stopped --transform-job-name my-job
```
