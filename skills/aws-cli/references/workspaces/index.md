# AWS CLI v2 — WorkSpaces Command Reference Index

> Based on AWS CLI v2 documentation. Sources: https://docs.aws.amazon.com/cli/latest/reference/workspaces/ and https://docs.aws.amazon.com/cli/latest/reference/workspaces-web/

---

## Quick Reference

| Command | Service | Category | Description |
|---------|---------|----------|-------------|
| `create-workspaces` | workspaces | WorkSpace | Create one or more WorkSpaces |
| `terminate-workspaces` | workspaces | WorkSpace | Terminate one or more WorkSpaces |
| `reboot-workspaces` | workspaces | WorkSpace | Reboot one or more WorkSpaces |
| `rebuild-workspaces` | workspaces | WorkSpace | Rebuild one or more WorkSpaces |
| `start-workspaces` | workspaces | WorkSpace | Start one or more stopped WorkSpaces |
| `stop-workspaces` | workspaces | WorkSpace | Stop one or more running WorkSpaces |
| `describe-workspaces` | workspaces | WorkSpace | Describe one or more WorkSpaces |
| `describe-workspaces-connection-status` | workspaces | WorkSpace | Describe connection status of WorkSpaces |
| `modify-workspace-properties` | workspaces | WorkSpace | Modify properties of a WorkSpace |
| `modify-workspace-state` | workspaces | WorkSpace | Set the state of a WorkSpace |
| `restore-workspace` | workspaces | WorkSpace | Restore a WorkSpace to its last known healthy state |
| `migrate-workspace` | workspaces | WorkSpace | Migrate a WorkSpace to a new bundle |
| `create-workspace-bundle` | workspaces | Bundle | Create a custom WorkSpace bundle |
| `delete-workspace-bundle` | workspaces | Bundle | Delete a WorkSpace bundle |
| `describe-workspace-bundles` | workspaces | Bundle | Describe available WorkSpace bundles |
| `update-workspace-bundle` | workspaces | Bundle | Update a WorkSpace bundle |
| `create-workspace-image` | workspaces | Image | Create a WorkSpace image |
| `delete-workspace-image` | workspaces | Image | Delete a WorkSpace image |
| `describe-workspace-images` | workspaces | Image | Describe WorkSpace images |
| `copy-workspace-image` | workspaces | Image | Copy a WorkSpace image to another region |
| `register-workspace-directory` | workspaces | Directory | Register a directory for use with WorkSpaces |
| `deregister-workspace-directory` | workspaces | Directory | Deregister a directory |
| `describe-workspace-directories` | workspaces | Directory | Describe registered directories |
| `modify-workspace-creation-properties` | workspaces | Directory | Modify default creation properties |
| `modify-workspace-access-properties` | workspaces | Directory | Modify access properties for a directory |
| `modify-selfservice-permissions` | workspaces | Directory | Modify self-service permissions |
| `modify-client-properties` | workspaces | Directory | Modify client properties for a resource |
| `describe-client-properties` | workspaces | Directory | Describe client properties |
| `create-ip-group` | workspaces | IP Group | Create an IP access control group |
| `delete-ip-group` | workspaces | IP Group | Delete an IP access control group |
| `describe-ip-groups` | workspaces | IP Group | Describe IP access control groups |
| `authorize-ip-rules` | workspaces | IP Group | Add rules to an IP access control group |
| `revoke-ip-rules` | workspaces | IP Group | Remove rules from an IP access control group |
| `update-rules-of-ip-group` | workspaces | IP Group | Replace rules of an IP access control group |
| `associate-ip-groups` | workspaces | IP Group | Associate IP groups with a directory |
| `disassociate-ip-groups` | workspaces | IP Group | Disassociate IP groups from a directory |
| `create-connection-alias` | workspaces | Connection Alias | Create a connection alias |
| `delete-connection-alias` | workspaces | Connection Alias | Delete a connection alias |
| `describe-connection-aliases` | workspaces | Connection Alias | Describe connection aliases |
| `associate-connection-alias` | workspaces | Connection Alias | Associate a connection alias with a directory |
| `disassociate-connection-alias` | workspaces | Connection Alias | Disassociate a connection alias |
| `create-workspaces-pool` | workspaces | Pool | Create a WorkSpaces pool |
| `terminate-workspaces-pool` | workspaces | Pool | Terminate a WorkSpaces pool |
| `describe-workspaces-pools` | workspaces | Pool | Describe WorkSpaces pools |
| `update-workspaces-pool` | workspaces | Pool | Update a WorkSpaces pool |
| `start-workspaces-pool` | workspaces | Pool | Start a WorkSpaces pool |
| `stop-workspaces-pool` | workspaces | Pool | Stop a WorkSpaces pool |
| `describe-workspaces-pool-sessions` | workspaces | Pool | Describe pool sessions |
| `describe-account` | workspaces | Account | Describe account settings |
| `describe-account-modifications` | workspaces | Account | Describe account modifications |
| `modify-account` | workspaces | Account | Modify account settings |
| `create-tags` | workspaces | Account | Add tags to a resource |
| `delete-tags` | workspaces | Account | Remove tags from a resource |
| `describe-tags` | workspaces | Account | Describe tags for a resource |
| `create-portal` | workspaces-web | Web Portal | Create a web portal |
| `delete-portal` | workspaces-web | Web Portal | Delete a web portal |
| `get-portal` | workspaces-web | Web Portal | Get a web portal |
| `list-portals` | workspaces-web | Web Portal | List web portals |
| `update-portal` | workspaces-web | Web Portal | Update a web portal |
| `create-browser-settings` | workspaces-web | Web Browser | Create browser settings |
| `delete-browser-settings` | workspaces-web | Web Browser | Delete browser settings |
| `get-browser-settings` | workspaces-web | Web Browser | Get browser settings |
| `list-browser-settings` | workspaces-web | Web Browser | List browser settings |
| `update-browser-settings` | workspaces-web | Web Browser | Update browser settings |
| `associate-browser-settings` | workspaces-web | Web Browser | Associate browser settings with a portal |
| `disassociate-browser-settings` | workspaces-web | Web Browser | Disassociate browser settings |
| `create-network-settings` | workspaces-web | Web Network | Create network settings |
| `delete-network-settings` | workspaces-web | Web Network | Delete network settings |
| `get-network-settings` | workspaces-web | Web Network | Get network settings |
| `list-network-settings` | workspaces-web | Web Network | List network settings |
| `update-network-settings` | workspaces-web | Web Network | Update network settings |
| `associate-network-settings` | workspaces-web | Web Network | Associate network settings with a portal |
| `disassociate-network-settings` | workspaces-web | Web Network | Disassociate network settings |
| `create-user-settings` | workspaces-web | Web User | Create user settings |
| `delete-user-settings` | workspaces-web | Web User | Delete user settings |
| `get-user-settings` | workspaces-web | Web User | Get user settings |
| `list-user-settings` | workspaces-web | Web User | List user settings |
| `update-user-settings` | workspaces-web | Web User | Update user settings |
| `associate-user-settings` | workspaces-web | Web User | Associate user settings with a portal |
| `disassociate-user-settings` | workspaces-web | Web User | Disassociate user settings |
| `create-identity-provider` | workspaces-web | Web Identity | Create an identity provider |
| `delete-identity-provider` | workspaces-web | Web Identity | Delete an identity provider |
| `get-identity-provider` | workspaces-web | Web Identity | Get an identity provider |
| `list-identity-providers` | workspaces-web | Web Identity | List identity providers |
| `update-identity-provider` | workspaces-web | Web Identity | Update an identity provider |
| `create-trust-store` | workspaces-web | Web Trust Store | Create a trust store |
| `delete-trust-store` | workspaces-web | Web Trust Store | Delete a trust store |
| `get-trust-store` | workspaces-web | Web Trust Store | Get a trust store |
| `list-trust-stores` | workspaces-web | Web Trust Store | List trust stores |
| `update-trust-store` | workspaces-web | Web Trust Store | Update a trust store |
| `associate-trust-store` | workspaces-web | Web Trust Store | Associate a trust store with a portal |
| `disassociate-trust-store` | workspaces-web | Web Trust Store | Disassociate a trust store |
| `tag-resource` | workspaces-web | Web Tags | Add tags to a resource |
| `untag-resource` | workspaces-web | Web Tags | Remove tags from a resource |
| `list-tags-for-resource` | workspaces-web | Web Tags | List tags for a resource |

