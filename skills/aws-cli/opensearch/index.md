# AWS CLI v2 — OpenSearch (Service + Serverless) Command Reference Index

> Based on AWS CLI v2 documentation. Sources: https://docs.aws.amazon.com/cli/latest/reference/opensearch/ , https://docs.aws.amazon.com/cli/latest/reference/opensearchserverless/

---

## Quick Reference — `aws opensearch`

| Command | Category | Description |
|---------|----------|-------------|
| `create-domain` | Domain | Create a new OpenSearch domain |
| `delete-domain` | Domain | Delete an OpenSearch domain |
| `describe-domain` | Domain | Describe a single domain |
| `describe-domains` | Domain | Describe multiple domains |
| `describe-domain-config` | Domain | View domain configuration |
| `update-domain-config` | Domain | Modify domain configuration |
| `list-domain-names` | Domain | List all domain names |
| `describe-domain-health` | Domain | Check domain health |
| `describe-domain-nodes` | Domain | Get domain node information |
| `describe-domain-auto-tunes` | Domain | View auto-tuning settings |
| `describe-domain-change-progress` | Domain | Check config change progress |
| `cancel-domain-config-change` | Domain | Cancel pending config change |
| `describe-instance-type-limits` | Domain | Get instance type limits |
| `list-instance-type-details` | Domain | List instance type details |
| `get-compatible-versions` | Domain | Check version compatibility |
| `list-versions` | Domain | List available engine versions |
| `describe-reserved-instances` | Domain | List reserved instances |
| `describe-reserved-instance-offerings` | Domain | View reserved instance offerings |
| `purchase-reserved-instance-offering` | Domain | Purchase a reserved instance |
| `upgrade-domain` | Upgrade | Upgrade domain engine version |
| `get-upgrade-status` | Upgrade | Check upgrade progress |
| `get-upgrade-history` | Upgrade | View upgrade history |
| `start-service-software-update` | Upgrade | Start service software update |
| `cancel-service-software-update` | Upgrade | Cancel software update |
| `list-scheduled-actions` | Upgrade | List scheduled actions |
| `update-scheduled-action` | Upgrade | Update a scheduled action |
| `create-package` | Package | Create a deployment package |
| `delete-package` | Package | Delete a package |
| `update-package` | Package | Update a package |
| `describe-packages` | Package | List packages |
| `associate-package` | Package | Associate package with domain |
| `dissociate-package` | Package | Dissociate package from domain |
| `get-package-version-history` | Package | View package version history |
| `list-domains-for-package` | Package | List domains using a package |
| `list-packages-for-domain` | Package | List packages in a domain |
| `create-outbound-connection` | Connection | Create outbound connection |
| `delete-outbound-connection` | Connection | Delete outbound connection |
| `describe-outbound-connections` | Connection | List outbound connections |
| `accept-inbound-connection` | Connection | Accept inbound connection |
| `delete-inbound-connection` | Connection | Delete inbound connection |
| `describe-inbound-connections` | Connection | List inbound connections |
| `reject-inbound-connection` | Connection | Reject inbound connection |
| `create-vpc-endpoint` | VPC | Create VPC endpoint |
| `delete-vpc-endpoint` | VPC | Delete VPC endpoint |
| `describe-vpc-endpoints` | VPC | List VPC endpoints |
| `list-vpc-endpoints-for-domain` | VPC | List VPC endpoints for a domain |
| `authorize-vpc-endpoint-access` | VPC | Authorize VPC endpoint access |
| `revoke-vpc-endpoint-access` | VPC | Revoke VPC endpoint access |
| `list-vpc-endpoint-access` | VPC | List VPC endpoint permissions |
| `update-vpc-endpoint` | VPC | Update VPC endpoint |
| `create-application` | Application | Create an application |
| `delete-application` | Application | Delete an application |
| `update-application` | Application | Update an application |
| `get-application` | Application | Get application details |
| `list-applications` | Application | List applications |
| `create-index` | Index | Create an index |
| `delete-index` | Index | Delete an index |
| `get-index` | Index | Get index details |
| `update-index` | Index | Update an index |
| `add-data-source` | Data Source | Add a data source |
| `delete-data-source` | Data Source | Delete a data source |
| `get-data-source` | Data Source | Get data source details |
| `list-data-sources` | Data Source | List data sources |
| `update-data-source` | Data Source | Update a data source |
| `add-direct-query-data-source` | Data Source | Add direct query data source |
| `delete-direct-query-data-source` | Data Source | Delete direct query data source |
| `get-direct-query-data-source` | Data Source | Get direct query data source |
| `list-direct-query-data-sources` | Data Source | List direct query data sources |
| `update-direct-query-data-source` | Data Source | Update direct query data source |
| `start-domain-maintenance` | Maintenance | Start domain maintenance |
| `get-domain-maintenance-status` | Maintenance | Get maintenance status |
| `list-domain-maintenances` | Maintenance | List domain maintenances |
| `describe-dry-run-progress` | Maintenance | Check dry-run status |
| `add-tags` | Tags | Add tags to a domain |
| `remove-tags` | Tags | Remove tags from a domain |
| `list-tags` | Tags | List domain tags |

