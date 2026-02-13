# AWS CLI v2 -- CloudTrail Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/cloudtrail/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-trail` | Trail | Create a new trail |
| `delete-trail` | Trail | Delete a trail |
| `describe-trails` | Trail | Describe one or more trails |
| `get-trail` | Trail | Get settings for a trail |
| `list-trails` | Trail | List all trails in the account |
| `update-trail` | Trail | Update trail configuration |
| `start-logging` | Trail | Start logging for a trail |
| `stop-logging` | Trail | Stop logging for a trail |
| `get-trail-status` | Events | Get the status of a trail |
| `lookup-events` | Events | Look up management and data events |
| `get-event-selectors` | Event Selectors | Get event selectors for a trail |
| `put-event-selectors` | Event Selectors | Set event selectors for a trail |
| `get-insight-selectors` | Event Selectors | Get insight selectors for a trail |
| `put-insight-selectors` | Event Selectors | Set insight selectors for a trail |
| `create-event-data-store` | Event Data Store | Create a CloudTrail Lake event data store |
| `delete-event-data-store` | Event Data Store | Delete an event data store |
| `describe-event-data-store` | Event Data Store | Describe an event data store |
| `get-event-data-store` | Event Data Store | Get event data store details |
| `list-event-data-stores` | Event Data Store | List event data stores |
| `update-event-data-store` | Event Data Store | Update an event data store |
| `restore-event-data-store` | Event Data Store | Restore a deleted event data store |
| `enable-federation` | Event Data Store | Enable federation on an event data store |
| `disable-federation` | Event Data Store | Disable federation on an event data store |
| `start-query` | Query | Start a CloudTrail Lake query |
| `describe-query` | Query | Get metadata about a query |
| `get-query-results` | Query | Get results of a completed query |
| `list-queries` | Query | List queries for an event data store |
| `cancel-query` | Query | Cancel a running query |
| `create-channel` | Channel | Create a channel for CloudTrail Lake |
| `delete-channel` | Channel | Delete a channel |
| `get-channel` | Channel | Get channel details |
| `list-channels` | Channel | List channels |
| `update-channel` | Channel | Update a channel |
| `create-import` | Import | Create an import from S3 |
| `get-import` | Import | Get import details |
| `list-imports` | Import | List imports |
| `start-import` | Import | Start or restart an import |
| `add-tags` | Tags | Add tags to a resource |
| `remove-tags` | Tags | Remove tags from a resource |
| `list-tags` | Tags | List tags for resources |

---

## Global Options

These options are available on ALL `aws cloudtrail` commands.

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

### Trail Types
| Type | Description |
|------|-------------|
| Single-region | Records events only in the region where created |
| Multi-region | Records events in all AWS regions |
| Organization | Records events for all accounts in an AWS Organization |

### Event Categories
| Category | Description |
|----------|-------------|
| Management events | Control plane operations (e.g., CreateBucket, RunInstances) |
| Data events | Data plane operations (e.g., GetObject, PutItem) |
| Insights events | Anomalous API activity patterns |
| Network activity events | Network-level events via VPC endpoints |

### Event Data Store Status Values
| Status | Description |
|--------|-------------|
| `CREATED` | Event data store is active and accepting events |
| `ENABLED` | Event data store is enabled |
| `PENDING_DELETION` | Marked for deletion (restorable within retention window) |
| `STARTING_INGESTION` | Starting to ingest events |
| `STOPPING_INGESTION` | Stopping event ingestion |
| `STOPPED_INGESTION` | Event ingestion stopped |

### Query Status Values
| Status | Description |
|--------|-------------|
| `QUEUED` | Query is queued |
| `RUNNING` | Query is executing |
| `FINISHED` | Query completed successfully |
| `FAILED` | Query failed |
| `CANCELLED` | Query was cancelled |
| `TIMED_OUT` | Query timed out |

### Import Status Values
| Status | Description |
|--------|-------------|
| `INITIALIZING` | Import is initializing |
| `IN_PROGRESS` | Import is running |
| `FAILED` | Import failed |
| `STOPPED` | Import was stopped |
| `COMPLETED` | Import completed successfully |

### Lookup Attribute Keys
| Key | Description |
|-----|-------------|
| `EventId` | Event ID |
| `EventName` | Event name (e.g., `RunInstances`) |
| `ReadOnly` | Read-only status (`true` or `false`) |
| `Username` | IAM user name |
| `ResourceType` | Resource type (e.g., `AWS::EC2::Instance`) |
| `ResourceName` | Resource name or ID |
| `EventSource` | Event source (e.g., `ec2.amazonaws.com`) |
| `AccessKeyId` | Access key ID used |
