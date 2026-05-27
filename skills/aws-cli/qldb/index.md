# AWS CLI v2 -- QLDB (Quantum Ledger Database) Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/qldb/

> **DEPRECATION NOTICE:** Amazon QLDB reached end of support on July 31, 2025.

---

## Quick Reference — `aws qldb`

| Command | Category | Description |
|---------|----------|-------------|
| `create-ledger` | Ledger | Create a new QLDB ledger |
| `delete-ledger` | Ledger | Delete a ledger (must disable deletion protection first) |
| `describe-ledger` | Ledger | Describe a ledger's properties and state |
| `list-ledgers` | Ledger | List all ledgers in the account and region |
| `update-ledger` | Ledger | Update ledger properties (deletion protection, KMS key) |
| `update-ledger-permissions-mode` | Ledger | Update the permissions mode of a ledger |
| `export-journal-to-s3` | Journal | Export journal contents to an S3 bucket |
| `describe-journal-s3-export` | Journal | Describe a journal S3 export job |
| `list-journal-s3-exports` | Journal | List all journal S3 exports across all ledgers |
| `list-journal-s3-exports-for-ledger` | Journal | List journal S3 exports for a specific ledger |
| `get-block` | Journal | Retrieve a block object at a specified address |
| `get-digest` | Journal | Get the digest of a ledger for verification |
| `get-revision` | Journal | Retrieve a document revision for verification |
| `stream-journal-to-kinesis` | Stream | Create a journal stream to Kinesis Data Streams |
| `describe-journal-kinesis-stream` | Stream | Describe a journal Kinesis stream |
| `list-journal-kinesis-streams-for-ledger` | Stream | List Kinesis streams for a ledger |
| `cancel-journal-kinesis-stream` | Stream | Cancel an active journal Kinesis stream |
| `tag-resource` | Tags | Add tags to a QLDB resource |
| `untag-resource` | Tags | Remove tags from a QLDB resource |
| `list-tags-for-resource` | Tags | List tags for a QLDB resource |

## Quick Reference — `aws qldb-session`

| Command | Category | Description |
|---------|----------|-------------|
| `send-command` | Session | Send a command to a QLDB ledger session (low-level data plane) |

---

## Global Options

These options are available on ALL `aws qldb` and `aws qldb-session` commands.

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

### Ledger States

| State | Description |
|-------|-------------|
| `CREATING` | Ledger is being created |
| `ACTIVE` | Ledger is ready for use |
| `DELETING` | Ledger is being deleted |
| `DELETED` | Ledger has been deleted |

### Permissions Modes

| Mode | Description |
|------|-------------|
| `ALLOW_ALL` | Legacy mode; all access allowed to any user with API access |
| `STANDARD` | Recommended; enables fine-grained IAM access control for ledgers, tables, and PartiQL commands |

### Journal Stream States

| Status | Description |
|--------|-------------|
| `ACTIVE` | Stream is actively delivering data |
| `COMPLETED` | Stream has finished (exclusive end time reached) |
| `CANCELED` | Stream was manually canceled |
| `FAILED` | Stream encountered an error |
| `IMPAIRED` | Stream is experiencing transient issues |

### S3 Export Statuses

| Status | Description |
|--------|-------------|
| `IN_PROGRESS` | Export is currently running |
| `COMPLETED` | Export finished successfully |
| `CANCELLED` | Export was cancelled |

### Encryption at Rest

QLDB supports AWS-owned keys (default) or customer-managed KMS keys for encryption at rest. The KMS key can be specified during ledger creation or updated afterwards.

| Key Type | Description |
|----------|-------------|
| `AWS_OWNED_KMS_KEY` | Default; AWS manages the key |
| Customer managed | You provide and manage the KMS key ARN |
