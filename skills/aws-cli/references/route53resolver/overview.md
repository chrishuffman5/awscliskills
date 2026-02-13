# AWS CLI v2 -- Route 53 Resolver Reference Overview

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/route53resolver/ and https://docs.aws.amazon.com/cli/latest/reference/route53profiles/

## Service Overview

Amazon Route 53 Resolver provides DNS resolution for VPCs and on-premises networks. It includes inbound and outbound resolver endpoints for hybrid DNS, forwarding rules, DNS Firewall for filtering malicious domains, query logging, DNSSEC validation, and Resolver on Outposts. Route 53 Profiles allow sharing DNS configurations across VPCs and accounts.

This reference covers both `route53resolver` and `route53profiles` CLI commands.

## Common Workflows

### Set Up Hybrid DNS Resolution

```bash
# 1. Create inbound endpoint (on-premises to AWS)
aws route53resolver create-resolver-endpoint \
    --name my-inbound \
    --creator-request-id $(date +%s) \
    --security-group-ids sg-12345678 \
    --direction INBOUND \
    --ip-addresses SubnetId=subnet-aaa,Ip=10.0.1.10 SubnetId=subnet-bbb,Ip=10.0.2.10

# 2. Create outbound endpoint (AWS to on-premises)
aws route53resolver create-resolver-endpoint \
    --name my-outbound \
    --creator-request-id $(date +%s) \
    --security-group-ids sg-12345678 \
    --direction OUTBOUND \
    --ip-addresses SubnetId=subnet-aaa SubnetId=subnet-bbb

# 3. Create forwarding rule for on-premises domain
aws route53resolver create-resolver-rule \
    --name forward-corp \
    --creator-request-id $(date +%s) \
    --rule-type FORWARD \
    --domain-name corp.example.com \
    --resolver-endpoint-id rslvr-out-abcdef \
    --target-ips "Ip=10.100.1.1" "Ip=10.100.1.2"

# 4. Associate rule with VPC
aws route53resolver associate-resolver-rule \
    --name my-association \
    --resolver-rule-id rslvr-rr-abcdef \
    --vpc-id vpc-12345678
```

### Configure DNS Firewall

```bash
# 1. Create domain list
aws route53resolver create-firewall-domain-list \
    --name blocked-domains \
    --creator-request-id $(date +%s)

# 2. Add domains to list
aws route53resolver update-firewall-domains \
    --firewall-domain-list-id rslvr-fdl-abcdef \
    --operation ADD \
    --domains "malware.example.com" "phishing.example.net"

# 3. Create rule group
aws route53resolver create-firewall-rule-group \
    --name my-firewall-rules \
    --creator-request-id $(date +%s)

# 4. Create blocking rule
aws route53resolver create-firewall-rule \
    --name block-malware \
    --firewall-rule-group-id rslvr-frg-abcdef \
    --firewall-domain-list-id rslvr-fdl-abcdef \
    --priority 100 \
    --action BLOCK \
    --block-response NXDOMAIN

# 5. Associate rule group with VPC
aws route53resolver associate-firewall-rule-group \
    --name my-fw-assoc \
    --creator-request-id $(date +%s) \
    --firewall-rule-group-id rslvr-frg-abcdef \
    --vpc-id vpc-12345678 \
    --priority 101
```

### Enable Query Logging

```bash
# 1. Create query log config
aws route53resolver create-resolver-query-log-config \
    --name my-query-logs \
    --destination-arn arn:aws:s3:::my-dns-logs-bucket

# 2. Associate with VPC
aws route53resolver associate-resolver-query-log-config \
    --resolver-query-log-config-id rqlc-abcdef \
    --resource-id vpc-12345678

# 3. Verify association
aws route53resolver get-resolver-query-log-config-association \
    --resolver-query-log-config-association-id rqlca-abcdef
```

### Use Route 53 Profiles

