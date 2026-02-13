# AWS CLI v2 — Secrets Manager Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/secretsmanager/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `batch-get-secret-value` | Retrieval | Retrieve multiple secret values in a single call |
| `cancel-rotate-secret` | Rotation | Turn off automatic rotation and cancel rotation in progress |
| `create-secret` | Lifecycle | Create a new secret |
| `delete-resource-policy` | Policy | Remove the resource-based policy attached to a secret |
| `delete-secret` | Lifecycle | Schedule a secret for deletion |
| `describe-secret` | Lifecycle | Retrieve metadata about a secret (not the value) |
| `get-random-password` | Password | Generate a random password |
| `get-resource-policy` | Policy | Retrieve the resource-based policy attached to a secret |
| `get-secret-value` | Retrieval | Retrieve the encrypted value of a secret |
| `list-secret-version-ids` | Versions | List all version IDs for a secret |
| `list-secrets` | Lifecycle | List secrets in the account |
| `put-resource-policy` | Policy | Attach a resource-based policy to a secret |
| `put-secret-value` | Lifecycle | Store a new version of a secret value |
| `remove-regions-from-replication` | Replication | Remove replica secrets from specified regions |
| `replicate-secret-to-regions` | Replication | Replicate a secret to other AWS regions |
| `restore-secret` | Lifecycle | Cancel the scheduled deletion of a secret |
| `rotate-secret` | Rotation | Configure and trigger secret rotation |
| `stop-replication-to-replica` | Replication | Promote a replica to a standalone primary secret |
| `tag-resource` | Tags | Add tags to a secret |
| `untag-resource` | Tags | Remove tags from a secret |
| `update-secret` | Lifecycle | Update secret metadata or value |
| `update-secret-version-stage` | Versions | Move a staging label between versions |
| `validate-resource-policy` | Policy | Validate a resource-based policy before attaching |

---

## Global Options Reference

These options are available on all `aws secretsmanager` subcommands:

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `--debug` | boolean | false | Enable debug logging |
| `--endpoint-url` | string | None | Override default service endpoint URL |
| `--no-verify-ssl` | boolean | false | Disable SSL certificate verification |
| `--no-paginate` | boolean | false | Disable automatic pagination |
| `--output` | string | `json` | Output format: `json`, `text`, `table`, `yaml`, `yaml-stream` |
| `--query` | string | None | JMESPath query to filter response |
| `--profile` | string | None | Named AWS credential profile |
| `--region` | string | None | AWS region to use |
| `--color` | string | `auto` | Color output: `on`, `off`, `auto` |
| `--no-sign-request` | boolean | false | Do not sign requests (for public endpoints) |
| `--ca-bundle` | string | None | CA certificate bundle for SSL verification |
| `--cli-read-timeout` | integer | 60 | Maximum socket read time in seconds |
| `--cli-connect-timeout` | integer | 60 | Maximum socket connect time in seconds |
| `--cli-binary-format` | string | `base64` | Binary blob format: `base64`, `raw-in-base64-out` |
| `--no-cli-pager` | boolean | false | Disable output pager |
| `--cli-auto-prompt` | boolean | false | Auto-prompt for CLI parameters |
| `--no-cli-auto-prompt` | boolean | false | Disable auto-prompt |
| `--cli-input-json` | string | None | Read arguments from JSON string |
| `--cli-input-yaml` | string | None | Read arguments from YAML string |
| `--generate-cli-skeleton` | string | None | Print skeleton without sending request: `input`, `yaml-input`, `output` |
