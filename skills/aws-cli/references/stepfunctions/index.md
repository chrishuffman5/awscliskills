# AWS CLI v2 — Step Functions Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/stepfunctions/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-state-machine` | State Machine | Create a new state machine |
| `delete-state-machine` | State Machine | Delete a state machine |
| `describe-state-machine` | State Machine | Get state machine details |
| `list-state-machines` | State Machine | List all state machines |
| `update-state-machine` | State Machine | Update state machine definition, role, or settings |
| `describe-state-machine-for-execution` | State Machine | Get the state machine definition used by a specific execution |
| `publish-state-machine-version` | State Machine | Publish a version of a state machine |
| `list-state-machine-versions` | State Machine | List published versions of a state machine |
| `create-state-machine-alias` | State Machine | Create an alias for a state machine |
| `delete-state-machine-alias` | State Machine | Delete a state machine alias |
| `describe-state-machine-alias` | State Machine | Describe a state machine alias |
| `list-state-machine-aliases` | State Machine | List aliases for a state machine |
| `update-state-machine-alias` | State Machine | Update a state machine alias |
| `start-execution` | Execution | Start a new execution |
| `start-sync-execution` | Execution | Start a synchronous Express execution |
| `stop-execution` | Execution | Stop a running execution |
| `describe-execution` | Execution | Get execution details |
| `list-executions` | Execution | List executions for a state machine |
| `get-execution-history` | Execution | Get event history for an execution |
| `redrive-execution` | Execution | Redrive a failed or timed-out execution |
| `create-activity` | Activity | Create an activity |
| `delete-activity` | Activity | Delete an activity |
| `describe-activity` | Activity | Get activity details |
| `list-activities` | Activity | List activities |
| `get-activity-task` | Activity | Get a task for an activity worker |
| `send-task-success` | Activity | Report task success |
| `send-task-failure` | Activity | Report task failure |
| `send-task-heartbeat` | Activity | Send a heartbeat for a task |
| `describe-map-run` | Map Run | Describe a Map Run |
| `list-map-runs` | Map Run | List Map Runs for an execution |
| `update-map-run` | Map Run | Update Map Run configuration |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |
| `validate-state-machine-definition` | Validation | Validate a state machine definition |

---

## Global Options

These options are available on ALL `aws stepfunctions` commands.

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

### State Machine Types
| Type | Description |
|------|-------------|
| `STANDARD` | Long-running workflows (up to 1 year), exactly-once execution, full history |
| `EXPRESS` | High-volume, short-duration (up to 5 minutes), at-least-once execution |

### Execution Status Values
| Status | Description |
|--------|-------------|
| `RUNNING` | Execution is currently in progress |
| `SUCCEEDED` | Execution completed successfully |
| `FAILED` | Execution failed |
| `TIMED_OUT` | Execution timed out |
| `ABORTED` | Execution was stopped |
| `PENDING_REDRIVE` | Execution is pending redrive |

### History Event Types (Common)
| Event Type | Description |
|------------|-------------|
| `ExecutionStarted` | Execution started |
| `ExecutionSucceeded` | Execution completed successfully |
| `ExecutionFailed` | Execution failed |
| `ExecutionAborted` | Execution was aborted |
| `ExecutionTimedOut` | Execution timed out |
| `TaskScheduled` | Task was scheduled |
| `TaskStarted` | Task started |
| `TaskSucceeded` | Task completed successfully |
| `TaskFailed` | Task failed |
| `TaskTimedOut` | Task timed out |
| `ChoiceStateEntered` | Choice state entered |
| `ParallelStateEntered` | Parallel state entered |
| `MapStateEntered` | Map state entered |
| `WaitStateEntered` | Wait state entered |
| `PassStateEntered` | Pass state entered |

### ARN Formats
```
State Machine:  arn:aws:states:<region>:<account>:stateMachine:<name>
Execution:      arn:aws:states:<region>:<account>:execution:<machine-name>:<execution-name>
Activity:       arn:aws:states:<region>:<account>:activity:<name>
```
