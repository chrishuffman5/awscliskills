# AWS CLI v2 -- Shield (AWS Shield Advanced) Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/shield/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-subscription` | Subscription | Activate Shield Advanced for the account |
| `describe-subscription` | Subscription | Get Shield Advanced subscription details |
| `update-subscription` | Subscription | Update subscription auto-renew setting |
| `get-subscription-state` | Subscription | Get current subscription state |
| `create-protection` | Protections | Create a Shield Advanced protection for a resource |
| `delete-protection` | Protections | Delete a Shield Advanced protection |
| `describe-protection` | Protections | Describe a Shield Advanced protection |
| `list-protections` | Protections | List all Shield Advanced protections |
| `create-protection-group` | Protections | Create a protection group |
| `delete-protection-group` | Protections | Delete a protection group |
| `describe-protection-group` | Protections | Describe a protection group |
| `list-protection-groups` | Protections | List all protection groups |
| `update-protection-group` | Protections | Update a protection group |
| `list-resources-in-protection-group` | Protections | List resources in a protection group |
| `describe-attack` | Attacks | Get details of a detected attack |
| `describe-attack-statistics` | Attacks | Get attack statistics summary |
| `list-attacks` | Attacks | List attacks within a time range |
| `associate-drt-role` | DRT Access | Grant DRT access via IAM role |
| `disassociate-drt-role` | DRT Access | Revoke DRT IAM role access |
| `associate-drt-log-bucket` | DRT Access | Grant DRT access to S3 log bucket |
| `disassociate-drt-log-bucket` | DRT Access | Revoke DRT access to S3 log bucket |
| `describe-drt-access` | DRT Access | Describe current DRT access configuration |
| `enable-proactive-engagement` | Proactive Engagement | Enable proactive DDoS engagement |
| `disable-proactive-engagement` | Proactive Engagement | Disable proactive DDoS engagement |
| `associate-proactive-engagement-details` | Proactive Engagement | Set emergency contact details |
| `describe-emergency-contact-settings` | Proactive Engagement | Get emergency contact settings |
| `update-emergency-contact-settings` | Proactive Engagement | Update emergency contact settings |
| `associate-health-check` | Proactive Engagement | Associate Route 53 health check with protection |
| `disassociate-health-check` | Proactive Engagement | Disassociate Route 53 health check |
| `enable-application-layer-automatic-response` | Automatic Response | Enable auto application-layer DDoS response |
| `disable-application-layer-automatic-response` | Automatic Response | Disable auto application-layer DDoS response |
| `update-application-layer-automatic-response` | Automatic Response | Update auto response action |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

---

## Global Options

These options are available on ALL `aws shield` commands.

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

### Protectable Resource Types
| Resource Type | Description |
|---------------|-------------|
| `CLOUDFRONT_DISTRIBUTION` | Amazon CloudFront distribution |
| `ROUTE_53_HOSTED_ZONE` | Amazon Route 53 hosted zone |
| `ELASTIC_IP_ALLOCATION` | Elastic IP address |
| `CLASSIC_LOAD_BALANCER` | Classic Load Balancer |
| `APPLICATION_LOAD_BALANCER` | Application Load Balancer |
| `GLOBAL_ACCELERATOR` | AWS Global Accelerator |

### Protection Group Aggregation
| Aggregation | Description |
|-------------|-------------|
| `SUM` | Sum of all resource data |
| `MEAN` | Mean of all resource data |
| `MAX` | Maximum of all resource data |

### Protection Group Patterns
| Pattern | Description |
|---------|-------------|
| `ALL` | All protected resources |
| `ARBITRARY` | Specific set of resource ARNs |
| `BY_RESOURCE_TYPE` | All resources of a specific type |

### Subscription States
| State | Description |
|-------|-------------|
| `ACTIVE` | Shield Advanced is active |
| `INACTIVE` | Shield Advanced is not active |

### Attack Layers
| Layer | Description |
|-------|-------------|
| `NETWORK` | Network/transport layer (Layer 3/4) attacks |
| `APPLICATION` | Application layer (Layer 7) attacks |
