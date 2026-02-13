# AWS CLI v2 -- EventBridge Command Reference Index

> Based on AWS CLI v2 documentation. Sources: https://docs.aws.amazon.com/cli/latest/reference/events/ , https://docs.aws.amazon.com/cli/latest/reference/schemas/ , https://docs.aws.amazon.com/cli/latest/reference/pipes/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `events create-event-bus` | Event Bus | Create a new event bus |
| `events delete-event-bus` | Event Bus | Delete an event bus |
| `events describe-event-bus` | Event Bus | Describe an event bus |
| `events list-event-buses` | Event Bus | List all event buses |
| `events put-events` | Event Bus | Put one or more events on an event bus |
| `events put-partner-events` | Event Bus | Put events from a partner event source |
| `events put-rule` | Rule | Create or update a rule |
| `events delete-rule` | Rule | Delete a rule |
| `events describe-rule` | Rule | Describe a rule |
| `events disable-rule` | Rule | Disable a rule |
| `events enable-rule` | Rule | Enable a rule |
| `events list-rules` | Rule | List rules on an event bus |
| `events list-rule-names-by-target` | Rule | List rules associated with a target |
| `events test-event-pattern` | Rule | Test whether an event matches a pattern |
| `events put-targets` | Target | Add targets to a rule |
| `events remove-targets` | Target | Remove targets from a rule |
| `events list-targets-by-rule` | Target | List targets for a rule |
| `events create-archive` | Archive | Create an archive of events |
| `events delete-archive` | Archive | Delete an archive |
| `events describe-archive` | Archive | Describe an archive |
| `events list-archives` | Archive | List archives |
| `events update-archive` | Archive | Update an archive |
| `events start-replay` | Replay | Start an event replay from an archive |
| `events cancel-replay` | Replay | Cancel a running replay |
| `events describe-replay` | Replay | Describe a replay |
| `events list-replays` | Replay | List replays |
| `events create-connection` | Connection | Create a connection for API destinations |
| `events delete-connection` | Connection | Delete a connection |
| `events describe-connection` | Connection | Describe a connection |
| `events list-connections` | Connection | List connections |
| `events update-connection` | Connection | Update a connection |
| `events deauthorize-connection` | Connection | Reset a connection's authorization credentials |
| `events create-api-destination` | API Destination | Create an API destination |
| `events delete-api-destination` | API Destination | Delete an API destination |
| `events describe-api-destination` | API Destination | Describe an API destination |
| `events list-api-destinations` | API Destination | List API destinations |
| `events update-api-destination` | API Destination | Update an API destination |
| `schemas create-schema` | Schema | Create a schema |
| `schemas delete-schema` | Schema | Delete a schema |
| `schemas describe-schema` | Schema | Describe a schema |
| `schemas list-schemas` | Schema | List schemas in a registry |
| `schemas update-schema` | Schema | Update a schema |
| `schemas search-schemas` | Schema | Search schemas by keyword |
| `schemas export-schema` | Schema | Export a schema |
| `schemas create-registry` | Schema | Create a schema registry |
| `schemas delete-registry` | Schema | Delete a schema registry |
| `schemas describe-registry` | Schema | Describe a schema registry |
| `schemas list-registries` | Schema | List schema registries |
| `schemas update-registry` | Schema | Update a schema registry |
| `schemas create-discoverer` | Schema | Create a schema discoverer |
| `schemas delete-discoverer` | Schema | Delete a schema discoverer |
| `schemas describe-discoverer` | Schema | Describe a schema discoverer |
| `schemas list-discoverers` | Schema | List schema discoverers |
| `schemas start-discoverer` | Schema | Start schema discovery |
| `schemas stop-discoverer` | Schema | Stop schema discovery |
| `pipes create-pipe` | Pipe | Create a pipe |
| `pipes delete-pipe` | Pipe | Delete a pipe |
| `pipes describe-pipe` | Pipe | Describe a pipe |
| `pipes list-pipes` | Pipe | List pipes |
| `pipes start-pipe` | Pipe | Start a stopped pipe |
| `pipes stop-pipe` | Pipe | Stop a running pipe |
| `pipes update-pipe` | Pipe | Update a pipe |
| `events tag-resource` | Tags | Add tags to a resource |
| `events untag-resource` | Tags | Remove tags from a resource |
| `events list-tags-for-resource` | Tags | List tags for a resource |

---

## Global Options

These options are available on ALL `aws events`, `aws schemas`, and `aws pipes` commands.

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

### Rule States
| State | Description |
|-------|-------------|
| `ENABLED` | Rule is active and matches events |
| `DISABLED` | Rule is inactive |
| `ENABLED_WITH_ALL_CLOUDTRAIL_MANAGEMENT_EVENTS` | Enabled for all CloudTrail management events |

### Replay States
| State | Description |
|-------|-------------|
| `STARTING` | Replay is starting |
| `RUNNING` | Replay is in progress |
| `CANCELLING` | Replay is being cancelled |
| `COMPLETED` | Replay finished successfully |
| `CANCELLED` | Replay was cancelled |
| `FAILED` | Replay failed |

### Connection Authorization Types
| Type | Description |
|------|-------------|
| `BASIC` | Basic (username/password) authentication |
| `OAUTH_CLIENT_CREDENTIALS` | OAuth 2.0 client credentials flow |
| `API_KEY` | API key authentication |

### Connection States
| State | Description |
|-------|-------------|
| `CREATING` | Connection is being created |
| `UPDATING` | Connection is being updated |
| `DELETING` | Connection is being deleted |
| `AUTHORIZED` | Connection is authorized |
| `DEAUTHORIZED` | Connection credentials have been reset |
| `AUTHORIZING` | Connection is being authorized |
| `DEAUTHORIZING` | Connection is being deauthorized |

### Pipe States
| State | Description |
|-------|-------------|
| `RUNNING` | Pipe is actively processing events |
| `STOPPED` | Pipe is stopped |
| `CREATING` | Pipe is being created |
| `UPDATING` | Pipe is being updated |
| `DELETING` | Pipe is being deleted |
| `STARTING` | Pipe is starting |
| `STOPPING` | Pipe is stopping |
| `CREATE_FAILED` | Pipe creation failed |
| `UPDATE_FAILED` | Pipe update failed |
| `START_FAILED` | Pipe failed to start |
| `STOP_FAILED` | Pipe failed to stop |
| `DELETE_FAILED` | Pipe deletion failed |

### Event Pattern Examples

**Match EC2 instance state changes:**
```json
{
    "source": ["aws.ec2"],
    "detail-type": ["EC2 Instance State-change Notification"],
    "detail": {
        "state": ["running", "stopped"]
    }
}
```

**Match S3 object creation:**
```json
{
    "source": ["aws.s3"],
    "detail-type": ["Object Created"],
    "detail": {
        "bucket": { "name": ["my-bucket"] }
    }
}
```
