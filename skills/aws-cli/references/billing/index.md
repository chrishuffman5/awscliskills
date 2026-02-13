# AWS CLI v2 -- Billing Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/billing/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-billing-view` | Billing View | Create a custom billing view |
| `delete-billing-view` | Billing View | Delete a billing view |
| `get-billing-view` | Billing View | Get billing view details and metadata |
| `list-billing-views` | Billing View | List billing views with optional filters (paginated) |
| `update-billing-view` | Billing View | Update a billing view name, description, or filters |
| `associate-source-views` | Billing View | Associate source views with a billing view |
| `disassociate-source-views` | Billing View | Remove source views from a billing view |
| `list-source-views-for-billing-view` | Billing View | List source views for a billing view (paginated) |
| `get-resource-policy` | Billing View | Get the resource policy for a billing view |
| `tag-resource` | Tags | Add tags to a billing resource |
| `untag-resource` | Tags | Remove tags from a billing resource |
| `list-tags-for-resource` | Tags | List tags on a billing resource |

---

## Global Options

These options are available on ALL `aws billing` commands.

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

### Billing View Types
| Type | Description |
|------|-------------|
| `PRIMARY` | Default billing view for the account |
| `BILLING_GROUP` | View for a billing group |
| `CUSTOM` | User-created custom billing view |
| `BILLING_TRANSFER` | Billing transfer view |
| `BILLING_TRANSFER_SHOWBACK` | Billing transfer showback view |

### Health Status Codes
| Status | Description |
|--------|-------------|
| `HEALTHY` | Billing view is healthy and functioning normally |
| `UNHEALTHY` | Billing view has issues |
| `CREATING` | Billing view is being created |
| `UPDATING` | Billing view is being updated |

### Health Status Reasons
| Reason | Description |
|--------|-------------|
| `SOURCE_VIEW_UNHEALTHY` | Source view is unhealthy |
| `SOURCE_VIEW_UPDATING` | Source view is being updated |
| `SOURCE_VIEW_ACCESS_DENIED` | Access denied to source view |
| `SOURCE_VIEW_NOT_FOUND` | Source view not found |
| `CYCLIC_DEPENDENCY` | Cyclic dependency detected |
| `SOURCE_VIEW_DEPTH_EXCEEDED` | Source view depth limit exceeded |
| `AGGREGATE_SOURCE` | Aggregate source issue |
| `VIEW_OWNER_NOT_MANAGEMENT_ACCOUNT` | View owner is not the management account |

### Data Filter Expression
Billing views support filtering by:
- **Dimensions**: `LINKED_ACCOUNT` with account ID values
- **Tags**: Tag key with tag values
- **Cost Categories**: Cost category key with values
- **Time Range**: `beginDateInclusive` and `endDateInclusive` timestamps
