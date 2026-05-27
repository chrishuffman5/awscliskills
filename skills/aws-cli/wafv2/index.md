# AWS CLI v2 -- WAF v2 Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/wafv2/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-web-acl` | Web ACL | Create a web ACL |
| `delete-web-acl` | Web ACL | Delete a web ACL |
| `get-web-acl` | Web ACL | Get a web ACL by name, scope, and ID |
| `get-web-acl-for-resource` | Web ACL | Get the web ACL associated with a resource |
| `list-web-acls` | Web ACL | List all web ACLs |
| `update-web-acl` | Web ACL | Update a web ACL |
| `associate-web-acl` | Web ACL | Associate a web ACL with a resource |
| `disassociate-web-acl` | Web ACL | Remove web ACL association from a resource |
| `list-resources-for-web-acl` | Web ACL | List resources associated with a web ACL |
| `check-capacity` | Web ACL | Check rule capacity requirements |
| `create-api-key` | Web ACL | Create an API key for CAPTCHA |
| `get-decrypted-api-key` | Web ACL | Get decrypted API key info |
| `generate-mobile-sdk-release-url` | Web ACL | Generate a mobile SDK download URL |
| `create-rule-group` | Rule Group | Create a rule group |
| `delete-rule-group` | Rule Group | Delete a rule group |
| `get-rule-group` | Rule Group | Get a rule group |
| `list-rule-groups` | Rule Group | List rule groups |
| `update-rule-group` | Rule Group | Update a rule group |
| `list-available-managed-rule-groups` | Rule Group | List AWS managed rule groups |
| `list-available-managed-rule-group-versions` | Rule Group | List versions of a managed rule group |
| `describe-managed-rule-group` | Rule Group | Describe rules in a managed rule group |
| `get-managed-rule-set` | Rule Group | Get a managed rule set (for providers) |
| `list-managed-rule-sets` | Rule Group | List managed rule sets (for providers) |
| `put-managed-rule-set-versions` | Rule Group | Publish managed rule set versions |
| `update-managed-rule-set-version-expiry-date` | Rule Group | Update version expiry for a managed rule set |
| `create-ip-set` | IP Set | Create an IP set |
| `delete-ip-set` | IP Set | Delete an IP set |
| `get-ip-set` | IP Set | Get an IP set |
| `list-ip-sets` | IP Set | List IP sets |
| `update-ip-set` | IP Set | Update an IP set |
| `create-regex-pattern-set` | Regex Pattern Set | Create a regex pattern set |
| `delete-regex-pattern-set` | Regex Pattern Set | Delete a regex pattern set |
| `get-regex-pattern-set` | Regex Pattern Set | Get a regex pattern set |
| `list-regex-pattern-sets` | Regex Pattern Set | List regex pattern sets |
| `update-regex-pattern-set` | Regex Pattern Set | Update a regex pattern set |
| `put-logging-configuration` | Logging | Set logging for a web ACL |
| `get-logging-configuration` | Logging | Get logging configuration for a web ACL |
| `delete-logging-configuration` | Logging | Delete logging for a web ACL |
| `list-logging-configurations` | Logging | List all logging configurations |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |
| `get-sampled-requests` | Analytics | Get a sample of web requests |
| `get-rate-based-statement-managed-keys` | Analytics | Get rate-limited IP addresses |
| `put-permission-policy` | Permissions | Set permission policy on a rule group |
| `get-permission-policy` | Permissions | Get permission policy for a rule group |
| `delete-permission-policy` | Permissions | Delete permission policy from a rule group |

---

## Global Options

These options are available on ALL `aws wafv2` commands.

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

### Scope
All WAF v2 resources are scoped to either `REGIONAL` (for ALB, API Gateway, etc.) or `CLOUDFRONT` (for CloudFront distributions).

| Scope | Region | Description |
|-------|--------|-------------|
| `REGIONAL` | Any region | Protects ALB, API Gateway, AppSync, Cognito, App Runner, Verified Access |
| `CLOUDFRONT` | `us-east-1` only | Protects CloudFront distributions |

### Lock Token
Most update and delete operations require a `--lock-token`. This is returned by the corresponding `get-*` or `create-*` operation and provides optimistic locking to prevent concurrent modifications.

### Rule Actions
| Action | Description |
|--------|-------------|
| `Allow` | Allow the request |
| `Block` | Block the request (returns 403) |
| `Count` | Count the request but do not block |
| `Captcha` | Present a CAPTCHA challenge |
| `Challenge` | Present a silent challenge |

### Common AWS Managed Rule Groups
| Name | Vendor | Description |
|------|--------|-------------|
| `AWSManagedRulesCommonRuleSet` | AWS | Core rule set (CRS) |
| `AWSManagedRulesKnownBadInputsRuleSet` | AWS | Known bad inputs |
| `AWSManagedRulesSQLiRuleSet` | AWS | SQL injection rules |
| `AWSManagedRulesLinuxRuleSet` | AWS | Linux-specific rules |
| `AWSManagedRulesAmazonIpReputationList` | AWS | Amazon IP reputation list |
| `AWSManagedRulesBotControlRuleSet` | AWS | Bot control rules |
| `AWSManagedRulesATPRuleSet` | AWS | Account takeover prevention |

### Supported Resource Types for Association
- Application Load Balancer (ALB)
- Amazon API Gateway REST API
- AWS AppSync GraphQL API
- Amazon Cognito user pool
- AWS App Runner service
- AWS Verified Access instance
- CloudFront distribution (CLOUDFRONT scope only)
