# AWS CLI v2 -- Service Catalog Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/servicecatalog/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-portfolio` | Portfolio | Create a portfolio |
| `delete-portfolio` | Portfolio | Delete a portfolio |
| `describe-portfolio` | Portfolio | Describe a portfolio |
| `update-portfolio` | Portfolio | Update a portfolio |
| `list-portfolios` | Portfolio | List all portfolios |
| `list-accepted-portfolio-shares` | Portfolio | List accepted portfolio shares |
| `accept-portfolio-share` | Portfolio | Accept a portfolio share |
| `reject-portfolio-share` | Portfolio | Reject a portfolio share |
| `create-portfolio-share` | Portfolio | Share a portfolio |
| `delete-portfolio-share` | Portfolio | Remove a portfolio share |
| `describe-portfolio-share-status` | Portfolio | Describe share operation status |
| `describe-portfolio-shares` | Portfolio | List shares for a portfolio |
| `list-portfolio-access` | Portfolio | List accounts with access to a portfolio |
| `list-organization-portfolio-access` | Portfolio | List org nodes with access to a portfolio |
| `update-portfolio-share` | Portfolio | Update a portfolio share |
| `create-product` | Product | Create a product |
| `delete-product` | Product | Delete a product |
| `describe-product` | Product | Describe a product (end user view) |
| `describe-product-as-admin` | Product | Describe a product (admin view) |
| `describe-product-view` | Product | Describe a product view |
| `update-product` | Product | Update a product |
| `list-portfolios-for-product` | Product | List portfolios associated with a product |
| `associate-product-with-portfolio` | Product | Associate a product with a portfolio |
| `disassociate-product-from-portfolio` | Product | Disassociate a product from a portfolio |
| `copy-product` | Product | Copy a product |
| `describe-copy-product-status` | Product | Describe copy product status |
| `search-products` | Product | Search products (end user view) |
| `search-products-as-admin` | Product | Search products (admin view) |
| `create-provisioning-artifact` | Provisioning Artifact | Create a provisioning artifact |
| `delete-provisioning-artifact` | Provisioning Artifact | Delete a provisioning artifact |
| `describe-provisioning-artifact` | Provisioning Artifact | Describe a provisioning artifact |
| `update-provisioning-artifact` | Provisioning Artifact | Update a provisioning artifact |
| `list-provisioning-artifacts` | Provisioning Artifact | List provisioning artifacts for a product |
| `describe-provisioning-parameters` | Provisioning Artifact | Describe parameters for provisioning |
| `provision-product` | Provisioned Product | Provision a product |
| `terminate-provisioned-product` | Provisioned Product | Terminate a provisioned product |
| `update-provisioned-product` | Provisioned Product | Update a provisioned product |
| `update-provisioned-product-properties` | Provisioned Product | Update provisioned product properties |
| `describe-provisioned-product` | Provisioned Product | Describe a provisioned product |
| `search-provisioned-products` | Provisioned Product | Search provisioned products |
| `scan-provisioned-products` | Provisioned Product | Scan provisioned products |
| `get-provisioned-product-outputs` | Provisioned Product | Get outputs of a provisioned product |
| `import-as-provisioned-product` | Provisioned Product | Import a resource as a provisioned product |
| `list-record-history` | Provisioned Product | List provisioning records |
| `describe-record` | Provisioned Product | Describe a provisioning record |
| `list-stack-instances-for-provisioned-product` | Provisioned Product | List stack instances |
| `create-provisioned-product-plan` | Plan | Create a provisioned product plan |
| `delete-provisioned-product-plan` | Plan | Delete a provisioned product plan |
| `describe-provisioned-product-plan` | Plan | Describe a provisioned product plan |
| `execute-provisioned-product-plan` | Plan | Execute a provisioned product plan |
| `list-provisioned-product-plans` | Plan | List provisioned product plans |
| `create-constraint` | Constraint | Create a constraint |
| `delete-constraint` | Constraint | Delete a constraint |
| `describe-constraint` | Constraint | Describe a constraint |
| `update-constraint` | Constraint | Update a constraint |
| `list-constraints-for-portfolio` | Constraint | List constraints for a portfolio |
| `list-launch-paths` | Constraint | List launch paths for a product |
| `create-service-action` | Service Action | Create a service action |
| `delete-service-action` | Service Action | Delete a service action |
| `describe-service-action` | Service Action | Describe a service action |
| `update-service-action` | Service Action | Update a service action |
| `list-service-actions` | Service Action | List service actions |
| `associate-service-action-with-provisioning-artifact` | Service Action | Associate a service action with an artifact |
| `disassociate-service-action-from-provisioning-artifact` | Service Action | Disassociate a service action |
| `batch-associate-service-action-with-provisioning-artifact` | Service Action | Batch associate service actions |
| `batch-disassociate-service-action-from-provisioning-artifact` | Service Action | Batch disassociate service actions |
| `list-service-actions-for-provisioning-artifact` | Service Action | List service actions for an artifact |
| `describe-service-action-execution-parameters` | Service Action | Describe execution parameters |
| `execute-provisioned-product-service-action` | Service Action | Execute a service action |
| `associate-principal-with-portfolio` | Principal | Associate a principal with a portfolio |
| `disassociate-principal-from-portfolio` | Principal | Disassociate a principal |
| `list-principals-for-portfolio` | Principal | List principals for a portfolio |
| `create-tag-option` | Tag Option | Create a tag option |
| `delete-tag-option` | Tag Option | Delete a tag option |
| `describe-tag-option` | Tag Option | Describe a tag option |
| `update-tag-option` | Tag Option | Update a tag option |
| `list-tag-options` | Tag Option | List tag options |
| `associate-tag-option-with-resource` | Tag Option | Associate a tag option with a resource |
| `disassociate-tag-option-from-resource` | Tag Option | Disassociate a tag option |
| `list-resources-for-tag-option` | Tag Option | List resources for a tag option |
| `associate-budget-with-resource` | Budget | Associate a budget with a resource |
| `disassociate-budget-from-resource` | Budget | Disassociate a budget |
| `list-budgets-for-resource` | Budget | List budgets for a resource |
| `enable-aws-organizations-access` | Organizations | Enable Organizations access |
| `disable-aws-organizations-access` | Organizations | Disable Organizations access |
| `get-aws-organizations-access-status` | Organizations | Get Organizations access status |
| `notify-provision-product-engine-workflow-result` | Notification | Notify provision workflow result |
| `notify-terminate-provisioned-product-engine-workflow-result` | Notification | Notify terminate workflow result |
| `notify-update-provisioned-product-engine-workflow-result` | Notification | Notify update workflow result |

