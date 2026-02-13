# AWS CLI v2 -- License Manager Command Reference Index

> Based on AWS CLI v2 documentation. Sources:
> - https://docs.aws.amazon.com/cli/latest/reference/license-manager/
> - https://docs.aws.amazon.com/cli/latest/reference/license-manager-linux-subscriptions/
> - https://docs.aws.amazon.com/cli/latest/reference/license-manager-user-subscriptions/

---

## Quick Reference

**Namespace:** `license-manager` (LM), `license-manager-linux-subscriptions` (LMLS), `license-manager-user-subscriptions` (LMUS)

| Command | Namespace | Category | Description |
|---------|-----------|----------|-------------|
| `create-license-configuration` | LM | License Configuration | Create a license configuration |
| `delete-license-configuration` | LM | License Configuration | Delete a license configuration |
| `get-license-configuration` | LM | License Configuration | Get license configuration details |
| `list-license-configurations` | LM | License Configuration | List license configurations (paginated) |
| `update-license-configuration` | LM | License Configuration | Update a license configuration |
| `list-license-configurations-for-organization` | LM | License Configuration | List configurations across organization |
| `list-usage-for-license-configuration` | LM | License Configuration | List usage data for a configuration (paginated) |
| `list-associations-for-license-configuration` | LM | License Configuration | List resource associations (paginated) |
| `list-failures-for-license-configuration-operations` | LM | License Configuration | List operation failures (paginated) |
| `update-license-specifications-for-resource` | LM | License Configuration | Update resource license specs |
| `list-license-specifications-for-resource` | LM | License Configuration | List resource license specs (paginated) |
| `list-resource-inventory` | LM | License Configuration | List resource inventory (paginated) |
| `create-license` | LM | License | Create a new license |
| `delete-license` | LM | License | Delete a license |
| `get-license` | LM | License | Get license details |
| `list-licenses` | LM | License | List licenses (paginated) |
| `create-license-version` | LM | License | Create a new license version |
| `list-license-versions` | LM | License | List license versions (paginated) |
| `get-license-usage` | LM | License | Get license usage information |
| `check-in-license` | LM | License | Check in a borrowed license |
| `checkout-license` | LM | License | Check out a license |
| `checkout-borrow-license` | LM | License | Check out and borrow a license |
| `extend-license-consumption` | LM | License | Extend license consumption period |
| `list-received-licenses` | LM | License | List received licenses (paginated) |
| `list-received-licenses-for-organization` | LM | License | List received licenses across organization (paginated) |
| `create-grant` | LM | Grant | Create a license grant |
| `delete-grant` | LM | Grant | Delete a grant |
| `get-grant` | LM | Grant | Get grant details |
| `create-grant-version` | LM | Grant | Create a new grant version |
| `list-distributed-grants` | LM | Grant | List distributed grants (paginated) |
| `list-received-grants` | LM | Grant | List received grants (paginated) |
| `list-received-grants-for-organization` | LM | Grant | List received grants across organization (paginated) |
| `accept-grant` | LM | Grant | Accept a license grant |
| `reject-grant` | LM | Grant | Reject a license grant |
| `create-token` | LM | Token | Create a refresh token (JWT) |
| `delete-token` | LM | Token | Delete a token |
| `list-tokens` | LM | Token | List tokens (paginated) |
| `get-access-token` | LM | Token | Get an access token from refresh token |
| `create-license-asset-group` | LM | Asset Group | Create a license asset group |
| `delete-license-asset-group` | LM | Asset Group | Delete a license asset group |
| `get-license-asset-group` | LM | Asset Group | Get license asset group details |
| `list-license-asset-groups` | LM | Asset Group | List license asset groups (paginated) |
| `update-license-asset-group` | LM | Asset Group | Update a license asset group |
| `list-assets-for-license-asset-group` | LM | Asset Group | List assets in an asset group (paginated) |
| `create-license-asset-ruleset` | LM | Asset Ruleset | Create a license asset ruleset |
| `delete-license-asset-ruleset` | LM | Asset Ruleset | Delete a license asset ruleset |
| `get-license-asset-ruleset` | LM | Asset Ruleset | Get license asset ruleset details |
| `list-license-asset-rulesets` | LM | Asset Ruleset | List license asset rulesets (paginated) |
| `update-license-asset-ruleset` | LM | Asset Ruleset | Update a license asset ruleset |
| `create-license-conversion-task-for-resource` | LM | Conversion | Create a license conversion task |
| `get-license-conversion-task` | LM | Conversion | Get conversion task details |
| `list-license-conversion-tasks` | LM | Conversion | List conversion tasks (paginated) |
| `create-license-manager-report-generator` | LM | Report | Create a report generator |
| `delete-license-manager-report-generator` | LM | Report | Delete a report generator |
| `get-license-manager-report-generator` | LM | Report | Get report generator details |
| `list-license-manager-report-generators` | LM | Report | List report generators (paginated) |
| `update-license-manager-report-generator` | LM | Report | Update a report generator |
| `get-service-settings` | LM | Service Settings | Get License Manager service settings |
| `update-service-settings` | LM | Service Settings | Update License Manager service settings |
| `list-linux-subscriptions` | LMLS | Linux Subscription | List Linux subscriptions (paginated) |
| `list-linux-subscription-instances` | LMLS | Linux Subscription | List Linux subscription instances (paginated) |
| `register-subscription-provider` | LMLS | Linux Subscription | Register a BYOL subscription provider |
| `deregister-subscription-provider` | LMLS | Linux Subscription | Deregister a subscription provider |
| `get-registered-subscription-provider` | LMLS | Linux Subscription | Get subscription provider details |
| `list-registered-subscription-providers` | LMLS | Linux Subscription | List subscription providers (paginated) |
| `get-service-settings` | LMLS | Linux Subscription | Get Linux subscriptions service settings |
| `update-service-settings` | LMLS | Linux Subscription | Update Linux subscriptions service settings |
| `register-identity-provider` | LMUS | User Subscription | Register an identity provider |
| `deregister-identity-provider` | LMUS | User Subscription | Deregister an identity provider |
| `list-identity-providers` | LMUS | User Subscription | List identity providers (paginated) |
| `update-identity-provider-settings` | LMUS | User Subscription | Update identity provider settings |
| `associate-user` | LMUS | User Subscription | Associate a user with an EC2 instance |
| `disassociate-user` | LMUS | User Subscription | Disassociate a user from an instance |
| `list-user-associations` | LMUS | User Subscription | List user associations (paginated) |
| `list-instances` | LMUS | User Subscription | List EC2 instances (paginated) |
| `list-product-subscriptions` | LMUS | User Subscription | List product subscriptions (paginated) |
| `start-product-subscription` | LMUS | User Subscription | Start a product subscription for a user |
| `stop-product-subscription` | LMUS | User Subscription | Stop a product subscription |
| `create-license-server-endpoint` | LMUS | User Subscription | Create a license server endpoint |
| `delete-license-server-endpoint` | LMUS | User Subscription | Delete a license server endpoint |
| `list-license-server-endpoints` | LMUS | User Subscription | List license server endpoints (paginated) |
| `tag-resource` | LM | Tags | Add tags to a License Manager resource |
| `untag-resource` | LM | Tags | Remove tags from a License Manager resource |
| `list-tags-for-resource` | LM | Tags | List tags on a License Manager resource |
| `tag-resource` | LMLS | Tags | Add tags to a Linux subscriptions resource |
| `untag-resource` | LMLS | Tags | Remove tags from a Linux subscriptions resource |
| `list-tags-for-resource` | LMLS | Tags | List tags on a Linux subscriptions resource |
| `tag-resource` | LMUS | Tags | Add tags to a user subscriptions resource |
| `untag-resource` | LMUS | Tags | Remove tags from a user subscriptions resource |
| `list-tags-for-resource` | LMUS | Tags | List tags on a user subscriptions resource |

