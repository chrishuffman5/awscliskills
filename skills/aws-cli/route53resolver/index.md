# AWS CLI v2 -- Route 53 Resolver Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/route53resolver/ and https://docs.aws.amazon.com/cli/latest/reference/route53profiles/

---

## Quick Reference -- route53resolver

| Command | Category | Description |
|---------|----------|-------------|
| `create-resolver-endpoint` | Endpoint | Create an inbound or outbound resolver endpoint |
| `delete-resolver-endpoint` | Endpoint | Delete a resolver endpoint |
| `get-resolver-endpoint` | Endpoint | Get details of a resolver endpoint |
| `list-resolver-endpoints` | Endpoint | List all resolver endpoints |
| `update-resolver-endpoint` | Endpoint | Update endpoint name, protocols, or type |
| `associate-resolver-endpoint-ip-address` | Endpoint | Add an IP address to an endpoint |
| `disassociate-resolver-endpoint-ip-address` | Endpoint | Remove an IP address from an endpoint |
| `list-resolver-endpoint-ip-addresses` | Endpoint | List IP addresses for an endpoint |
| `create-resolver-rule` | Rule | Create a forwarding or system rule |
| `delete-resolver-rule` | Rule | Delete a resolver rule |
| `get-resolver-rule` | Rule | Get details of a resolver rule |
| `list-resolver-rules` | Rule | List all resolver rules |
| `update-resolver-rule` | Rule | Update rule name, endpoints, or targets |
| `associate-resolver-rule` | Rule | Associate a rule with a VPC |
| `disassociate-resolver-rule` | Rule | Remove a rule-VPC association |
| `get-resolver-rule-association` | Rule | Get rule-VPC association details |
| `list-resolver-rule-associations` | Rule | List all rule-VPC associations |
| `get-resolver-rule-policy` | Rule | Get RAM sharing policy for a rule |
| `put-resolver-rule-policy` | Rule | Set RAM sharing policy for a rule |
| `create-firewall-rule-group` | Firewall | Create a DNS Firewall rule group |
| `delete-firewall-rule-group` | Firewall | Delete a firewall rule group |
| `get-firewall-rule-group` | Firewall | Get firewall rule group details |
| `list-firewall-rule-groups` | Firewall | List all firewall rule groups |
| `associate-firewall-rule-group` | Firewall | Associate a rule group with a VPC |
| `disassociate-firewall-rule-group` | Firewall | Remove a rule group-VPC association |
| `get-firewall-rule-group-association` | Firewall | Get rule group-VPC association details |
| `list-firewall-rule-group-associations` | Firewall | List rule group-VPC associations |
| `get-firewall-rule-group-policy` | Firewall | Get RAM sharing policy for a rule group |
| `put-firewall-rule-group-policy` | Firewall | Set RAM sharing policy for a rule group |
| `create-firewall-domain-list` | Firewall | Create a domain list for firewall rules |
| `delete-firewall-domain-list` | Firewall | Delete a firewall domain list |
| `get-firewall-domain-list` | Firewall | Get domain list details |
| `list-firewall-domain-lists` | Firewall | List all firewall domain lists |
| `list-firewall-domains` | Firewall | List domains in a domain list |
| `import-firewall-domains` | Firewall | Import domains from S3 |
| `update-firewall-domains` | Firewall | Add or remove domains in a list |
| `create-firewall-rule` | Firewall | Create a rule in a rule group |
| `delete-firewall-rule` | Firewall | Delete a firewall rule |
| `list-firewall-rules` | Firewall | List rules in a rule group |
| `update-firewall-rule` | Firewall | Update a firewall rule |
| `update-firewall-rule-group-association` | Firewall | Update rule group association priority or mutation protection |
| `get-firewall-config` | Firewall | Get firewall config for a VPC |
| `list-firewall-configs` | Firewall | List firewall configs |
| `update-firewall-config` | Firewall | Update firewall fail-open behavior |
| `create-resolver-query-log-config` | Logging | Create a query logging configuration |
| `delete-resolver-query-log-config` | Logging | Delete a query logging config |
| `get-resolver-query-log-config` | Logging | Get query logging config details |
| `list-resolver-query-log-configs` | Logging | List all query logging configs |
| `associate-resolver-query-log-config` | Logging | Associate query logging with a VPC |
| `disassociate-resolver-query-log-config` | Logging | Remove query logging association |
| `get-resolver-query-log-config-association` | Logging | Get logging association details |
| `list-resolver-query-log-config-associations` | Logging | List logging associations |
| `get-resolver-query-log-config-policy` | Logging | Get RAM sharing policy for logging config |
| `put-resolver-query-log-config-policy` | Logging | Set RAM sharing policy for logging config |
| `get-resolver-dnssec-config` | DNSSEC | Get DNSSEC validation config for a VPC |
| `list-resolver-dnssec-configs` | DNSSEC | List all DNSSEC configs |
| `update-resolver-dnssec-config` | DNSSEC | Enable/disable DNSSEC validation |
| `get-resolver-config` | Config | Get resolver config for a VPC |
| `list-resolver-configs` | Config | List resolver configs |
| `update-resolver-config` | Config | Update autodefined reverse DNS config |
| `create-outpost-resolver` | Outpost | Create a Resolver on Outpost |
| `delete-outpost-resolver` | Outpost | Delete an Outpost Resolver |
| `get-outpost-resolver` | Outpost | Get Outpost Resolver details |
| `list-outpost-resolvers` | Outpost | List all Outpost Resolvers |
| `update-outpost-resolver` | Outpost | Update an Outpost Resolver |
| `tag-resource` | Tags | Add tags to a resolver resource |
| `untag-resource` | Tags | Remove tags from a resolver resource |
| `list-tags-for-resource` | Tags | List tags for a resolver resource |

