# AWS CLI v2 -- MWAA (Managed Workflows for Apache Airflow) Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/mwaa/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-environment` | Environment | Create a new MWAA environment |
| `get-environment` | Environment | Get details about an environment |
| `update-environment` | Environment | Update an existing environment |
| `delete-environment` | Environment | Delete an environment |
| `list-environments` | Environment | List all environments in a region |
| `create-cli-token` | Access | Create a CLI token for Airflow CLI access |
| `create-web-login-token` | Access | Create a web login token for Airflow UI |
| `invoke-rest-api` | Access | Invoke the Apache Airflow REST API |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

---

## Global Options

These options are available on ALL `aws mwaa` commands.

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

### Environment Name Constraints
- **Length:** 1-80 characters
- **Pattern:** Must start with a letter, followed by letters, numbers, hyphens, or underscores

### Environment Status Values
| Status | Description |
|--------|-------------|
| `CREATING` | Environment is being created |
| `CREATE_FAILED` | Environment creation failed |
| `AVAILABLE` | Environment is ready for use |
| `UPDATING` | Environment is being updated |
| `DELETING` | Environment is being deleted |
| `DELETED` | Environment has been deleted |
| `UNAVAILABLE` | Environment is temporarily unavailable |
| `UPDATE_FAILED` | Environment update failed |
| `ROLLING_BACK` | Environment is rolling back an update |
| `CREATING_SNAPSHOT` | Environment is creating a snapshot |
| `PENDING` | Environment operation is pending |
| `MAINTENANCE` | Environment is under maintenance |

### Environment Classes
| Class | Description |
|-------|-------------|
| `mw1.micro` | Micro (for testing/development) |
| `mw1.small` | Small |
| `mw1.medium` | Medium |
| `mw1.large` | Large |
| `mw1.xlarge` | Extra large |
| `mw1.2xlarge` | 2x extra large |

### Service Endpoints
| Endpoint | Usage |
|----------|-------|
| `api.airflow.{region}.amazonaws.com` | Environment management operations |
| `env.airflow.{region}.amazonaws.com` | Airflow environment operations (CLI tokens, web tokens, REST API) |
