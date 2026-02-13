# AWS CLI v2 -- CloudFormation Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/cloudformation/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-stack` | Stack | Create a new CloudFormation stack |
| `update-stack` | Stack | Update an existing stack |
| `delete-stack` | Stack | Delete a stack |
| `describe-stacks` | Stack | Describe one or more stacks |
| `list-stacks` | Stack | List stacks with optional status filter |
| `describe-stack-events` | Stack | List events for a stack |
| `describe-stack-resources` | Stack | Describe all resources in a stack |
| `describe-stack-resource` | Stack | Describe a single resource in a stack |
| `list-stack-resources` | Stack | List resources in a stack (paginated) |
| `get-template` | Stack | Retrieve the template for a stack |
| `get-template-summary` | Stack | Get summary info about a template |
| `validate-template` | Stack | Validate a template |
| `get-stack-policy` | Stack | Get the stack policy |
| `set-stack-policy` | Stack | Set a stack policy |
| `cancel-update-stack` | Stack | Cancel a stack update in progress |
| `continue-update-rollback` | Stack | Continue rolling back a stack |
| `rollback-stack` | Stack | Roll back a stack to the last stable state |
| `update-termination-protection` | Stack | Enable or disable termination protection |
| `estimate-template-cost` | Stack | Estimate monthly cost of a template |
| `signal-resource` | Stack | Send a signal to a wait condition or resource |
| `deploy` | Stack | Deploy a template (create or update with change set) |
| `package` | Stack | Package local artifacts and upload to S3 |
| `create-change-set` | Change Set | Create a change set for a stack |
| `describe-change-set-hooks` | Change Set | Describe hooks for a change set |
| `delete-change-set` | Change Set | Delete a change set |
| `describe-change-set` | Change Set | Describe a change set |
| `execute-change-set` | Change Set | Execute a change set |
| `list-change-sets` | Change Set | List change sets for a stack |
| `create-stack-set` | Stack Set | Create a stack set |
| `update-stack-set` | Stack Set | Update a stack set |
| `delete-stack-set` | Stack Set | Delete a stack set |
| `describe-stack-set` | Stack Set | Describe a stack set |
| `list-stack-sets` | Stack Set | List stack sets |
| `create-stack-instances` | Stack Set | Create stack instances in a stack set |
| `update-stack-instances` | Stack Set | Update stack instances |
| `delete-stack-instances` | Stack Set | Delete stack instances |
| `describe-stack-instance` | Stack Set | Describe a stack instance |
| `list-stack-instances` | Stack Set | List stack instances |
| `describe-stack-set-operation` | Stack Set | Describe a stack set operation |
| `list-stack-set-operations` | Stack Set | List stack set operations |
| `list-stack-set-operation-results` | Stack Set | List results of a stack set operation |
| `stop-stack-set-operation` | Stack Set | Stop a stack set operation |
| `import-stacks-to-stack-set` | Stack Set | Import stacks into a stack set |
| `detect-stack-drift` | Drift | Start drift detection on a stack |
| `detect-stack-resource-drift` | Drift | Detect drift on a specific resource |
| `detect-stack-set-drift` | Drift | Start drift detection on a stack set |
| `describe-stack-drift-detection-status` | Drift | Check drift detection status |
| `describe-stack-resource-drifts` | Drift | List resource drift results |
| `create-stack-refactor` | Refactor | Create a stack refactor |
| `execute-stack-refactor` | Refactor | Execute a stack refactor |
| `list-stack-refactor-actions` | Refactor | List actions for a stack refactor |
| `describe-stack-refactor` | Refactor | Describe a stack refactor |
| `list-stack-refactors` | Refactor | List stack refactors |
| `execute-stack-refactor` | Refactor | Execute a stack refactor |
| `create-generated-template` | Generated Template | Create a generated template |
| `delete-generated-template` | Generated Template | Delete a generated template |
| `describe-generated-template` | Generated Template | Describe a generated template |
| `get-generated-template` | Generated Template | Get the template body |
| `list-generated-templates` | Generated Template | List generated templates |
| `update-generated-template` | Generated Template | Update a generated template |
| `start-resource-scan` | Resource Scan | Start scanning for resources |
| `describe-resource-scan` | Resource Scan | Describe a resource scan |
| `list-resource-scans` | Resource Scan | List resource scans |
| `list-resource-scan-resources` | Resource Scan | List scanned resources |
| `list-resource-scan-related-resources` | Resource Scan | List related resources |
| `register-type` | Type Registry | Register a type (resource, module, hook) |
| `deregister-type` | Type Registry | Deregister a type version |
| `describe-type` | Type Registry | Describe a registered type |
| `describe-type-registration` | Type Registry | Describe type registration status |
| `list-types` | Type Registry | List registered types |
| `list-type-registrations` | Type Registry | List type registration attempts |
| `list-type-versions` | Type Registry | List versions of a type |
| `set-type-default-version` | Type Registry | Set default version for a type |
| `set-type-configuration` | Type Registry | Set configuration for a type |
| `batch-describe-type-configurations` | Type Registry | Batch describe type configurations |
| `publish-type` | Type Registry | Publish a type to the registry |
| `test-type` | Type Registry | Test a registered type |
| `activate-type` | Type Registry | Activate a third-party type |
| `deactivate-type` | Type Registry | Deactivate a type |
| `register-publisher` | Type Registry | Register as a type publisher |
| `describe-publisher` | Type Registry | Describe a registered publisher |
| `record-handler-progress` | Type Registry | Record handler progress for a type |
| `list-exports` | Export/Import | List all stack exports |
| `list-imports` | Export/Import | List stacks importing an export |
| `describe-account-limits` | Export/Import | Describe CloudFormation account limits |
| `activate-organizations-access` | Organizations | Enable Organizations access |
| `deactivate-organizations-access` | Organizations | Disable Organizations access |
| `describe-organizations-access` | Organizations | Describe Organizations access status |
| `list-hook-results` | Hooks | List hook results for a stack operation |
| `get-hook-result` | Hooks | Get details for a specific hook result |

