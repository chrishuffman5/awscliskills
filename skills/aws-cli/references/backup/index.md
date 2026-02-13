# AWS CLI v2 -- Backup Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/backup/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-backup-plan` | Plan | Create a backup plan with rules and schedules |
| `update-backup-plan` | Plan | Update an existing backup plan |
| `delete-backup-plan` | Plan | Delete a backup plan |
| `get-backup-plan` | Plan | Get backup plan details |
| `list-backup-plans` | Plan | List all backup plans |
| `list-backup-plan-versions` | Plan | List versions of a backup plan |
| `list-backup-plan-templates` | Plan | List backup plan templates |
| `get-backup-plan-from-template` | Plan | Get a plan from a template |
| `get-backup-plan-from-json` | Plan | Parse a JSON backup plan |
| `export-backup-plan-template` | Plan | Export a plan as a template |
| `create-backup-selection` | Plan | Assign resources to a backup plan |
| `delete-backup-selection` | Plan | Remove resources from a plan |
| `get-backup-selection` | Plan | Get selection details |
| `list-backup-selections` | Plan | List selections for a plan |
| `create-backup-vault` | Vault | Create a backup vault |
| `delete-backup-vault` | Vault | Delete a backup vault |
| `describe-backup-vault` | Vault | Describe a backup vault |
| `list-backup-vaults` | Vault | List all backup vaults |
| `create-logically-air-gapped-backup-vault` | Vault | Create an air-gapped vault |
| `put-backup-vault-access-policy` | Vault | Set vault access policy |
| `get-backup-vault-access-policy` | Vault | Get vault access policy |
| `delete-backup-vault-access-policy` | Vault | Delete vault access policy |
| `put-backup-vault-lock-configuration` | Vault | Lock a vault (immutability) |
| `delete-backup-vault-lock-configuration` | Vault | Remove vault lock |
| `put-backup-vault-notifications` | Vault | Set SNS notifications |
| `get-backup-vault-notifications` | Vault | Get SNS notifications |
| `delete-backup-vault-notifications` | Vault | Remove SNS notifications |
| `create-restore-access-backup-vault` | Vault | Create restore access vault |
| `list-restore-access-backup-vaults` | Vault | List restore access vaults |
| `revoke-restore-access-backup-vault` | Vault | Revoke restore access |
| `start-backup-job` | Backup Job | Start an on-demand backup |
| `describe-backup-job` | Backup Job | Describe a backup job |
| `list-backup-jobs` | Backup Job | List backup jobs |
| `list-backup-job-summaries` | Backup Job | List job summaries |
| `stop-backup-job` | Backup Job | Stop a running backup job |
| `start-copy-job` | Copy Job | Copy recovery point to another vault |
| `describe-copy-job` | Copy Job | Describe a copy job |
| `list-copy-jobs` | Copy Job | List copy jobs |
| `list-copy-job-summaries` | Copy Job | List copy job summaries |
| `start-restore-job` | Restore Job | Restore from a recovery point |
| `describe-restore-job` | Restore Job | Describe a restore job |
| `list-restore-jobs` | Restore Job | List restore jobs |
| `list-restore-job-summaries` | Restore Job | List restore job summaries |
| `list-restore-jobs-by-protected-resource` | Restore Job | List restores for a resource |
| `get-restore-job-metadata` | Restore Job | Get restore job metadata |
| `put-restore-validation-result` | Restore Job | Submit restore validation |
| `describe-recovery-point` | Recovery Point | Describe a recovery point |
| `list-recovery-points-by-backup-vault` | Recovery Point | List recovery points in a vault |
| `list-recovery-points-by-resource` | Recovery Point | List recovery points for a resource |
| `list-recovery-points-by-legal-hold` | Recovery Point | List recovery points under legal hold |
| `list-indexed-recovery-points` | Recovery Point | List indexed recovery points |
| `delete-recovery-point` | Recovery Point | Delete a recovery point |
| `disassociate-recovery-point` | Recovery Point | Disassociate a recovery point |
| `disassociate-recovery-point-from-parent` | Recovery Point | Disassociate from parent |
| `update-recovery-point-lifecycle` | Recovery Point | Update lifecycle settings |
| `update-recovery-point-index-settings` | Recovery Point | Update index settings |
| `get-recovery-point-restore-metadata` | Recovery Point | Get restore metadata |
| `get-recovery-point-index-details` | Recovery Point | Get index details |
| `describe-protected-resource` | Protected Resource | Describe a protected resource |
| `list-protected-resources` | Protected Resource | List all protected resources |
| `list-protected-resources-by-backup-vault` | Protected Resource | List resources by vault |
| `get-supported-resource-types` | Protected Resource | Get supported resource types |
| `create-framework` | Framework | Create a compliance framework |
| `update-framework` | Framework | Update a framework |
| `delete-framework` | Framework | Delete a framework |
| `describe-framework` | Framework | Describe a framework |
| `list-frameworks` | Framework | List all frameworks |
| `create-report-plan` | Report | Create a report plan |
| `update-report-plan` | Report | Update a report plan |
| `delete-report-plan` | Report | Delete a report plan |
| `describe-report-plan` | Report | Describe a report plan |
| `list-report-plans` | Report | List all report plans |
| `describe-report-job` | Report | Describe a report job |
| `list-report-jobs` | Report | List report jobs |
| `start-report-job` | Report | Start a report job |
| `create-restore-testing-plan` | Restore Testing | Create a restore testing plan |
| `update-restore-testing-plan` | Restore Testing | Update a restore testing plan |
| `delete-restore-testing-plan` | Restore Testing | Delete a restore testing plan |
| `get-restore-testing-plan` | Restore Testing | Get a restore testing plan |
| `list-restore-testing-plans` | Restore Testing | List restore testing plans |
| `create-restore-testing-selection` | Restore Testing | Create a restore testing selection |
| `update-restore-testing-selection` | Restore Testing | Update a restore testing selection |
| `delete-restore-testing-selection` | Restore Testing | Delete a restore testing selection |
| `get-restore-testing-selection` | Restore Testing | Get a restore testing selection |
| `list-restore-testing-selections` | Restore Testing | List restore testing selections |
| `get-restore-testing-inferred-metadata` | Restore Testing | Get inferred metadata |
| `create-legal-hold` | Legal Hold | Create a legal hold |
| `cancel-legal-hold` | Legal Hold | Cancel a legal hold |
| `get-legal-hold` | Legal Hold | Get legal hold details |
| `list-legal-holds` | Legal Hold | List legal holds |
| `create-tiering-configuration` | Tiering | Create tiering configuration |
| `update-tiering-configuration` | Tiering | Update tiering configuration |
| `delete-tiering-configuration` | Tiering | Delete tiering configuration |
| `get-tiering-configuration` | Tiering | Get tiering configuration |
| `list-tiering-configurations` | Tiering | List tiering configurations |
| `start-scan-job` | Scanning | Start a malware scan job |
| `describe-scan-job` | Scanning | Describe a scan job |
| `list-scan-jobs` | Scanning | List scan jobs |
| `list-scan-job-summaries` | Scanning | List scan job summaries |
| `describe-global-settings` | Settings | Describe global settings |
| `update-global-settings` | Settings | Update global settings |
| `describe-region-settings` | Settings | Describe region settings |
| `update-region-settings` | Settings | Update region settings |
| `tag-resource` | Tags | Tag a backup resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags` | Tags | List tags for a resource |

### Backup Gateway Commands (`aws backup-gateway`)

| Command | Category | Description |
|---------|----------|-------------|
| `create-gateway` | Gateway | Create a backup gateway |
| `delete-gateway` | Gateway | Delete a gateway |
| `get-gateway` | Gateway | Get gateway details |
| `list-gateways` | Gateway | List all gateways |
| `update-gateway-information` | Gateway | Update gateway name/timezone |
| `update-gateway-software-now` | Gateway | Trigger software update |
| `associate-gateway-to-server` | Gateway | Associate gateway with server |
| `disassociate-gateway-from-server` | Gateway | Disassociate gateway from server |
| `import-hypervisor-configuration` | Hypervisor | Import hypervisor config |
| `get-hypervisor` | Hypervisor | Get hypervisor details |
| `list-hypervisors` | Hypervisor | List hypervisors |
| `update-hypervisor` | Hypervisor | Update hypervisor config |
| `delete-hypervisor` | Hypervisor | Delete a hypervisor |
| `test-hypervisor-configuration` | Hypervisor | Test hypervisor config |
| `get-virtual-machine` | VM | Get VM details |
| `list-virtual-machines` | VM | List virtual machines |
| `start-virtual-machines-metadata-sync` | VM | Start VM metadata sync |
| `put-maintenance-start-time` | Gateway | Set maintenance window |
| `get-bandwidth-rate-limit-schedule` | Gateway | Get bandwidth schedule |
| `put-bandwidth-rate-limit-schedule` | Gateway | Set bandwidth schedule |
| `get-hypervisor-property-mappings` | Hypervisor | Get property mappings |
| `put-hypervisor-property-mappings` | Hypervisor | Set property mappings |
| `tag-resource` | Tags | Tag a gateway resource |
| `untag-resource` | Tags | Remove tags |
| `list-tags-for-resource` | Tags | List tags |

---

## Global Options

These options are available on ALL `aws backup` commands.

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

### Supported Resource Types
`Aurora`, `CloudFormation`, `DocumentDB`, `DynamoDB`, `EBS`, `EC2`, `EFS`, `FSx`, `Neptune`, `RDS`, `Redshift`, `S3`, `Storage Gateway`, `Timestream`, `VirtualMachine`

### Backup Job States
| State | Description |
|-------|-------------|
| `CREATED` | Job created |
| `PENDING` | Job pending |
| `RUNNING` | Job in progress |
| `ABORTING` | Job being aborted |
| `ABORTED` | Job was aborted |
| `COMPLETED` | Job completed successfully |
| `FAILED` | Job failed |
| `EXPIRED` | Job expired |
| `PARTIAL` | Job partially completed |

### Recovery Point Status Values
| Status | Description |
|--------|-------------|
| `COMPLETED` | Recovery point available |
| `PARTIAL` | Partially completed |
| `DELETING` | Being deleted |
| `EXPIRED` | Past retention period |
