# AWS CLI v2 -- Inspector (Amazon Inspector + Inspector Scan) Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/inspector2/ , https://docs.aws.amazon.com/cli/latest/reference/inspector-scan/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `enable` | Enablement | Enable Inspector scanning for resource types |
| `disable` | Enablement | Disable Inspector scanning for resource types |
| `batch-get-account-status` | Enablement | Get Inspector status for multiple accounts |
| `batch-get-free-trial-info` | Enablement | Get free trial information for accounts |
| `get-configuration` | Enablement | Get Inspector configuration for ECR scan duration |
| `update-configuration` | Enablement | Update Inspector configuration |
| `update-organization-configuration` | Enablement | Update organization-wide auto-enable settings |
| `describe-organization-configuration` | Enablement | Describe organization auto-enable configuration |
| `list-account-permissions` | Enablement | List account permissions for Inspector |
| `list-usage-totals` | Enablement | List usage totals for accounts |
| `get-member` | Enablement | Get details for a member account |
| `list-members` | Enablement | List member accounts |
| `associate-member` | Enablement | Associate a member account |
| `disassociate-member` | Enablement | Disassociate a member account |
| `batch-get-member-ec2-deep-inspection-status` | Enablement | Get EC2 deep inspection status for members |
| `batch-update-member-ec2-deep-inspection-status` | Enablement | Update EC2 deep inspection status for members |
| `get-ec2-deep-inspection-configuration` | Enablement | Get EC2 deep inspection configuration |
| `update-ec2-deep-inspection-configuration` | Enablement | Update EC2 deep inspection configuration |
| `update-org-ec2-deep-inspection-configuration` | Enablement | Update organization EC2 deep inspection configuration |
| `list-findings` | Findings | List findings with optional filters |
| `list-finding-aggregations` | Findings | List finding aggregations by group |
| `batch-get-finding-details` | Findings | Get detailed finding information |
| `search-vulnerabilities` | Findings | Search for vulnerability intelligence |
| `create-filter` | Filters | Create a suppression or findings filter |
| `delete-filter` | Filters | Delete a filter |
| `update-filter` | Filters | Update an existing filter |
| `list-filters` | Filters | List all filters |
| `create-findings-report` | Findings Reports | Export findings report to S3 |
| `cancel-findings-report` | Findings Reports | Cancel a findings report generation |
| `get-findings-report-status` | Findings Reports | Get status of a findings report |
| `create-sbom-export` | Findings Reports | Export an SBOM report to S3 |
| `cancel-sbom-export` | Findings Reports | Cancel an SBOM export |
| `get-sbom-export` | Findings Reports | Get status of an SBOM export |
| `list-coverage` | Coverage | List covered resources |
| `list-coverage-statistics` | Coverage | List coverage statistics by group |
| `get-clusters-for-image` | Coverage | Get ECS clusters running an image |
| `create-cis-scan-configuration` | CIS Scans | Create a CIS scan configuration |
| `delete-cis-scan-configuration` | CIS Scans | Delete a CIS scan configuration |
| `update-cis-scan-configuration` | CIS Scans | Update a CIS scan configuration |
| `list-cis-scan-configurations` | CIS Scans | List CIS scan configurations |
| `list-cis-scans` | CIS Scans | List CIS scans |
| `get-cis-scan-report` | CIS Scans | Get a CIS scan report |
| `get-cis-scan-result-details` | CIS Scans | Get CIS scan result details |
| `list-cis-scan-results-aggregated-by-checks` | CIS Scans | List CIS results aggregated by checks |
| `list-cis-scan-results-aggregated-by-target-resource` | CIS Scans | List CIS results aggregated by target resource |
| `start-cis-session` | CIS Scans | Start a CIS scan session |
| `stop-cis-session` | CIS Scans | Stop a CIS scan session |
| `send-cis-session-health` | CIS Scans | Send CIS session health data |
| `send-cis-session-telemetry` | CIS Scans | Send CIS session telemetry data |
| `create-code-security-integration` | Code Security | Create a code security integration |
| `delete-code-security-integration` | Code Security | Delete a code security integration |
| `update-code-security-integration` | Code Security | Update a code security integration |
| `get-code-security-integration` | Code Security | Get code security integration details |
| `list-code-security-integrations` | Code Security | List code security integrations |
| `create-code-security-scan-configuration` | Code Security | Create a code security scan configuration |
| `delete-code-security-scan-configuration` | Code Security | Delete a code security scan configuration |
| `update-code-security-scan-configuration` | Code Security | Update a code security scan configuration |
| `get-code-security-scan-configuration` | Code Security | Get code security scan configuration |
| `list-code-security-scan-configurations` | Code Security | List code security scan configurations |
| `list-code-security-scan-configuration-associations` | Code Security | List scan configuration associations |
| `batch-associate-code-security-scan-configuration` | Code Security | Batch associate scan configurations |
| `batch-disassociate-code-security-scan-configuration` | Code Security | Batch disassociate scan configurations |
| `start-code-security-scan` | Code Security | Start a code security scan |
| `get-code-security-scan` | Code Security | Get code security scan status |
| `get-encryption-key` | Encryption | Get the KMS encryption key |
| `update-encryption-key` | Encryption | Update the KMS encryption key |
| `reset-encryption-key` | Encryption | Reset to AWS-managed encryption key |
| `enable-delegated-admin-account` | Delegated Admin | Enable delegated admin for Organizations |
| `disable-delegated-admin-account` | Delegated Admin | Disable delegated admin |
| `get-delegated-admin-account` | Delegated Admin | Get delegated admin account details |
| `list-delegated-admin-accounts` | Delegated Admin | List delegated admin accounts |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |
| `scan-sbom` | SBOM Scan | Scan an SBOM for vulnerabilities (inspector-scan) |

---

## Global Options

These options are available on ALL `aws inspector2` and `aws inspector-scan` commands.

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

### Account Status Values
| Status | Description |
|--------|-------------|
| `ENABLING` | Inspector is being enabled |
| `ENABLED` | Inspector is active |
| `DISABLING` | Inspector is being disabled |
| `DISABLED` | Inspector is not active |
| `SUSPENDING` | Inspector is being suspended |
| `SUSPENDED` | Inspector is suspended (free trial ended, no payment) |

### Resource Types for Scanning
| Type | Description |
|------|-------------|
| `EC2` | Amazon EC2 instance scanning |
| `ECR` | Amazon ECR container image scanning |
| `LAMBDA` | AWS Lambda function scanning |
| `LAMBDA_CODE` | AWS Lambda code scanning |
| `CODE_REPOSITORY` | Code repository scanning |

### Finding Severity Values
| Severity | Description |
|----------|-------------|
| `CRITICAL` | Critical vulnerability requiring immediate attention |
| `HIGH` | High severity vulnerability |
| `MEDIUM` | Medium severity vulnerability |
| `LOW` | Low severity vulnerability |
| `INFORMATIONAL` | Informational finding |
| `UNTRIAGED` | Severity not yet determined |

### Finding Status Values
| Status | Description |
|--------|-------------|
| `ACTIVE` | Finding is active and requires attention |
| `SUPPRESSED` | Finding matches a suppression filter |
| `CLOSED` | Finding has been resolved |

### Scan Type Values
| Type | Description |
|------|-------------|
| `NETWORK` | Network reachability scan |
| `PACKAGE` | Software package vulnerability scan |
| `CODE` | Code vulnerability scan |
