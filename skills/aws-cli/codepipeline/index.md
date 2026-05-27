# AWS CLI v2 -- CodePipeline Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/codepipeline/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-pipeline` | Pipeline | Create a new pipeline |
| `delete-pipeline` | Pipeline | Delete a pipeline |
| `get-pipeline` | Pipeline | Get the pipeline structure |
| `list-pipelines` | Pipeline | List all pipelines |
| `update-pipeline` | Pipeline | Update a pipeline structure |
| `start-pipeline-execution` | Pipeline | Start a pipeline execution |
| `stop-pipeline-execution` | Pipeline | Stop a pipeline execution |
| `get-pipeline-state` | Pipeline | Get the state of a pipeline |
| `get-pipeline-execution` | Pipeline | Get details of a pipeline execution |
| `list-pipeline-executions` | Pipeline | List executions for a pipeline |
| `retry-stage-execution` | Pipeline | Retry a failed stage |
| `rollback-stage` | Pipeline | Roll back a stage to a previous successful execution |
| `enable-stage-transition` | Stage | Enable a stage transition |
| `disable-stage-transition` | Stage | Disable a stage transition |
| `put-approval-result` | Stage | Provide an approval result for a manual approval action |
| `put-job-success-result` | Action | Report a job success (custom action) |
| `put-job-failure-result` | Action | Report a job failure (custom action) |
| `put-third-party-job-success-result` | Action | Report third-party job success |
| `put-third-party-job-failure-result` | Action | Report third-party job failure |
| `poll-for-jobs` | Action | Poll for available jobs (custom action) |
| `poll-for-third-party-jobs` | Action | Poll for third-party jobs |
| `acknowledge-job` | Action | Acknowledge a job (custom action) |
| `acknowledge-third-party-job` | Action | Acknowledge a third-party job |
| `put-action-revision` | Action | Provide a revision for a source action |
| `list-action-executions` | Action | List action executions for a pipeline |
| `get-action-type` | Action Type | Get details of an action type |
| `list-action-types` | Action Type | List available action types |
| `update-action-type` | Action Type | Update an action type |
| `put-webhook` | Webhook | Create or update a webhook |
| `delete-webhook` | Webhook | Delete a webhook |
| `deregister-webhook-with-third-party` | Webhook | Deregister a webhook from the third party |
| `list-webhooks` | Webhook | List webhooks |
| `register-webhook-with-third-party` | Webhook | Register a webhook with the third party |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

---

## Global Options

These options are available on ALL `aws codepipeline` commands.

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

### Pipeline Execution Status Values
| Status | Description |
|--------|-------------|
| `Cancelled` | Execution was cancelled |
| `InProgress` | Execution is currently running |
| `Stopped` | Execution was stopped |
| `Stopping` | Execution is being stopped |
| `Succeeded` | Execution completed successfully |
| `Superseded` | Execution was superseded by a newer execution |
| `Failed` | Execution failed |

### Stage Execution Status Values
| Status | Description |
|--------|-------------|
| `Cancelled` | Stage execution was cancelled |
| `InProgress` | Stage is currently executing |
| `Failed` | Stage execution failed |
| `Stopped` | Stage execution was stopped |
| `Stopping` | Stage is being stopped |
| `Succeeded` | Stage completed successfully |

### Action Execution Status Values
| Status | Description |
|--------|-------------|
| `InProgress` | Action is running |
| `Abandoned` | Action was abandoned |
| `Succeeded` | Action completed successfully |
| `Failed` | Action failed |

### Action Category Values
| Category | Description |
|----------|-------------|
| `Source` | Source action (e.g., CodeCommit, S3, GitHub) |
| `Build` | Build action (e.g., CodeBuild) |
| `Deploy` | Deploy action (e.g., CodeDeploy, ECS, S3) |
| `Test` | Test action (e.g., CodeBuild test) |
| `Invoke` | Invoke action (e.g., Lambda) |
| `Approval` | Manual approval action |

### Action Owner Values
| Owner | Description |
|-------|-------------|
| `AWS` | Built-in AWS action |
| `ThirdParty` | Third-party integration |
| `Custom` | Custom action type |

### Trigger Types
| Type | Description |
|------|-------------|
| `CreatePipeline` | Pipeline was just created |
| `StartPipelineExecution` | Manual start |
| `PollForSourceChanges` | Polling detected a change |
| `Webhook` | Webhook triggered |
| `CloudWatchEvent` | EventBridge rule triggered |
| `PutActionRevision` | Action revision was put |
| `WebhookV2` | Connections-based trigger |
| `ManualRollback` | Manual rollback triggered |
| `AutomatedRollback` | Automated rollback triggered |
