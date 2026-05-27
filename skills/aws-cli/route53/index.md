# AWS CLI v2 -- Route 53 Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/route53/ and https://docs.aws.amazon.com/cli/latest/reference/route53domains/

---


## All Route 53 Subcommands (Quick Reference)

### `aws route53` Commands

| Command | Category | Description |
|---------|----------|-------------|
| `activate-key-signing-key` | DNSSEC | Activate a key signing key |
| `associate-vpc-with-hosted-zone` | Hosted Zones | Associate VPC with private hosted zone |
| `change-cidr-collection` | CIDR | Modify a CIDR collection |
| `change-resource-record-sets` | Records | Create, update, or delete DNS records |
| `change-tags-for-resource` | Tags | Add, edit, or delete tags for a resource |
| `create-cidr-collection` | CIDR | Create a new CIDR collection |
| `create-health-check` | Health Checks | Create a new health check |
| `create-hosted-zone` | Hosted Zones | Create a new hosted zone |
| `create-key-signing-key` | DNSSEC | Create a key signing key |
| `create-query-logging-config` | Query Logging | Create DNS query logging configuration |
| `create-reusable-delegation-set` | Delegation Sets | Create a reusable delegation set |
| `create-traffic-policy` | Traffic Policies | Create a traffic policy |
| `create-traffic-policy-instance` | Traffic Policies | Create records using a traffic policy |
| `create-traffic-policy-version` | Traffic Policies | Create a new version of a traffic policy |
| `create-vpc-association-authorization` | Hosted Zones | Authorize VPC association by another account |
| `deactivate-key-signing-key` | DNSSEC | Deactivate a key signing key |
| `delete-cidr-collection` | CIDR | Delete a CIDR collection |
| `delete-health-check` | Health Checks | Delete a health check |
| `delete-hosted-zone` | Hosted Zones | Delete a hosted zone |
| `delete-key-signing-key` | DNSSEC | Delete a key signing key |
| `delete-query-logging-config` | Query Logging | Delete a query logging configuration |
| `delete-reusable-delegation-set` | Delegation Sets | Delete a reusable delegation set |
| `delete-traffic-policy` | Traffic Policies | Delete a traffic policy |
| `delete-traffic-policy-instance` | Traffic Policies | Delete a traffic policy instance |
| `delete-vpc-association-authorization` | Hosted Zones | Remove VPC association authorization |
| `disable-hosted-zone-dnssec` | DNSSEC | Disable DNSSEC signing |
| `disassociate-vpc-from-hosted-zone` | Hosted Zones | Disassociate VPC from private hosted zone |
| `enable-hosted-zone-dnssec` | DNSSEC | Enable DNSSEC signing |
| `get-account-limit` | Account | Get account-level limits |
| `get-change` | Records | Get status of a change batch |
| `get-checker-ip-ranges` | Health Checks | Get IP ranges used by health checkers |
| `get-dnssec` | DNSSEC | Get DNSSEC signing information |
| `get-geo-location` | Routing | Get geo location details |
| `get-health-check` | Health Checks | Get health check details |
| `get-health-check-count` | Health Checks | Get total number of health checks |
| `get-health-check-last-failure-reason` | Health Checks | Get last failure reason |
| `get-health-check-status` | Health Checks | Get current status of health checkers |
| `get-hosted-zone` | Hosted Zones | Get hosted zone details |
| `get-hosted-zone-count` | Hosted Zones | Get total number of hosted zones |
| `get-hosted-zone-limit` | Hosted Zones | Get hosted zone limits |
| `get-query-logging-config` | Query Logging | Get query logging configuration |
| `get-reusable-delegation-set` | Delegation Sets | Get reusable delegation set details |
| `get-reusable-delegation-set-limit` | Delegation Sets | Get delegation set limits |
| `get-traffic-policy` | Traffic Policies | Get traffic policy details |
| `get-traffic-policy-instance` | Traffic Policies | Get traffic policy instance details |
| `get-traffic-policy-instance-count` | Traffic Policies | Get total traffic policy instances |
| `list-cidr-blocks` | CIDR | List CIDR blocks in a collection |
| `list-cidr-collections` | CIDR | List CIDR collections |
| `list-cidr-locations` | CIDR | List CIDR locations |
| `list-geo-locations` | Routing | List supported geo locations |
| `list-health-checks` | Health Checks | List all health checks |
| `list-hosted-zones` | Hosted Zones | List all hosted zones |
| `list-hosted-zones-by-name` | Hosted Zones | List hosted zones ordered by name |
| `list-hosted-zones-by-vpc` | Hosted Zones | List private hosted zones associated with a VPC |
| `list-query-logging-configs` | Query Logging | List query logging configurations |
| `list-resource-record-sets` | Records | List DNS records in a hosted zone |
| `list-reusable-delegation-sets` | Delegation Sets | List reusable delegation sets |
| `list-tags-for-resource` | Tags | List tags for a single resource |
| `list-tags-for-resources` | Tags | List tags for multiple resources |
| `list-traffic-policies` | Traffic Policies | List all traffic policies |
| `list-traffic-policy-instances` | Traffic Policies | List all traffic policy instances |
| `list-traffic-policy-instances-by-hosted-zone` | Traffic Policies | List instances for a hosted zone |
| `list-traffic-policy-instances-by-policy` | Traffic Policies | List instances for a traffic policy |
| `list-traffic-policy-versions` | Traffic Policies | List versions of a traffic policy |
| `list-vpc-association-authorizations` | Hosted Zones | List VPC association authorizations |
| `test-dns-answer` | Records | Simulate DNS query response |
| `update-health-check` | Health Checks | Update a health check |
| `update-hosted-zone-comment` | Hosted Zones | Update hosted zone comment |
| `update-traffic-policy-comment` | Traffic Policies | Update traffic policy comment |
| `update-traffic-policy-instance` | Traffic Policies | Update a traffic policy instance |

