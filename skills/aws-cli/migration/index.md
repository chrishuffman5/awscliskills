# AWS CLI v2 -- Migration Command Reference Index

> Based on AWS CLI v2 documentation. Sources:
> - https://docs.aws.amazon.com/cli/latest/reference/mgn/
> - https://docs.aws.amazon.com/cli/latest/reference/migrationhub-config/
> - https://docs.aws.amazon.com/cli/latest/reference/migrationhuborchestrator/

---

## Quick Reference — MGN (Application Migration Service)

| Command | Category | Description |
|---------|----------|-------------|
| `describe-source-servers` | Source Server | Describe source servers |
| `delete-source-server` | Source Server | Delete a source server |
| `update-source-server` | Source Server | Update source server properties |
| `update-source-server-replication-type` | Source Server | Change replication type |
| `change-server-life-cycle-state` | Source Server | Change lifecycle state |
| `mark-as-archived` | Source Server | Mark source server as archived |
| `disconnect-from-service` | Source Server | Disconnect source server |
| `describe-vcenter-clients` | Source Server | Describe vCenter clients |
| `delete-vcenter-client` | Source Server | Delete a vCenter client |
| `create-replication-configuration-template` | Replication | Create replication config template |
| `delete-replication-configuration-template` | Replication | Delete replication config template |
| `describe-replication-configuration-templates` | Replication | Describe replication config templates |
| `update-replication-configuration-template` | Replication | Update replication config template |
| `get-replication-configuration` | Replication | Get server replication config |
| `update-replication-configuration` | Replication | Update server replication config |
| `start-replication` | Replication | Start replication for a server |
| `stop-replication` | Replication | Stop replication for a server |
| `pause-replication` | Replication | Pause replication |
| `resume-replication` | Replication | Resume paused replication |
| `retry-data-replication` | Replication | Retry failed data replication |
| `create-launch-configuration-template` | Launch Config | Create launch config template |
| `delete-launch-configuration-template` | Launch Config | Delete launch config template |
| `describe-launch-configuration-templates` | Launch Config | Describe launch config templates |
| `update-launch-configuration-template` | Launch Config | Update launch config template |
| `get-launch-configuration` | Launch Config | Get server launch configuration |
| `update-launch-configuration` | Launch Config | Update server launch configuration |
| `start-test` | Cutover | Launch test instances |
| `start-cutover` | Cutover | Launch cutover instances |
| `finalize-cutover` | Cutover | Finalize server cutover |
| `terminate-target-instances` | Cutover | Terminate launched instances |
| `create-wave` | Wave | Create a migration wave |
| `delete-wave` | Wave | Delete a migration wave |
| `list-waves` | Wave | List migration waves |
| `update-wave` | Wave | Update a migration wave |
| `archive-wave` | Wave | Archive a wave |
| `unarchive-wave` | Wave | Unarchive a wave |
| `create-application` | Application | Create an application |
| `delete-application` | Application | Delete an application |
| `list-applications` | Application | List applications |
| `update-application` | Application | Update an application |
| `archive-application` | Application | Archive an application |
| `unarchive-application` | Application | Unarchive an application |
| `associate-applications` | Application | Associate applications to a wave |
| `disassociate-applications` | Application | Disassociate applications from a wave |
| `associate-source-servers` | Application | Associate servers to an application |
| `disassociate-source-servers` | Application | Disassociate servers from an application |
| `create-connector` | Connector | Create a connector |
| `delete-connector` | Connector | Delete a connector |
| `list-connectors` | Connector | List connectors |
| `update-connector` | Connector | Update a connector |
| `put-source-server-action` | Action | Add action to a source server |
| `remove-source-server-action` | Action | Remove action from a source server |
| `list-source-server-actions` | Action | List source server actions |
| `put-template-action` | Action | Add action to a template |
| `remove-template-action` | Action | Remove action from a template |
| `list-template-actions` | Action | List template actions |
| `describe-jobs` | Job | Describe migration jobs |
| `describe-job-log-items` | Job | Describe job log items |
| `delete-job` | Job | Delete a job |
| `start-import` | Import/Export | Start a bulk import |
| `list-imports` | Import/Export | List imports |
| `list-import-errors` | Import/Export | List import errors |
| `start-export` | Import/Export | Start a bulk export |
| `list-exports` | Import/Export | List exports |
| `list-export-errors` | Import/Export | List export errors |
| `initialize-service` | Service | Initialize MGN service |
| `list-managed-accounts` | Service | List managed accounts |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

