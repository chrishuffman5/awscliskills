# AWS CLI v2 -- CodeGuru (Code Reviews + Security Scanning) Command Reference Index

> Based on AWS CLI v2 documentation. Sources: https://docs.aws.amazon.com/cli/latest/reference/codeguru-reviewer/ and https://docs.aws.amazon.com/cli/latest/reference/codeguru-security/

---

## Quick Reference

| Command | CLI | Category | Description |
|---------|-----|----------|-------------|
| `associate-repository` | codeguru-reviewer | Repository | Associate a repository for code reviews |
| `disassociate-repository` | codeguru-reviewer | Repository | Disassociate a repository |
| `describe-repository-association` | codeguru-reviewer | Repository | Describe a repository association |
| `list-repository-associations` | codeguru-reviewer | Repository | List repository associations |
| `create-code-review` | codeguru-reviewer | Code Review | Create a code review |
| `describe-code-review` | codeguru-reviewer | Code Review | Describe a code review |
| `list-code-reviews` | codeguru-reviewer | Code Review | List code reviews |
| `list-recommendations` | codeguru-reviewer | Recommendation | List recommendations for a code review |
| `list-recommendation-feedback` | codeguru-reviewer | Recommendation | List recommendation feedback |
| `describe-recommendation-feedback` | codeguru-reviewer | Recommendation | Describe recommendation feedback |
| `put-recommendation-feedback` | codeguru-reviewer | Recommendation | Submit feedback on a recommendation |
| `create-scan` | codeguru-security | Security Scan | Create a security scan |
| `get-scan` | codeguru-security | Security Scan | Get details of a security scan |
| `list-scans` | codeguru-security | Security Scan | List security scans |
| `create-upload-url` | codeguru-security | Security Scan | Create a pre-signed URL for uploading code |
| `get-findings` | codeguru-security | Security Finding | Get security findings for a scan |
| `batch-get-findings` | codeguru-security | Security Finding | Batch get security findings |
| `list-findings-metrics` | codeguru-security | Security Finding | List findings metrics over time |
| `get-metrics-summary` | codeguru-security | Security Finding | Get a summary of security metrics |
| `get-account-configuration` | codeguru-security | Account | Get account-level configuration |
| `update-account-configuration` | codeguru-security | Account | Update account-level configuration |
| `tag-resource` | both | Tags | Add tags to a resource |
| `untag-resource` | both | Tags | Remove tags from a resource |
| `list-tags-for-resource` | both | Tags | List tags for a resource |
| `wait code-review-completed` | codeguru-reviewer | Wait | Wait until a code review is completed |
| `wait repository-association-succeeded` | codeguru-reviewer | Wait | Wait until a repository association succeeds |

---

## Global Options

These options are available on ALL `aws codeguru-reviewer` and `aws codeguru-security` commands.

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

### Repository Types
| Type | Description |
|------|-------------|
| `CodeCommit` | AWS CodeCommit repository |
| `Bitbucket` | Bitbucket repository |
| `GitHubEnterpriseServer` | GitHub Enterprise Server repository |
| `S3Bucket` | S3 bucket (for CodeGuru Security) |

### Code Review States
| State | Description |
|-------|-------------|
| `Completed` | Code review is complete |
| `Pending` | Code review is pending |
| `Failed` | Code review failed |
| `Deleting` | Code review is being deleted |

### Repository Association States
| State | Description |
|-------|-------------|
| `Associated` | Repository is associated |
| `Associating` | Association is in progress |
| `Failed` | Association failed |
| `Disassociating` | Disassociation is in progress |
| `Disassociated` | Repository is disassociated |

### Security Scan States
| State | Description |
|-------|-------------|
| `InProgress` | Scan is running |
| `Successful` | Scan completed successfully |
| `Failed` | Scan failed |

### Finding Severity Levels
| Severity | Description |
|----------|-------------|
| `Critical` | Critical severity finding |
| `High` | High severity finding |
| `Medium` | Medium severity finding |
| `Low` | Low severity finding |
| `Info` | Informational finding |

### Wait Commands
The `aws codeguru-reviewer wait` subcommand blocks until a resource reaches a specific state:

| Waiter | Description |
|--------|-------------|
| `code-review-completed` | Wait until a code review is completed |
| `repository-association-succeeded` | Wait until a repository association succeeds |

```bash
aws codeguru-reviewer wait code-review-completed \
  --code-review-arn arn:aws:codeguru-reviewer:us-east-1:123456789012:code-review:uuid
aws codeguru-reviewer wait repository-association-succeeded \
  --association-arn arn:aws:codeguru-reviewer:us-east-1:123456789012:association:uuid
```