---

## Quick Reference — `aws opensearchserverless`

| Command | Category | Description |
|---------|----------|-------------|
| `create-collection` | Collection | Create a serverless collection |
| `delete-collection` | Collection | Delete a collection |
| `batch-get-collection` | Collection | Get multiple collections |
| `list-collections` | Collection | List collections |
| `update-collection` | Collection | Update a collection |
| `create-collection-group` | Collection | Create a collection group |
| `delete-collection-group` | Collection | Delete a collection group |
| `batch-get-collection-group` | Collection | Get multiple collection groups |
| `list-collection-groups` | Collection | List collection groups |
| `update-collection-group` | Collection | Update a collection group |
| `create-security-policy` | Security | Create encryption/network policy |
| `delete-security-policy` | Security | Delete a security policy |
| `get-security-policy` | Security | Get a security policy |
| `list-security-policies` | Security | List security policies |
| `update-security-policy` | Security | Update a security policy |
| `create-access-policy` | Security | Create a data access policy |
| `delete-access-policy` | Security | Delete an access policy |
| `get-access-policy` | Security | Get an access policy |
| `list-access-policies` | Security | List access policies |
| `update-access-policy` | Security | Update an access policy |
| `create-security-config` | Security | Create SAML/IAM Identity Center config |
| `delete-security-config` | Security | Delete a security config |
| `get-security-config` | Security | Get a security config |
| `list-security-configs` | Security | List security configs |
| `update-security-config` | Security | Update a security config |
| `create-vpc-endpoint` | VPC | Create a serverless VPC endpoint |
| `delete-vpc-endpoint` | VPC | Delete a VPC endpoint |
| `batch-get-vpc-endpoint` | VPC | Get multiple VPC endpoints |
| `list-vpc-endpoints` | VPC | List VPC endpoints |
| `update-vpc-endpoint` | VPC | Update a VPC endpoint |
| `create-lifecycle-policy` | Lifecycle | Create a lifecycle policy |
| `delete-lifecycle-policy` | Lifecycle | Delete a lifecycle policy |
| `batch-get-lifecycle-policy` | Lifecycle | Get multiple lifecycle policies |
| `batch-get-effective-lifecycle-policy` | Lifecycle | Get effective lifecycle policies |
| `list-lifecycle-policies` | Lifecycle | List lifecycle policies |
| `update-lifecycle-policy` | Lifecycle | Update a lifecycle policy |
| `create-index` | Index | Create a serverless index |
| `delete-index` | Index | Delete a serverless index |
| `get-index` | Index | Get index details |
| `update-index` | Index | Update an index |
| `get-account-settings` | Settings | Get account settings |
| `update-account-settings` | Settings | Update account settings |
| `get-policies-stats` | Settings | Get policy statistics |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List resource tags |

---

## Global Options

These options are available on ALL `aws opensearch` and `aws opensearchserverless` commands.

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

### Domain Processing Status Values
| Status | Description |
|--------|-------------|
| `Creating` | Domain is being created |
| `Active` | Domain is fully operational |
| `Modifying` | Domain configuration is being updated |
| `UpgradingEngineVersion` | Engine version upgrade in progress |
| `UpdatingServiceSoftware` | Service software update in progress |
| `Isolated` | Domain is isolated |
| `Deleting` | Domain is being deleted |

### Serverless Collection Types
| Type | Description |
|------|-------------|
| `SEARCH` | Full-text search workloads |
| `TIMESERIES` | Log analytics and time-series data |
| `VECTORSEARCH` | Machine learning vector embeddings |

### Serverless Collection Status Values
| Status | Description |
|--------|-------------|
| `CREATING` | Collection is being created |
| `DELETING` | Collection is being deleted |
| `ACTIVE` | Collection is ready |
| `FAILED` | Collection creation failed |

### Security Policy Types
| Type | Description |
|------|-------------|
| `encryption` | Encryption at rest configuration |
| `network` | Network access configuration |

### Connection Status Values
| Status | Description |
|--------|-------------|
| `PENDING_ACCEPTANCE` | Waiting for acceptance |
| `APPROVED` | Connection approved |
| `PROVISIONING` | Connection being provisioned |
| `ACTIVE` | Connection is active |
| `REJECTING` | Connection being rejected |
| `REJECTED` | Connection was rejected |
| `DELETING` | Connection being deleted |
| `DELETED` | Connection deleted |

### Instance Types (Common)
| Type | Description |
|------|-------------|
| `t3.small.search` | Development/testing |
| `m6g.large.search` | General purpose |
| `r6g.large.search` | Memory optimized |
| `c6g.large.search` | Compute optimized |
| `or1.medium.search` | OR1 instances |
| `ultrawarm1.medium.search` | UltraWarm (warm storage) |
