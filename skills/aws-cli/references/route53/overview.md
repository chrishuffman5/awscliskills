
# AWS CLI v2 — Route 53 (DNS Service)

## Overview

Complete reference for `aws route53` and `aws route53domains` subcommands in AWS CLI v2. Covers hosted zone management, DNS record operations (A, AAAA, CNAME, MX, TXT, NS, SOA, SRV, alias), health checks, routing policies (simple, weighted, latency, failover, geolocation, multivalue), domain registration, and traffic flow.

## Quick Reference — Common Workflows

### Create a hosted zone
```bash
aws route53 create-hosted-zone --name example.com --caller-reference $(date +%s)
```

### Create an A record
```bash
aws route53 change-resource-record-sets --hosted-zone-id Z123 \
  --change-batch '{
    "Changes":[{
      "Action":"UPSERT",
      "ResourceRecordSet":{
        "Name":"app.example.com",
        "Type":"A",
        "TTL":300,
        "ResourceRecords":[{"Value":"1.2.3.4"}]
      }
    }]
  }'
```

### Create alias record pointing to ALB
```bash
aws route53 change-resource-record-sets --hosted-zone-id Z123 \
  --change-batch '{
    "Changes":[{
      "Action":"UPSERT",
      "ResourceRecordSet":{
        "Name":"app.example.com",
        "Type":"A",
        "AliasTarget":{
          "HostedZoneId":"Z35SXDOTRQ7X7K",
          "DNSName":"my-alb-123.us-east-1.elb.amazonaws.com",
          "EvaluateTargetHealth":true
        }
      }
    }]
  }'
```

### List records in a hosted zone
```bash
aws route53 list-resource-record-sets --hosted-zone-id Z123 \
  --query 'ResourceRecordSets[].{Name:Name,Type:Type,TTL:TTL}'
```

### Create a health check
```bash
aws route53 create-health-check --caller-reference $(date +%s) \
  --health-check-config '{
    "Type":"HTTPS",
    "FullyQualifiedDomainName":"app.example.com",
    "Port":443,
    "RequestInterval":30,
    "FailureThreshold":3
  }'
```

## Covered Command Groups

| Group | Commands | CLI Service |
|-------|----------|-------------|
| Hosted Zones | create, delete, get, list, update, associate/disassociate VPC | `aws route53` |
| Records | change-resource-record-sets, list-resource-record-sets, test-dns-answer | `aws route53` |
| Health Checks | create, delete, get, list, update, get-status | `aws route53` |
| Traffic Policies | create, delete, get, list, update, create/get/list policy instances | `aws route53` |
| DNSSEC | enable/disable-hosted-zone-dnssec, get-dnssec | `aws route53` |
| Query Logging | create, delete, list query logging configs | `aws route53` |
| Domain Registration | register, transfer, renew, check-availability, get/update details | `aws route53domains` |

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Hosted Zones | [`hosted-zones.md`](hosted-zones.md) | create-hosted-zone, delete-hosted-zone, get-hosted-zone, list-hosted-zones, list-hosted-zones-by-name, update-hosted-zone-comment, associate-vpc-with-hosted-zone, disassociate-vpc-from-hosted-zone, list-hosted-zones-by-vpc, get-hosted-zone-count, get-hosted-zone-limit |
| Records | [`records.md`](records.md) | change-resource-record-sets, list-resource-record-sets, test-dns-answer, get-change |
| Health Checks | [`health-checks.md`](health-checks.md) | create-health-check, delete-health-check, get-health-check, list-health-checks, update-health-check, get-health-check-status, get-health-check-last-failure-reason, get-health-check-count, get-checker-ip-ranges |
| Traffic Policies | [`traffic-policies.md`](traffic-policies.md) | create-traffic-policy, create-traffic-policy-version, get-traffic-policy, delete-traffic-policy, list-traffic-policies, list-traffic-policy-versions, update-traffic-policy-comment, create-traffic-policy-instance, get-traffic-policy-instance, delete-traffic-policy-instance, list-traffic-policy-instances, list-traffic-policy-instances-by-hosted-zone, list-traffic-policy-instances-by-policy, update-traffic-policy-instance, get-traffic-policy-instance-count |
| DNSSEC | [`dnssec.md`](dnssec.md) | enable-hosted-zone-dnssec, disable-hosted-zone-dnssec, get-dnssec, create-key-signing-key, delete-key-signing-key, activate-key-signing-key, deactivate-key-signing-key |
| Query Logging | [`query-logging.md`](query-logging.md) | create-query-logging-config, delete-query-logging-config, get-query-logging-config, list-query-logging-configs |
| Reusable Delegation Sets | [`reusable-delegation-sets.md`](reusable-delegation-sets.md) | create-reusable-delegation-set, delete-reusable-delegation-set, get-reusable-delegation-set, list-reusable-delegation-sets |
| Domain Registration | [`domain-registration.md`](domain-registration.md) | register-domain, transfer-domain, renew-domain, check-domain-availability, check-domain-transferability, get-domain-detail, list-domains, update-domain-nameservers, update-domain-contact, enable-domain-auto-renew, disable-domain-auto-renew, enable-domain-transfer-lock, disable-domain-transfer-lock, get-operation-detail, list-operations, list-prices, delete-domain |
| Tags | [`tags.md`](tags.md) | change-tags-for-resource, list-tags-for-resource, list-tags-for-resources, list-tags-for-domain, update-tags-for-domain, delete-tags-for-domain |
