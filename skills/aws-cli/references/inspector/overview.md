# AWS CLI v2 — Inspector (Amazon Inspector + Inspector Scan)

## Overview

Complete reference for all `aws inspector2` and `aws inspector-scan` subcommands in AWS CLI v2. Covers vulnerability scanning enablement, finding management, suppression filters, findings reports, coverage tracking, CIS scan configurations, code security integrations, encryption key management, delegated administrator setup, tagging, and SBOM scanning.

## Quick Reference — Common Workflows

### Enable Inspector scanning for EC2 and ECR
```bash
aws inspector2 enable --resource-types EC2 ECR
```

### Check account scanning status
```bash
aws inspector2 batch-get-account-status
```

### List active findings sorted by severity
```bash
aws inspector2 list-findings \
  --sort-criteria 'field=SEVERITY,sortOrder=DESC' \
  --filter-criteria '{"findingStatus":[{"comparison":"EQUALS","value":"ACTIVE"}]}'
```

### List critical and high severity findings
```bash
aws inspector2 list-findings \
  --filter-criteria '{"severity":[{"comparison":"EQUALS","value":"CRITICAL"},{"comparison":"EQUALS","value":"HIGH"}]}'
```

### Create a suppression filter
```bash
aws inspector2 create-filter \
  --name "SuppressInfoFindings" \
  --action SUPPRESS \
  --filter-criteria '{"severity":[{"comparison":"EQUALS","value":"INFORMATIONAL"}]}'
```

### Export findings report to S3
```bash
aws inspector2 create-findings-report \
  --report-format CSV \
  --s3-destination bucketName=my-bucket,kmsKeyArn=arn:aws:kms:us-east-1:123456789012:key/my-key
```

### List resource coverage
```bash
aws inspector2 list-coverage \
  --filter-criteria '{"resourceType":[{"comparison":"EQUALS","value":"AWS_EC2_INSTANCE"}]}'
```

### Create a CIS scan configuration
```bash
aws inspector2 create-cis-scan-configuration \
  --scan-name "weekly-cis-scan" \
  --security-level LEVEL_1 \
  --schedule 'weekly={startTime={timeOfDay="03:00",timezone="UTC"},days=["MON"]}' \
  --targets 'accountIds=123456789012,targetResourceTags={Environment=["production"]}'
```

### Scan an SBOM for vulnerabilities
```bash
aws inspector-scan scan-sbom \
  --sbom file://sbom.json \
  --output-format CYCLONE_DX_1_5
```

### Enable delegated administrator
```bash
aws inspector2 enable-delegated-admin-account \
  --delegated-admin-account-id 123456789012
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Enablement | [`enablement.md`](enablement.md) | enable, disable, batch-get-account-status, batch-get-free-trial-info, get-configuration, update-configuration, update-organization-configuration, describe-organization-configuration, list-account-permissions, list-usage-totals, get-member, list-members, associate-member, disassociate-member, batch-get-member-ec2-deep-inspection-status, batch-update-member-ec2-deep-inspection-status, get-ec2-deep-inspection-configuration, update-ec2-deep-inspection-configuration, update-org-ec2-deep-inspection-configuration |
| Findings | [`findings.md`](findings.md) | list-findings, list-finding-aggregations, batch-get-finding-details, search-vulnerabilities |
| Filters | [`filters.md`](filters.md) | create-filter, delete-filter, update-filter, list-filters |
| Findings Reports | [`findings-reports.md`](findings-reports.md) | create-findings-report, cancel-findings-report, get-findings-report-status, create-sbom-export, cancel-sbom-export, get-sbom-export |
| Coverage | [`coverage.md`](coverage.md) | list-coverage, list-coverage-statistics, get-clusters-for-image |
| CIS Scans | [`cis-scans.md`](cis-scans.md) | create-cis-scan-configuration, delete-cis-scan-configuration, update-cis-scan-configuration, list-cis-scan-configurations, list-cis-scans, get-cis-scan-report, get-cis-scan-result-details, list-cis-scan-results-aggregated-by-checks, list-cis-scan-results-aggregated-by-target-resource, start-cis-session, stop-cis-session, send-cis-session-health, send-cis-session-telemetry |
| Code Security | [`code-security.md`](code-security.md) | create-code-security-integration, delete-code-security-integration, update-code-security-integration, get-code-security-integration, list-code-security-integrations, create-code-security-scan-configuration, delete-code-security-scan-configuration, update-code-security-scan-configuration, get-code-security-scan-configuration, list-code-security-scan-configurations, list-code-security-scan-configuration-associations, batch-associate-code-security-scan-configuration, batch-disassociate-code-security-scan-configuration, start-code-security-scan, get-code-security-scan |
| Encryption | [`encryption.md`](encryption.md) | get-encryption-key, update-encryption-key, reset-encryption-key |
| Delegated Admin | [`delegated-admin.md`](delegated-admin.md) | enable-delegated-admin-account, disable-delegated-admin-account, get-delegated-admin-account, list-delegated-admin-accounts |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
| SBOM Scan | [`scan-sbom.md`](scan-sbom.md) | scan-sbom (inspector-scan) |
