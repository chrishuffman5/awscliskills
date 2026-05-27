# AWS CLI v2 — CloudFront (Content Delivery Network) Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/cloudfront/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-cache-policy` | Cache Policy | Create a cache policy |
| `create-cloud-front-origin-access-identity` | OAI (legacy) | Create an origin access identity |
| `create-continuous-deployment-policy` | Continuous Deployment | Create a continuous deployment policy |
| `create-distribution` | Distribution | Create a new distribution |
| `create-distribution-with-tags` | Distribution | Create a distribution with tags |
| `create-field-level-encryption-config` | Field-Level Encryption | Create field-level encryption config |
| `create-field-level-encryption-profile` | Field-Level Encryption | Create field-level encryption profile |
| `create-function` | Function | Create a CloudFront function |
| `create-invalidation` | Invalidation | Create a cache invalidation |
| `create-key-group` | Key Group | Create a key group for signed URLs |
| `create-key-value-store` | Key Value Store | Create a key value store |
| `create-monitoring-subscription` | Monitoring | Create a monitoring subscription |
| `create-origin-access-control` | OAC | Create origin access control |
| `create-origin-request-policy` | Origin Request Policy | Create origin request policy |
| `create-public-key` | Public Key | Upload a public key |
| `create-realtime-log-config` | Real-Time Logs | Create real-time log configuration |
| `create-response-headers-policy` | Response Headers Policy | Create response headers policy |
| `create-streaming-distribution` | Streaming (legacy) | Create a streaming distribution |
| `create-streaming-distribution-with-tags` | Streaming (legacy) | Create streaming distribution with tags |
| `delete-cache-policy` | Cache Policy | Delete a cache policy |
| `delete-cloud-front-origin-access-identity` | OAI (legacy) | Delete an origin access identity |
| `delete-continuous-deployment-policy` | Continuous Deployment | Delete a continuous deployment policy |
| `delete-distribution` | Distribution | Delete a distribution |
| `delete-field-level-encryption-config` | Field-Level Encryption | Delete field-level encryption config |
| `delete-field-level-encryption-profile` | Field-Level Encryption | Delete field-level encryption profile |
| `delete-function` | Function | Delete a CloudFront function |
| `delete-key-group` | Key Group | Delete a key group |
| `delete-key-value-store` | Key Value Store | Delete a key value store |
| `delete-monitoring-subscription` | Monitoring | Delete a monitoring subscription |
| `delete-origin-access-control` | OAC | Delete origin access control |
| `delete-origin-request-policy` | Origin Request Policy | Delete origin request policy |
| `delete-public-key` | Public Key | Delete a public key |
| `delete-realtime-log-config` | Real-Time Logs | Delete real-time log configuration |
| `delete-response-headers-policy` | Response Headers Policy | Delete response headers policy |
| `delete-streaming-distribution` | Streaming (legacy) | Delete a streaming distribution |
| `describe-function` | Function | Get summary information about a function |
| `describe-key-value-store` | Key Value Store | Get details of a key value store |
| `get-cache-policy` | Cache Policy | Get a cache policy |
| `get-cache-policy-config` | Cache Policy | Get cache policy configuration |
| `get-cloud-front-origin-access-identity` | OAI (legacy) | Get an origin access identity |
| `get-cloud-front-origin-access-identity-config` | OAI (legacy) | Get OAI configuration |
| `get-continuous-deployment-policy` | Continuous Deployment | Get a continuous deployment policy |
| `get-continuous-deployment-policy-config` | Continuous Deployment | Get continuous deployment policy config |
| `get-distribution` | Distribution | Get distribution details |
| `get-distribution-config` | Distribution | Get distribution configuration |
| `get-field-level-encryption` | Field-Level Encryption | Get field-level encryption config |
| `get-field-level-encryption-config` | Field-Level Encryption | Get field-level encryption configuration |
| `get-field-level-encryption-profile` | Field-Level Encryption | Get field-level encryption profile |
| `get-field-level-encryption-profile-config` | Field-Level Encryption | Get profile configuration |
| `get-function` | Function | Get function code and configuration |
| `get-invalidation` | Invalidation | Get invalidation details |
| `get-key-group` | Key Group | Get a key group |
| `get-key-group-config` | Key Group | Get key group configuration |
| `get-monitoring-subscription` | Monitoring | Get monitoring subscription |
| `get-origin-access-control` | OAC | Get origin access control |
| `get-origin-access-control-config` | OAC | Get OAC configuration |
| `get-origin-request-policy` | Origin Request Policy | Get origin request policy |
| `get-origin-request-policy-config` | Origin Request Policy | Get origin request policy config |
| `get-public-key` | Public Key | Get a public key |
| `get-public-key-config` | Public Key | Get public key configuration |
| `get-realtime-log-config` | Real-Time Logs | Get real-time log configuration |
| `get-response-headers-policy` | Response Headers Policy | Get response headers policy |
| `get-response-headers-policy-config` | Response Headers Policy | Get response headers policy config |
| `get-streaming-distribution` | Streaming (legacy) | Get streaming distribution |
| `get-streaming-distribution-config` | Streaming (legacy) | Get streaming distribution config |
| `list-cache-policies` | Cache Policy | List cache policies |
| `list-cloud-front-origin-access-identities` | OAI (legacy) | List origin access identities |
| `list-conflicting-aliases` | Distribution | List conflicting CNAME aliases |
| `list-continuous-deployment-policies` | Continuous Deployment | List continuous deployment policies |
| `list-distributions` | Distribution | List distributions |
| `list-distributions-by-cache-policy-id` | Distribution | List distributions using a cache policy |
| `list-distributions-by-key-group` | Distribution | List distributions using a key group |
| `list-distributions-by-origin-request-policy-id` | Distribution | List distributions using an origin request policy |
| `list-distributions-by-realtime-log-config` | Distribution | List distributions using a real-time log config |
| `list-distributions-by-response-headers-policy-id` | Distribution | List distributions using a response headers policy |
| `list-distributions-by-web-acl-id` | Distribution | List distributions associated with a WAF ACL |
| `list-field-level-encryption-configs` | Field-Level Encryption | List field-level encryption configs |
| `list-field-level-encryption-profiles` | Field-Level Encryption | List field-level encryption profiles |
| `list-functions` | Function | List CloudFront functions |
| `list-invalidations` | Invalidation | List invalidations |
| `list-key-groups` | Key Group | List key groups |
| `list-key-value-stores` | Key Value Store | List key value stores |
| `list-origin-access-controls` | OAC | List origin access controls |
| `list-origin-request-policies` | Origin Request Policy | List origin request policies |
| `list-public-keys` | Public Key | List public keys |
| `list-realtime-log-configs` | Real-Time Logs | List real-time log configurations |
| `list-response-headers-policies` | Response Headers Policy | List response headers policies |
| `list-streaming-distributions` | Streaming (legacy) | List streaming distributions |
| `list-tags-for-resource` | Tags | List tags for a resource |
| `publish-function` | Function | Publish a function from DEVELOPMENT to LIVE |
| `sign` | Utility | Generate signed URLs or cookies |
| `tag-resource` | Tags | Add tags to a resource |
| `test-function` | Function | Test a CloudFront function |
| `untag-resource` | Tags | Remove tags from a resource |
| `update-cache-policy` | Cache Policy | Update a cache policy |
| `update-cloud-front-origin-access-identity` | OAI (legacy) | Update an origin access identity |
| `update-continuous-deployment-policy` | Continuous Deployment | Update a continuous deployment policy |
| `update-distribution` | Distribution | Update a distribution |
| `update-distribution-with-staging-config` | Continuous Deployment | Promote staging to production |
| `update-field-level-encryption-config` | Field-Level Encryption | Update field-level encryption config |
| `update-field-level-encryption-profile` | Field-Level Encryption | Update field-level encryption profile |
| `update-function` | Function | Update a CloudFront function |
| `update-key-group` | Key Group | Update a key group |
| `update-key-value-store` | Key Value Store | Update a key value store |
| `update-origin-access-control` | OAC | Update origin access control |
| `update-origin-request-policy` | Origin Request Policy | Update origin request policy |
| `update-public-key` | Public Key | Update a public key |
| `update-realtime-log-config` | Real-Time Logs | Update real-time log configuration |
| `update-response-headers-policy` | Response Headers Policy | Update response headers policy |
| `update-streaming-distribution` | Streaming (legacy) | Update a streaming distribution |