### `aws route53domains` Commands

| Command | Category | Description |
|---------|----------|-------------|
| `accept-domain-transfer-from-another-aws-account` | Transfer | Accept inbound domain transfer |
| `associate-delegation-signer-to-domain` | DNSSEC | Add DNSSEC signing to domain |
| `cancel-domain-transfer-to-another-aws-account` | Transfer | Cancel outbound domain transfer |
| `check-domain-availability` | Registration | Check if a domain is available |
| `check-domain-transferability` | Transfer | Check if a domain can be transferred |
| `delete-domain` | Registration | Delete a registered domain |
| `delete-tags-for-domain` | Tags | Delete tags from a domain |
| `disable-domain-auto-renew` | Registration | Disable auto-renewal |
| `disable-domain-transfer-lock` | Transfer | Disable transfer lock |
| `disassociate-delegation-signer-from-domain` | DNSSEC | Remove DNSSEC signing from domain |
| `enable-domain-auto-renew` | Registration | Enable auto-renewal |
| `enable-domain-transfer-lock` | Transfer | Enable transfer lock |
| `get-contact-reachability-status` | Registration | Check contact email verification |
| `get-domain-detail` | Registration | Get domain registration details |
| `get-domain-suggestions` | Registration | Get domain name suggestions |
| `get-operation-detail` | Operations | Get status of an async operation |
| `list-domains` | Registration | List registered domains |
| `list-operations` | Operations | List recent domain operations |
| `list-prices` | Registration | List domain registration prices |
| `list-tags-for-domain` | Tags | List tags for a domain |
| `push-domain` | Transfer | Push domain to another registrar |
| `register-domain` | Registration | Register a new domain |
| `reject-domain-transfer-from-another-aws-account` | Transfer | Reject inbound domain transfer |
| `renew-domain` | Registration | Renew a domain registration |
| `resend-contact-reachability-email` | Registration | Resend verification email |
| `resend-operation-authorization` | Operations | Resend operation auth email |
| `retrieve-domain-auth-code` | Transfer | Get domain auth code for transfer |
| `transfer-domain` | Transfer | Transfer domain to Route 53 |
| `transfer-domain-to-another-aws-account` | Transfer | Transfer domain to another AWS account |
| `update-domain-contact` | Registration | Update domain contact info |
| `update-domain-contact-privacy` | Registration | Update WHOIS privacy settings |
| `update-domain-nameservers` | Registration | Update domain nameservers |
| `update-tags-for-domain` | Tags | Add/update tags for a domain |
| `view-billing` | Billing | View billing records |

---


## Global Options Reference

These options are available on ALL `aws route53` and `aws route53domains` commands.

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `--debug` | boolean | false | Enable debug logging to stderr |
| `--endpoint-url` | string | -- | Override the default service endpoint URL |
| `--no-verify-ssl` | boolean | false | Disable SSL certificate verification |
| `--no-paginate` | boolean | false | Disable automatic pagination |
| `--output` | string | `json` | Output format: `json`, `text`, `table`, `yaml`, `yaml-stream` |
| `--query` | string | -- | JMESPath query to filter output |
| `--profile` | string | `default` | Named AWS credential profile |
| `--region` | string | from config | AWS region (`route53domains` requires `us-east-1`) |
| `--version` | string | -- | Display the CLI version |
| `--color` | string | `auto` | Toggle color output: `on`, `off`, `auto` |
| `--no-sign-request` | boolean | false | Do not sign requests |
| `--ca-bundle` | string | -- | Path to custom CA certificate bundle |
| `--cli-read-timeout` | integer | 60 | Socket read timeout in seconds |
| `--cli-connect-timeout` | integer | 60 | Socket connect timeout in seconds |
| `--cli-binary-format` | string | `base64` | Binary input format: `base64`, `raw-in-base64-out` |
| `--no-cli-pager` | boolean | false | Disable the output pager |
| `--cli-auto-prompt` | boolean | false | Auto-prompt for missing parameters |
| `--no-cli-auto-prompt` | boolean | false | Disable auto-prompt |
| `--cli-input-json` | string | -- | Read arguments from JSON string or `file://` path |
| `--cli-input-yaml` | string | -- | Read arguments from YAML string or `file://` path |
| `--generate-cli-skeleton` | string | -- | Print skeleton: `input`, `yaml-input`, `output` |

