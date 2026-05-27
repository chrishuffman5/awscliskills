# AWS CLI v2 -- Batch Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/batch/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `submit-job` | Job | Submit a job to a job queue |
| `cancel-job` | Job | Cancel a pending or runnable job |
| `terminate-job` | Job | Terminate a running job |
| `describe-jobs` | Job | Describe one or more jobs |
| `list-jobs` | Job | List jobs in a job queue or by status |
| `get-job-queue-snapshot` | Job | Get a snapshot of job queue state |
| `register-job-definition` | Job Definition | Register a new job definition |
| `deregister-job-definition` | Job Definition | Deregister a job definition |
| `describe-job-definitions` | Job Definition | Describe job definitions |
| `create-job-queue` | Job Queue | Create a job queue |
| `update-job-queue` | Job Queue | Update a job queue |
| `delete-job-queue` | Job Queue | Delete a job queue |
| `describe-job-queues` | Job Queue | Describe job queues |
| `create-compute-environment` | Compute Environment | Create a compute environment |
| `update-compute-environment` | Compute Environment | Update a compute environment |
| `delete-compute-environment` | Compute Environment | Delete a compute environment |
| `describe-compute-environments` | Compute Environment | Describe compute environments |
| `create-scheduling-policy` | Scheduling Policy | Create a scheduling policy |
| `update-scheduling-policy` | Scheduling Policy | Update a scheduling policy |
| `delete-scheduling-policy` | Scheduling Policy | Delete a scheduling policy |
| `describe-scheduling-policies` | Scheduling Policy | Describe scheduling policies |
| `list-scheduling-policies` | Scheduling Policy | List scheduling policies |
| `create-consumable-resource` | Consumable Resource | Create a consumable resource |
| `update-consumable-resource` | Consumable Resource | Update a consumable resource |
| `delete-consumable-resource` | Consumable Resource | Delete a consumable resource |
| `describe-consumable-resource` | Consumable Resource | Describe a consumable resource |
| `list-consumable-resources` | Consumable Resource | List consumable resources |
| `list-jobs-by-consumable-resource` | Consumable Resource | List jobs using a consumable resource |
| `create-service-environment` | Service Environment | Create a service environment |
| `update-service-environment` | Service Environment | Update a service environment |
| `delete-service-environment` | Service Environment | Delete a service environment |
| `describe-service-environments` | Service Environment | Describe service environments |
| `describe-service-job` | Service Environment | Describe a service job |
| `submit-service-job` | Service Environment | Submit a job to a service environment |
| `list-service-jobs` | Service Environment | List service jobs |
| `terminate-service-job` | Service Environment | Terminate a service job |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

---

## Global Options

These options are available on ALL `aws batch` commands.

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

### Job States
| Status | Description |
|--------|-------------|
| `SUBMITTED` | Job has been submitted |
| `PENDING` | Job is waiting for dependencies |
| `RUNNABLE` | Job is ready to be scheduled |
| `STARTING` | Job is being placed on a compute resource |
| `RUNNING` | Job is running |
| `SUCCEEDED` | Job completed successfully |
| `FAILED` | Job failed |

### Compute Environment Types
| Type | Description |
|------|-------------|
| `MANAGED` | AWS Batch manages the compute resources |
| `UNMANAGED` | You manage the compute resources |

### Compute Resource Types
| Type | Description |
|------|-------------|
| `EC2` | On-Demand EC2 instances |
| `SPOT` | Spot EC2 instances |
| `FARGATE` | Fargate compute |
| `FARGATE_SPOT` | Fargate Spot compute |
