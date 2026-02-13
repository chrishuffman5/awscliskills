# AWS CLI v2 -- Audit Manager Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/auditmanager/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-assessment` | Assessments | Create a new assessment |
| `get-assessment` | Assessments | Get assessment details |
| `update-assessment` | Assessments | Update an assessment |
| `delete-assessment` | Assessments | Delete an assessment |
| `list-assessments` | Assessments | List all assessments |
| `update-assessment-status` | Assessments | Update assessment status (active/inactive) |
| `update-assessment-control` | Assessments | Update a control within an assessment |
| `update-assessment-control-set-status` | Assessments | Update control set status |
| `get-change-logs` | Assessments | Get change logs for an assessment |
| `create-assessment-framework` | Assessment Frameworks | Create a custom framework |
| `get-assessment-framework` | Assessment Frameworks | Get framework details |
| `update-assessment-framework` | Assessment Frameworks | Update a custom framework |
| `delete-assessment-framework` | Assessment Frameworks | Delete a custom framework |
| `list-assessment-frameworks` | Assessment Frameworks | List all frameworks |
| `start-assessment-framework-share` | Assessment Frameworks | Share a framework with another account |
| `update-assessment-framework-share` | Assessment Frameworks | Update a framework share request |
| `delete-assessment-framework-share` | Assessment Frameworks | Delete a framework share request |
| `list-assessment-framework-share-requests` | Assessment Frameworks | List framework share requests |
| `create-control` | Controls | Create a custom control |
| `get-control` | Controls | Get control details |
| `update-control` | Controls | Update a custom control |
| `delete-control` | Controls | Delete a custom control |
| `list-controls` | Controls | List controls by type |
| `get-services-in-scope` | Controls | Get AWS services in scope |
| `list-keywords-for-data-source` | Controls | List keywords for a data source |
| `create-assessment-report` | Assessment Reports | Generate an assessment report |
| `delete-assessment-report` | Assessment Reports | Delete an assessment report |
| `list-assessment-reports` | Assessment Reports | List assessment reports |
| `get-assessment-report-url` | Assessment Reports | Get report download URL |
| `associate-assessment-report-evidence-folder` | Assessment Reports | Associate evidence folder with report |
| `disassociate-assessment-report-evidence-folder` | Assessment Reports | Disassociate evidence folder from report |
| `batch-associate-assessment-report-evidence` | Assessment Reports | Batch associate evidence with report |
| `batch-disassociate-assessment-report-evidence` | Assessment Reports | Batch disassociate evidence from report |
| `validate-assessment-report-integrity` | Assessment Reports | Validate report integrity |
| `get-evidence` | Evidence | Get a specific evidence item |
| `get-evidence-by-evidence-folder` | Evidence | Get evidence in a folder |
| `get-evidence-folder` | Evidence | Get evidence folder details |
| `get-evidence-folders-by-assessment` | Evidence | Get evidence folders for an assessment |
| `get-evidence-folders-by-assessment-control` | Evidence | Get evidence folders for a control |
| `batch-import-evidence-to-assessment-control` | Evidence | Import manual evidence |
| `get-evidence-file-upload-url` | Evidence | Get presigned URL for evidence upload |
| `get-delegations` | Delegations | Get delegations for the current user |
| `batch-create-delegation-by-assessment` | Delegations | Create delegations for an assessment |
| `batch-delete-delegation-by-assessment` | Delegations | Delete delegations for an assessment |
| `get-insights` | Insights | Get cross-assessment compliance insights |
| `get-insights-by-assessment` | Insights | Get insights for a specific assessment |
| `list-assessment-control-insights-by-control-domain` | Insights | List control insights by domain |
| `list-control-domain-insights` | Insights | List control domain insights |
| `list-control-domain-insights-by-assessment` | Insights | List domain insights for an assessment |
| `list-control-insights-by-control-domain` | Insights | List control insights by control domain |
| `register-account` | Account Settings | Register Audit Manager account |
| `deregister-account` | Account Settings | Deregister Audit Manager account |
| `get-account-status` | Account Settings | Get registration status |
| `get-settings` | Account Settings | Get Audit Manager settings |
| `update-settings` | Account Settings | Update Audit Manager settings |
| `register-organization-admin-account` | Account Settings | Register org delegated admin |
| `deregister-organization-admin-account` | Account Settings | Deregister org delegated admin |
| `get-organization-admin-account` | Account Settings | Get org admin account |
| `list-notifications` | Account Settings | List notifications |
| `list-tags-for-resource` | Account Settings | List tags for a resource |
| `tag-resource` | Account Settings | Add tags to a resource |
| `untag-resource` | Account Settings | Remove tags from a resource |

---

## Global Options

These options are available on ALL `aws auditmanager` commands.

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

### Assessment Status Values
| Status | Description |
|--------|-------------|
| `ACTIVE` | Assessment is actively collecting evidence |
| `INACTIVE` | Assessment is paused |

### Framework Types
| Type | Description |
|------|-------------|
| `Standard` | AWS-managed standard framework |
| `Custom` | User-created custom framework |

### Control Types
| Type | Description |
|------|-------------|
| `Standard` | AWS-managed standard control |
| `Custom` | User-created custom control |
| `Core` | Core control |

### Evidence Source Types
| Source | Description |
|--------|-------------|
| `AWS_Cloudtrail` | Evidence from AWS CloudTrail |
| `AWS_Config` | Evidence from AWS Config |
| `AWS_Security_Hub` | Evidence from Security Hub |
| `AWS_API_Call` | Evidence from API calls |
| `MANUAL` | Manually uploaded evidence |
| `Common_Control` | Common control evidence |
| `Core_Control` | Core control evidence |

### Source Frequency
| Frequency | Description |
|-----------|-------------|
| `DAILY` | Collected daily |
| `WEEKLY` | Collected weekly |
| `MONTHLY` | Collected monthly |

### Share Request Action Types
| Action | Description |
|--------|-------------|
| `ACCEPT` | Accept the share request |
| `DECLINE` | Decline the share request |
| `REVOKE` | Revoke the share request |