---

## Global Options

These options are available on ALL `aws servicecatalog` commands.

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

### Product Types
| Type | Description |
|------|-------------|
| `CLOUD_FORMATION_TEMPLATE` | AWS CloudFormation template |
| `MARKETPLACE` | AWS Marketplace product |
| `TERRAFORM_OPEN_SOURCE` | Terraform open-source template |
| `TERRAFORM_CLOUD` | Terraform Cloud template |
| `EXTERNAL` | External product type |

### Provisioned Product Status Values
| Status | Description |
|--------|-------------|
| `AVAILABLE` | Product is available and operational |
| `UNDER_CHANGE` | Product is being updated |
| `TAINTED` | Product has drifted from expected state |
| `ERROR` | An error occurred during provisioning |
| `PLAN_IN_PROGRESS` | A plan is being evaluated |

### Record Status Values
| Status | Description |
|--------|-------------|
| `CREATED` | Record has been created |
| `IN_PROGRESS` | Operation is in progress |
| `IN_PROGRESS_IN_ERROR` | Operation in progress with errors |
| `SUCCEEDED` | Operation succeeded |
| `FAILED` | Operation failed |

### Constraint Types
| Type | Description |
|------|-------------|
| `LAUNCH` | Launch constraint (IAM role) |
| `NOTIFICATION` | SNS notification constraint |
| `STACKSET` | AWS CloudFormation StackSet constraint |
| `TEMPLATE` | Template constraint (parameter rules) |
| `RESOURCE_UPDATE` | Tag update constraint |

### Portfolio Share Types
| Type | Description |
|------|-------------|
| `IMPORTED` | Share imported from another account |
| `AWS_SERVICECATALOG` | Shared via Service Catalog |
| `AWS_ORGANIZATIONS` | Shared via AWS Organizations |
