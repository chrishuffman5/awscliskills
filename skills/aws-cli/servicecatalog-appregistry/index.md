# Service Catalog AppRegistry — Quick Reference

## All Commands

| Command | Description |
|---------|-------------|
| `create-application` | Create a new application |
| `get-application` | Retrieve application details |
| `list-applications` | List all applications |
| `update-application` | Update an application |
| `delete-application` | Delete an application |
| `create-attribute-group` | Create a new attribute group |
| `get-attribute-group` | Retrieve attribute group details |
| `list-attribute-groups` | List all attribute groups |
| `update-attribute-group` | Update an attribute group |
| `delete-attribute-group` | Delete an attribute group |
| `list-attribute-groups-for-application` | List attribute groups for an application |
| `associate-attribute-group` | Associate an attribute group with an application |
| `disassociate-attribute-group` | Disassociate an attribute group from an application |
| `associate-resource` | Associate a resource with an application |
| `disassociate-resource` | Disassociate a resource from an application |
| `get-associated-resource` | Get details about an associated resource |
| `list-associated-attribute-groups` | List attribute groups associated with an application |
| `list-associated-resources` | List resources associated with an application |
| `sync-resource` | Synchronize a resource with its application |
| `get-configuration` | Get tag query configuration settings |
| `put-configuration` | Set tag query configuration settings |
| `tag-resource` | Add tags to a resource |
| `untag-resource` | Remove tags from a resource |
| `list-tags-for-resource` | List tags for a resource |

## Global Options

These options are available on ALL `aws servicecatalog-appregistry` commands.

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

### Resource Types
| Type | Description |
|------|-------------|
| `CFN_STACK` | AWS CloudFormation stack |
| `RESOURCE_TAG_VALUE` | Resource identified by tag value |

### Resource Group States
| State | Description |
|-------|-------------|
| `CREATING` | Resource group is being created |
| `CREATE_COMPLETE` | Resource group creation complete |
| `CREATE_FAILED` | Resource group creation failed |
| `UPDATING` | Resource group is being updated |
| `UPDATE_COMPLETE` | Resource group update complete |
| `UPDATE_FAILED` | Resource group update failed |

### Application Tag Options
| Option | Description |
|--------|-------------|
| `APPLY_APPLICATION_TAG` | Apply the application tag to the resource |
| `SKIP_APPLICATION_TAG` | Skip applying the application tag |