## Quick Reference -- route53profiles

| Command | Category | Description |
|---------|----------|-------------|
| `create-profile` | Profile | Create a Route 53 Profile |
| `delete-profile` | Profile | Delete a profile |
| `get-profile` | Profile | Get profile details |
| `list-profiles` | Profile | List all profiles |
| `associate-profile` | Profile | Associate a profile with a VPC |
| `disassociate-profile` | Profile | Remove a profile-VPC association |
| `get-profile-association` | Profile | Get profile-VPC association details |
| `list-profile-associations` | Profile | List profile-VPC associations |
| `associate-resource-to-profile` | Profile | Associate a DNS resource with a profile |
| `disassociate-resource-from-profile` | Profile | Remove a resource-profile association |
| `get-profile-resource-association` | Profile | Get resource-profile association details |
| `list-profile-resource-associations` | Profile | List resource-profile associations |
| `update-profile-resource-association` | Profile | Update a resource-profile association |
| `tag-resource` | Tags | Add tags to a profile resource |
| `untag-resource` | Tags | Remove tags from a profile resource |
| `list-tags-for-resource` | Tags | List tags for a profile resource |

---

## Global Options

These options are available on ALL `aws route53resolver` and `aws route53profiles` commands.

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
| `--ca-bundle` | string | -- | Path to custom CA certificate bundle for SSL |
| `--cli-read-timeout` | integer | 60 | Socket read timeout in seconds |
| `--cli-connect-timeout` | integer | 60 | Socket connect timeout in seconds |
| `--cli-binary-format` | string | `base64` | Format for binary blob input: `base64`, `raw-in-base64-out` |
| `--no-cli-pager` | boolean | false | Disable the output pager |
| `--cli-auto-prompt` | boolean | false | Auto-prompt for missing parameters |
| `--no-cli-auto-prompt` | boolean | false | Disable auto-prompt |

---

## Common Patterns

### Resolver Endpoint Status

| Status | Description |
|--------|-------------|
| `CREATING` | Network interfaces being configured |
| `OPERATIONAL` | Endpoint is functioning correctly |
| `UPDATING` | Associating/disassociating network interfaces |
| `AUTO_RECOVERING` | Attempting recovery of failed interfaces |
| `ACTION_NEEDED` | Endpoint unhealthy; manual intervention required |
| `DELETING` | Endpoint being deleted |

### Resolver Rule Types

| Type | Description |
|------|-------------|
| `FORWARD` | Forward DNS queries to specified target IPs |
| `SYSTEM` | Use default Route 53 Resolver behavior (auto-created) |
| `RECURSIVE` | Use recursive resolution |
| `DELEGATE` | Delegate DNS queries to resolvers specified in delegation record |

### DNS Firewall Actions

| Action | Description |
|--------|-------------|
| `ALLOW` | Allow the DNS query |
| `BLOCK` | Block the DNS query (with NODATA, NXDOMAIN, or OVERRIDE response) |
| `ALERT` | Allow but log the DNS query |

### Profile Status

| Status | Description |
|--------|-------------|
| `CREATING` | Profile is being created |
| `COMPLETE` | Profile is ready for use |
| `UPDATING` | Profile is being updated |
| `DELETING` | Profile is being deleted |
| `DELETED` | Profile has been deleted |
| `FAILED` | Profile operation failed |

### Supported Protocols

| Protocol | Description |
|----------|-------------|
| `Do53` | Traditional DNS over port 53 (default) |
| `DoH` | DNS over HTTPS |
| `DoH-FIPS` | DNS over HTTPS with FIPS compliance |
