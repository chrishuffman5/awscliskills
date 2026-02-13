# AWS CLI v2 — Resource Groups Tagging API

## Overview

Complete reference for all `aws resourcegroupstaggingapi` subcommands in AWS CLI v2. Covers cross-service tag management including tagging and untagging AWS resources, discovering resources by tag, retrieving tag keys and values, and tag compliance reporting.

## Quick Reference — Common Workflows

### Tag multiple resources

```bash
aws resourcegroupstaggingapi tag-resources \
  --resource-arn-list arn:aws:ec2:us-east-1:123456789012:instance/i-1234567890abcdef0 \
    arn:aws:s3:::my-bucket \
  --tags Environment=production,Team=platform
```

### Untag resources

```bash
aws resourcegroupstaggingapi untag-resources \
  --resource-arn-list arn:aws:ec2:us-east-1:123456789012:instance/i-1234567890abcdef0 \
  --tag-keys Environment Team
```

### Find all resources with a specific tag

```bash
aws resourcegroupstaggingapi get-resources \
  --tag-filters Key=Environment,Values=production \
  --query 'ResourceTagMappingList[].ResourceARN' --output text
```

### Find resources of a specific type with tags

```bash
aws resourcegroupstaggingapi get-resources \
  --resource-type-filters ec2:instance s3 \
  --tag-filters Key=Team,Values=platform
```

### List all tag keys in the account

```bash
aws resourcegroupstaggingapi get-tag-keys \
  --query 'TagKeys' --output table
```

### List all values for a specific tag key

```bash
aws resourcegroupstaggingapi get-tag-values \
  --key Environment \
  --query 'TagValues' --output table
```

### Get tag compliance summary

```bash
aws resourcegroupstaggingapi get-compliance-summary \
  --tag-key-filters Environment \
  --region-filters us-east-1 us-west-2
```

### Get detailed noncompliant resources

```bash
aws resourcegroupstaggingapi describe-report-creation
aws resourcegroupstaggingapi start-report-creation \
  --s3-bucket my-compliance-reports
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Tagging | [`tagging.md`](tagging.md) | get-resources, get-tag-keys, get-tag-values, tag-resources, untag-resources |
| Compliance | [`compliance.md`](compliance.md) | get-compliance-summary, start-report-creation, describe-report-creation |
