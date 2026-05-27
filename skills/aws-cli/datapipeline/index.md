# AWS CLI v2 -- Data Pipeline Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/datapipeline/

> **LEGACY SERVICE:** For new workloads, consider AWS Step Functions, AWS Glue, or Amazon MWAA instead.

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-pipeline` | Pipeline | Create a new, empty pipeline |
| `delete-pipeline` | Pipeline | Delete a pipeline and its definition |
| `describe-pipelines` | Pipeline | Describe metadata for one or more pipelines |
| `list-pipelines` | Pipeline | List all pipelines in the account |
| `activate-pipeline` | Pipeline | Activate a pipeline to begin processing |
| `deactivate-pipeline` | Pipeline | Deactivate a running pipeline |
| `put-pipeline-definition` | Definition | Upload or update a pipeline definition |
| `get-pipeline-definition` | Definition | Retrieve a pipeline's definition |
| `validate-pipeline-definition` | Definition | Validate a pipeline definition without saving |
| `describe-objects` | Objects | Describe pipeline objects (nodes, activities, etc.) |
| `query-objects` | Objects | Query for pipeline objects matching criteria |
| `evaluate-expression` | Objects | Evaluate a pipeline expression |
| `set-status` | Objects | Set the status of pipeline objects |
| `poll-for-task` | Task Runner | Request the next task for a task runner |
| `report-task-progress` | Task Runner | Report progress on a running task |
| `report-task-runner-heartbeat` | Task Runner | Send a heartbeat from a task runner |
| `set-task-status` | Task Runner | Set the final status of a task |
| `add-tags` | Tags | Add tags to a pipeline |
| `remove-tags` | Tags | Remove tags from a pipeline |

---

## Global Options

These options are available on ALL `aws datapipeline` commands.

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
| `--no-sign-request` | boolean | false | Do not sign requests (for anonymous access) |
| `--ca-bundle` | string | -- | Path to custom CA certificate bundle for SSL |
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

### Pipeline ID Format

Pipeline IDs follow the pattern `df-` followed by a 17-character alphanumeric string (e.g., `df-0123456789ABCDEFG`).

### Pipeline States

| State | Description |
|-------|-------------|
| `PENDING` | Pipeline has been created but not yet activated |
| `SCHEDULING` | Pipeline is being scheduled |
| `RUNNING` | Pipeline is actively running |
| `WAITING_ON_DEPENDENCIES` | Pipeline is waiting for dependencies |
| `FINISHED` | Pipeline execution completed successfully |
| `DEACTIVATING` | Pipeline is being deactivated |
| `PAUSED` | Pipeline has been deactivated |
| `CANCELED` | Pipeline has been canceled |
| `CASCADE_FAILED` | Pipeline failed due to upstream failure |
| `FAILED` | Pipeline execution failed |

### Object Types

| Type | Description |
|------|-------------|
| `DataNode` | Represents data source or destination (S3, DynamoDB, RDS, etc.) |
| `Activity` | Computation or data transformation (ShellCommandActivity, CopyActivity, etc.) |
| `Schedule` | Defines when and how frequently pipeline runs |
| `Precondition` | Condition that must be met before activity executes |
| `Resource` | Compute resource that runs activities (Ec2Resource, EmrCluster) |

### Task Runner Statuses

| Status | Description |
|--------|-------------|
| `FINISHED` | Task completed successfully |
| `FAILED` | Task failed |
| `FALSE` | Task precondition evaluated to false |
