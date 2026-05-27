# AWS CLI v2 -- DRS (Elastic Disaster Recovery) Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/drs/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `describe-source-servers` | Source Server | Describe source servers |
| `delete-source-server` | Source Server | Delete a source server |
| `disconnect-source-server` | Source Server | Disconnect a source server |
| `create-extended-source-server` | Source Server | Create an extended source server |
| `list-extensible-source-servers` | Source Server | List extensible source servers |
| `start-replication` | Source Server | Start replication for a source server |
| `stop-replication` | Source Server | Stop replication for a source server |
| `describe-recovery-instances` | Recovery Instance | Describe recovery instances |
| `delete-recovery-instance` | Recovery Instance | Delete a recovery instance |
| `disconnect-recovery-instance` | Recovery Instance | Disconnect a recovery instance |
| `terminate-recovery-instances` | Recovery Instance | Terminate recovery instances |
| `describe-recovery-snapshots` | Recovery Instance | Describe recovery snapshots |
| `create-replication-configuration-template` | Replication Config | Create a replication config template |
| `delete-replication-configuration-template` | Replication Config | Delete a replication config template |
| `describe-replication-configuration-templates` | Replication Config | Describe replication config templates |
| `update-replication-configuration-template` | Replication Config | Update a replication config template |
| `get-replication-configuration` | Replication Config | Get replication config for a source server |
| `update-replication-configuration` | Replication Config | Update replication config for a source server |
| `create-launch-configuration-template` | Launch Config | Create a launch config template |
| `delete-launch-configuration-template` | Launch Config | Delete a launch config template |
| `describe-launch-configuration-templates` | Launch Config | Describe launch config templates |
| `update-launch-configuration-template` | Launch Config | Update a launch config template |
| `get-launch-configuration` | Launch Config | Get launch config for a source server |
| `update-launch-configuration` | Launch Config | Update launch config for a source server |
| `put-launch-action` | Launch Config | Add or update a launch action |
| `delete-launch-action` | Launch Config | Delete a launch action |
| `list-launch-actions` | Launch Config | List launch actions |
| `start-recovery` | Recovery Operation | Start a recovery (failover) |
| `start-failback-launch` | Recovery Operation | Start failback launch |
| `stop-failback` | Recovery Operation | Stop failback |
| `reverse-replication` | Recovery Operation | Reverse replication direction |
| `get-failback-replication-configuration` | Recovery Operation | Get failback replication config |
| `update-failback-replication-configuration` | Recovery Operation | Update failback replication config |
| `initialize-service` | Recovery Operation | Initialize the DRS service |
| `create-source-network` | Source Network | Create a source network |
| `delete-source-network` | Source Network | Delete a source network |
| `describe-source-networks` | Source Network | Describe source networks |
| `start-source-network-recovery` | Source Network | Start source network recovery |
| `start-source-network-replication` | Source Network | Start source network replication |
| `stop-source-network-replication` | Source Network | Stop source network replication |
| `associate-source-network-stack` | Source Network | Associate a source network stack |
| `export-source-network-cfn-template` | Source Network | Export CFN template for source network |
| `describe-jobs` | Job | Describe DRS jobs |
| `delete-job` | Job | Delete a job |
| `describe-job-log-items` | Job | Describe job log items |
| `list-staging-accounts` | Job | List staging accounts |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

---

## Global Options

These options are available on ALL `aws drs` commands.

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

### Replication Direction Values
| Direction | Description |
|-----------|-------------|
| `FAILOVER` | Replication from source to target |
| `FAILBACK` | Replication from target back to source |

### Data Replication State Values
| State | Description |
|-------|-------------|
| `STOPPED` | Replication is stopped |
| `INITIATING` | Replication is being initiated |
| `INITIAL_SYNC` | Initial data sync in progress |
| `BACKLOG` | Replication backlog is being processed |
| `CREATING_SNAPSHOT` | Creating a recovery snapshot |
| `CONTINUOUS` | Continuous replication active |
| `PAUSED` | Replication is paused |
| `RESCAN` | Rescan in progress |
| `STALLED` | Replication is stalled |
| `DISCONNECTED` | Source server is disconnected |

### Recovery Instance Data Replication State Values
| State | Description |
|-------|-------------|
| `STOPPED` | Failback replication stopped |
| `INITIATING` | Failback replication initiating |
| `INITIAL_SYNC` | Initial sync for failback |
| `BACKLOG` | Failback backlog processing |
| `CREATING_SNAPSHOT` | Creating snapshot for failback |
| `CONTINUOUS` | Continuous failback replication |
| `PAUSED` | Failback replication paused |
| `RESCAN` | Failback rescan |
| `STALLED` | Failback replication stalled |
| `DISCONNECTED` | Recovery instance disconnected |
| `REPLICATION_STATE_NOT_AVAILABLE` | Replication state not available |
| `NOT_STARTED` | Failback replication not started |

### Job Status Values
| Status | Description |
|--------|-------------|
| `PENDING` | Job is pending |
| `STARTED` | Job has started |
| `COMPLETED` | Job completed successfully |

### Job Type Values
| Type | Description |
|------|-------------|
| `LAUNCH` | Recovery launch job |
| `TERMINATE` | Terminate recovery instances |
| `CREATE_CONVERTED_SNAPSHOT` | Convert snapshot |
