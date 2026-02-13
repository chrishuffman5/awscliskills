# AWS CLI v2 -- Directory Service Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/ds/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-directory` | Directory | Create a Simple AD directory |
| `create-microsoft-ad` | Directory | Create a Managed Microsoft AD directory |
| `delete-directory` | Directory | Delete a directory |
| `describe-directories` | Directory | Describe directories |
| `get-directory-limits` | Directory | Get directory creation limits |
| `create-alias` | Directory | Create an alias for a directory |
| `create-computer` | Directory | Create a computer account in a directory |
| `describe-settings` | Directory | Describe directory settings |
| `update-settings` | Directory | Update directory settings |
| `describe-update-directory` | Directory | Describe directory update status |
| `update-directory-setup` | Directory | Update directory setup |
| `describe-domain-controllers` | Directory | Describe domain controllers |
| `update-number-of-domain-controllers` | Directory | Update the number of domain controllers |
| `describe-regions` | Directory | Describe directory regions |
| `add-region` | Directory | Add a region to a directory |
| `remove-region` | Directory | Remove a region from a directory |
| `connect-directory` | Hybrid AD | Create an AD Connector |
| `create-hybrid-ad` | Hybrid AD | Create a hybrid AD setup |
| `describe-hybrid-ad-update` | Hybrid AD | Describe hybrid AD update status |
| `update-hybrid-ad` | Hybrid AD | Update hybrid AD configuration |
| `create-trust` | Trust | Create a trust relationship |
| `delete-trust` | Trust | Delete a trust relationship |
| `describe-trusts` | Trust | Describe trust relationships |
| `update-trust` | Trust | Update a trust relationship |
| `verify-trust` | Trust | Verify a trust relationship |
| `create-conditional-forwarder` | Conditional Forwarder | Create a conditional forwarder |
| `delete-conditional-forwarder` | Conditional Forwarder | Delete a conditional forwarder |
| `describe-conditional-forwarders` | Conditional Forwarder | Describe conditional forwarders |
| `update-conditional-forwarder` | Conditional Forwarder | Update a conditional forwarder |
| `create-snapshot` | Snapshot | Create a directory snapshot |
| `delete-snapshot` | Snapshot | Delete a snapshot |
| `describe-snapshots` | Snapshot | Describe snapshots |
| `restore-from-snapshot` | Snapshot | Restore a directory from a snapshot |
| `get-snapshot-limits` | Snapshot | Get snapshot creation limits |
| `add-ip-routes` | Networking | Add IP routes to a directory |
| `remove-ip-routes` | Networking | Remove IP routes |
| `list-ip-routes` | Networking | List IP routes for a directory |
| `enable-sso` | Authentication | Enable single sign-on |
| `disable-sso` | Authentication | Disable single sign-on |
| `enable-radius` | Authentication | Enable RADIUS authentication |
| `disable-radius` | Authentication | Disable RADIUS authentication |
| `update-radius` | Authentication | Update RADIUS configuration |
| `enable-ldaps` | Authentication | Enable LDAPS |
| `disable-ldaps` | Authentication | Disable LDAPS |
| `describe-ldaps-settings` | Authentication | Describe LDAPS settings |
| `enable-client-authentication` | Authentication | Enable client authentication |
| `disable-client-authentication` | Authentication | Disable client authentication |
| `describe-client-authentication-settings` | Authentication | Describe client authentication settings |
| `reset-user-password` | Authentication | Reset a user password |
| `register-certificate` | Certificate | Register a certificate |
| `deregister-certificate` | Certificate | Deregister a certificate |
| `describe-certificate` | Certificate | Describe a certificate |
| `list-certificates` | Certificate | List certificates |
| `enable-ca-enrollment-policy` | Certificate | Enable CA enrollment policy |
| `disable-ca-enrollment-policy` | Certificate | Disable CA enrollment policy |
| `describe-ca-enrollment-policy` | Certificate | Describe CA enrollment policy |
| `enable-directory-data-access` | Data Access | Enable directory data access |
| `disable-directory-data-access` | Data Access | Disable directory data access |
| `describe-directory-data-access` | Data Access | Describe directory data access |
| `share-directory` | Sharing | Share a directory |
| `unshare-directory` | Sharing | Unshare a directory |
| `accept-shared-directory` | Sharing | Accept a shared directory |
| `reject-shared-directory` | Sharing | Reject a shared directory |
| `describe-shared-directories` | Sharing | Describe shared directories |
| `start-ad-assessment` | Assessment | Start an AD assessment |
| `delete-ad-assessment` | Assessment | Delete an AD assessment |
| `describe-ad-assessment` | Assessment | Describe an AD assessment |
| `list-ad-assessments` | Assessment | List AD assessments |
| `register-event-topic` | Events | Register an SNS event topic |
| `deregister-event-topic` | Events | Deregister an event topic |
| `describe-event-topics` | Events | Describe event topics |
| `add-tags-to-resource` | Tags | Add tags to a directory |
| `remove-tags-from-resource` | Tags | Remove tags from a directory |
| `list-tags-for-resource` | Tags | List tags for a directory |
| `create-log-subscription` | Logging | Create a CloudWatch log subscription |
| `delete-log-subscription` | Logging | Delete a log subscription |
| `list-log-subscriptions` | Logging | List log subscriptions |
| `start-schema-extension` | Schema | Start a schema extension |
| `cancel-schema-extension` | Schema | Cancel a schema extension |
| `list-schema-extensions` | Schema | List schema extensions |

---

## Global Options

These options are available on ALL `aws ds` commands.

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

### Directory Types
| Type | Description |
|------|-------------|
| `SimpleAD` | Standalone managed directory powered by Samba 4 |
| `ADConnector` | Proxy to redirect requests to self-managed AD |
| `MicrosoftAD` | AWS Managed Microsoft AD |
| `SharedMicrosoftAD` | A Managed Microsoft AD shared from another account |

### Directory Stages
| Stage | Description |
|-------|-------------|
| `Requested` | Directory creation requested |
| `Creating` | Directory is being created |
| `Created` | Directory created but not yet active |
| `Active` | Directory is active and ready |
| `Inoperable` | Directory is not functional |
| `Impaired` | Directory is partially functional |
| `Restoring` | Directory is being restored from snapshot |
| `RestoreFailed` | Restore from snapshot failed |
| `Deleting` | Directory is being deleted |
| `Deleted` | Directory has been deleted |
| `Failed` | Directory creation failed |
| `Updating` | Directory is being updated |

### Trust Directions
| Direction | Description |
|-----------|-------------|
| `One-Way: Outgoing` | Users in remote domain can access resources in your directory |
| `One-Way: Incoming` | Users in your directory can access resources in remote domain |
| `Two-Way` | Bidirectional trust |

### Trust Types
| Type | Description |
|------|-------------|
| `Forest` | Forest-level trust (recommended) |
| `External` | External domain trust |

### Directory ID Format
All directory IDs follow the pattern `d-[0-9a-f]{10}` (e.g., `d-1234567890`).
