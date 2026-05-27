# AWS CLI v2 -- EFS (Elastic File System) Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/efs/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-file-system` | File System | Create a new EFS file system |
| `delete-file-system` | File System | Delete an EFS file system |
| `describe-file-systems` | File System | Describe one or more file systems |
| `update-file-system` | File System | Update throughput mode or provisioned throughput |
| `put-lifecycle-configuration` | File System | Set lifecycle policies (transition to IA/Archive) |
| `describe-lifecycle-configuration` | File System | Describe lifecycle configuration |
| `put-backup-policy` | File System | Enable or disable automatic backups |
| `describe-backup-policy` | File System | Describe backup policy |
| `put-file-system-policy` | File System | Set the resource policy for a file system |
| `describe-file-system-policy` | File System | Describe the resource policy |
| `delete-file-system-policy` | File System | Delete the resource policy |
| `create-mount-target` | Mount Target | Create a mount target in a subnet |
| `delete-mount-target` | Mount Target | Delete a mount target |
| `describe-mount-targets` | Mount Target | Describe mount targets |
| `describe-mount-target-security-groups` | Mount Target | List security groups for a mount target |
| `modify-mount-target-security-groups` | Mount Target | Replace security groups on a mount target |
| `create-access-point` | Access Point | Create an access point for a file system |
| `delete-access-point` | Access Point | Delete an access point |
| `describe-access-points` | Access Point | Describe access points |
| `create-replication-configuration` | Replication | Create a replication configuration |
| `delete-replication-configuration` | Replication | Delete a replication configuration |
| `describe-replication-configurations` | Replication | Describe replication configurations |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |
| `create-tags` | Tags | (Legacy) Create tags on a file system |
| `delete-tags` | Tags | (Legacy) Delete tags from a file system |

---

## Global Options

These options are available on ALL `aws efs` commands.

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

### File System ID Format
- **Pattern:** `fs-` followed by 8 or 17 hex characters (e.g., `fs-12345678` or `fs-0123456789abcdef0`)

### Performance Modes
| Mode | Description |
|------|-------------|
| `generalPurpose` | Default. Lowest latency, ideal for most workloads |
| `maxIO` | Higher aggregate throughput, slightly higher latency. For large-scale parallel workloads |

### Throughput Modes
| Mode | Description |
|------|-------------|
| `bursting` | Default. Throughput scales with file system size |
| `provisioned` | Fixed provisioned throughput regardless of size (deprecated, use `elastic`) |
| `elastic` | Automatically scales throughput up or down based on workload |

### Lifecycle Policy Values
| Policy | Values |
|--------|--------|
| `TransitionToIA` | `AFTER_7_DAYS`, `AFTER_14_DAYS`, `AFTER_30_DAYS`, `AFTER_60_DAYS`, `AFTER_90_DAYS`, `AFTER_1_DAY` |
| `TransitionToPrimaryStorageClass` | `AFTER_1_ACCESS` |
| `TransitionToArchive` | `AFTER_1_DAY`, `AFTER_7_DAYS`, `AFTER_14_DAYS`, `AFTER_30_DAYS`, `AFTER_60_DAYS`, `AFTER_90_DAYS`, `AFTER_180_DAYS`, `AFTER_270_DAYS`, `AFTER_365_DAYS` |

### File System Lifecycle States
| State | Description |
|-------|-------------|
| `creating` | File system is being created |
| `available` | File system is ready for use |
| `updating` | File system is being updated |
| `deleting` | File system is being deleted |
| `deleted` | File system has been deleted |
| `error` | File system creation failed |

### Mount Target Lifecycle States
| State | Description |
|-------|-------------|
| `creating` | Mount target is being created |
| `available` | Mount target is ready |
| `updating` | Mount target is being updated |
| `deleting` | Mount target is being deleted |
| `deleted` | Mount target has been deleted |
| `error` | Mount target creation failed |
