# AWS CLI v2 — WAF v2

## Overview

Complete reference for all `aws wafv2` subcommands in AWS CLI v2. Covers web ACL management, rule groups, IP sets, regex pattern sets, managed rule groups, logging configuration, and tagging. WAF v2 protects CloudFront distributions, ALBs, API Gateway REST APIs, AppSync GraphQL APIs, Cognito user pools, App Runner services, and Verified Access instances.

## Quick Reference — Common Workflows

### Create a web ACL with a rate-based rule
```bash
aws wafv2 create-web-acl --name my-web-acl \
  --scope REGIONAL --default-action Allow={} \
  --visibility-config SampledRequestsEnabled=true,CloudWatchMetricsEnabled=true,MetricName=my-web-acl \
  --rules file://rules.json
```

### Create an IP set for blocking
```bash
aws wafv2 create-ip-set --name blocked-ips \
  --scope REGIONAL --ip-address-version IPV4 \
  --addresses "192.0.2.0/24" "198.51.100.0/24"
```

### Associate a web ACL with an ALB
```bash
aws wafv2 associate-web-acl \
  --web-acl-arn arn:aws:wafv2:us-east-1:123456789012:regional/webacl/my-web-acl/abc123 \
  --resource-arn arn:aws:elasticloadbalancing:us-east-1:123456789012:loadbalancer/app/my-alb/abc123
```

### List available managed rule groups
```bash
aws wafv2 list-available-managed-rule-groups --scope REGIONAL
```

### Enable logging to CloudWatch Logs
```bash
aws wafv2 put-logging-configuration --logging-configuration '{
  "ResourceArn": "arn:aws:wafv2:us-east-1:123456789012:regional/webacl/my-web-acl/abc123",
  "LogDestinationConfigs": ["arn:aws:logs:us-east-1:123456789012:log-group:aws-waf-logs-my-web-acl"]
}'
```

### Get a web ACL and its rules
```bash
aws wafv2 get-web-acl --name my-web-acl --scope REGIONAL --id abc123-def456
```

### Create a rule group
```bash
aws wafv2 create-rule-group --name my-rules \
  --scope REGIONAL --capacity 100 \
  --visibility-config SampledRequestsEnabled=true,CloudWatchMetricsEnabled=true,MetricName=my-rules \
  --rules file://rule-group-rules.json
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Web ACLs | [`web-acls.md`](web-acls.md) | create-web-acl, delete-web-acl, get-web-acl, get-web-acl-for-resource, list-web-acls, update-web-acl, associate-web-acl, disassociate-web-acl, list-resources-for-web-acl, check-capacity, generate-mobile-sdk-release-url, get-decrypted-api-key, create-api-key |
| Rule Groups | [`rule-groups.md`](rule-groups.md) | create-rule-group, delete-rule-group, get-rule-group, list-rule-groups, update-rule-group, list-available-managed-rule-groups, list-available-managed-rule-group-versions, describe-managed-rule-group, get-managed-rule-set, list-managed-rule-sets, put-managed-rule-set-versions, update-managed-rule-set-version-expiry-date |
| IP Sets | [`ip-sets.md`](ip-sets.md) | create-ip-set, delete-ip-set, get-ip-set, list-ip-sets, update-ip-set |
| Regex Pattern Sets | [`regex-pattern-sets.md`](regex-pattern-sets.md) | create-regex-pattern-set, delete-regex-pattern-set, get-regex-pattern-set, list-regex-pattern-sets, update-regex-pattern-set |
| Logging | [`logging.md`](logging.md) | put-logging-configuration, get-logging-configuration, delete-logging-configuration, list-logging-configurations |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
