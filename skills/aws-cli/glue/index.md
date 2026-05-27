# AWS CLI v2 — Glue Quick Reference

## Subcommand Quick Reference

| Subcommand | Description |
|------------|-------------|
| `create-job` | Create an ETL job |
| `delete-job` | Delete a job |
| `get-job` | Get job details |
| `get-jobs` | List all jobs |
| `update-job` | Update a job |
| `batch-get-jobs` | Get multiple jobs |
| `start-job-run` | Start a job run |
| `batch-stop-job-run` | Stop multiple job runs |
| `get-job-run` | Get job run details |
| `get-job-runs` | List job runs |
| `get-job-bookmark` | Get job bookmark |
| `reset-job-bookmark` | Reset job bookmark |
| `create-crawler` | Create a crawler |
| `delete-crawler` | Delete a crawler |
| `get-crawler` | Get crawler details |
| `get-crawlers` | List all crawlers |
| `update-crawler` | Update a crawler |
| `start-crawler` | Start a crawler |
| `stop-crawler` | Stop a running crawler |
| `batch-get-crawlers` | Get multiple crawlers |
| `get-crawler-metrics` | Get crawler metrics |
| `start-crawler-schedule` | Start a crawler schedule |
| `stop-crawler-schedule` | Stop a crawler schedule |
| `list-crawlers` | List crawler names |
| `create-database` | Create a Data Catalog database |
| `delete-database` | Delete a database |
| `get-database` | Get database details |
| `get-databases` | List all databases |
| `update-database` | Update a database |
| `create-table` | Create a Data Catalog table |
| `delete-table` | Delete a table |
| `get-table` | Get table details |
| `get-tables` | List tables in a database |
| `update-table` | Update a table |
| `batch-delete-table` | Delete multiple tables |
| `get-table-version` | Get a specific table version |
| `get-table-versions` | List table versions |
| `delete-table-version` | Delete a table version |
| `batch-delete-table-version` | Delete multiple table versions |
| `search-tables` | Search tables by properties |
| `create-partition` | Create a partition |
| `delete-partition` | Delete a partition |
| `get-partition` | Get partition details |
| `get-partitions` | List partitions |
| `update-partition` | Update a partition |
| `batch-create-partition` | Create multiple partitions |
| `batch-delete-partition` | Delete multiple partitions |
| `batch-get-partition` | Get multiple partitions |
| `batch-update-partition` | Update multiple partitions |
| `get-partition-indexes` | List partition indexes |
| `create-partition-index` | Create a partition index |
| `delete-partition-index` | Delete a partition index |
| `create-connection` | Create a connection |
| `delete-connection` | Delete a connection |
| `get-connection` | Get connection details |
| `get-connections` | List connections |
| `update-connection` | Update a connection |
| `batch-delete-connection` | Delete multiple connections |
| `create-classifier` | Create a classifier |
| `delete-classifier` | Delete a classifier |
| `get-classifier` | Get classifier details |
| `get-classifiers` | List classifiers |
| `update-classifier` | Update a classifier |
| `create-trigger` | Create a trigger |
| `delete-trigger` | Delete a trigger |
| `get-trigger` | Get trigger details |
| `get-triggers` | List triggers |
| `update-trigger` | Update a trigger |
| `start-trigger` | Activate a trigger |
| `stop-trigger` | Deactivate a trigger |
| `batch-get-triggers` | Get multiple triggers |
| `list-triggers` | List trigger names |
| `create-workflow` | Create a workflow |
| `delete-workflow` | Delete a workflow |
| `get-workflow` | Get workflow details |
| `get-workflows` | List workflows (deprecated — use list-workflows) |
| `update-workflow` | Update a workflow |
| `start-workflow-run` | Start a workflow run |
| `stop-workflow-run` | Stop a running workflow |
| `get-workflow-run` | Get workflow run details |
| `get-workflow-runs` | List workflow runs |
| `get-workflow-run-properties` | Get run properties |
| `put-workflow-run-properties` | Set run properties |
| `batch-get-workflows` | Get multiple workflows |
| `list-workflows` | List workflow names |
| `resume-workflow-run` | Resume a failed workflow run |
| `create-blueprint` | Create a blueprint |
| `delete-blueprint` | Delete a blueprint |
| `get-blueprint` | Get blueprint details |
| `get-blueprint-run` | Get a blueprint run |
| `get-blueprint-runs` | List blueprint runs |
| `list-blueprints` | List blueprint names |
| `start-blueprint-run` | Start a blueprint run |
| `update-blueprint` | Update a blueprint |
| `batch-get-blueprints` | Get multiple blueprints |
| `create-dev-endpoint` | Create a dev endpoint |
| `delete-dev-endpoint` | Delete a dev endpoint |
| `get-dev-endpoint` | Get dev endpoint details |
| `get-dev-endpoints` | List dev endpoints |
| `update-dev-endpoint` | Update a dev endpoint |
| `batch-get-dev-endpoints` | Get multiple dev endpoints |
| `list-dev-endpoints` | List dev endpoint names |
| `create-ml-transform` | Create an ML transform |
| `delete-ml-transform` | Delete an ML transform |
| `get-ml-transform` | Get ML transform details |
| `get-ml-transforms` | List ML transforms |
| `update-ml-transform` | Update an ML transform |
| `start-ml-evaluation-task-run` | Start ML evaluation |
| `start-ml-labeling-set-generation-task-run` | Generate ML labeling set |
| `cancel-ml-task-run` | Cancel an ML task run |
| `get-ml-task-run` | Get ML task run details |
| `get-ml-task-runs` | List ML task runs |
| `list-ml-transforms` | List ML transform IDs |
| `create-data-quality-ruleset` | Create a data quality ruleset |
| `delete-data-quality-ruleset` | Delete a ruleset |
| `get-data-quality-ruleset` | Get ruleset details |
| `get-data-quality-result` | Get a data quality result |
| `list-data-quality-rulesets` | List rulesets |
| `list-data-quality-results` | List results |
| `start-data-quality-ruleset-evaluation-run` | Start ruleset evaluation |
| `start-data-quality-rule-recommendation-run` | Start rule recommendation |
| `cancel-data-quality-ruleset-evaluation-run` | Cancel evaluation run |
| `get-data-quality-ruleset-evaluation-run` | Get evaluation run details |
| `list-data-quality-ruleset-evaluation-runs` | List evaluation runs |
| `batch-get-data-quality-result` | Get multiple results |
| `update-data-quality-ruleset` | Update a ruleset |
| `create-registry` | Create a schema registry |
| `delete-registry` | Delete a registry |
| `get-registry` | Get registry details |
| `update-registry` | Update a registry |
| `list-registries` | List registries |
| `create-schema` | Create a schema |
| `delete-schema` | Delete a schema |
| `get-schema` | Get schema details |
| `get-schema-version` | Get a schema version |
| `update-schema` | Update a schema |
| `list-schemas` | List schemas |
| `list-schema-versions` | List schema versions |
| `register-schema-version` | Register a new schema version |
| `get-schema-by-definition` | Get schema by definition |
| `get-schema-versions-diff` | Diff two schema versions |
| `put-schema-version-metadata` | Add schema version metadata |
| `remove-schema-version-metadata` | Remove schema version metadata |
| `query-schema-version-metadata` | Query schema version metadata |
| `delete-schema-versions` | Delete schema versions |
| `check-schema-version-validity` | Validate a schema version |
| `create-session` | Create an interactive session |
| `delete-session` | Delete a session |
| `get-session` | Get session details |
| `list-sessions` | List sessions |
| `stop-session` | Stop a session |
| `run-statement` | Run a statement in a session |
| `cancel-statement` | Cancel a running statement |
| `get-statement` | Get statement details |
| `list-statements` | List statements in a session |
| `create-integration` | Create a zero-ETL integration |
| `delete-integration` | Delete an integration |
| `get-integration` | Get integration details |
| `describe-integrations` | List integrations |
| `modify-integration` | Modify an integration |
| `create-integration-resource-property` | Create integration resource property |
| `get-integration-resource-property` | Get integration resource property |
| `update-integration-resource-property` | Update integration resource property |
| `create-integration-table-properties` | Create integration table properties |
| `get-integration-table-properties` | Get integration table properties |
| `update-integration-table-properties` | Update integration table properties |
| `describe-inbound-integrations` | Describe inbound integrations |
| `get-column-statistics-for-table` | Get column stats for a table |
| `update-column-statistics-for-table` | Update column stats for a table |
| `delete-column-statistics-for-table` | Delete column stats for a table |
| `get-column-statistics-for-partition` | Get column stats for a partition |
| `update-column-statistics-for-partition` | Update column stats for a partition |
| `delete-column-statistics-for-partition` | Delete column stats for a partition |
| `get-column-statistics-task-run` | Get column stats task run |
| `get-column-statistics-task-runs` | List column stats task runs |
| `start-column-statistics-task-run` | Start column stats task |
| `stop-column-statistics-task-run` | Stop column stats task |
| `create-security-configuration` | Create a security configuration |
| `delete-security-configuration` | Delete a security configuration |
| `get-security-configuration` | Get security config details |
| `get-security-configurations` | List security configurations |
| `create-custom-entity-type` | Create a custom entity type |
| `delete-custom-entity-type` | Delete a custom entity type |
| `get-custom-entity-type` | Get custom entity type details |
| `batch-get-custom-entity-types` | Get multiple custom entity types |
| `list-custom-entity-types` | List custom entity types |
| `get-resource-policies` | List resource policies |
| `get-resource-policy` | Get a resource policy |
| `put-resource-policy` | Set a resource policy |
| `delete-resource-policy` | Delete a resource policy |
| `get-user-defined-function` | Get a UDF |
| `get-user-defined-functions` | List UDFs |
| `create-user-defined-function` | Create a UDF |
| `update-user-defined-function` | Update a UDF |
| `delete-user-defined-function` | Delete a UDF |
| `tag-resource` | Add tags to a resource |
| `untag-resource` | Remove tags from a resource |
| `get-tags` | List tags for a resource |

## Global Options

These options apply to all `aws glue` subcommands:

| Option | Description |
|--------|-------------|
| `--region` | AWS region |
| `--output` | Output format: `json`, `yaml`, `text`, `table` |
| `--query` | JMESPath query for filtering output |
| `--profile` | Named profile |
| `--no-cli-pager` | Disable pager |
| `--cli-input-json` | Read input from JSON file |
| `--cli-input-yaml` | Read input from YAML file |
| `--generate-cli-skeleton` | Generate input skeleton |
| `--debug` | Enable debug logging |
| `--endpoint-url` | Override endpoint URL |
| `--no-verify-ssl` | Disable SSL verification |
| `--no-paginate` | Disable automatic pagination |
| `--no-sign-request` | Skip request signing |
| `--ca-bundle` | Custom CA bundle path |
| `--cli-connect-timeout` | Connection timeout in seconds |
| `--cli-read-timeout` | Read timeout in seconds |
| `--color` | Toggle color output: `on`, `off`, `auto` |
