# AWS CLI v2 -- AppStream 2.0 Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/appstream/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-fleet` | Fleet | Create a new streaming fleet |
| `delete-fleet` | Fleet | Delete a fleet |
| `describe-fleets` | Fleet | Describe one or more fleets |
| `update-fleet` | Fleet | Update fleet configuration |
| `start-fleet` | Fleet | Start a fleet |
| `stop-fleet` | Fleet | Stop a fleet |
| `associate-fleet` | Fleet | Associate a fleet with a stack |
| `disassociate-fleet` | Fleet | Disassociate a fleet from a stack |
| `list-associated-fleets` | Fleet | List fleets associated with a stack |
| `list-associated-stacks` | Fleet | List stacks associated with a fleet |
| `create-stack` | Stack | Create a new stack |
| `delete-stack` | Stack | Delete a stack |
| `describe-stacks` | Stack | Describe one or more stacks |
| `update-stack` | Stack | Update stack configuration |
| `create-streaming-url` | Stack | Create a streaming URL for a user |
| `describe-sessions` | Stack | Describe streaming sessions |
| `expire-session` | Stack | Expire a streaming session |
| `describe-images` | Image | Describe one or more images |
| `delete-image` | Image | Delete an image |
| `copy-image` | Image | Copy an image to another region |
| `describe-image-permissions` | Image | Describe image sharing permissions |
| `update-image-permissions` | Image | Update image sharing permissions |
| `delete-image-permissions` | Image | Delete image sharing permissions |
| `create-updated-image` | Image | Create a new image from an existing one |
| `create-image-builder` | Image Builder | Create a new image builder |
| `delete-image-builder` | Image Builder | Delete an image builder |
| `describe-image-builders` | Image Builder | Describe one or more image builders |
| `start-image-builder` | Image Builder | Start an image builder |
| `stop-image-builder` | Image Builder | Stop an image builder |
| `create-image-builder-streaming-url` | Image Builder | Create a streaming URL for an image builder |
| `create-app-block` | App Block | Create an app block |
| `delete-app-block` | App Block | Delete an app block |
| `describe-app-blocks` | App Block | Describe app blocks |
| `create-app-block-builder` | App Block Builder | Create an app block builder |
| `delete-app-block-builder` | App Block Builder | Delete an app block builder |
| `describe-app-block-builders` | App Block Builder | Describe app block builders |
| `update-app-block-builder` | App Block Builder | Update an app block builder |
| `start-app-block-builder` | App Block Builder | Start an app block builder |
| `stop-app-block-builder` | App Block Builder | Stop an app block builder |
| `create-application` | Application | Create an application |
| `delete-application` | Application | Delete an application |
| `describe-applications` | Application | Describe applications |
| `update-application` | Application | Update an application |
| `associate-application-fleet` | Application | Associate an application with a fleet |
| `disassociate-application-fleet` | Application | Disassociate an application from a fleet |
| `describe-application-fleet-associations` | Application | Describe application-fleet associations |
| `create-entitlement` | Entitlement | Create an entitlement |
| `delete-entitlement` | Entitlement | Delete an entitlement |
| `describe-entitlements` | Entitlement | Describe entitlements |
| `update-entitlement` | Entitlement | Update an entitlement |
| `list-entitled-applications` | Entitlement | List entitled applications |
| `create-directory-config` | Directory Config | Create a directory configuration |
| `delete-directory-config` | Directory Config | Delete a directory configuration |
| `describe-directory-configs` | Directory Config | Describe directory configurations |
| `update-directory-config` | Directory Config | Update a directory configuration |
| `create-user` | User | Create a new user |
| `delete-user` | User | Delete a user |
| `describe-users` | User | Describe users |
| `disable-user` | User | Disable a user |
| `enable-user` | User | Enable a user |
| `batch-associate-user-stack` | User | Associate users with stacks in batch |
| `batch-disassociate-user-stack` | User | Disassociate users from stacks in batch |
| `describe-user-stack-associations` | User | Describe user-stack associations |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |
| `wait fleet-started` | Wait | Wait until fleet is started |
| `wait fleet-stopped` | Wait | Wait until fleet is stopped |

---

## Global Options

These options are available on ALL `aws appstream` commands.

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

### Fleet Types
| Type | Description |
|------|-------------|
| `ALWAYS_ON` | Instances run continuously and are available immediately |
| `ON_DEMAND` | Instances run only when users stream; startup delay applies |
| `ELASTIC` | Instances are managed by AppStream 2.0 elastic fleets |

### Fleet States
| State | Description |
|-------|-------------|
| `STARTING` | Fleet is starting up |
| `RUNNING` | Fleet is running and available |
| `STOPPING` | Fleet is stopping |
| `STOPPED` | Fleet is stopped |

### Image Builder States
| State | Description |
|-------|-------------|
| `PENDING` | Image builder is pending |
| `UPDATING_AGENT` | Agent is being updated |
| `RUNNING` | Image builder is running |
| `STOPPING` | Image builder is stopping |
| `STOPPED` | Image builder is stopped |
| `REBOOTING` | Image builder is rebooting |
| `SNAPSHOTTING` | Image builder is creating a snapshot |
| `DELETING` | Image builder is being deleted |
| `FAILED` | Image builder has failed |

### Authentication Types
| Type | Description |
|------|-------------|
| `API` | Authenticated via the AppStream 2.0 API |
| `SAML` | Authenticated via SAML 2.0 federation |
| `USERPOOL` | Authenticated via AppStream 2.0 user pool |
| `AWS_AD` | Authenticated via AWS Managed Microsoft AD |

### Wait Commands
The `aws appstream wait` subcommand blocks until a resource reaches a specific state:

| Waiter | Description |
|--------|-------------|
| `fleet-started` | Wait until fleet reaches RUNNING state |
| `fleet-stopped` | Wait until fleet reaches STOPPED state |

```bash
aws appstream wait fleet-started --name my-fleet
aws appstream wait fleet-stopped --name my-fleet
```
