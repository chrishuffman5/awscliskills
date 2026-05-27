# SWF — Quick Reference

## All Commands

| Command | Description |
|---------|-------------|
| `register-domain` | Register a new SWF domain |
| `describe-domain` | Describe a domain |
| `list-domains` | List domains by registration status |
| `deprecate-domain` | Deprecate a domain |
| `undeprecate-domain` | Undeprecate a domain |
| `register-workflow-type` | Register a new workflow type |
| `describe-workflow-type` | Describe a workflow type |
| `list-workflow-types` | List workflow types |
| `deprecate-workflow-type` | Deprecate a workflow type |
| `undeprecate-workflow-type` | Undeprecate a workflow type |
| `delete-workflow-type` | Delete a workflow type |
| `register-activity-type` | Register a new activity type |
| `describe-activity-type` | Describe an activity type |
| `list-activity-types` | List activity types |
| `deprecate-activity-type` | Deprecate an activity type |
| `undeprecate-activity-type` | Undeprecate an activity type |
| `delete-activity-type` | Delete an activity type |
| `start-workflow-execution` | Start a new workflow execution |
| `describe-workflow-execution` | Describe a workflow execution |
| `get-workflow-execution-history` | Get history events for a workflow execution |
| `list-open-workflow-executions` | List open workflow executions |
| `list-closed-workflow-executions` | List closed workflow executions |
| `request-cancel-workflow-execution` | Request cancellation of a workflow execution |
| `signal-workflow-execution` | Send a signal to a workflow execution |
| `terminate-workflow-execution` | Terminate a workflow execution |
| `poll-for-activity-task` | Poll for an activity task |
| `record-activity-task-heartbeat` | Record activity task heartbeat |
| `respond-activity-task-completed` | Report activity task completed |
| `respond-activity-task-failed` | Report activity task failed |
| `respond-activity-task-canceled` | Report activity task canceled |
| `poll-for-decision-task` | Poll for a decision task |
| `respond-decision-task-completed` | Report decision task completed with decisions |
| `count-open-workflow-executions` | Count open workflow executions |
| `count-closed-workflow-executions` | Count closed workflow executions |
| `count-pending-activity-tasks` | Count pending activity tasks in a task list |
| `count-pending-decision-tasks` | Count pending decision tasks in a task list |
| `tag-resource` | Add tags to a resource |
| `untag-resource` | Remove tags from a resource |
| `list-tags-for-resource` | List tags for a resource |

## Global Options

These options are available on ALL `aws swf` commands.

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

## Common Patterns

### Execution Status Values
| Status | Description |
|--------|-------------|
| `OPEN` | Workflow execution is currently running |
| `CLOSED` | Workflow execution has completed |

### Close Status Values
| Status | Description |
|--------|-------------|
| `COMPLETED` | Execution completed successfully |
| `FAILED` | Execution failed |
| `CANCELED` | Execution was canceled |
| `TERMINATED` | Execution was terminated |
| `CONTINUED_AS_NEW` | Execution continued as new |
| `TIMED_OUT` | Execution timed out |

### Child Policy Values
| Policy | Description |
|--------|-------------|
| `TERMINATE` | Terminate child workflow executions |
| `REQUEST_CANCEL` | Request cancellation of child executions |
| `ABANDON` | Abandon child executions (no action) |

### Registration Status Values
| Status | Description |
|--------|-------------|
| `REGISTERED` | Active and available for use |
| `DEPRECATED` | Still accessible but no new executions can be started |