---

## Global Options

These options are available on ALL `aws workspaces` and `aws workspaces-web` commands.

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

### WorkSpace States
| State | Description |
|-------|-------------|
| `PENDING` | WorkSpace is being created |
| `AVAILABLE` | WorkSpace is running and available |
| `IMPAIRED` | WorkSpace is not healthy |
| `UNHEALTHY` | WorkSpace is not responding |
| `REBOOTING` | WorkSpace is being rebooted |
| `STARTING` | WorkSpace is being started |
| `REBUILDING` | WorkSpace is being rebuilt |
| `RESTORING` | WorkSpace is being restored |
| `MAINTENANCE` | WorkSpace is under maintenance |
| `ADMIN_MAINTENANCE` | WorkSpace is under admin maintenance |
| `TERMINATING` | WorkSpace is being terminated |
| `TERMINATED` | WorkSpace has been terminated |
| `SUSPENDED` | WorkSpace has been suspended |
| `UPDATING` | WorkSpace is being updated |
| `STOPPING` | WorkSpace is being stopped |
| `STOPPED` | WorkSpace is stopped |
| `ERROR` | WorkSpace is in an error state |

### Running Modes
| Mode | Description |
|------|-------------|
| `AUTO_STOP` | WorkSpace stops after inactivity timeout |
| `ALWAYS_ON` | WorkSpace is always running |
| `MANUAL` | WorkSpace must be manually started/stopped |

### Compute Types
| Type | Description |
|------|-------------|
| `VALUE` | 1 vCPU, 2 GiB memory |
| `STANDARD` | 2 vCPU, 4 GiB memory |
| `PERFORMANCE` | 2 vCPU, 8 GiB memory |
| `POWER` | 4 vCPU, 16 GiB memory |
| `GRAPHICS` | 8 vCPU, 15 GiB memory, 1 GPU |
| `POWERPRO` | 8 vCPU, 32 GiB memory |
| `GRAPHICSPRO` | 16 vCPU, 122 GiB memory, 1 GPU |
| `GRAPHICS_G4DN` | 4 vCPU, 16 GiB memory, 1 GPU |
| `GRAPHICSPRO_G4DN` | 16 vCPU, 128 GiB memory, 1 GPU |
