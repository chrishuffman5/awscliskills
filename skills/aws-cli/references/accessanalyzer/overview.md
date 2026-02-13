# AWS CLI v2 — IAM Access Analyzer (accessanalyzer)

## Overview

Complete reference for all `aws accessanalyzer` subcommands in AWS CLI v2. Covers analyzer management, findings lifecycle, archive rules, access previews, policy validation, policy generation, and custom policy checks. IAM Access Analyzer helps identify resources shared with external principals, detect unused access, and validate IAM policies against best practices. Supports account-level and organization-level analyzers for external access, unused access, and internal access analysis.

## Quick Reference — Common Workflows

### Create an account-level analyzer
```bash
aws accessanalyzer create-analyzer \
  --analyzer-name my-account-analyzer \
  --type ACCOUNT
```

### Create an organization-level analyzer
```bash
aws accessanalyzer create-analyzer \
  --analyzer-name my-org-analyzer \
  --type ORGANIZATION
```

### List all analyzers
```bash
aws accessanalyzer list-analyzers
```

### List active findings for an analyzer
```bash
aws accessanalyzer list-findings \
  --analyzer-arn arn:aws:access-analyzer:us-east-1:123456789012:analyzer/my-analyzer \
  --filter '{"status": {"eq": ["ACTIVE"]}}'
```

### Get details of a specific finding
```bash
aws accessanalyzer get-finding \
  --analyzer-arn arn:aws:access-analyzer:us-east-1:123456789012:analyzer/my-analyzer \
  --id 0910eedb-381e-4e95-adda-0d25c19e6e90
```

### Archive findings
```bash
aws accessanalyzer update-findings \
  --analyzer-arn arn:aws:access-analyzer:us-east-1:123456789012:analyzer/my-analyzer \
  --ids 0910eedb-381e-4e95-adda-0d25c19e6e90 \
  --status ARCHIVED
```

### Create an archive rule
```bash
aws accessanalyzer create-archive-rule \
  --analyzer-name my-analyzer \
  --rule-name auto-archive-s3 \
  --filter '{"resourceType": {"eq": ["AWS::S3::Bucket"]}, "isPublic": {"eq": ["false"]}}'
```

### Validate a policy document
```bash
aws accessanalyzer validate-policy \
  --policy-document file://policy.json \
  --policy-type IDENTITY_POLICY
```

### Check that a policy does not grant specific access
```bash
aws accessanalyzer check-access-not-granted \
  --policy-document file://policy.json \
  --access actions=s3:DeleteBucket,s3:GetBucketLocation \
  --policy-type IDENTITY_POLICY
```

### Generate a policy from CloudTrail activity
```bash
aws accessanalyzer start-policy-generation \
  --policy-generation-details '{"principalArn":"arn:aws:iam::123456789012:role/MyRole"}' \
  --cloud-trail-details file://trail-config.json
aws accessanalyzer get-generated-policy --job-id c557dc4a-0338-4489-95dd-739014860ff9
```

### Create an access preview
```bash
aws accessanalyzer create-access-preview \
  --analyzer-arn arn:aws:access-analyzer:us-east-1:123456789012:analyzer/my-analyzer \
  --configurations file://preview-config.json
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Analyzers | [`analyzers.md`](analyzers.md) | create-analyzer, get-analyzer, list-analyzers, update-analyzer, delete-analyzer, get-analyzed-resource, list-analyzed-resources, start-resource-scan |
| Findings | [`findings.md`](findings.md) | list-findings, get-finding, list-findings-v2, get-finding-v2, get-findings-statistics, update-findings, generate-finding-recommendation, get-finding-recommendation |
| Archive Rules | [`archive-rules.md`](archive-rules.md) | create-archive-rule, get-archive-rule, list-archive-rules, update-archive-rule, delete-archive-rule, apply-archive-rule |
| Access Previews | [`access-previews.md`](access-previews.md) | create-access-preview, get-access-preview, list-access-previews, list-access-preview-findings |
| Policy Tools | [`policy-tools.md`](policy-tools.md) | validate-policy, check-access-not-granted, check-no-new-access, check-no-public-access, start-policy-generation, get-generated-policy, list-policy-generations, cancel-policy-generation |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
