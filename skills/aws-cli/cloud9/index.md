# AWS CLI v2 — Cloud9 Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/cloud9/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-environment-ec2` | Environment | Create an EC2-backed Cloud9 development environment |
| `delete-environment` | Environment | Delete a Cloud9 development environment |
| `describe-environments` | Environment | Describe one or more environments |
| `list-environments` | Environment | List environment identifiers |
| `update-environment` | Environment | Update an environment's settings |
| `describe-environment-status` | Environment | Get the status of an environment |
| `create-environment-membership` | Membership | Add a member to an environment |
| `delete-environment-membership` | Membership | Remove a member from an environment |
| `describe-environment-memberships` | Membership | List environment members |
| `update-environment-membership` | Membership | Update a member's permissions |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

---

## Global Options

These options are available on ALL `aws cloud9` commands.

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

### Environment Types
| Type | Description |
|------|-------------|
| `ec2` | Environment backed by an Amazon EC2 instance |
| `ssh` | Environment backed by a customer-managed server (SSH) |

### Environment Statuses
| Status | Description |
|--------|-------------|
| `error` | Environment is in an error state |
| `creating` | Environment is being created |
| `connecting` | Environment is connecting |
| `ready` | Environment is ready to use |
| `stopping` | Environment is stopping |
| `stopped` | Environment is stopped |
| `deleting` | Environment is being deleted |

### Environment Lifecycle Statuses
| Status | Description |
|--------|-------------|
| `CREATING` | Environment is being created |
| `CREATED` | Environment has been created |
| `CREATE_FAILED` | Environment creation failed |
| `DELETING` | Environment is being deleted |
| `DELETE_FAILED` | Environment deletion failed |

### Membership Permissions
| Permission | Description |
|------------|-------------|
| `read-write` | Member can read and write files |
| `read-only` | Member can only read files |
| `owner` | Environment owner (full access) |
