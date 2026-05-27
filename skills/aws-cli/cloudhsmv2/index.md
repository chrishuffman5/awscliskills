# AWS CLI v2 -- CloudHSM (cloudhsmv2) Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/cloudhsmv2/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-cluster` | Cluster | Create a new CloudHSM cluster |
| `delete-cluster` | Cluster | Delete a CloudHSM cluster |
| `describe-clusters` | Cluster | List and describe clusters |
| `modify-cluster` | Cluster | Modify cluster settings |
| `initialize-cluster` | Cluster | Initialize a cluster with signed certificate |
| `create-hsm` | HSM | Create an HSM in a cluster |
| `delete-hsm` | HSM | Delete an HSM from a cluster |
| `describe-backups` | Backup | List and describe backups |
| `delete-backup` | Backup | Delete a backup |
| `copy-backup-to-region` | Backup | Copy a backup to another region |
| `restore-backup` | Backup | Restore a deleted backup |
| `modify-backup-attributes` | Backup | Modify backup attributes |
| `get-resource-policy` | Policy | Get the resource policy for a backup |
| `put-resource-policy` | Policy | Create or update a resource policy |
| `delete-resource-policy` | Policy | Delete a resource policy |
| `tag-resource` | Tag | Add tags to a resource |
| `untag-resource` | Tag | Remove tags from a resource |
| `list-tags` | Tag | List tags for a resource |

---

## Global Options

These options are available on ALL `aws cloudhsmv2` commands.

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

### Cluster States
| State | Description |
|-------|-------------|
| `CREATE_IN_PROGRESS` | Cluster is being created |
| `UNINITIALIZED` | Cluster created but not yet initialized |
| `INITIALIZE_IN_PROGRESS` | Cluster initialization in progress |
| `INITIALIZED` | Cluster has been initialized |
| `ACTIVE` | Cluster is active and operational |
| `UPDATE_IN_PROGRESS` | Cluster is being updated |
| `MODIFY_IN_PROGRESS` | Cluster is being modified |
| `ROLLBACK_IN_PROGRESS` | Cluster modification is rolling back |
| `DELETE_IN_PROGRESS` | Cluster is being deleted |
| `DELETED` | Cluster has been deleted |
| `DEGRADED` | Cluster is in a degraded state |

### HSM States
| State | Description |
|-------|-------------|
| `CREATE_IN_PROGRESS` | HSM is being created |
| `ACTIVE` | HSM is active |
| `DEGRADED` | HSM is degraded |
| `DELETE_IN_PROGRESS` | HSM is being deleted |
| `DELETED` | HSM has been deleted |

### Backup States
| State | Description |
|-------|-------------|
| `CREATE_IN_PROGRESS` | Backup is being created |
| `READY` | Backup is ready for use |
| `DELETED` | Backup has been deleted |
| `PENDING_DELETION` | Backup is pending deletion |

### HSM Types
| Type | Description |
|------|-------------|
| `hsm1.medium` | Standard CloudHSM instance |
| `hsm2m.medium` | Next-generation CloudHSM instance |

### Cluster Modes
| Mode | Description |
|------|-------------|
| `FIPS` | FIPS 140-2 validated mode |
| `NON_FIPS` | Non-FIPS mode |

### Network Types
| Type | Description |
|------|-------------|
| `IPV4` | IPv4 only (default) |
| `DUALSTACK` | IPv4 and IPv6 |

### ID Patterns
- **Cluster ID:** `cluster-[2-7a-zA-Z]{11,16}`
- **HSM ID:** `hsm-[2-7a-zA-Z]{11,16}`
- **Backup ID:** `backup-[2-7a-zA-Z]{11,16}`
