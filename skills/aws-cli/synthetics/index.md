# AWS CLI v2 — CloudWatch Synthetics Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/synthetics/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-canary` | Canary | Create a new canary |
| `delete-canary` | Canary | Delete a canary |
| `get-canary` | Canary | Get details about a canary |
| `describe-canaries` | Canary | List all canaries with details |
| `update-canary` | Canary | Update a canary's configuration |
| `start-canary` | Canary | Start a canary to begin running on schedule |
| `stop-canary` | Canary | Stop a canary from running |
| `start-canary-dry-run` | Canary | Start a dry run of a canary |
| `get-canary-runs` | Canary | Get details about canary runs |
| `describe-canaries-last-run` | Canary | Get last run info for all canaries |
| `describe-runtime-versions` | Canary | List available canary runtime versions |
| `create-group` | Group | Create a canary group |
| `delete-group` | Group | Delete a canary group |
| `get-group` | Group | Get details about a group |
| `list-groups` | Group | List canary groups |
| `associate-resource` | Group | Associate a canary with a group |
| `disassociate-resource` | Group | Disassociate a canary from a group |
| `list-group-resources` | Group | List canaries in a group |
| `list-associated-groups` | Group | List groups a canary is associated with |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

---

## Global Options

These options are available on ALL `aws synthetics` commands.

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

### Canary States
| State | Description |
|-------|-------------|
| `CREATING` | Canary is being created |
| `READY` | Canary is ready to run |
| `STARTING` | Canary is starting |
| `RUNNING` | Canary is currently running |
| `UPDATING` | Canary is being updated |
| `STOPPING` | Canary is stopping |
| `STOPPED` | Canary is stopped |
| `ERROR` | Canary is in an error state |
| `DELETING` | Canary is being deleted |

### Canary Run States
| State | Description |
|-------|-------------|
| `RUNNING` | Run is in progress |
| `PASSED` | Run completed successfully |
| `FAILED` | Run failed |

### Canary Run State Reason Codes
| Code | Description |
|------|-------------|
| `CANARY_FAILURE` | The canary script failed |
| `EXECUTION_FAILURE` | Infrastructure failure during execution |

### Runtime Versions
Canary runtime versions follow the pattern `syn-<runtime>-<version>` (e.g., `syn-nodejs-puppeteer-9.0`, `syn-python-selenium-4.0`).
