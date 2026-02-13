# AWS CLI v2 -- CodeStar Connections & Notifications Command Reference Index

> Based on AWS CLI v2 documentation.
> Sources: https://docs.aws.amazon.com/cli/latest/reference/codestar-connections/ and https://docs.aws.amazon.com/cli/latest/reference/codestar-notifications/

---

## Quick Reference

| Command | CLI Service | Category | Description |
|---------|-------------|----------|-------------|
| `create-connection` | codestar-connections | Connection | Create a connection to a third-party provider |
| `delete-connection` | codestar-connections | Connection | Delete a connection |
| `get-connection` | codestar-connections | Connection | Get details of a connection |
| `list-connections` | codestar-connections | Connection | List connections |
| `create-host` | codestar-connections | Host | Create a host for a third-party provider |
| `delete-host` | codestar-connections | Host | Delete a host |
| `get-host` | codestar-connections | Host | Get details of a host |
| `list-hosts` | codestar-connections | Host | List hosts |
| `update-host` | codestar-connections | Host | Update a host |
| `create-repository-link` | codestar-connections | Repository Link | Create a repository link |
| `delete-repository-link` | codestar-connections | Repository Link | Delete a repository link |
| `get-repository-link` | codestar-connections | Repository Link | Get details of a repository link |
| `list-repository-links` | codestar-connections | Repository Link | List repository links |
| `update-repository-link` | codestar-connections | Repository Link | Update a repository link |
| `get-repository-sync-status` | codestar-connections | Repository Link | Get sync status for a repository |
| `list-repository-sync-definitions` | codestar-connections | Repository Link | List sync definitions for a repository |
| `create-sync-configuration` | codestar-connections | Sync | Create a sync configuration |
| `delete-sync-configuration` | codestar-connections | Sync | Delete a sync configuration |
| `get-sync-configuration` | codestar-connections | Sync | Get a sync configuration |
| `list-sync-configurations` | codestar-connections | Sync | List sync configurations |
| `update-sync-configuration` | codestar-connections | Sync | Update a sync configuration |
| `get-resource-sync-status` | codestar-connections | Sync | Get sync status for a resource |
| `get-sync-blocker-summary` | codestar-connections | Sync | Get summary of sync blockers |
| `update-sync-blocker` | codestar-connections | Sync | Update a sync blocker |
| `create-notification-rule` | codestar-notifications | Notification | Create a notification rule |
| `delete-notification-rule` | codestar-notifications | Notification | Delete a notification rule |
| `describe-notification-rule` | codestar-notifications | Notification | Describe a notification rule |
| `list-notification-rules` | codestar-notifications | Notification | List notification rules |
| `update-notification-rule` | codestar-notifications | Notification | Update a notification rule |
| `list-event-types` | codestar-notifications | Notification | List available event types |
| `subscribe` | codestar-notifications | Notification Target | Subscribe a target to a notification rule |
| `unsubscribe` | codestar-notifications | Notification Target | Unsubscribe a target from a notification rule |
| `list-targets` | codestar-notifications | Notification Target | List notification targets |
| `delete-target` | codestar-notifications | Notification Target | Delete a notification target |
| `tag-resource` | both | Tags | Add tags to a resource |
| `untag-resource` | both | Tags | Remove tags from a resource |
| `list-tags-for-resource` | both | Tags | List tags for a resource |

---

## Global Options

These options are available on ALL `aws codestar-connections` and `aws codestar-notifications` commands.

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

### Provider Types
| Provider | Description |
|----------|-------------|
| `Bitbucket` | Bitbucket Cloud |
| `GitHub` | GitHub |
| `GitHubEnterpriseServer` | GitHub Enterprise Server |
| `GitLab` | GitLab.com |
| `GitLabSelfManaged` | Self-managed GitLab |

### Connection Statuses
| Status | Description |
|--------|-------------|
| `PENDING` | Connection created but not yet authorized via console |
| `AVAILABLE` | Connection is authorized and ready to use |
| `ERROR` | Connection has an error |

### Sync Types
| Type | Description |
|------|-------------|
| `CFN_STACK_SYNC` | CloudFormation stack sync |

### Notification Detail Types
| Type | Description |
|------|-------------|
| `BASIC` | Basic notification with limited details |
| `FULL` | Full notification with all available details |

### Notification Target Types
| Type | Description |
|------|-------------|
| `SNS` | Amazon SNS topic |
| `AWSChatbotSlack` | AWS Chatbot (Slack) |
| `AWSChatbotMicrosoftTeams` | AWS Chatbot (Microsoft Teams) |
