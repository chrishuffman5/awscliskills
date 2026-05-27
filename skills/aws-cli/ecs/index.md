# AWS CLI v2 -- ECS (Elastic Container Service) Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/ecs/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-cluster` | Cluster | Create a new ECS cluster |
| `delete-cluster` | Cluster | Delete an ECS cluster |
| `describe-clusters` | Cluster | Describe one or more clusters |
| `list-clusters` | Cluster | List all clusters in an account |
| `update-cluster` | Cluster | Update cluster configuration |
| `update-cluster-settings` | Cluster | Modify cluster settings (Container Insights) |
| `put-cluster-capacity-providers` | Cluster | Associate capacity providers with a cluster |
| `create-service` | Service | Create a new ECS service |
| `delete-service` | Service | Delete an ECS service |
| `describe-services` | Service | Describe one or more services |
| `list-services` | Service | List services in a cluster |
| `update-service` | Service | Update service configuration |
| `update-service-primary-task-set` | Service | Set the primary task set for a service |
| `run-task` | Task | Run a new task from a task definition |
| `start-task` | Task | Start a task on a specific container instance |
| `stop-task` | Task | Stop a running task |
| `describe-tasks` | Task | Describe one or more tasks |
| `list-tasks` | Task | List tasks in a cluster |
| `register-task-definition` | Task Definition | Register a new task definition |
| `deregister-task-definition` | Task Definition | Deregister a task definition revision |
| `describe-task-definition` | Task Definition | Describe a task definition |
| `list-task-definitions` | Task Definition | List task definition revisions |
| `list-task-definition-families` | Task Definition | List task definition family names |
| `delete-task-definitions` | Task Definition | Delete one or more task definition revisions |
| `register-container-instance` | Container Instance | Register an EC2 instance with a cluster |
| `deregister-container-instance` | Container Instance | Deregister a container instance |
| `describe-container-instances` | Container Instance | Describe container instances |
| `list-container-instances` | Container Instance | List container instances in a cluster |
| `update-container-instances-state` | Container Instance | Update container instance state (DRAINING) |
| `update-container-agent` | Container Instance | Update the ECS container agent |
| `create-capacity-provider` | Capacity Provider | Create a capacity provider |
| `delete-capacity-provider` | Capacity Provider | Delete a capacity provider |
| `describe-capacity-providers` | Capacity Provider | Describe capacity providers |
| `update-capacity-provider` | Capacity Provider | Update a capacity provider |
| `create-task-set` | Task Set | Create a task set in a service |
| `delete-task-set` | Task Set | Delete a task set |
| `describe-task-sets` | Task Set | Describe task sets |
| `update-task-set` | Task Set | Update task set scale |
| `list-account-settings` | Account Settings | List account settings |
| `put-account-setting` | Account Settings | Set an account setting for a principal |
| `put-account-setting-default` | Account Settings | Set the default account setting |
| `delete-account-setting` | Account Settings | Delete an account setting |
| `describe-service-deployments` | Service Deployment | Describe service deployments |
| `list-service-deployments` | Service Deployment | List service deployments |
| `describe-service-revisions` | Service Deployment | Describe service revisions |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |
| `put-attributes` | Attributes | Add custom attributes to resources |
| `delete-attributes` | Attributes | Delete custom attributes |
| `list-attributes` | Attributes | List attributes for resources |
| `execute-command` | Execute Command | Execute a command in a running container |
| `get-task-protection` | Task Protection | Get task scale-in protection |
| `update-task-protection` | Task Protection | Update task scale-in protection |
| `list-services-by-namespace` | Service | List services by Cloud Map namespace |
| `discover-poll-endpoint` | Internal | Discover the poll endpoint for ECS agent |

---

## Global Options

These options are available on ALL `aws ecs` commands.

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

### Cluster Name Constraints
- **Length:** Up to 255 characters
- **Pattern:** Letters (uppercase and lowercase), numbers, hyphens, underscores
- Defaults to `default` if not specified

### Container Instance Status Values
| Status | Description |
|--------|-------------|
| `REGISTERING` | Instance is being registered with the cluster |
| `REGISTRATION_FAILED` | Registration failed |
| `ACTIVE` | Instance is accepting task placements |
| `INACTIVE` | Instance has been deregistered |
| `DEREGISTERING` | Instance is being deregistered |
| `DRAINING` | Instance will not accept new task placements; existing tasks are being drained |

### Task Stop Codes
| Code | Description |
|------|-------------|
| `TaskFailedToStart` | Task could not start |
| `EssentialContainerExited` | An essential container exited |
| `UserInitiated` | Task was stopped by a user |
| `ServiceSchedulerInitiated` | Service scheduler stopped the task |
| `SpotInterruption` | Spot Instance was interrupted |
| `TerminationNotice` | Instance is being terminated |

### Failure Structure
All describe/batch operations return a `failures` array for resources that could not be processed:
```json
{
    "arn": "string",
    "reason": "string",
    "detail": "string"
}
```

Common `reason` values: `MISSING`, `AGENT_NOT_CONNECTED`, `ATTRIBUTE`.

### Service Deployment Statuses
| Status | Description |
|--------|-------------|
| `PENDING` | Deployment has been created but not started |
| `IN_PROGRESS` | Deployment is actively rolling out |
| `SUCCESSFUL` | Deployment completed successfully |
| `STOPPED` | Deployment was stopped |
| `STOP_REQUESTED` | A stop has been requested |
| `ROLLBACK_IN_PROGRESS` | Deployment is rolling back |
| `ROLLBACK_SUCCESSFUL` | Rollback completed successfully |
| `ROLLBACK_FAILED` | Rollback failed |

### Wait Commands
The `aws ecs wait` subcommand blocks until a resource reaches a specific state:

| Waiter | Description |
|--------|-------------|
| `services-stable` | Wait until service deployments are stable |
| `services-inactive` | Wait until services are inactive |
| `tasks-running` | Wait until tasks are running |
| `tasks-stopped` | Wait until tasks are stopped |

```bash
aws ecs wait services-stable --cluster my-cluster --services my-service
aws ecs wait tasks-running --cluster my-cluster --tasks task-id
```
