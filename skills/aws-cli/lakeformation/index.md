# AWS CLI v2 -- Lake Formation Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/lakeformation/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `grant-permissions` | Permissions | Grant permissions to a principal |
| `revoke-permissions` | Permissions | Revoke permissions from a principal |
| `batch-grant-permissions` | Permissions | Grant permissions in batch |
| `batch-revoke-permissions` | Permissions | Revoke permissions in batch |
| `list-permissions` | Permissions | List permissions for a principal or resource |
| `get-effective-permissions-for-path` | Permissions | Get effective permissions for an S3 path |
| `get-data-lake-settings` | Permissions | Get data lake settings |
| `put-data-lake-settings` | Permissions | Set data lake settings |
| `get-data-lake-principal` | Permissions | Get the calling principal identity |
| `create-lf-tag` | LF-Tags | Create an LF-Tag |
| `get-lf-tag` | LF-Tags | Get an LF-Tag |
| `update-lf-tag` | LF-Tags | Update LF-Tag values |
| `delete-lf-tag` | LF-Tags | Delete an LF-Tag |
| `list-lf-tags` | LF-Tags | List all LF-Tags |
| `add-lf-tags-to-resource` | LF-Tags | Assign LF-Tags to a resource |
| `remove-lf-tags-from-resource` | LF-Tags | Remove LF-Tags from a resource |
| `get-resource-lf-tags` | LF-Tags | Get LF-Tags assigned to a resource |
| `search-databases-by-lf-tags` | LF-Tags | Search databases by LF-Tag values |
| `search-tables-by-lf-tags` | LF-Tags | Search tables by LF-Tag values |
| `create-lf-tag-expression` | LF-Tags | Create an LF-Tag expression |
| `get-lf-tag-expression` | LF-Tags | Get an LF-Tag expression |
| `update-lf-tag-expression` | LF-Tags | Update an LF-Tag expression |
| `delete-lf-tag-expression` | LF-Tags | Delete an LF-Tag expression |
| `list-lf-tag-expressions` | LF-Tags | List LF-Tag expressions |
| `create-data-cells-filter` | Data Cells Filter | Create a row/column-level filter |
| `update-data-cells-filter` | Data Cells Filter | Update a data cells filter |
| `delete-data-cells-filter` | Data Cells Filter | Delete a data cells filter |
| `get-data-cells-filter` | Data Cells Filter | Get a data cells filter |
| `list-data-cells-filter` | Data Cells Filter | List data cells filters |
| `register-resource` | Resource | Register an S3 location with Lake Formation |
| `deregister-resource` | Resource | Deregister a resource |
| `describe-resource` | Resource | Describe a registered resource |
| `update-resource` | Resource | Update a registered resource |
| `list-resources` | Resource | List registered resources |
| `list-table-storage-optimizers` | Resource | List table storage optimizers |
| `update-table-storage-optimizer` | Resource | Update table storage optimizer config |
| `create-lake-formation-opt-in` | Opt-In | Opt in a principal to Lake Formation permissions |
| `delete-lake-formation-opt-in` | Opt-In | Remove a Lake Formation opt-in |
| `list-lake-formation-opt-ins` | Opt-In | List Lake Formation opt-ins |
| `start-transaction` | Transaction | Start a governed transaction |
| `commit-transaction` | Transaction | Commit a transaction |
| `cancel-transaction` | Transaction | Cancel a transaction |
| `describe-transaction` | Transaction | Describe a transaction |
| `extend-transaction` | Transaction | Extend a transaction heartbeat |
| `list-transactions` | Transaction | List transactions |
| `get-table-objects` | Transaction | Get governed table objects |
| `update-table-objects` | Transaction | Update governed table objects |
| `delete-objects-on-cancel` | Transaction | Delete objects if transaction is cancelled |
| `get-temporary-glue-table-credentials` | Credentials | Get temporary credentials for a Glue table |
| `get-temporary-glue-partition-credentials` | Credentials | Get temporary credentials for a partition |
| `get-temporary-data-location-credentials` | Credentials | Get temporary credentials for a data location |
| `assume-decorated-role-with-saml` | Credentials | Assume a decorated role using SAML |
| `create-lake-formation-identity-center-configuration` | Identity Center | Create Identity Center integration |
| `describe-lake-formation-identity-center-configuration` | Identity Center | Describe Identity Center configuration |
| `update-lake-formation-identity-center-configuration` | Identity Center | Update Identity Center configuration |
| `delete-lake-formation-identity-center-configuration` | Identity Center | Delete Identity Center configuration |
| `start-query-planning` | Query | Start query planning |
| `get-query-state` | Query | Get query planning state |
| `get-query-statistics` | Query | Get query execution statistics |
| `get-work-units` | Query | Get work units for a query |
| `get-work-unit-results` | Query | Get work unit results |

---

## Global Options

These options are available on ALL `aws lakeformation` commands.

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

### Permission Values
| Permission | Description |
|------------|-------------|
| `ALL` | All permissions |
| `SELECT` | Read data from a table |
| `ALTER` | Alter a database or table |
| `DROP` | Drop a database or table |
| `DELETE` | Delete data from a table |
| `INSERT` | Insert data into a table |
| `DESCRIBE` | Describe a database or table |
| `CREATE_DATABASE` | Create a database in the catalog |
| `CREATE_TABLE` | Create a table in a database |
| `DATA_LOCATION_ACCESS` | Access data at an S3 location |
| `CREATE_LF_TAG` | Create an LF-Tag |
| `ASSOCIATE` | Associate LF-Tags with resources |
| `GRANT_WITH_LF_TAG_EXPRESSION` | Grant using LF-Tag expressions |
| `CREATE_LF_TAG_EXPRESSION` | Create LF-Tag expressions |
| `CREATE_CATALOG` | Create a catalog |
| `SUPER_USER` | Super user permissions |

### Resource Types
| Resource | Key Fields |
|----------|------------|
| `Catalog` | `Id` (optional) |
| `Database` | `Name` (required), `CatalogId` |
| `Table` | `DatabaseName`, `Name` or `TableWildcard` |
| `TableWithColumns` | `DatabaseName`, `Name`, `ColumnNames` or `ColumnWildcard` |
| `DataLocation` | `ResourceArn` (S3 ARN) |
| `DataCellsFilter` | `DatabaseName`, `TableName`, `Name` |
| `LFTag` | `TagKey`, `TagValues` |
| `LFTagPolicy` | `ResourceType`, `Expression` |

### Transaction Status Values
| Status | Description |
|--------|-------------|
| `ACTIVE` | Transaction is active |
| `COMMITTED` | Transaction has been committed |
| `ABORTED` | Transaction was cancelled |
| `COMMIT_IN_PROGRESS` | Commit is in progress |