---

## Global Options Reference

These options are available for all `aws cloudfront` commands:

| Option | Type | Description |
|--------|------|-------------|
| `--debug` | boolean | Enable debug logging |
| `--endpoint-url` | string | Override default endpoint URL |
| `--no-verify-ssl` | boolean | Disable SSL certificate verification |
| `--no-paginate` | boolean | Disable automatic pagination |
| `--output` | string | Output format: `json`, `text`, `table`, `yaml`, `yaml-stream` |
| `--query` | string | JMESPath query to filter output |
| `--profile` | string | Named credential profile |
| `--region` | string | AWS region |
| `--version` | boolean | Display CLI version |
| `--color` | string | `on`, `off`, `auto` |
| `--no-sign-request` | boolean | Skip request signing |
| `--ca-bundle` | string | CA certificate bundle path |
| `--cli-read-timeout` | integer | Read timeout in seconds |
| `--cli-connect-timeout` | integer | Connection timeout in seconds |
| `--cli-binary-format` | string | `base64` or `raw-in-base64-out` |
| `--no-cli-pager` | boolean | Disable output pager |
| `--cli-auto-prompt` | boolean | Enable auto-prompt mode |
| `--cli-input-json` | string | Read arguments from JSON string or file (`file://`) |
| `--cli-input-yaml` | string | Read arguments from YAML string or file (`file://`) |
| `--generate-cli-skeleton` | string | Print JSON/YAML skeleton: `input` or `output` |
