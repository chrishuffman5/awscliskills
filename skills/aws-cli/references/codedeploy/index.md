# AWS CLI v2 -- CodeDeploy Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/deploy/
>
> **Note:** The CLI service command is `aws deploy`, not `aws codedeploy`.

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-application` | Application | Create a new application |
| `delete-application` | Application | Delete an application |
| `get-application` | Application | Get information about an application |
| `list-applications` | Application | List application names |
| `update-application` | Application | Change an application name |
| `batch-get-applications` | Application | Get information about multiple applications |
| `create-deployment-group` | Deployment Group | Create a deployment group |
| `delete-deployment-group` | Deployment Group | Delete a deployment group |
| `get-deployment-group` | Deployment Group | Get information about a deployment group |
| `list-deployment-groups` | Deployment Group | List deployment groups for an application |
| `update-deployment-group` | Deployment Group | Update a deployment group |
| `batch-get-deployment-groups` | Deployment Group | Get information about multiple deployment groups |
| `create-deployment` | Deployment | Create a deployment |
| `get-deployment` | Deployment | Get information about a deployment |
| `list-deployments` | Deployment | List deployment IDs |
| `stop-deployment` | Deployment | Stop a deployment |
| `batch-get-deployments` | Deployment | Get information about multiple deployments |
| `continue-deployment` | Deployment | Continue a blue/green deployment |
| `create-deployment-config` | Deployment Config | Create a deployment configuration |
| `delete-deployment-config` | Deployment Config | Delete a deployment configuration |
| `get-deployment-config` | Deployment Config | Get information about a deployment configuration |
| `list-deployment-configs` | Deployment Config | List deployment configurations |
| `register-application-revision` | Revision | Register an application revision |
| `get-application-revision` | Revision | Get information about an application revision |
| `list-application-revisions` | Revision | List application revisions |
| `batch-get-application-revisions` | Revision | Get information about multiple application revisions |
| `register-on-premises-instance` | Instance | Register an on-premises instance |
| `deregister-on-premises-instance` | Instance | Deregister an on-premises instance |
| `get-on-premises-instance` | Instance | Get information about an on-premises instance |
| `list-on-premises-instances` | Instance | List on-premises instances |
| `batch-get-on-premises-instances` | Instance | Get information about multiple on-premises instances |
| `add-tags-to-on-premises-instances` | Instance | Add tags to on-premises instances |
| `remove-tags-from-on-premises-instances` | Instance | Remove tags from on-premises instances |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

---

## Global Options

These options are available on ALL `aws deploy` commands.

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

### Compute Platforms
| Platform | Description |
|----------|-------------|
| `Server` | EC2/on-premises instances |
| `Lambda` | AWS Lambda functions |
| `ECS` | Amazon ECS services |

### Deployment Status Values
| Status | Description |
|--------|-------------|
| `Created` | Deployment created but not started |
| `Queued` | Deployment is queued |
| `InProgress` | Deployment is in progress |
| `Baking` | Deployment is in the baking period (waiting after rerouting traffic) |
| `Succeeded` | Deployment completed successfully |
| `Failed` | Deployment failed |
| `Stopped` | Deployment was stopped |
| `Ready` | Replacement environment ready (blue/green) |

### Deployment Types
| Type | Description |
|------|-------------|
| `IN_PLACE` | Application on existing instances is stopped, new revision installed |
| `BLUE_GREEN` | Traffic shifted from original to replacement environment |

### Built-in Deployment Configurations
| Config Name | Description |
|-------------|-------------|
| `CodeDeployDefault.OneAtATime` | Deploy one instance at a time |
| `CodeDeployDefault.HalfAtATime` | Deploy to half the instances at a time |
| `CodeDeployDefault.AllAtOnce` | Deploy to all instances simultaneously |
| `CodeDeployDefault.ECSLinear10PercentEvery1Minutes` | Shift 10% of traffic every 1 minute |
| `CodeDeployDefault.ECSLinear10PercentEvery3Minutes` | Shift 10% of traffic every 3 minutes |
| `CodeDeployDefault.ECSCanary10Percent5Minutes` | Shift 10% first, then remaining after 5 minutes |
| `CodeDeployDefault.ECSCanary10Percent15Minutes` | Shift 10% first, then remaining after 15 minutes |
| `CodeDeployDefault.ECSAllAtOnce` | Shift all traffic at once (ECS) |
| `CodeDeployDefault.LambdaLinear10PercentEvery1Minute` | Shift 10% of traffic every 1 minute (Lambda) |
| `CodeDeployDefault.LambdaLinear10PercentEvery2Minutes` | Shift 10% of traffic every 2 minutes (Lambda) |
| `CodeDeployDefault.LambdaLinear10PercentEvery3Minutes` | Shift 10% of traffic every 3 minutes (Lambda) |
| `CodeDeployDefault.LambdaLinear10PercentEvery10Minutes` | Shift 10% of traffic every 10 minutes (Lambda) |
| `CodeDeployDefault.LambdaCanary10Percent5Minutes` | Shift 10% first, then remaining after 5 minutes (Lambda) |
| `CodeDeployDefault.LambdaCanary10Percent10Minutes` | Shift 10% first, then remaining after 10 minutes (Lambda) |
| `CodeDeployDefault.LambdaCanary10Percent15Minutes` | Shift 10% first, then remaining after 15 minutes (Lambda) |
| `CodeDeployDefault.LambdaCanary10Percent30Minutes` | Shift 10% first, then remaining after 30 minutes (Lambda) |
| `CodeDeployDefault.LambdaAllAtOnce` | Shift all traffic at once (Lambda) |

### Bundle Types
| Type | Description |
|------|-------------|
| `tar` | TAR archive |
| `tgz` | Gzipped TAR archive |
| `zip` | ZIP archive |
| `YAML` | YAML AppSpec file |
| `JSON` | JSON AppSpec file |

### Wait Commands
| Waiter | Description |
|--------|-------------|
| `deployment-successful` | Wait until a deployment completes successfully |

```bash
aws deploy wait deployment-successful --deployment-id d-XXXXXXXXX
```
