# AWS CLI v2 -- Auto Scaling Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/autoscaling/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-auto-scaling-group` | Group | Create a new Auto Scaling group |
| `update-auto-scaling-group` | Group | Update an Auto Scaling group |
| `delete-auto-scaling-group` | Group | Delete an Auto Scaling group |
| `describe-auto-scaling-groups` | Group | Describe Auto Scaling groups |
| `set-desired-capacity` | Group | Set the desired capacity of a group |
| `attach-instances` | Group | Attach instances to a group |
| `detach-instances` | Group | Detach instances from a group |
| `enter-standby` | Group | Move instances into standby |
| `exit-standby` | Group | Move instances out of standby |
| `set-instance-protection` | Group | Set instance scale-in protection |
| `terminate-instance-in-auto-scaling-group` | Group | Terminate a specific instance |
| `set-instance-health` | Group | Set instance health status |
| `describe-auto-scaling-instances` | Group | Describe instances in Auto Scaling groups |
| `describe-scaling-activities` | Group | Describe scaling activities |
| `describe-adjustment-types` | Group | List available adjustment types |
| `create-launch-configuration` | Launch Config | Create a launch configuration |
| `delete-launch-configuration` | Launch Config | Delete a launch configuration |
| `describe-launch-configurations` | Launch Config | Describe launch configurations |
| `put-scaling-policy` | Scaling Policy | Create or update a scaling policy |
| `delete-policy` | Scaling Policy | Delete a scaling policy |
| `describe-policies` | Scaling Policy | Describe scaling policies |
| `execute-policy` | Scaling Policy | Execute a scaling policy |
| `describe-scaling-process-types` | Scaling Policy | List scaling process types |
| `suspend-processes` | Scaling Policy | Suspend scaling processes |
| `resume-processes` | Scaling Policy | Resume scaling processes |
| `put-lifecycle-hook` | Lifecycle Hook | Create or update a lifecycle hook |
| `delete-lifecycle-hook` | Lifecycle Hook | Delete a lifecycle hook |
| `describe-lifecycle-hooks` | Lifecycle Hook | Describe lifecycle hooks |
| `describe-lifecycle-hook-types` | Lifecycle Hook | List lifecycle hook types |
| `complete-lifecycle-action` | Lifecycle Hook | Complete a lifecycle action |
| `record-lifecycle-action-heartbeat` | Lifecycle Hook | Record a lifecycle action heartbeat |
| `put-scheduled-update-group-action` | Scheduled Action | Create or update a scheduled action |
| `delete-scheduled-action` | Scheduled Action | Delete a scheduled action |
| `describe-scheduled-actions` | Scheduled Action | Describe scheduled actions |
| `batch-put-scheduled-update-group-action` | Scheduled Action | Create or update multiple scheduled actions |
| `batch-delete-scheduled-action` | Scheduled Action | Delete multiple scheduled actions |
| `start-instance-refresh` | Instance Refresh | Start an instance refresh |
| `cancel-instance-refresh` | Instance Refresh | Cancel an instance refresh |
| `describe-instance-refreshes` | Instance Refresh | Describe instance refreshes |
| `rollback-instance-refresh` | Instance Refresh | Rollback an instance refresh |
| `put-warm-pool` | Warm Pool | Create or update a warm pool |
| `delete-warm-pool` | Warm Pool | Delete a warm pool |
| `describe-warm-pool` | Warm Pool | Describe a warm pool |
| `attach-load-balancers` | Load Balancer | Attach Classic Load Balancers |
| `detach-load-balancers` | Load Balancer | Detach Classic Load Balancers |
| `describe-load-balancers` | Load Balancer | Describe attached Classic Load Balancers |
| `attach-load-balancer-target-groups` | Load Balancer | Attach ALB/NLB target groups |
| `detach-load-balancer-target-groups` | Load Balancer | Detach ALB/NLB target groups |
| `describe-load-balancer-target-groups` | Load Balancer | Describe attached target groups |
| `attach-traffic-sources` | Load Balancer | Attach traffic sources |
| `detach-traffic-sources` | Load Balancer | Detach traffic sources |
| `describe-traffic-sources` | Load Balancer | Describe traffic sources |
| `put-notification-configuration` | Notification | Create or update notification config |
| `delete-notification-configuration` | Notification | Delete notification config |
| `describe-notification-configurations` | Notification | Describe notification configs |
| `enable-metrics-collection` | Metrics | Enable group metrics collection |
| `disable-metrics-collection` | Metrics | Disable group metrics collection |
| `describe-metric-collection-types` | Metrics | List available metrics |
| `describe-account-limits` | Account | Describe account-level limits |
| `create-or-update-tags` | Tags | Create or update tags |
| `delete-tags` | Tags | Delete tags |
| `describe-tags` | Tags | Describe tags |

---

## Global Options

These options are available on ALL `aws autoscaling` commands.

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

### Auto Scaling Group Health Check Types
| Type | Description |
|------|-------------|
| `EC2` | Uses EC2 instance status checks |
| `ELB` | Uses Elastic Load Balancer health checks |
| `VPC_LATTICE` | Uses VPC Lattice target group health checks |

### Scaling Policy Types
| Type | Description |
|------|-------------|
| `TargetTrackingScaling` | Adjusts capacity to maintain a target metric value |
| `StepScaling` | Adjusts capacity in steps based on alarm breaches |
| `SimpleScaling` | Adjusts capacity by a fixed amount with a cooldown |
| `PredictiveScaling` | Uses machine learning to forecast and schedule capacity |

### Instance Lifecycle States
| State | Description |
|-------|-------------|
| `Pending` | Instance is launching |
| `Pending:Wait` | Instance is waiting for lifecycle hook |
| `Pending:Proceed` | Instance is proceeding from lifecycle hook |
| `InService` | Instance is in service |
| `Terminating` | Instance is terminating |
| `Terminating:Wait` | Instance is waiting for lifecycle hook |
| `Terminating:Proceed` | Instance is proceeding from lifecycle hook |
| `Terminated` | Instance has been terminated |
| `Detaching` | Instance is being detached |
| `Detached` | Instance has been detached |
| `EnteringStandby` | Instance is entering standby |
| `Standby` | Instance is in standby |
| `Warmed:Pending` | Warm pool instance is pending |
| `Warmed:Pending:Wait` | Warm pool instance waiting for hook |
| `Warmed:Pending:Proceed` | Warm pool instance proceeding |
| `Warmed:Running` | Warm pool instance running |
| `Warmed:Stopped` | Warm pool instance stopped |
| `Warmed:Terminated` | Warm pool instance terminated |
| `Warmed:Hibernated` | Warm pool instance hibernated |

### Scaling Process Types
| Process | Description |
|---------|-------------|
| `Launch` | Launching new instances |
| `Terminate` | Terminating instances |
| `AddToLoadBalancer` | Adding instances to load balancer |
| `AlarmNotification` | Processing CloudWatch alarm notifications |
| `AZRebalance` | Rebalancing across Availability Zones |
| `HealthCheck` | Health check process |
| `InstanceRefresh` | Instance refresh process |
| `ReplaceUnhealthy` | Replacing unhealthy instances |
| `ScheduledActions` | Processing scheduled actions |

### Adjustment Types
| Type | Description |
|------|-------------|
| `ChangeInCapacity` | Increase or decrease by a specified number |
| `ExactCapacity` | Set capacity to a specified number |
| `PercentChangeInCapacity` | Increase or decrease by a percentage |
