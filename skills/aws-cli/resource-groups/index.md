# AWS CLI v2 -- Resource Groups Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/resource-groups/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-group` | Group | Create a resource group |
| `get-group` | Group | Get details of a resource group |
| `list-groups` | Group | List all resource groups |
| `update-group` | Group | Update a resource group |
| `delete-group` | Group | Delete a resource group |
| `list-group-resources` | Group | List resources in a group |
| `get-group-query` | Query | Get the resource query for a group |
| `update-group-query` | Query | Update the resource query for a group |
| `search-resources` | Query | Search for resources matching a query |
| `get-group-configuration` | Configuration | Get the service configuration for a group |
| `put-group-configuration` | Configuration | Set the service configuration for a group |
| `group-resources` | Configuration | Add resources to a group manually |
| `ungroup-resources` | Configuration | Remove resources from a group manually |
| `list-grouping-statuses` | Configuration | List status of grouping/ungrouping requests |
| `start-tag-sync-task` | Tag Sync | Start a tag sync task |
| `get-tag-sync-task` | Tag Sync | Get tag sync task details |
| `list-tag-sync-tasks` | Tag Sync | List tag sync tasks |
| `cancel-tag-sync-task` | Tag Sync | Cancel a tag sync task |
| `tag` | Tags | Add tags to a resource group |
| `untag` | Tags | Remove tags from a resource group |
| `get-tags` | Tags | Get tags for a resource group |
| `get-account-settings` | Settings | Get account-level resource group settings |
| `update-account-settings` | Settings | Update account-level resource group settings |

---

## Global Options

These options are available on ALL `aws resource-groups` commands.

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

### Query Types
| Type | Description |
|------|-------------|
| `TAG_FILTERS_1_0` | Tag-based resource query |
| `CLOUDFORMATION_STACK_1_0` | CloudFormation stack-based query |

### Group Types
| Type | Description |
|------|-------------|
| `AWS::ResourceGroups::Generic` | Standard resource group (tag or stack based) |
| `AWS::EC2::HostManagement` | Dedicated Host management group |
| `AWS::EC2::CapacityReservationPool` | Capacity reservation pool |
| `AWS::CloudFormation::Stack` | CloudFormation stack-based group |

### Resource Status Values
| Status | Description |
|--------|-------------|
| `PENDING` | Resource is pending addition to the group |

### Tag Sync Task Statuses
| Status | Description |
|--------|-------------|
| `ACTIVE` | Tag sync task is running |
| `ERROR` | Tag sync task encountered an error |

### Group Configuration Types
Groups can be configured for specific AWS services. Common configuration types include:
- `AWS::EC2::HostManagement` - Dedicated Host management
- `AWS::EC2::CapacityReservationPool` - Capacity reservation pools
- `AWS::ResourceGroups::Generic` - Generic resource grouping
- `AWS::NetworkFirewall::RuleGroup` - Network Firewall rule groups
