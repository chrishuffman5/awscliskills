# AWS CLI v2 -- ELBv2 (Elastic Load Balancing v2) Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/elbv2/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `add-listener-certificates` | Certificates | Add certificates to a listener |
| `add-tags` | Tags | Add tags to resources |
| `add-trust-store-revocations` | Trust Stores | Add revocations to a trust store |
| `create-listener` | Listeners | Create a listener for a load balancer |
| `create-load-balancer` | Load Balancers | Create an ALB, NLB, or GWLB |
| `create-rule` | Rules | Create a routing rule for a listener |
| `create-target-group` | Target Groups | Create a target group |
| `create-trust-store` | Trust Stores | Create a trust store for mutual TLS |
| `delete-listener` | Listeners | Delete a listener |
| `delete-load-balancer` | Load Balancers | Delete a load balancer |
| `delete-rule` | Rules | Delete a rule |
| `delete-shared-trust-store-association` | Trust Stores | Delete a shared trust store association |
| `delete-target-group` | Target Groups | Delete a target group |
| `delete-trust-store` | Trust Stores | Delete a trust store |
| `deregister-targets` | Target Groups | Deregister targets from a target group |
| `describe-account-limits` | Account | Describe ELBv2 account limits |
| `describe-capacity-reservation` | Load Balancers | Describe capacity reservation status |
| `describe-listener-attributes` | Listeners | Describe listener attributes |
| `describe-listener-certificates` | Certificates | List certificates for a listener |
| `describe-listeners` | Listeners | Describe listeners for a load balancer |
| `describe-load-balancer-attributes` | Load Balancers | Describe load balancer attributes |
| `describe-load-balancers` | Load Balancers | Describe load balancers |
| `describe-rules` | Rules | Describe rules for a listener |
| `describe-ssl-policies` | SSL Policies | Describe available SSL/TLS policies |
| `describe-tags` | Tags | Describe tags for resources |
| `describe-target-group-attributes` | Target Groups | Describe target group attributes |
| `describe-target-groups` | Target Groups | Describe target groups |
| `describe-target-health` | Target Groups | Describe health of registered targets |
| `describe-trust-store-associations` | Trust Stores | Describe trust store associations |
| `describe-trust-store-revocations` | Trust Stores | Describe trust store revocations |
| `describe-trust-stores` | Trust Stores | Describe trust stores |
| `get-resource-policy` | Load Balancers | Get resource policy for a resource |
| `get-trust-store-ca-certificates-bundle` | Trust Stores | Get CA certificates bundle from trust store |
| `get-trust-store-revocation-content` | Trust Stores | Get revocation content from trust store |
| `modify-capacity-reservation` | Load Balancers | Modify capacity reservation |
| `modify-ip-pools` | Load Balancers | Modify IP pools |
| `modify-listener` | Listeners | Modify a listener |
| `modify-listener-attributes` | Listeners | Modify listener attributes |
| `modify-load-balancer-attributes` | Load Balancers | Modify load balancer attributes |
| `modify-rule` | Rules | Modify a rule |
| `modify-target-group` | Target Groups | Modify target group health checks |
| `modify-target-group-attributes` | Target Groups | Modify target group attributes |
| `modify-trust-store` | Trust Stores | Modify a trust store |
| `register-targets` | Target Groups | Register targets with a target group |
| `remove-listener-certificates` | Certificates | Remove certificates from a listener |
| `remove-tags` | Tags | Remove tags from resources |
| `remove-trust-store-revocations` | Trust Stores | Remove revocations from a trust store |
| `set-ip-address-type` | Load Balancers | Set IP address type for a load balancer |
| `set-rule-priorities` | Rules | Set priorities for rules |
| `set-security-groups` | Load Balancers | Set security groups for a load balancer |
| `set-subnets` | Load Balancers | Set subnets for a load balancer |
| `wait` | Wait | Wait for load balancer operations |

---

## Global Options

These options apply to all `aws elbv2` subcommands:

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `--debug` | boolean | false | Enable debug logging |
| `--endpoint-url` | string | -- | Override default AWS endpoint URL |
| `--no-verify-ssl` | boolean | false | Disable SSL certificate verification |
| `--no-paginate` | boolean | false | Disable automatic pagination |
| `--output` | string | `json` | Output format: `json`, `text`, `table`, `yaml`, `yaml-stream` |
| `--query` | string | -- | JMESPath query to filter output |
| `--profile` | string | -- | Named profile from config file |
| `--region` | string | -- | AWS region |
| `--version` | -- | -- | Display CLI version |
| `--color` | string | `auto` | Color output: `on`, `off`, `auto` |
| `--no-sign-request` | boolean | false | Do not sign requests |
| `--ca-bundle` | string | -- | CA certificate bundle for SSL |
| `--cli-read-timeout` | integer | 60 | Socket read timeout (seconds) |
| `--cli-connect-timeout` | integer | 60 | Socket connect timeout (seconds) |
| `--cli-binary-format` | string | `base64` | Binary format: `base64`, `raw-in-base64-out` |
| `--no-cli-pager` | boolean | false | Disable output pager |
| `--cli-auto-prompt` | boolean | false | Enable auto-prompt |
| `--no-cli-auto-prompt` | boolean | false | Disable auto-prompt |
| `--cli-input-json` | string | -- | Read arguments from JSON string |
| `--cli-input-yaml` | string | -- | Read arguments from YAML string |
| `--generate-cli-skeleton` | string | -- | Generate skeleton: `input`, `yaml-input`, `output` |
