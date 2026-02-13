# Resource Explorer — Quick Reference

## All Commands

| Command | Category | Description |
|---------|----------|-------------|
| `create-index` | Indexes | Create a local index in the current Region |
| `delete-index` | Indexes | Delete an index (turns off Resource Explorer in that Region) |
| `get-index` | Indexes | Get details of the index in the current Region |
| `list-indexes` | Indexes | List indexes across Regions (filterable by type) |
| `update-index-type` | Indexes | Promote local index to aggregator or demote |
| `list-indexes-for-members` | Indexes | List indexes for specified Organization member accounts |
| `get-service-index` | Indexes | Get the service-managed index in the current Region |
| `list-service-indexes` | Indexes | List service-managed indexes across Regions |
| `create-view` | Views | Create a view with optional filters and included properties |
| `delete-view` | Views | Delete a view |
| `get-view` | Views | Get details of a specific view |
| `list-views` | Views | List view ARNs in the current Region |
| `update-view` | Views | Update view filters or included properties |
| `batch-get-view` | Views | Get details for multiple views at once (up to 20) |
| `get-managed-view` | Views | Get details of an AWS-managed view |
| `list-managed-views` | Views | List AWS-managed view ARNs |
| `get-service-view` | Views | Get details of a service-managed view |
| `list-service-views` | Views | List service-managed view ARNs |
| `associate-default-view` | Views | Set a view as default for the Region |
| `disassociate-default-view` | Views | Remove the default view for the Region |
| `get-default-view` | Views | Get the ARN of the current default view |
| `search` | Search | Search resources using query string and view |
| `list-resources` | Search | List resources matching filter criteria |
| `list-supported-resource-types` | Search | List all resource types Resource Explorer supports |
| `create-resource-explorer-setup` | Setup | Set up Resource Explorer across multiple Regions |
| `delete-resource-explorer-setup` | Setup | Delete Resource Explorer setup across Regions |
| `get-resource-explorer-setup` | Setup | Get status of a setup/deletion task |
| `get-account-level-service-configuration` | Setup | Get Organization service access configuration |
| `list-streaming-access-for-services` | Setup | List services with streaming access |
| `tag-resource` | Tags | Add tags to a Resource Explorer resource |
| `untag-resource` | Tags | Remove tags from a Resource Explorer resource |
| `list-tags-for-resource` | Tags | List tags on a Resource Explorer resource |

## Global Options

| Option | Description |
|--------|-------------|
| `--output` | `json`, `text`, `table`, `yaml`, `yaml-stream` |
| `--query` | JMESPath query for filtering response |
| `--region` | AWS Region |
| `--profile` | Named credential profile |
| `--no-paginate` | Disable automatic pagination |
| `--max-items` | Limit total items returned (paginated commands) |
| `--page-size` | Items per API call (paginated commands) |

## Common Patterns

**Index Types:**
- `LOCAL` — Indexes resources only in the Region where the index exists
- `AGGREGATOR` — Receives replicated resource data from all other Regions (one per account)

**Index States:** `CREATING`, `ACTIVE`, `DELETING`, `DELETED`, `UPDATING`

**Search Query Syntax:**
- Free text: `my-bucket` (searches across all fields)
- Service filter: `service:ec2`
- Resource type: `resourcetype:ec2:instance`
- Region: `region:us-east-1`
- Tag: `tag:Environment=Production`
- Negation: `-service:s3`
- Combine: `service:ec2 region:us-west-2 tag:Team=Platform`

**View Filters:** Use `FilterString` with the same query syntax as search. Filters are ANDed with the search query.
