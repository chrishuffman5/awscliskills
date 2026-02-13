# AWS CLI v2 — Redshift Command Reference Index

> Based on AWS CLI v2 documentation. Sources:
> - https://docs.aws.amazon.com/cli/latest/reference/redshift/
> - https://docs.aws.amazon.com/cli/latest/reference/redshift-data/
> - https://docs.aws.amazon.com/cli/latest/reference/redshift-serverless/

---

## Quick Reference — `aws redshift`

| Command | Category | Description |
|---------|----------|-------------|
| `create-cluster` | Cluster | Create a new Redshift cluster |
| `delete-cluster` | Cluster | Delete a cluster (optionally creating final snapshot) |
| `describe-clusters` | Cluster | Describe one or more clusters |
| `modify-cluster` | Cluster | Modify cluster settings |
| `reboot-cluster` | Cluster | Reboot a cluster |
| `resize-cluster` | Cluster | Resize a cluster (node type or count) |
| `pause-cluster` | Cluster | Pause a cluster |
| `resume-cluster` | Cluster | Resume a paused cluster |
| `restore-from-cluster-snapshot` | Cluster | Restore a cluster from a snapshot |
| `create-cluster-snapshot` | Snapshot | Create a manual snapshot |
| `delete-cluster-snapshot` | Snapshot | Delete a manual snapshot |
| `describe-cluster-snapshots` | Snapshot | List and describe snapshots |
| `copy-cluster-snapshot` | Snapshot | Copy a snapshot to another region |
| `modify-cluster-snapshot-attribute` | Snapshot | Modify snapshot sharing attributes |
| `authorize-snapshot-access` | Snapshot | Grant another account access to a snapshot |
| `revoke-snapshot-access` | Snapshot | Revoke snapshot access from an account |
| `batch-delete-cluster-snapshots` | Snapshot | Delete multiple snapshots in a batch |
| `modify-snapshot-copy-retention-period` | Snapshot | Modify cross-region copy retention |
| `enable-snapshot-copy` | Snapshot | Enable cross-region snapshot copy |
| `disable-snapshot-copy` | Snapshot | Disable cross-region snapshot copy |
| `modify-cluster-snapshot-schedule` | Snapshot | Associate or disassociate a snapshot schedule |
| `create-snapshot-schedule` | Snapshot | Create a snapshot schedule |
| `delete-snapshot-schedule` | Snapshot | Delete a snapshot schedule |
| `describe-snapshot-schedules` | Snapshot | Describe snapshot schedules |
| `modify-snapshot-schedule` | Snapshot | Modify a snapshot schedule |
| `create-snapshot-copy-grant` | Snapshot | Create a KMS grant for cross-region copy |
| `delete-snapshot-copy-grant` | Snapshot | Delete a snapshot copy grant |
| `describe-snapshot-copy-grants` | Snapshot | Describe snapshot copy grants |
| `create-cluster-parameter-group` | Parameter Group | Create a parameter group |
| `delete-cluster-parameter-group` | Parameter Group | Delete a parameter group |
| `describe-cluster-parameter-groups` | Parameter Group | List parameter groups |
| `describe-cluster-parameters` | Parameter Group | List parameters in a group |
| `modify-cluster-parameter-group` | Parameter Group | Modify parameters |
| `reset-cluster-parameter-group` | Parameter Group | Reset parameters to defaults |
| `describe-default-cluster-parameters` | Parameter Group | Describe default parameters |
| `create-cluster-security-group` | Security | Create a cluster security group (EC2-Classic) |
| `delete-cluster-security-group` | Security | Delete a cluster security group |
| `describe-cluster-security-groups` | Security | Describe cluster security groups |
| `authorize-cluster-security-group-ingress` | Security | Authorize ingress to a security group |
| `revoke-cluster-security-group-ingress` | Security | Revoke ingress from a security group |
| `create-cluster-subnet-group` | Networking | Create a subnet group |
| `delete-cluster-subnet-group` | Networking | Delete a subnet group |
| `describe-cluster-subnet-groups` | Networking | Describe subnet groups |
| `modify-cluster-subnet-group` | Networking | Modify a subnet group |
| `modify-cluster-iam-roles` | Security | Add or remove IAM roles from cluster |
| `create-endpoint-access` | Networking | Create a Redshift-managed VPC endpoint |
| `delete-endpoint-access` | Networking | Delete a managed VPC endpoint |
| `describe-endpoint-access` | Networking | Describe managed VPC endpoints |
| `modify-endpoint-access` | Networking | Modify a managed VPC endpoint |
| `create-authentication-profile` | Security | Create an authentication profile |
| `delete-authentication-profile` | Security | Delete an authentication profile |
| `describe-authentication-profiles` | Security | Describe authentication profiles |
| `modify-cluster-maintenance` | Cluster | Modify cluster maintenance settings |
| `create-data-share` | Data Sharing | Create a datashare |
| `delete-data-share` | Data Sharing | Delete a datashare |
| `describe-data-shares` | Data Sharing | Describe datashares |
| `describe-data-shares-for-consumer` | Data Sharing | Describe datashares for consumer |
| `describe-data-shares-for-producer` | Data Sharing | Describe datashares for producer |
| `associate-data-share-consumer` | Data Sharing | Associate a consumer with a datashare |
| `disassociate-data-share-consumer` | Data Sharing | Remove consumer from a datashare |
| `authorize-data-share` | Data Sharing | Authorize datashare for a consumer |
| `deauthorize-data-share` | Data Sharing | Deauthorize datashare for a consumer |
| `create-scheduled-action` | Scheduled Action | Create a scheduled action |
| `delete-scheduled-action` | Scheduled Action | Delete a scheduled action |
| `describe-scheduled-actions` | Scheduled Action | Describe scheduled actions |
| `modify-scheduled-action` | Scheduled Action | Modify a scheduled action |
| `create-event-subscription` | Events | Create an event notification subscription |
| `delete-event-subscription` | Events | Delete an event subscription |
| `describe-event-subscriptions` | Events | Describe event subscriptions |
| `modify-event-subscription` | Events | Modify an event subscription |
| `describe-events` | Events | Describe events for a cluster |
| `describe-event-categories` | Events | Describe event categories |
| `enable-logging` | Logging | Enable audit logging |
| `disable-logging` | Logging | Disable audit logging |
| `describe-logging-status` | Logging | Describe logging status |
| `create-integration` | Integration | Create a zero-ETL integration |
| `delete-integration` | Integration | Delete a zero-ETL integration |
| `describe-integrations` | Integration | Describe zero-ETL integrations |
| `modify-integration` | Integration | Modify a zero-ETL integration |
| `create-redshift-idc-application` | IDC Auth | Create an Identity Center application |
| `delete-redshift-idc-application` | IDC Auth | Delete an Identity Center application |
| `describe-redshift-idc-applications` | IDC Auth | Describe Identity Center applications |
| `modify-redshift-idc-application` | IDC Auth | Modify an Identity Center application |
| `create-hsm-client-certificate` | HSM | Create an HSM client certificate |
| `delete-hsm-client-certificate` | HSM | Delete an HSM client certificate |
| `describe-hsm-client-certificates` | HSM | Describe HSM client certificates |
| `create-hsm-configuration` | HSM | Create an HSM configuration |
| `delete-hsm-configuration` | HSM | Delete an HSM configuration |
| `describe-hsm-configurations` | HSM | Describe HSM configurations |
| `describe-reserved-nodes` | Reserved Node | Describe reserved nodes |
| `describe-reserved-node-offerings` | Reserved Node | List reserved node offerings |
| `purchase-reserved-node-offering` | Reserved Node | Purchase a reserved node offering |
| `accept-reserved-node-exchange` | Reserved Node | Accept a reserved node exchange |
| `describe-reserved-node-exchange-status` | Reserved Node | Describe reserved node exchange status |
| `get-reserved-node-exchange-offerings` | Reserved Node | Get available exchange offerings |
| `get-reserved-node-exchange-configuration-options` | Reserved Node | Get exchange configuration options |
| `add-partner` | Partner | Add a partner integration |
| `delete-partner` | Partner | Delete a partner integration |
| `describe-partners` | Partner | Describe partner integrations |
| `create-tags` | Tags | Add tags to a resource |
| `delete-tags` | Tags | Remove tags from a resource |
| `describe-tags` | Tags | Describe tags for resources |