---


## Common Patterns

### Record Types

| Type | Description | Example Value |
|------|-------------|---------------|
| `A` | IPv4 address | `192.0.2.1` |
| `AAAA` | IPv6 address | `2001:db8::1` |
| `CNAME` | Canonical name | `www.example.com` |
| `MX` | Mail exchange | `10 mail.example.com` |
| `TXT` | Text record | `"v=spf1 include:example.com ~all"` |
| `NS` | Nameserver | `ns-1234.awsdns-01.org` |
| `SOA` | Start of authority | `ns-1234.awsdns-01.org. awsdns-hostmaster.amazon.com. 1 7200 900 1209600 86400` |
| `SRV` | Service locator | `10 5 5269 xmpp-server.example.com` |
| `CAA` | Certification authority | `0 issue "letsencrypt.org"` |
| `DS` | Delegation signer | `12345 13 2 ABCDEF...` |
| `PTR` | Pointer | `host.example.com` |
| `NAPTR` | Name authority pointer | `100 10 "u" "E2U+sip" "!^.*$!sip:info@example.com!" .` |

### Alias Target Hosted Zone IDs

Common AWS service hosted zone IDs for alias records:

| Service | Region | Hosted Zone ID |
|---------|--------|---------------|
| ALB / NLB (us-east-1) | us-east-1 | `Z35SXDOTRQ7X7K` |
| ALB / NLB (us-west-2) | us-west-2 | `Z1H1FL5HABSF5` |
| ALB / NLB (eu-west-1) | eu-west-1 | `Z32O12XQLNTSW2` |
| CloudFront | Global | `Z2FDTNDATAQYW2` |
| S3 Website (us-east-1) | us-east-1 | `Z3AQBSTGFYJSTF` |
| API Gateway (us-east-1) | us-east-1 | `Z1UJRXOUMOOFQ8` |

> Full list: https://docs.aws.amazon.com/general/latest/gr/r53.html

### Routing Policy Patterns

**Weighted routing** (requires `SetIdentifier` and `Weight`):
```json
{
    "Name": "app.example.com",
    "Type": "A",
    "SetIdentifier": "us-east",
    "Weight": 70,
    "TTL": 60,
    "ResourceRecords": [{"Value": "1.2.3.4"}]
}
```

**Latency-based routing** (requires `SetIdentifier` and `Region`):
```json
{
    "Name": "app.example.com",
    "Type": "A",
    "SetIdentifier": "us-east-1",
    "Region": "us-east-1",
    "TTL": 60,
    "ResourceRecords": [{"Value": "1.2.3.4"}]
}
```

**Failover routing** (requires `SetIdentifier` and `Failover`):
```json
{
    "Name": "app.example.com",
    "Type": "A",
    "SetIdentifier": "primary",
    "Failover": "PRIMARY",
    "TTL": 60,
    "ResourceRecords": [{"Value": "1.2.3.4"}],
    "HealthCheckId": "abcd-1234"
}
```

**Geolocation routing** (requires `SetIdentifier` and `GeoLocation`):
```json
{
    "Name": "app.example.com",
    "Type": "A",
    "SetIdentifier": "europe",
    "GeoLocation": {
        "ContinentCode": "EU"
    },
    "TTL": 60,
    "ResourceRecords": [{"Value": "1.2.3.4"}]
}
```

**Multivalue answer routing** (requires `SetIdentifier` and `MultiValueAnswer`):
```json
{
    "Name": "app.example.com",
    "Type": "A",
    "SetIdentifier": "server-1",
    "MultiValueAnswer": true,
    "TTL": 60,
    "ResourceRecords": [{"Value": "1.2.3.4"}],
    "HealthCheckId": "abcd-1234"
}
```

### Change Status Values

| Status | Description |
|--------|-------------|
| `PENDING` | Change submitted but not yet applied to all Route 53 DNS servers |
| `INSYNC` | Change has propagated to all Route 53 DNS servers |

### Health Check Types

| Type | Description |
|------|-------------|
| `HTTP` | Connect to TCP port 80, send HTTP GET |
| `HTTPS` | Connect to TCP port 443, send HTTPS GET |
| `HTTP_STR_MATCH` | HTTP GET and search response body for string |
| `HTTPS_STR_MATCH` | HTTPS GET and search response body for string |
| `TCP` | Attempt TCP connection |
| `CALCULATED` | Aggregate status of child health checks |
| `CLOUDWATCH_METRIC` | Based on CloudWatch alarm state |
| `RECOVERY_CONTROL` | Based on Route 53 Application Recovery Controller |

### Domain Operation Status Values

| Status | Description |
|--------|-------------|
| `SUBMITTED` | Operation submitted |
| `IN_PROGRESS` | Operation is being processed |
| `ERROR` | Operation encountered an error |
| `SUCCESSFUL` | Operation completed successfully |
| `FAILED` | Operation failed |
