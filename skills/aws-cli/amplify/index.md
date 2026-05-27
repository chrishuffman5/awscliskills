# AWS CLI v2 -- Amplify (Amplify Hosting) Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/amplify/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-app` | App | Create a new Amplify app |
| `delete-app` | App | Delete an Amplify app |
| `get-app` | App | Get details of an Amplify app |
| `list-apps` | App | List all Amplify apps |
| `update-app` | App | Update an Amplify app |
| `generate-access-logs` | App | Generate access logs for a specified time range |
| `create-branch` | Branch | Create a new branch for an app |
| `delete-branch` | Branch | Delete a branch for an app |
| `get-branch` | Branch | Get details of a branch |
| `list-branches` | Branch | List branches for an app |
| `update-branch` | Branch | Update a branch |
| `create-domain-association` | Domain | Create a domain association for an app |
| `delete-domain-association` | Domain | Delete a domain association |
| `get-domain-association` | Domain | Get details of a domain association |
| `list-domain-associations` | Domain | List domain associations for an app |
| `update-domain-association` | Domain | Update a domain association |
| `start-job` | Job | Start a deployment job |
| `stop-job` | Job | Stop a running job |
| `get-job` | Job | Get details of a job |
| `list-jobs` | Job | List jobs for a branch |
| `delete-job` | Job | Delete a job |
| `create-deployment` | Deployment | Create a manual deployment |
| `start-deployment` | Deployment | Start a manual deployment |
| `get-artifact-url` | Artifact | Get the artifact URL for a build |
| `list-artifacts` | Artifact | List artifacts for a branch/job/step |
| `create-backend-environment` | Backend Environment | Create a backend environment |
| `delete-backend-environment` | Backend Environment | Delete a backend environment |
| `get-backend-environment` | Backend Environment | Get details of a backend environment |
| `list-backend-environments` | Backend Environment | List backend environments |
| `create-webhook` | Webhook | Create a webhook |
| `delete-webhook` | Webhook | Delete a webhook |
| `get-webhook` | Webhook | Get details of a webhook |
| `list-webhooks` | Webhook | List webhooks for an app |
| `update-webhook` | Webhook | Update a webhook |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

---

## Global Options

These options are available on ALL `aws amplify` commands.

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

### App Stage Values
| Stage | Description |
|-------|-------------|
| `PRODUCTION` | Production stage |
| `BETA` | Beta/staging stage |
| `DEVELOPMENT` | Development stage |
| `EXPERIMENTAL` | Experimental stage |
| `PULL_REQUEST` | Pull request preview |

### Job Types
| Type | Description |
|------|-------------|
| `RELEASE` | Standard release deployment |
| `RETRY` | Retry a previous job |
| `MANUAL` | Manual deployment |
| `WEB_HOOK` | Deployment triggered by a webhook |

### Job Status Values
| Status | Description |
|--------|-------------|
| `PENDING` | Job is queued |
| `PROVISIONING` | Provisioning build environment |
| `RUNNING` | Build is running |
| `FAILED` | Job failed |
| `SUCCEED` | Job completed successfully |
| `CANCELLING` | Job is being cancelled |
| `CANCELLED` | Job was cancelled |

### Domain Status Values
| Status | Description |
|--------|-------------|
| `PENDING_VERIFICATION` | Waiting for DNS verification |
| `IN_PROGRESS` | Domain setup in progress |
| `AVAILABLE` | Domain is active and available |
| `PENDING_DEPLOYMENT` | Waiting for deployment |
| `FAILED` | Domain setup failed |
| `CREATING` | Domain association is being created |
| `REQUESTING_CERTIFICATE` | SSL certificate is being requested |
| `UPDATING` | Domain association is being updated |