## Quick Reference — `aws redshift-data`

| Command | Category | Description |
|---------|----------|-------------|
| `execute-statement` | Data API | Execute a SQL statement |
| `batch-execute-statement` | Data API | Execute multiple SQL statements in a batch |
| `cancel-statement` | Data API | Cancel a running statement |
| `describe-statement` | Data API | Describe a SQL statement execution |
| `get-statement-result` | Data API | Get result rows from a completed statement |
| `list-statements` | Data API | List SQL statement executions |
| `list-databases` | Data API | List databases in a cluster or workgroup |
| `list-schemas` | Data API | List schemas in a database |
| `list-tables` | Data API | List tables in a schema |
| `describe-table` | Data API | Describe columns of a table |

## Quick Reference — `aws redshift-serverless`

| Command | Category | Description |
|---------|----------|-------------|
| `create-namespace` | Namespace | Create a serverless namespace |
| `delete-namespace` | Namespace | Delete a serverless namespace |
| `get-namespace` | Namespace | Get namespace details |
| `list-namespaces` | Namespace | List all namespaces |
| `update-namespace` | Namespace | Update namespace configuration |
| `create-workgroup` | Workgroup | Create a serverless workgroup |
| `delete-workgroup` | Workgroup | Delete a serverless workgroup |
| `get-workgroup` | Workgroup | Get workgroup details |
| `list-workgroups` | Workgroup | List all workgroups |
| `update-workgroup` | Workgroup | Update workgroup configuration |
| `get-endpoint-access` | Workgroup | Get VPC endpoint details |
| `create-endpoint-access` | Workgroup | Create a VPC endpoint |
| `delete-endpoint-access` | Workgroup | Delete a VPC endpoint |
| `list-endpoint-access` | Workgroup | List VPC endpoints |
| `update-endpoint-access` | Workgroup | Update a VPC endpoint |
| `create-snapshot` | Snapshot | Create a serverless snapshot |
| `delete-snapshot` | Snapshot | Delete a serverless snapshot |
| `get-snapshot` | Snapshot | Get snapshot details |
| `list-snapshots` | Snapshot | List serverless snapshots |
| `update-snapshot` | Snapshot | Update snapshot retention |
| `restore-from-snapshot` | Snapshot | Restore a namespace from snapshot |
| `convert-recovery-point-to-snapshot` | Snapshot | Convert a recovery point to a snapshot |
| `get-recovery-point` | Snapshot | Get recovery point details |
| `list-recovery-points` | Snapshot | List recovery points |
| `restore-table-from-snapshot` | Snapshot | Restore a table from a snapshot |
| `create-scheduled-action` | Scheduling | Create a serverless scheduled action |
| `delete-scheduled-action` | Scheduling | Delete a serverless scheduled action |
| `get-scheduled-action` | Scheduling | Get scheduled action details |
| `list-scheduled-actions` | Scheduling | List serverless scheduled actions |
| `update-scheduled-action` | Scheduling | Update a serverless scheduled action |
| `create-custom-domain-association` | Domain | Create a custom domain association |
| `delete-custom-domain-association` | Domain | Delete a custom domain association |
| `get-custom-domain-association` | Domain | Get custom domain association details |
| `list-custom-domain-associations` | Domain | List custom domain associations |
| `update-custom-domain-association` | Domain | Update a custom domain association |
| `tag-resource` | Tags | Add tags to a serverless resource |
| `untag-resource` | Tags | Remove tags from a serverless resource |
| `list-tags-for-resource` | Tags | List tags on a serverless resource |
| `get-credentials` | Credentials | Get temporary credentials for a workgroup |
| `get-table-restore-status` | Table Restore | Get table restore status |
| `list-table-restore-status` | Table Restore | List table restore operations |