## Quick Reference — Migration Hub Config

| Command | Category | Description |
|---------|----------|-------------|
| `create-home-region-control` | Home Region | Set the Migration Hub home region |
| `delete-home-region-control` | Home Region | Delete home region control |
| `describe-home-region-controls` | Home Region | Describe home region controls |
| `get-home-region` | Home Region | Get the current home region |

## Quick Reference — Migration Hub Orchestrator

| Command | Category | Description |
|---------|----------|-------------|
| `create-workflow` | Workflow | Create a migration workflow |
| `delete-workflow` | Workflow | Delete a workflow |
| `get-workflow` | Workflow | Get workflow details |
| `list-workflows` | Workflow | List workflows |
| `update-workflow` | Workflow | Update a workflow |
| `start-workflow` | Workflow | Start a workflow |
| `stop-workflow` | Workflow | Stop a running workflow |
| `create-workflow-step` | Step | Create a workflow step |
| `delete-workflow-step` | Step | Delete a workflow step |
| `get-workflow-step` | Step | Get step details |
| `list-workflow-steps` | Step | List workflow steps |
| `update-workflow-step` | Step | Update a workflow step |
| `retry-workflow-step` | Step | Retry a failed step |
| `create-workflow-step-group` | Step Group | Create a step group |
| `delete-workflow-step-group` | Step Group | Delete a step group |
| `get-workflow-step-group` | Step Group | Get step group details |
| `list-workflow-step-groups` | Step Group | List step groups |
| `update-workflow-step-group` | Step Group | Update a step group |
| `create-template` | Template | Create a migration template |
| `delete-template` | Template | Delete a template |
| `get-template` | Template | Get template details |
| `list-templates` | Template | List templates |
| `update-template` | Template | Update a template |
| `get-template-step` | Template | Get a template step |
| `list-template-steps` | Template | List template steps |
| `get-template-step-group` | Template | Get a template step group |
| `list-template-step-groups` | Template | List template step groups |
| `list-plugins` | Plugin | List available plugins |

---

## Global Options

These options are available on ALL `aws mgn`, `aws migrationhub-config`, and `aws migrationhuborchestrator` commands.

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

### Source Server Lifecycle States

| State | Description |
|-------|-------------|
| `STOPPED` | Replication stopped |
| `NOT_READY` | Server not ready for testing |
| `READY_FOR_TEST` | Ready to launch test instance |
| `TESTING` | Test instance is running |
| `READY_FOR_CUTOVER` | Ready to start cutover |
| `CUTTING_OVER` | Cutover in progress |
| `CUTOVER` | Cutover complete |
| `DISCONNECTED` | Agent disconnected |
| `DISCOVERED` | Server discovered but agent not installed |
| `PENDING_INSTALLATION` | Agent installation pending |

### Replication Types

| Type | Description |
|------|-------------|
| `AGENT_BASED` | Uses the AWS Replication Agent |
| `SNAPSHOT_SHIPPING` | Uses EBS snapshot shipping |

### Data Replication States

| State | Description |
|-------|-------------|
| `STOPPED` | Replication stopped |
| `INITIATING` | Replication initiating |
| `INITIAL_SYNC` | Initial data sync in progress |
| `BACKLOG` | Data backlog being processed |
| `CREATING_SNAPSHOT` | Creating snapshot |
| `CONTINUOUS` | Continuous replication active |
| `PAUSED` | Replication paused |
| `RESCAN` | Rescan in progress |
| `STALLED` | Replication stalled |
| `DISCONNECTED` | Agent disconnected |

### Job Types

| Type | Description |
|------|-------------|
| `LAUNCH` | Launch job (test or cutover) |
| `TERMINATE` | Terminate target instances |
