# AWS CLI v2 -- QuickSight Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/quicksight/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-account-customization` | Account | Create account customization |
| `describe-account-customization` | Account | Describe account customization |
| `update-account-customization` | Account | Update account customization |
| `delete-account-customization` | Account | Delete account customization |
| `describe-account-settings` | Account | Describe account settings |
| `update-account-settings` | Account | Update account settings |
| `describe-account-subscription` | Account | Describe account subscription |
| `create-account-subscription` | Account | Create account subscription |
| `delete-account-subscription` | Account | Delete account subscription |
| `create-dashboard` | Dashboard | Create a dashboard |
| `describe-dashboard` | Dashboard | Describe a dashboard |
| `describe-dashboard-definition` | Dashboard | Describe dashboard definition |
| `update-dashboard` | Dashboard | Update a dashboard |
| `delete-dashboard` | Dashboard | Delete a dashboard |
| `list-dashboards` | Dashboard | List dashboards |
| `list-dashboard-versions` | Dashboard | List dashboard versions |
| `search-dashboards` | Dashboard | Search dashboards |
| `update-dashboard-published-version` | Dashboard | Update published version |
| `update-dashboard-links` | Dashboard | Update dashboard links |
| `describe-dashboard-permissions` | Dashboard | Describe dashboard permissions |
| `update-dashboard-permissions` | Dashboard | Update dashboard permissions |
| `describe-dashboards-qa-configuration` | Dashboard | Describe QA configuration |
| `update-dashboards-qa-configuration` | Dashboard | Update QA configuration |
| `start-dashboard-snapshot-job` | Snapshot | Start a dashboard snapshot job |
| `describe-dashboard-snapshot-job` | Snapshot | Describe snapshot job |
| `describe-dashboard-snapshot-job-result` | Snapshot | Get snapshot job results |
| `start-dashboard-snapshot-job-schedule` | Snapshot | Start snapshot schedule |
| `create-analysis` | Analysis | Create an analysis |
| `describe-analysis` | Analysis | Describe an analysis |
| `describe-analysis-definition` | Analysis | Describe analysis definition |
| `update-analysis` | Analysis | Update an analysis |
| `delete-analysis` | Analysis | Delete an analysis |
| `list-analyses` | Analysis | List analyses |
| `search-analyses` | Analysis | Search analyses |
| `restore-analysis` | Analysis | Restore a deleted analysis |
| `describe-analysis-permissions` | Analysis | Describe analysis permissions |
| `update-analysis-permissions` | Analysis | Update analysis permissions |
| `create-template` | Template | Create a template |
| `describe-template` | Template | Describe a template |
| `describe-template-definition` | Template | Describe template definition |
| `update-template` | Template | Update a template |
| `delete-template` | Template | Delete a template |
| `list-templates` | Template | List templates |
| `list-template-versions` | Template | List template versions |
| `describe-template-permissions` | Template | Describe template permissions |
| `update-template-permissions` | Template | Update template permissions |
| `create-template-alias` | Template | Create template alias |
| `describe-template-alias` | Template | Describe template alias |
| `update-template-alias` | Template | Update template alias |
| `delete-template-alias` | Template | Delete template alias |
| `list-template-aliases` | Template | List template aliases |
| `create-theme` | Theme | Create a theme |
| `describe-theme` | Theme | Describe a theme |
| `update-theme` | Theme | Update a theme |
| `delete-theme` | Theme | Delete a theme |
| `list-themes` | Theme | List themes |
| `list-theme-versions` | Theme | List theme versions |
| `describe-theme-permissions` | Theme | Describe theme permissions |
| `update-theme-permissions` | Theme | Update theme permissions |
| `create-theme-alias` | Theme | Create theme alias |
| `describe-theme-alias` | Theme | Describe theme alias |
| `update-theme-alias` | Theme | Update theme alias |
| `delete-theme-alias` | Theme | Delete theme alias |
| `list-theme-aliases` | Theme | List theme aliases |
| `create-data-set` | Data Set | Create a data set |
| `describe-data-set` | Data Set | Describe a data set |
| `update-data-set` | Data Set | Update a data set |
| `delete-data-set` | Data Set | Delete a data set |
| `list-data-sets` | Data Set | List data sets |
| `search-data-sets` | Data Set | Search data sets |
| `describe-data-set-permissions` | Data Set | Describe data set permissions |
| `update-data-set-permissions` | Data Set | Update data set permissions |
| `describe-data-set-refresh-properties` | Data Set | Describe refresh properties |
| `put-data-set-refresh-properties` | Data Set | Set refresh properties |
| `delete-data-set-refresh-properties` | Data Set | Delete refresh properties |
| `create-data-source` | Data Source | Create a data source |
| `describe-data-source` | Data Source | Describe a data source |
| `update-data-source` | Data Source | Update a data source |
| `delete-data-source` | Data Source | Delete a data source |
| `list-data-sources` | Data Source | List data sources |
| `search-data-sources` | Data Source | Search data sources |
| `describe-data-source-permissions` | Data Source | Describe data source permissions |
| `update-data-source-permissions` | Data Source | Update data source permissions |
| `create-ingestion` | Ingestion | Create a SPICE ingestion |
| `describe-ingestion` | Ingestion | Describe an ingestion |
| `list-ingestions` | Ingestion | List ingestions |
| `cancel-ingestion` | Ingestion | Cancel an ingestion |
| `create-refresh-schedule` | Ingestion | Create a refresh schedule |
| `describe-refresh-schedule` | Ingestion | Describe a refresh schedule |
| `update-refresh-schedule` | Ingestion | Update a refresh schedule |
| `delete-refresh-schedule` | Ingestion | Delete a refresh schedule |
| `list-refresh-schedules` | Ingestion | List refresh schedules |
| `create-folder` | Folder | Create a folder |
| `describe-folder` | Folder | Describe a folder |
| `update-folder` | Folder | Update a folder |
| `delete-folder` | Folder | Delete a folder |
| `list-folders` | Folder | List folders |
| `search-folders` | Folder | Search folders |
| `create-folder-membership` | Folder | Add member to folder |
| `delete-folder-membership` | Folder | Remove folder membership |
| `list-folder-members` | Folder | List folder members |
| `list-folders-for-resource` | Folder | List folders for a resource |
| `describe-folder-permissions` | Folder | Describe folder permissions |
| `describe-folder-resolved-permissions` | Folder | Describe resolved permissions |
| `update-folder-permissions` | Folder | Update folder permissions |
| `register-user` | User | Register a new user |
| `describe-user` | User | Describe a user |
| `update-user` | User | Update a user |
| `delete-user` | User | Delete a user |
| `delete-user-by-principal-id` | User | Delete user by principal ID |
| `list-users` | User | List users |
| `create-group` | Group | Create a group |
| `describe-group` | Group | Describe a group |
| `update-group` | Group | Update a group |
| `delete-group` | Group | Delete a group |
| `list-groups` | Group | List groups |
| `search-groups` | Group | Search groups |
| `create-group-membership` | Group | Add user to group |
| `describe-group-membership` | Group | Describe group membership |
| `delete-group-membership` | Group | Remove group membership |
| `list-group-memberships` | Group | List group memberships |
| `list-user-groups` | Group | List groups for a user |
| `create-namespace` | Namespace | Create a namespace |
| `describe-namespace` | Namespace | Describe a namespace |
| `delete-namespace` | Namespace | Delete a namespace |
| `list-namespaces` | Namespace | List namespaces |
| `create-iam-policy-assignment` | IAM | Create IAM policy assignment |
| `describe-iam-policy-assignment` | IAM | Describe IAM policy assignment |
| `update-iam-policy-assignment` | IAM | Update IAM policy assignment |
| `delete-iam-policy-assignment` | IAM | Delete IAM policy assignment |
| `list-iam-policy-assignments` | IAM | List IAM policy assignments |
| `list-iam-policy-assignments-for-user` | IAM | List assignments for a user |
| `create-role-membership` | IAM | Add role membership |
| `delete-role-membership` | IAM | Delete role membership |
| `list-role-memberships` | IAM | List role memberships |
| `create-topic` | Topic | Create a Q topic |
| `describe-topic` | Topic | Describe a topic |
| `update-topic` | Topic | Update a topic |
| `delete-topic` | Topic | Delete a topic |
| `list-topics` | Topic | List topics |
| `search-topics` | Topic | Search topics |
| `describe-topic-permissions` | Topic | Describe topic permissions |
| `update-topic-permissions` | Topic | Update topic permissions |
| `describe-topic-refresh` | Topic | Describe topic refresh |
| `describe-topic-refresh-schedule` | Topic | Describe topic refresh schedule |
| `update-topic-refresh-schedule` | Topic | Update topic refresh schedule |
| `list-topic-refresh-schedules` | Topic | List topic refresh schedules |
| `batch-create-topic-reviewed-answer` | Topic | Create reviewed answers |
| `batch-delete-topic-reviewed-answer` | Topic | Delete reviewed answers |
| `list-topic-reviewed-answers` | Topic | List reviewed answers |
| `create-vpc-connection` | VPC | Create VPC connection |
| `describe-vpc-connection` | VPC | Describe VPC connection |
| `update-vpc-connection` | VPC | Update VPC connection |
| `delete-vpc-connection` | VPC | Delete VPC connection |
| `list-vpc-connections` | VPC | List VPC connections |
| `generate-embed-url-for-registered-user` | Embedding | Generate embed URL for registered user |
| `generate-embed-url-for-registered-user-with-identity` | Embedding | Generate embed URL with identity |
| `generate-embed-url-for-anonymous-user` | Embedding | Generate embed URL for anonymous user |
| `get-dashboard-embed-url` | Embedding | Get dashboard embed URL |
| `get-session-embed-url` | Embedding | Get session embed URL |
| `start-asset-bundle-export-job` | Asset Bundle | Start export job |
| `describe-asset-bundle-export-job` | Asset Bundle | Describe export job |
| `list-asset-bundle-export-jobs` | Asset Bundle | List export jobs |
| `start-asset-bundle-import-job` | Asset Bundle | Start import job |
| `describe-asset-bundle-import-job` | Asset Bundle | Describe import job |
| `list-asset-bundle-import-jobs` | Asset Bundle | List import jobs |
| `create-brand` | Brand | Create a brand |
| `describe-brand` | Brand | Describe a brand |
| `update-brand` | Brand | Update a brand |
| `delete-brand` | Brand | Delete a brand |
| `list-brands` | Brand | List brands |
| `describe-brand-assignment` | Brand | Describe brand assignment |
| `update-brand-assignment` | Brand | Update brand assignment |
| `delete-brand-assignment` | Brand | Delete brand assignment |
| `describe-brand-published-version` | Brand | Describe published version |
| `update-brand-published-version` | Brand | Update published version |
| `create-action-connector` | Action Connector | Create action connector |
| `describe-action-connector` | Action Connector | Describe action connector |
| `update-action-connector` | Action Connector | Update action connector |
| `delete-action-connector` | Action Connector | Delete action connector |
| `list-action-connectors` | Action Connector | List action connectors |
| `search-action-connectors` | Action Connector | Search action connectors |
| `describe-action-connector-permissions` | Action Connector | Describe permissions |
| `update-action-connector-permissions` | Action Connector | Update permissions |
| `create-custom-permissions` | Custom Permissions | Create custom permissions |
| `describe-custom-permissions` | Custom Permissions | Describe custom permissions |
| `update-custom-permissions` | Custom Permissions | Update custom permissions |
| `delete-custom-permissions` | Custom Permissions | Delete custom permissions |
| `list-custom-permissions` | Custom Permissions | List custom permissions |
| `describe-ip-restriction` | Identity & Security | Describe IP restriction |
| `update-ip-restriction` | Identity & Security | Update IP restriction |
| `describe-key-registration` | Identity & Security | Describe key registration |
| `update-key-registration` | Identity & Security | Update key registration |
| `list-identity-propagation-configs` | Identity & Security | List identity propagation configs |
| `update-identity-propagation-config` | Identity & Security | Update identity propagation config |
| `delete-identity-propagation-config` | Identity & Security | Delete identity propagation config |
| `update-public-sharing-settings` | Identity & Security | Update public sharing settings |
| `get-identity-context` | Identity & Security | Get identity context |
| `list-tags-for-resource` | Tags | List tags for a resource |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-flows` | Flow | List flows |
| `search-flows` | Flow | Search flows |
| `get-flow-metadata` | Flow | Get flow metadata |
| `get-flow-permissions` | Flow | Get flow permissions |
| `update-flow-permissions` | Flow | Update flow permissions |

---

## Global Options

These options are available on ALL `aws quicksight` commands.

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

### User Roles
| Role | Description |
|------|-------------|
| `ADMIN` | Full administrative access |
| `AUTHOR` | Can create analyses and dashboards |
| `READER` | Can view dashboards |
| `ADMIN_PRO` | Admin with pro features |
| `AUTHOR_PRO` | Author with pro features |
| `READER_PRO` | Reader with pro features |

### Identity Types
| Type | Description |
|------|-------------|
| `IAM` | IAM user or role |
| `QUICKSIGHT` | QuickSight native user |
| `IAM_IDENTITY_CENTER` | IAM Identity Center user |

### Import Modes
| Mode | Description |
|------|-------------|
| `SPICE` | Import data into SPICE engine |
| `DIRECT_QUERY` | Query data source directly |

### Common Data Source Types
`ADOBE_ANALYTICS`, `AMAZON_ELASTICSEARCH`, `AMAZON_OPENSEARCH`, `ATHENA`, `AURORA`, `AURORA_POSTGRESQL`, `AWS_IOT_ANALYTICS`, `DATABRICKS`, `EXASOL`, `JIRA`, `MARIADB`, `MYSQL`, `ORACLE`, `POSTGRESQL`, `PRESTO`, `REDSHIFT`, `S3`, `SALESFORCE`, `SERVICENOW`, `SNOWFLAKE`, `SPARK`, `SQLSERVER`, `TERADATA`, `TIMESTREAM`, `TWITTER`

### Common Response Structure
Most QuickSight commands return:
```json
{
    "Status": 200,
    "RequestId": "string",
    "Arn": "string"
}
```