---

## Global Options

These options are available on ALL commands across all three namespaces.

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

### License Counting Types
| Type | Description |
|------|-------------|
| `vCPU` | Count by virtual CPUs |
| `Instance` | Count by instance |
| `Core` | Count by physical cores |
| `Socket` | Count by physical sockets |

### License Statuses
| Status | Description |
|--------|-------------|
| `AVAILABLE` | License is available for use |
| `PENDING_AVAILABLE` | License is pending availability |
| `DEACTIVATED` | License has been deactivated |
| `SUSPENDED` | License has been suspended |
| `EXPIRED` | License has expired |
| `PENDING_DELETE` | License deletion is pending |
| `DELETED` | License has been deleted |

### Grant Statuses
| Status | Description |
|--------|-------------|
| `PENDING_WORKFLOW` | Grant workflow is pending |
| `PENDING_ACCEPT` | Grant is pending acceptance |
| `REJECTED` | Grant was rejected |
| `ACTIVE` | Grant is active |
| `FAILED_WORKFLOW` | Grant workflow failed |
| `DELETED` | Grant has been deleted |
| `PENDING_DELETE` | Grant deletion is pending |
| `DISABLED` | Grant is disabled |
| `WORKFLOW_COMPLETED` | Grant workflow completed |

### Allowed Grant Operations
- `CreateGrant`
- `CheckoutLicense`
- `CheckoutBorrowLicense`
- `CheckInLicense`
- `ExtendConsumptionLicense`
- `ListPurchasedLicenses`
- `CreateToken`

### User Subscription Products
| Product | Description |
|---------|-------------|
| `VISUAL_STUDIO_ENTERPRISE` | Visual Studio Enterprise |
| `VISUAL_STUDIO_PROFESSIONAL` | Visual Studio Professional |
| `OFFICE_PROFESSIONAL_PLUS` | Office Professional Plus |
| `REMOTE_DESKTOP_SERVICES` | Remote Desktop Services |
