# AWS CLI v2 -- Data Exchange Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/dataexchange/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-data-set` | Data Set | Create a new data set |
| `get-data-set` | Data Set | Get details of a data set |
| `list-data-sets` | Data Set | List data sets owned or entitled |
| `update-data-set` | Data Set | Update data set name or description |
| `delete-data-set` | Data Set | Delete a data set |
| `send-data-set-notification` | Data Set | Send a notification for a data set |
| `create-revision` | Revision | Create a revision in a data set |
| `get-revision` | Revision | Get details of a revision |
| `list-data-set-revisions` | Revision | List revisions for a data set |
| `update-revision` | Revision | Update or finalize a revision |
| `delete-revision` | Revision | Delete a revision |
| `revoke-revision` | Revision | Revoke subscriber access to a revision |
| `get-asset` | Asset | Get details of an asset |
| `list-revision-assets` | Asset | List assets in a revision |
| `update-asset` | Asset | Update asset name |
| `delete-asset` | Asset | Delete an asset |
| `send-api-asset` | Asset | Send a request to an API asset endpoint |
| `create-job` | Job | Create an import or export job |
| `start-job` | Job | Start a created job |
| `get-job` | Job | Get details and status of a job |
| `list-jobs` | Job | List jobs |
| `cancel-job` | Job | Cancel a running job |
| `create-data-grant` | Data Grant | Create a data grant for cross-account sharing |
| `get-data-grant` | Data Grant | Get details of a data grant |
| `list-data-grants` | Data Grant | List data grants sent |
| `delete-data-grant` | Data Grant | Delete a data grant |
| `accept-data-grant` | Data Grant | Accept a received data grant |
| `get-received-data-grant` | Data Grant | Get details of a received data grant |
| `list-received-data-grants` | Data Grant | List received data grants |
| `create-event-action` | Event Action | Create an event-triggered action |
| `get-event-action` | Event Action | Get details of an event action |
| `list-event-actions` | Event Action | List event actions |
| `update-event-action` | Event Action | Update an event action |
| `delete-event-action` | Event Action | Delete an event action |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

---

## Global Options

These options are available on ALL `aws dataexchange` commands.

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

### Asset Types
| Type | Description |
|------|-------------|
| `S3_SNAPSHOT` | S3 file snapshot assets |
| `REDSHIFT_DATA_SHARE` | Amazon Redshift data share |
| `API_GATEWAY_API` | API Gateway REST API |
| `S3_DATA_ACCESS` | S3 data access (direct bucket access) |
| `LAKE_FORMATION_DATA_PERMISSION` | Lake Formation tag-based permission |

### Job Types
| Type | Description |
|------|-------------|
| `IMPORT_ASSETS_FROM_S3` | Import files from S3 into a revision |
| `IMPORT_ASSET_FROM_SIGNED_URL` | Import a single file via signed URL |
| `EXPORT_ASSETS_TO_S3` | Export assets to S3 |
| `EXPORT_ASSET_TO_SIGNED_URL` | Export a single asset via signed URL |
| `EXPORT_REVISIONS_TO_S3` | Export entire revisions to S3 |
| `IMPORT_ASSETS_FROM_REDSHIFT_DATA_SHARES` | Import Redshift data shares |
| `IMPORT_ASSET_FROM_API_GATEWAY_API` | Import an API Gateway API |
| `CREATE_S3_DATA_ACCESS_FROM_S3_BUCKET` | Create S3 data access from a bucket |
| `IMPORT_ASSETS_FROM_LAKE_FORMATION_TAG_POLICY` | Import Lake Formation tag-based assets |

### Job States
| State | Description |
|-------|-------------|
| `WAITING` | Job created, not yet started |
| `IN_PROGRESS` | Job is running |
| `COMPLETED` | Job finished successfully |
| `ERROR` | Job failed |
| `CANCELLED` | Job was cancelled |
| `TIMED_OUT` | Job timed out |

### Data Grant Acceptance States
| State | Description |
|-------|-------------|
| `PENDING_RECEIVER_ACCEPTANCE` | Grant awaiting receiver acceptance |
| `ACCEPTED` | Grant has been accepted |
