# AWS CLI v2 -- Kendra Command Reference Index

> Based on AWS CLI v2 documentation. Sources: https://docs.aws.amazon.com/cli/latest/reference/kendra/ and https://docs.aws.amazon.com/cli/latest/reference/kendra-ranking/

---

## Quick Reference — `aws kendra`

| Command | Category | Description |
|---------|----------|-------------|
| `create-index` | Index | Create a new Kendra index |
| `delete-index` | Index | Delete a Kendra index |
| `describe-index` | Index | Get details about an index |
| `list-indices` | Index | List all indexes in the account |
| `update-index` | Index | Update index settings and capacity |
| `create-data-source` | Data Source | Create a data source connector |
| `delete-data-source` | Data Source | Delete a data source |
| `describe-data-source` | Data Source | Get data source details |
| `list-data-sources` | Data Source | List data sources for an index |
| `update-data-source` | Data Source | Update data source configuration |
| `start-data-source-sync-job` | Data Source | Start a sync job for a data source |
| `stop-data-source-sync-job` | Data Source | Stop a running sync job |
| `list-data-source-sync-jobs` | Data Source | List sync job history |
| `batch-put-document` | Document | Add documents directly to an index |
| `batch-delete-document` | Document | Remove documents from an index |
| `batch-get-document-status` | Document | Get ingestion status of documents |
| `query` | Search | Search the index with natural language |
| `retrieve` | Search | Retrieve relevant passages (for RAG/LLM) |
| `get-snapshots` | Search | Get search analytics snapshots |
| `submit-feedback` | Search | Submit relevance feedback for a query |
| `create-faq` | FAQ | Add an FAQ to an index |
| `delete-faq` | FAQ | Delete an FAQ |
| `describe-faq` | FAQ | Get FAQ details |
| `list-faqs` | FAQ | List FAQs for an index |
| `create-thesaurus` | Thesaurus | Create a thesaurus for synonym matching |
| `delete-thesaurus` | Thesaurus | Delete a thesaurus |
| `describe-thesaurus` | Thesaurus | Get thesaurus details |
| `list-thesauri` | Thesaurus | List thesauri for an index |
| `update-thesaurus` | Thesaurus | Update a thesaurus |
| `get-query-suggestions` | Query Suggestions | Get query suggestions as user types |
| `describe-query-suggestions-config` | Query Suggestions | Get query suggestions configuration |
| `update-query-suggestions-config` | Query Suggestions | Update query suggestions settings |
| `clear-query-suggestions` | Query Suggestions | Clear all query suggestion history |
| `create-query-suggestions-block-list` | Query Suggestions | Create a block list for suggestions |
| `delete-query-suggestions-block-list` | Query Suggestions | Delete a block list |
| `describe-query-suggestions-block-list` | Query Suggestions | Get block list details |
| `list-query-suggestions-block-lists` | Query Suggestions | List block lists for an index |
| `update-query-suggestions-block-list` | Query Suggestions | Update a block list |
| `create-featured-results-set` | Featured Results | Create a featured results set |
| `delete-featured-results-set` | Featured Results | Delete a featured results set |
| `describe-featured-results-set` | Featured Results | Get featured results set details |
| `list-featured-results-sets` | Featured Results | List featured results sets |
| `update-featured-results-set` | Featured Results | Update a featured results set |
| `create-access-control-configuration` | Access Control | Create document access control config |
| `delete-access-control-configuration` | Access Control | Delete access control config |
| `describe-access-control-configuration` | Access Control | Get access control config details |
| `list-access-control-configurations` | Access Control | List access control configs |
| `update-access-control-configuration` | Access Control | Update access control config |
| `put-principal-mapping` | Access Control | Map users to groups for access control |
| `delete-principal-mapping` | Access Control | Delete principal mapping |
| `describe-principal-mapping` | Access Control | Get principal mapping details |
| `list-groups-older-than-ordering-id` | Access Control | List groups with outdated mappings |
| `create-experience` | Experience | Create a search experience |
| `delete-experience` | Experience | Delete a search experience |
| `describe-experience` | Experience | Get experience details |
| `list-experiences` | Experience | List experiences for an index |
| `update-experience` | Experience | Update an experience |
| `associate-entities-to-experience` | Experience | Associate users/groups to an experience |
| `disassociate-entities-from-experience` | Experience | Remove users/groups from an experience |
| `list-experience-entities` | Experience | List entities in an experience |
| `associate-personas-to-entities` | Experience | Assign personas to experience entities |
| `disassociate-personas-from-entities` | Experience | Remove personas from entities |
| `list-entity-personas` | Experience | List personas for an entity |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

## Quick Reference — `aws kendra-ranking`

| Command | Category | Description |
|---------|----------|-------------|
| `create-rescore-execution-plan` | Ranking | Create a rescore execution plan |
| `delete-rescore-execution-plan` | Ranking | Delete a rescore execution plan |
| `describe-rescore-execution-plan` | Ranking | Get plan details |
| `list-rescore-execution-plans` | Ranking | List all plans |
| `update-rescore-execution-plan` | Ranking | Update a plan |
| `rescore` | Ranking | Re-rank search results using semantic search |
| `tag-resource` | Tags | Add tags to a ranking resource |
| `untag-resource` | Tags | Remove tags from a ranking resource |
| `list-tags-for-resource` | Tags | List tags for a ranking resource |

---

## Global Options

These options are available on ALL `aws kendra` and `aws kendra-ranking` commands.

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
| `--cli-binary-format` | string | `base64` | Format for binary blob input |
| `--no-cli-pager` | boolean | false | Disable the output pager |
| `--cli-auto-prompt` | boolean | false | Auto-prompt for missing parameters |
| `--no-cli-auto-prompt` | boolean | false | Disable auto-prompt |
| `--cli-input-json` | string | -- | Read arguments from a JSON string or `file://` path |
| `--cli-input-yaml` | string | -- | Read arguments from a YAML string or `file://` path |
| `--generate-cli-skeleton` | string | -- | Print input/output skeleton |

---

## Common Patterns

### Index Editions
| Edition | Description |
|---------|-------------|
| `DEVELOPER_EDITION` | For development and testing (lower cost) |
| `ENTERPRISE_EDITION` | For production workloads |
| `GEN_AI_ENTERPRISE_EDITION` | Enterprise with generative AI features |

### Index Status Values
| Status | Description |
|--------|-------------|
| `CREATING` | Index is being created |
| `ACTIVE` | Index is ready for use |
| `DELETING` | Index is being deleted |
| `FAILED` | Index creation failed |
| `UPDATING` | Index is being updated |
| `SYSTEM_UPDATING` | System update in progress |

### Data Source Types
`S3`, `SHAREPOINT`, `DATABASE`, `SALESFORCE`, `ONEDRIVE`, `SERVICENOW`, `CUSTOM`, `CONFLUENCE`, `GOOGLEDRIVE`, `WEBCRAWLER`, `WORKDOCS`, `FSX`, `SLACK`, `BOX`, `QUIP`, `JIRA`, `GITHUB`, `ALFRESCO`, `TEMPLATE`

### Score Confidence Levels
| Level | Description |
|-------|-------------|
| `VERY_HIGH` | Highest confidence result |
| `HIGH` | High confidence result |
| `MEDIUM` | Medium confidence result |
| `LOW` | Lower confidence result |
| `NOT_AVAILABLE` | Score not available |
