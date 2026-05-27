# AWS CLI v2 -- Proton Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/proton/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-environment` | Environment | Create a new Proton environment |
| `update-environment` | Environment | Update an environment |
| `delete-environment` | Environment | Delete an environment |
| `get-environment` | Environment | Get environment details |
| `list-environments` | Environment | List environments |
| `cancel-environment-deployment` | Environment | Cancel an in-progress environment deployment |
| `list-environment-outputs` | Environment | List environment outputs |
| `list-environment-provisioned-resources` | Environment | List provisioned resources |
| `create-environment-template` | Env Template | Create an environment template |
| `update-environment-template` | Env Template | Update an environment template |
| `delete-environment-template` | Env Template | Delete an environment template |
| `get-environment-template` | Env Template | Get environment template details |
| `list-environment-templates` | Env Template | List environment templates |
| `create-environment-template-version` | Env Template | Create a template version |
| `update-environment-template-version` | Env Template | Update a template version |
| `delete-environment-template-version` | Env Template | Delete a template version |
| `get-environment-template-version` | Env Template | Get template version details |
| `list-environment-template-versions` | Env Template | List template versions |
| `create-service` | Service | Create a Proton service |
| `update-service` | Service | Update a service |
| `delete-service` | Service | Delete a service |
| `get-service` | Service | Get service details |
| `list-services` | Service | List services |
| `update-service-instance` | Service Instance | Update a service instance |
| `get-service-instance` | Service Instance | Get service instance details |
| `list-service-instances` | Service Instance | List service instances |
| `list-service-instance-outputs` | Service Instance | List instance outputs |
| `list-service-instance-provisioned-resources` | Service Instance | List provisioned resources |
| `create-service-template` | Svc Template | Create a service template |
| `update-service-template` | Svc Template | Update a service template |
| `delete-service-template` | Svc Template | Delete a service template |
| `get-service-template` | Svc Template | Get service template details |
| `list-service-templates` | Svc Template | List service templates |
| `create-service-template-version` | Svc Template | Create a template version |
| `update-service-template-version` | Svc Template | Update a template version |
| `delete-service-template-version` | Svc Template | Delete a template version |
| `get-service-template-version` | Svc Template | Get template version details |
| `list-service-template-versions` | Svc Template | List template versions |
| `create-component` | Component | Create a component |
| `update-component` | Component | Update a component |
| `delete-component` | Component | Delete a component |
| `get-component` | Component | Get component details |
| `list-components` | Component | List components |
| `cancel-component-deployment` | Component | Cancel a component deployment |
| `list-component-outputs` | Component | List component outputs |
| `list-component-provisioned-resources` | Component | List provisioned resources |
| `create-environment-account-connection` | Account | Create account connection |
| `update-environment-account-connection` | Account | Update account connection |
| `delete-environment-account-connection` | Account | Delete account connection |
| `get-environment-account-connection` | Account | Get account connection details |
| `list-environment-account-connections` | Account | List account connections |
| `accept-environment-account-connection` | Account | Accept account connection |
| `reject-environment-account-connection` | Account | Reject account connection |
| `create-repository` | Repository | Link a repository |
| `delete-repository` | Repository | Unlink a repository |
| `get-repository` | Repository | Get repository details |
| `list-repositories` | Repository | List repositories |
| `get-repository-sync-status` | Sync | Get sync status |
| `create-template-sync-config` | Sync | Create template sync config |
| `update-template-sync-config` | Sync | Update template sync config |
| `delete-template-sync-config` | Sync | Delete template sync config |
| `get-template-sync-config` | Sync | Get template sync config |
| `get-template-sync-status` | Sync | Get template sync status |
| `create-service-sync-config` | Sync | Create service sync config |
| `update-service-sync-config` | Sync | Update service sync config |
| `delete-service-sync-config` | Sync | Delete service sync config |
| `get-service-sync-config` | Sync | Get service sync config |
| `get-service-sync-blocker-summary` | Sync | Get sync blocker summary |
| `notify-resource-deployment-status-change` | Sync | Notify deployment status change |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

---

## Global Options

These options are available on ALL `aws proton` commands.

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

### Deployment Status Values
| Status | Description |
|--------|-------------|
| `IN_PROGRESS` | Deployment in progress |
| `FAILED` | Deployment failed |
| `SUCCEEDED` | Deployment succeeded |
| `DELETE_IN_PROGRESS` | Deletion in progress |
| `DELETE_FAILED` | Deletion failed |
| `DELETE_COMPLETE` | Deletion completed |
| `CANCELLING` | Deployment cancellation in progress |
| `CANCELLED` | Deployment cancelled |

### Template Version Status Values
| Status | Description |
|--------|-------------|
| `REGISTRATION_IN_PROGRESS` | Template version registration in progress |
| `REGISTRATION_FAILED` | Registration failed |
| `DRAFT` | Template version is a draft |
| `PUBLISHED` | Template version is published |

### Deployment Types
| Type | Description |
|------|-------------|
| `NONE` | No deployment |
| `CURRENT_VERSION` | Deploy with current template version |
| `MINOR_VERSION` | Deploy with latest minor version |
| `MAJOR_VERSION` | Deploy with latest major version |

### Wait Commands
| Waiter | Description |
|--------|-------------|
| `environment-deployed` | Wait until environment deployment completes |
| `environment-template-version-registered` | Wait until template version is registered |
| `service-created` | Wait until service is created |
| `service-deleted` | Wait until service is deleted |
| `service-updated` | Wait until service is updated |
| `service-instance-deployed` | Wait until service instance deployment completes |
| `service-pipeline-deployed` | Wait until service pipeline deployment completes |
| `service-template-version-registered` | Wait until service template version is registered |
| `component-deployed` | Wait until component deployment completes |
| `component-deleted` | Wait until component is deleted |
