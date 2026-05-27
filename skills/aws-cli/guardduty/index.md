# AWS CLI v2 -- GuardDuty Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/guardduty/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-detector` | Detector | Create a new GuardDuty detector |
| `delete-detector` | Detector | Delete a GuardDuty detector |
| `get-detector` | Detector | Get detector details |
| `list-detectors` | Detector | List all detectors in the account |
| `update-detector` | Detector | Update detector settings |
| `get-findings` | Finding | Retrieve detailed finding information |
| `list-findings` | Finding | List finding IDs matching criteria |
| `get-findings-statistics` | Finding | Get aggregate finding statistics |
| `archive-findings` | Finding | Archive findings |
| `unarchive-findings` | Finding | Unarchive findings |
| `update-findings-feedback` | Finding | Mark findings as useful or not useful |
| `create-sample-findings` | Finding | Generate sample findings |
| `create-filter` | Filter | Create a findings filter |
| `delete-filter` | Filter | Delete a findings filter |
| `get-filter` | Filter | Get filter details |
| `list-filters` | Filter | List all filters for a detector |
| `update-filter` | Filter | Update a findings filter |
| `create-ip-set` | IP Set | Create a trusted IP set |
| `delete-ip-set` | IP Set | Delete an IP set |
| `get-ip-set` | IP Set | Get IP set details |
| `list-ip-sets` | IP Set | List all IP sets for a detector |
| `update-ip-set` | IP Set | Update an IP set |
| `create-threat-intel-set` | Threat Intel Set | Create a threat intelligence set |
| `delete-threat-intel-set` | Threat Intel Set | Delete a threat intelligence set |
| `get-threat-intel-set` | Threat Intel Set | Get threat intelligence set details |
| `list-threat-intel-sets` | Threat Intel Set | List all threat intelligence sets |
| `update-threat-intel-set` | Threat Intel Set | Update a threat intelligence set |
| `create-threat-entity-set` | Threat Entity Set | Create a threat entity set |
| `delete-threat-entity-set` | Threat Entity Set | Delete a threat entity set |
| `get-threat-entity-set` | Threat Entity Set | Get threat entity set details |
| `list-threat-entity-sets` | Threat Entity Set | List all threat entity sets |
| `update-threat-entity-set` | Threat Entity Set | Update a threat entity set |
| `create-trusted-entity-set` | Trusted Entity Set | Create a trusted entity set |
| `delete-trusted-entity-set` | Trusted Entity Set | Delete a trusted entity set |
| `get-trusted-entity-set` | Trusted Entity Set | Get trusted entity set details |
| `list-trusted-entity-sets` | Trusted Entity Set | List all trusted entity sets |
| `update-trusted-entity-set` | Trusted Entity Set | Update a trusted entity set |
| `create-malware-protection-plan` | Malware Protection | Create a malware protection plan |
| `delete-malware-protection-plan` | Malware Protection | Delete a malware protection plan |
| `get-malware-protection-plan` | Malware Protection | Get malware protection plan details |
| `list-malware-protection-plans` | Malware Protection | List malware protection plans |
| `update-malware-protection-plan` | Malware Protection | Update a malware protection plan |
| `start-malware-scan` | Malware Protection | Start a malware scan |
| `get-malware-scan` | Malware Protection | Get malware scan details |
| `get-malware-scan-settings` | Malware Protection | Get malware scan settings |
| `update-malware-scan-settings` | Malware Protection | Update malware scan settings |
| `describe-malware-scans` | Malware Protection | Describe malware scan results |
| `list-malware-scans` | Malware Protection | List malware scans |
| `send-object-malware-scan` | Malware Protection | Send object for malware scanning |
| `create-publishing-destination` | Publishing | Create a publishing destination |
| `delete-publishing-destination` | Publishing | Delete a publishing destination |
| `describe-publishing-destination` | Publishing | Describe a publishing destination |
| `list-publishing-destinations` | Publishing | List publishing destinations |
| `update-publishing-destination` | Publishing | Update a publishing destination |
| `create-members` | Member | Add member accounts |
| `delete-members` | Member | Remove member accounts |
| `get-members` | Member | Get member account details |
| `invite-members` | Member | Invite member accounts |
| `list-members` | Member | List member accounts |
| `disassociate-members` | Member | Disassociate member accounts |
| `start-monitoring-members` | Member | Start monitoring member accounts |
| `stop-monitoring-members` | Member | Stop monitoring member accounts |
| `accept-administrator-invitation` | Member | Accept administrator invitation |
| `disassociate-from-administrator-account` | Member | Disassociate from administrator |
| `get-administrator-account` | Member | Get administrator account details |
| `get-invitations-count` | Member | Get count of pending invitations |
| `list-invitations` | Member | List pending invitations |
| `decline-invitations` | Member | Decline invitations |
| `delete-invitations` | Member | Delete invitations |
| `get-member-detectors` | Member | Get member detector feature settings |
| `update-member-detectors` | Member | Update member detector settings |
| `get-remaining-free-trial-days` | Member | Get remaining free trial days |
| `enable-organization-admin-account` | Organization | Enable organization admin account |
| `disable-organization-admin-account` | Organization | Disable organization admin account |
| `list-organization-admin-accounts` | Organization | List organization admin accounts |
| `describe-organization-configuration` | Organization | Describe organization configuration |
| `update-organization-configuration` | Organization | Update organization configuration |
| `get-organization-statistics` | Organization | Get organization statistics |
| `list-coverage` | Coverage | List coverage details |
| `get-coverage-statistics` | Coverage | Get coverage statistics |
| `get-usage-statistics` | Usage | Get usage statistics |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