---

## Global Options

These options are available on ALL `aws redshift`, `aws redshift-data`, and `aws redshift-serverless` commands.

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

### Cluster Status Values
| Status | Description |
|--------|-------------|
| `available` | Cluster is ready for queries |
| `creating` | Cluster is being created |
| `deleting` | Cluster is being deleted |
| `modifying` | Cluster is being modified |
| `rebooting` | Cluster is rebooting |
| `resizing` | Cluster is being resized |
| `paused` | Cluster is paused |
| `resuming` | Cluster is resuming from paused |
| `rotating-keys` | Encryption keys are being rotated |
| `storage-full` | Cluster has reached storage capacity |
| `hardware-failure` | Hardware failure detected |

### Node Types
| Family | Types | Description |
|--------|-------|-------------|
| RA3 | `ra3.xlplus`, `ra3.4xlarge`, `ra3.16xlarge` | Managed storage, recommended |
| DC2 | `dc2.large`, `dc2.8xlarge` | Dense compute, local SSD |
| DS2 | `ds2.xlarge`, `ds2.8xlarge` | Dense storage (legacy) |

### Data API Statement Status Values
| Status | Description |
|--------|-------------|
| `SUBMITTED` | Statement has been submitted |
| `PICKED` | Statement has been picked up for processing |
| `STARTED` | Statement has started running |
| `FINISHED` | Statement completed successfully |
| `ABORTED` | Statement was cancelled |
| `FAILED` | Statement failed |
| `ALL` | Filter value for list-statements |

### Wait Commands
| Waiter | Description |
|--------|-------------|
| `cluster-available` | Wait until cluster status is `available` |
| `cluster-deleted` | Wait until cluster is deleted |
| `cluster-restored` | Wait until restored cluster is `available` |
| `snapshot-available` | Wait until snapshot status is `available` |

```bash
aws redshift wait cluster-available --cluster-identifier my-cluster
aws redshift wait snapshot-available --snapshot-identifier my-snap --cluster-identifier my-cluster
```