---

## Global Options

These options are available on ALL `aws cloudformation` commands.

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

### Stack Status Values
| Status | Description |
|--------|-------------|
| `CREATE_IN_PROGRESS` | Stack creation in progress |
| `CREATE_FAILED` | Stack creation failed |
| `CREATE_COMPLETE` | Stack creation complete |
| `ROLLBACK_IN_PROGRESS` | Stack creation rollback in progress |
| `ROLLBACK_FAILED` | Stack creation rollback failed |
| `ROLLBACK_COMPLETE` | Stack creation rollback complete |
| `DELETE_IN_PROGRESS` | Stack deletion in progress |
| `DELETE_FAILED` | Stack deletion failed |
| `DELETE_COMPLETE` | Stack deletion complete |
| `UPDATE_IN_PROGRESS` | Stack update in progress |
| `UPDATE_COMPLETE_CLEANUP_IN_PROGRESS` | Cleanup after update |
| `UPDATE_COMPLETE` | Stack update complete |
| `UPDATE_FAILED` | Stack update failed |
| `UPDATE_ROLLBACK_IN_PROGRESS` | Rollback of stack update in progress |
| `UPDATE_ROLLBACK_FAILED` | Rollback of stack update failed |
| `UPDATE_ROLLBACK_COMPLETE_CLEANUP_IN_PROGRESS` | Cleanup after rollback |
| `UPDATE_ROLLBACK_COMPLETE` | Rollback complete |
| `REVIEW_IN_PROGRESS` | Stack is being reviewed (change set) |
| `IMPORT_IN_PROGRESS` | Resource import in progress |
| `IMPORT_COMPLETE` | Resource import complete |
| `IMPORT_ROLLBACK_IN_PROGRESS` | Import rollback in progress |
| `IMPORT_ROLLBACK_FAILED` | Import rollback failed |
| `IMPORT_ROLLBACK_COMPLETE` | Import rollback complete |

### Change Set Status Values
| Status | Description |
|--------|-------------|
| `CREATE_PENDING` | Change set is being created |
| `CREATE_IN_PROGRESS` | Change set creation in progress |
| `CREATE_COMPLETE` | Change set ready to execute |
| `DELETE_FAILED` | Change set deletion failed |
| `DELETE_COMPLETE` | Change set deleted |
| `FAILED` | Change set creation failed (e.g., no changes) |

### Drift Status Values
| Status | Description |
|--------|-------------|
| `DRIFTED` | Resource or stack has drifted |
| `IN_SYNC` | Resource or stack matches template |
| `NOT_CHECKED` | Drift detection not performed |
| `DELETED` | Resource was deleted |
| `MODIFIED` | Resource was modified |

### Capabilities
When a template creates IAM resources, you must acknowledge with one of:
- `CAPABILITY_IAM` — Template creates IAM resources
- `CAPABILITY_NAMED_IAM` — Template creates IAM resources with custom names
- `CAPABILITY_AUTO_EXPAND` — Template uses macros or nested stacks

### Wait Commands
The `aws cloudformation wait` subcommand blocks until a resource reaches a specific state:

| Waiter | Description |
|--------|-------------|
| `stack-create-complete` | Wait until stack creation completes |
| `stack-update-complete` | Wait until stack update completes |
| `stack-delete-complete` | Wait until stack is deleted |
| `stack-exists` | Wait until stack exists |
| `stack-import-complete` | Wait until import completes |
| `stack-rollback-complete` | Wait until rollback completes |
| `change-set-create-complete` | Wait until change set is ready |
| `type-registration-complete` | Wait until type registration completes |

```bash
aws cloudformation wait stack-create-complete --stack-name my-stack
aws cloudformation wait change-set-create-complete \
  --stack-name my-stack --change-set-name my-changes
```