---

## Global Options

These options are available on ALL `aws guardduty` commands.

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

### Detector ID
- All GuardDuty operations require a detector ID (1-300 characters)
- Each region has one detector per account
- Use `list-detectors` to find your detector ID

### Finding Severity Values
| Severity Range | Level | Description |
|----------------|-------|-------------|
| 8.0 - 8.9 | High | Resource is compromised and actively used for unauthorized purposes |
| 4.0 - 6.9 | Medium | Suspicious activity that deviates from normally observed behavior |
| 1.0 - 3.9 | Low | Suspicious or malicious activity that was blocked before compromising the resource |

### Finding Criteria Attributes
Common filter attributes for `--finding-criteria`:
- `severity` — Finding severity (numeric)
- `type` — Finding type string
- `region` — AWS region
- `accountId` — AWS account ID
- `resource.resourceType` — Resource type (e.g., `Instance`, `AccessKey`, `S3Bucket`)
- `service.archived` — Whether finding is archived
- `updatedAt` — Last updated timestamp

### IP Set / Threat Intel Set Formats
| Format | Description |
|--------|-------------|
| `TXT` | Plain text, one IP per line |
| `STIX` | STIX 2.0/2.1 format |
| `OTX_CSV` | OTX CSV format |
| `ALIEN_VAULT` | AlienVault reputation format |
| `PROOF_POINT` | Proofpoint ET Intelligence format |
| `FIRE_EYE` | FireEye iSight threat intelligence format |

### Feature Names
| Feature | Description |
|---------|-------------|
| `S3_DATA_EVENTS` | S3 data event monitoring |
| `EKS_AUDIT_LOGS` | EKS audit log monitoring |
| `EBS_MALWARE_PROTECTION` | EBS volume malware scanning |
| `RDS_LOGIN_EVENTS` | RDS login event monitoring |
| `EKS_RUNTIME_MONITORING` | EKS runtime monitoring |
| `LAMBDA_NETWORK_LOGS` | Lambda network activity monitoring |
| `RUNTIME_MONITORING` | Runtime monitoring for EC2, ECS, EKS |
