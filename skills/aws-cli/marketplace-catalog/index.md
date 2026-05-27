# AWS CLI v2 -- Marketplace Catalog Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/marketplace-catalog/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `describe-entity` | Entity | Describe metadata and content of a single entity |
| `list-entities` | Entity | List entities of a given type (paginated) |
| `batch-describe-entities` | Entity | Describe multiple entities in a single batch call |
| `start-change-set` | Change Set | Create and start a new change set for entity updates |
| `cancel-change-set` | Change Set | Cancel a pending change set before it applies |
| `describe-change-set` | Change Set | Get details and status of a change set |
| `list-change-sets` | Change Set | List change sets with optional filters (paginated) |
| `get-resource-policy` | Resource Policy | Retrieve a resource-based policy on an entity |
| `put-resource-policy` | Resource Policy | Attach or update a resource-based policy on an entity |
| `delete-resource-policy` | Resource Policy | Delete a resource-based policy from an entity |
| `tag-resource` | Tags | Add tags to an entity or change set |
| `untag-resource` | Tags | Remove tags from an entity or change set |
| `list-tags-for-resource` | Tags | List tags on an entity or change set |

---

## Global Options

These options are available on ALL `aws marketplace-catalog` commands.

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

### Catalog Value
All Marketplace Catalog API calls require `--catalog AWSMarketplace`. This is always the fixed string `AWSMarketplace`.

### Entity Types
| Entity Type | Description |
|-------------|-------------|
| `AmiProduct` | AMI-based product listing |
| `ContainerProduct` | Container-based product listing |
| `DataProduct` | Data product listing |
| `SaaSProduct` | SaaS product listing |
| `Offer` | Pricing offer for a product |
| `OfferSet` | Group of related offers |
| `ResaleAuthorization` | Resale authorization for channel partners |
| `Seller` | Seller profile |
| `Experience` | Private Marketplace experience |
| `Audience` | Private Marketplace audience |
| `BrandingSettings` | Private Marketplace branding |
| `ProcurementPolicy` | Private Marketplace procurement policy |
| `Solution` | Partner solution entity |

### Change Set Statuses
| Status | Description |
|--------|-------------|
| `PREPARING` | Change set is being prepared |
| `APPLYING` | Change set is being applied (cannot cancel) |
| `SUCCEEDED` | Change set completed successfully |
| `CANCELLED` | Change set was cancelled |
| `FAILED` | Change set failed |

### Change Set Failure Codes
| Code | Description |
|------|-------------|
| `CLIENT_ERROR` | Error in the change request |
| `SERVER_FAULT` | Internal service error |

### Entity Identifier Format
Entities use the format `EntityId@RevisionId` for versioned references and plain `EntityId` for latest.
