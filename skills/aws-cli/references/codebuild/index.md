# AWS CLI v2 -- CodeBuild Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/codebuild/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-project` | Project | Create a new build project |
| `delete-project` | Project | Delete a build project |
| `batch-get-projects` | Project | Get information about one or more build projects |
| `list-projects` | Project | List build project names |
| `update-project` | Project | Update a build project |
| `start-build` | Build | Start a build |
| `stop-build` | Build | Stop a running build |
| `retry-build` | Build | Retry a failed build |
| `batch-get-builds` | Build | Get information about one or more builds |
| `list-builds` | Build | List build IDs |
| `list-builds-for-project` | Build | List build IDs for a specific project |
| `start-build-batch` | Build Batch | Start a batch build |
| `stop-build-batch` | Build Batch | Stop a running batch build |
| `retry-build-batch` | Build Batch | Retry a failed batch build |
| `delete-build-batch` | Build Batch | Delete a batch build |
| `batch-get-build-batches` | Build Batch | Get information about batch builds |
| `list-build-batches` | Build Batch | List batch build IDs |
| `list-build-batches-for-project` | Build Batch | List batch build IDs for a project |
| `create-report-group` | Report Group | Create a report group |
| `delete-report-group` | Report Group | Delete a report group |
| `batch-get-report-groups` | Report Group | Get information about report groups |
| `list-report-groups` | Report Group | List report group ARNs |
| `update-report-group` | Report Group | Update a report group |
| `batch-get-reports` | Report | Get information about reports |
| `delete-report` | Report | Delete a report |
| `describe-test-cases` | Report | Get test case details for a report |
| `list-reports` | Report | List report ARNs |
| `list-reports-for-report-group` | Report | List report ARNs for a report group |
| `import-source-credentials` | Source Credentials | Import source repository credentials |
| `delete-source-credentials` | Source Credentials | Delete source repository credentials |
| `list-source-credentials` | Source Credentials | List source repository credentials |
| `create-webhook` | Webhook | Create a webhook for a project |
| `delete-webhook` | Webhook | Delete a webhook |
| `update-webhook` | Webhook | Update a webhook |
| `create-fleet` | Fleet | Create a compute fleet |
| `delete-fleet` | Fleet | Delete a compute fleet |
| `batch-get-fleets` | Fleet | Get information about compute fleets |
| `list-fleets` | Fleet | List compute fleet names |
| `update-fleet` | Fleet | Update a compute fleet |

---

## Global Options

These options are available on ALL `aws codebuild` commands.

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

### Build Project Name Constraints
- **Length:** 2 to 255 characters
- **Pattern:** Letters, numbers, hyphens, underscores, periods

### Build Status Values
| Status | Description |
|--------|-------------|
| `SUCCEEDED` | Build completed successfully |
| `FAILED` | Build failed |
| `FAULT` | Build faulted (internal error) |
| `TIMED_OUT` | Build timed out |
| `IN_PROGRESS` | Build is currently running |
| `STOPPED` | Build was manually stopped |

### Build Batch Status Values
| Status | Description |
|--------|-------------|
| `SUCCEEDED` | All builds in the batch succeeded |
| `FAILED` | One or more builds in the batch failed |
| `FAULT` | Internal error in batch build |
| `TIMED_OUT` | Batch build timed out |
| `IN_PROGRESS` | Batch build is running |
| `STOPPED` | Batch build was stopped |

### Source Types
| Type | Description |
|------|-------------|
| `CODECOMMIT` | AWS CodeCommit repository |
| `CODEPIPELINE` | Source provided by CodePipeline |
| `GITHUB` | GitHub repository |
| `GITHUB_ENTERPRISE` | GitHub Enterprise repository |
| `BITBUCKET` | Bitbucket repository |
| `S3` | S3 bucket |
| `NO_SOURCE` | No source (inline buildspec) |
| `GITLAB` | GitLab repository |
| `GITLAB_SELF_MANAGED` | Self-managed GitLab repository |

### Environment Types
| Type | Description |
|------|-------------|
| `WINDOWS_CONTAINER` | Windows Server container |
| `LINUX_CONTAINER` | Linux container |
| `LINUX_GPU_CONTAINER` | Linux GPU container |
| `ARM_CONTAINER` | ARM-based Linux container |
| `WINDOWS_SERVER_2019_CONTAINER` | Windows Server 2019 container |
| `LINUX_LAMBDA_CONTAINER` | Linux Lambda container |
| `ARM_LAMBDA_CONTAINER` | ARM Lambda container |

### Compute Types
| Type | vCPUs | Memory |
|------|-------|--------|
| `BUILD_GENERAL1_SMALL` | 2 | 3 GB |
| `BUILD_GENERAL1_MEDIUM` | 4 | 7 GB |
| `BUILD_GENERAL1_LARGE` | 8 | 15 GB |
| `BUILD_GENERAL1_XLARGE` | 36 | 70 GB |
| `BUILD_GENERAL1_2XLARGE` | 72 | 145 GB |
| `BUILD_LAMBDA_1GB` | 2 | 1 GB |
| `BUILD_LAMBDA_2GB` | 2 | 2 GB |
| `BUILD_LAMBDA_4GB` | 2 | 4 GB |
| `BUILD_LAMBDA_8GB` | 4 | 8 GB |
| `BUILD_LAMBDA_10GB` | 4 | 10 GB |

### Artifact Types
| Type | Description |
|------|-------------|
| `CODEPIPELINE` | Artifacts managed by CodePipeline |
| `S3` | Artifacts stored in S3 |
| `NO_ARTIFACTS` | No artifacts produced |