```bash
# 1. Create a profile
aws route53profiles create-profile --name my-dns-profile

# 2. Associate resources (e.g., firewall rule group)
aws route53profiles associate-resource-to-profile \
    --name fw-association \
    --profile-id rp-abcdef123456 \
    --resource-arn arn:aws:route53resolver:us-east-1:123456789012:firewall-rule-group/rslvr-frg-abcdef \
    --resource-properties '{"priority": 102}'

# 3. Associate profile with VPC
aws route53profiles associate-profile \
    --name vpc-association \
    --profile-id rp-abcdef123456 \
    --resource-id vpc-12345678
```

## Command Reference

| Group | File | Commands |
|-------|------|----------|
| Resolver Endpoints | [`resolver-endpoints.md`](resolver-endpoints.md) | `create-resolver-endpoint`, `delete-resolver-endpoint`, `get-resolver-endpoint`, `list-resolver-endpoints`, `update-resolver-endpoint`, `associate-resolver-endpoint-ip-address`, `disassociate-resolver-endpoint-ip-address`, `list-resolver-endpoint-ip-addresses` |
| Resolver Rules | [`resolver-rules.md`](resolver-rules.md) | `create-resolver-rule`, `delete-resolver-rule`, `get-resolver-rule`, `list-resolver-rules`, `update-resolver-rule`, `associate-resolver-rule`, `disassociate-resolver-rule`, `get-resolver-rule-association`, `list-resolver-rule-associations`, `get-resolver-rule-policy`, `put-resolver-rule-policy` |
| DNS Firewall | [`dns-firewall.md`](dns-firewall.md) | `create-firewall-rule-group`, `delete-firewall-rule-group`, `get-firewall-rule-group`, `list-firewall-rule-groups`, `associate-firewall-rule-group`, `disassociate-firewall-rule-group`, `get-firewall-rule-group-association`, `list-firewall-rule-group-associations`, `get-firewall-rule-group-policy`, `put-firewall-rule-group-policy`, `create-firewall-domain-list`, `delete-firewall-domain-list`, `get-firewall-domain-list`, `list-firewall-domain-lists`, `list-firewall-domains`, `import-firewall-domains`, `update-firewall-domains`, `create-firewall-rule`, `delete-firewall-rule`, `list-firewall-rules`, `update-firewall-rule`, `update-firewall-rule-group-association`, `get-firewall-config`, `list-firewall-configs`, `update-firewall-config` |
| Query Logging | [`query-logging.md`](query-logging.md) | `create-resolver-query-log-config`, `delete-resolver-query-log-config`, `get-resolver-query-log-config`, `list-resolver-query-log-configs`, `associate-resolver-query-log-config`, `disassociate-resolver-query-log-config`, `get-resolver-query-log-config-association`, `list-resolver-query-log-config-associations`, `get-resolver-query-log-config-policy`, `put-resolver-query-log-config-policy` |
| DNSSEC Config | [`dnssec-config.md`](dnssec-config.md) | `get-resolver-dnssec-config`, `list-resolver-dnssec-configs`, `update-resolver-dnssec-config`, `get-resolver-config`, `list-resolver-configs`, `update-resolver-config` |
| Outpost Resolvers | [`outpost-resolvers.md`](outpost-resolvers.md) | `create-outpost-resolver`, `delete-outpost-resolver`, `get-outpost-resolver`, `list-outpost-resolvers`, `update-outpost-resolver` |
| Profiles | [`profiles.md`](profiles.md) | `create-profile`, `delete-profile`, `get-profile`, `list-profiles`, `associate-profile`, `disassociate-profile`, `get-profile-association`, `list-profile-associations`, `associate-resource-to-profile`, `disassociate-resource-from-profile`, `get-profile-resource-association`, `list-profile-resource-associations`, `update-profile-resource-association` |
| Tags | [`tags.md`](tags.md) | `tag-resource`, `untag-resource`, `list-tags-for-resource` (both route53resolver and route53profiles) |
