# AWS CLI v2 -- FIS (Fault Injection Service) Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/fis/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-experiment-template` | Experiment Template | Create a new experiment template |
| `delete-experiment-template` | Experiment Template | Delete an experiment template |
| `get-experiment-template` | Experiment Template | Get details of an experiment template |
| `list-experiment-templates` | Experiment Template | List experiment templates |
| `update-experiment-template` | Experiment Template | Update an experiment template |
| `start-experiment` | Experiment | Start an experiment from a template |
| `stop-experiment` | Experiment | Stop a running experiment |
| `get-experiment` | Experiment | Get details of an experiment |
| `list-experiments` | Experiment | List experiments |
| `list-experiment-resolved-targets` | Experiment | List resolved targets for an experiment |
| `get-action` | Action | Get details of an FIS action |
| `list-actions` | Action | List available FIS actions |
| `get-target-resource-type` | Resource Type | Get details of a target resource type |
| `list-target-resource-types` | Resource Type | List available target resource types |
| `create-target-account-configuration` | Target Account | Create a target account configuration |
| `delete-target-account-configuration` | Target Account | Delete a target account configuration |
| `get-target-account-configuration` | Target Account | Get a target account configuration |
| `list-target-account-configurations` | Target Account | List target account configurations |
| `update-target-account-configuration` | Target Account | Update a target account configuration |
| `get-experiment-target-account-configuration` | Target Account | Get target account config for an experiment |
| `list-experiment-target-account-configurations` | Target Account | List target account configs for an experiment |
| `get-safety-lever` | Safety | Get state of a safety lever |
| `update-safety-lever-state` | Safety | Update the state of a safety lever |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

---

## Global Options

These options are available on ALL `aws fis` commands.

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

### Experiment States
| State | Description |
|-------|-------------|
| `pending` | Experiment has been created |
| `initiating` | Experiment is starting |
| `running` | Experiment is in progress |
| `completed` | Experiment completed successfully |
| `stopping` | Experiment is stopping |
| `stopped` | Experiment was stopped |
| `failed` | Experiment failed |

### Selection Modes
| Mode | Description |
|------|-------------|
| `ALL` | Select all matching targets |
| `COUNT(n)` | Select n random targets |
| `PERCENT(n)` | Select n% of targets |

### Common Action IDs
| Action | Description |
|--------|-------------|
| `aws:ec2:stop-instances` | Stop EC2 instances |
| `aws:ec2:terminate-instances` | Terminate EC2 instances |
| `aws:ec2:reboot-instances` | Reboot EC2 instances |
| `aws:ecs:drain-container-instances` | Drain ECS container instances |
| `aws:ecs:stop-task` | Stop ECS tasks |
| `aws:eks:terminate-nodegroup-instances` | Terminate EKS node group instances |
| `aws:rds:reboot-db-instances` | Reboot RDS instances |
| `aws:rds:failover-db-cluster` | Failover RDS cluster |
| `aws:ssm:send-command` | Run SSM document on targets |
| `aws:network:disrupt-connectivity` | Disrupt network connectivity |
| `aws:fis:inject-api-internal-error` | Inject internal API errors |
| `aws:fis:inject-api-throttle-error` | Inject API throttle errors |
| `aws:fis:inject-api-unavailable-error` | Inject API unavailable errors |
| `aws:fis:wait` | Wait for a duration |

### Stop Condition Sources
| Source | Description |
|--------|-------------|
| `none` | No stop condition |
| `aws:cloudwatch:alarm` | Stop when CloudWatch alarm triggers |

### Safety Lever States
| State | Description |
|-------|-------------|
| `disengaged` | Safety lever is off (experiments can run normally) |
| `engaged` | Safety lever is on (all running experiments stop) |
