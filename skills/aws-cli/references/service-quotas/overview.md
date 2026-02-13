# AWS CLI v2 — Service Quotas

## Overview

Complete reference for all `aws service-quotas` subcommands in AWS CLI v2. Covers service quota lookups, quota increase requests, quota templates for AWS Organizations, auto-applied quota management, and tagging. Service Quotas enables you to view and manage your quotas (formerly called limits) for AWS services from a central location.

## Quick Reference — Common Workflows

### List services with quotas
```bash
aws service-quotas list-services \
  --query 'Services[].{Code:ServiceCode,Name:ServiceName}' \
  --output table
```

### Get a specific quota value
```bash
aws service-quotas get-service-quota \
  --service-code ec2 \
  --quota-code L-1216C47A
```

### Get the default quota value
```bash
aws service-quotas get-aws-default-service-quota \
  --service-code ec2 \
  --quota-code L-1216C47A
```

### List all quotas for a service
```bash
aws service-quotas list-service-quotas --service-code ec2 \
  --query 'Quotas[].{Name:QuotaName,Value:Value,Code:QuotaCode}'
```

### Request a quota increase
```bash
aws service-quotas request-service-quota-increase \
  --service-code ec2 \
  --quota-code L-1216C47A \
  --desired-value 100
```

### Check quota increase request history
```bash
aws service-quotas list-requested-service-quota-change-history-by-quota \
  --service-code ec2 \
  --quota-code L-1216C47A
```

### Associate a quota template with Organizations
```bash
aws service-quotas associate-service-quota-template
```

### Put a quota into the template
```bash
aws service-quotas put-service-quota-increase-request-into-template \
  --service-code ec2 \
  --quota-code L-1216C47A \
  --desired-value 100 \
  --aws-region us-east-1
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Quotas | [`quotas.md`](quotas.md) | get-service-quota, get-aws-default-service-quota, list-services, list-service-quotas, list-aws-default-service-quotas |
| Quota Requests | [`quota-requests.md`](quota-requests.md) | request-service-quota-increase, get-requested-service-quota-change, list-requested-service-quota-change-history, list-requested-service-quota-change-history-by-quota |
| Templates | [`templates.md`](templates.md) | associate-service-quota-template, disassociate-service-quota-template, get-association-for-service-quota-template, put-service-quota-increase-request-into-template, get-service-quota-increase-request-from-template, list-service-quota-increase-requests-in-template, delete-service-quota-increase-request-from-template |
| Auto Management | [`auto-management.md`](auto-management.md) | get-service-quota (adjustable quotas), list-service-quotas (with applied values) |
| Utilization | [`utilization.md`](utilization.md) | get-service-quota (usage metrics), list-service-quotas (usage tracking) |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
