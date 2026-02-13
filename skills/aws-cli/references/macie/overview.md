# AWS CLI v2 — Macie (macie2)

## Overview

Complete reference for all `aws macie2` subcommands in AWS CLI v2. Covers Macie session management, classification jobs, findings, findings filters, allow lists, custom data identifiers, S3 bucket analysis, automated discovery, resource profiles, sensitivity settings, member account management, and organization configuration. Amazon Macie is a data security service that discovers sensitive data using machine learning and pattern matching, provides visibility into data security risks, and enables automated protection against those risks.

## Quick Reference — Common Workflows

### Enable Macie
```bash
aws macie2 enable-macie --status ENABLED \
  --finding-publishing-frequency FIFTEEN_MINUTES
```

### Create a classification job
```bash
aws macie2 create-classification-job --job-type ONE_TIME \
  --name "Scan PII in production" \
  --s3-job-definition '{"bucketDefinitions":[{"accountId":"123456789012","buckets":["my-prod-bucket"]}]}' \
  --managed-data-identifier-ids '["PII","FINANCIAL"]'
```

### List and get findings
```bash
aws macie2 list-findings --sort-criteria '{"attributeName":"severity.score","orderBy":"DESC"}' \
  --finding-criteria '{"criterion":{"severity.description":{"eq":["High"]}}}'
aws macie2 get-findings --finding-ids id1 id2
```

### Create a findings filter
```bash
aws macie2 create-findings-filter --name "High severity" --action ARCHIVE \
  --finding-criteria '{"criterion":{"severity.description":{"eq":["High"]}}}'
```

### Create an allow list
```bash
aws macie2 create-allow-list --name "Internal emails" \
  --criteria '{"s3WordsList":{"bucketName":"my-config-bucket","objectKey":"allow-list.txt"}}' \
  --description "Internal email addresses to ignore"
```

### Describe S3 buckets monitored by Macie
```bash
aws macie2 describe-buckets \
  --criteria '{"bucketName":{"eq":["my-bucket"]}}'
```

### Enable automated discovery
```bash
aws macie2 update-automated-discovery-configuration \
  --status ENABLED \
  --auto-enable-organization-members ALL
```

### Manage organization Macie deployment
```bash
aws macie2 enable-organization-admin-account --admin-account-id 123456789012
aws macie2 update-organization-configuration --auto-enable
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Session | [`session.md`](session.md) | enable-macie, disable-macie, get-macie-session, update-macie-session |
| Classification Jobs | [`classification-jobs.md`](classification-jobs.md) | create-classification-job, describe-classification-job, list-classification-jobs, update-classification-job |
| Findings | [`findings.md`](findings.md) | get-findings, list-findings, get-finding-statistics, create-sample-findings |
| Findings Filters | [`findings-filters.md`](findings-filters.md) | create-findings-filter, delete-findings-filter, get-findings-filter, list-findings-filters, update-findings-filter, get-findings-publication-configuration, put-findings-publication-configuration |
| Allow Lists | [`allow-lists.md`](allow-lists.md) | create-allow-list, delete-allow-list, get-allow-list, list-allow-lists, update-allow-list |
| Data Identifiers | [`data-identifiers.md`](data-identifiers.md) | create-custom-data-identifier, delete-custom-data-identifier, get-custom-data-identifier, list-custom-data-identifiers, batch-get-custom-data-identifiers, list-managed-data-identifiers, test-custom-data-identifier |
| Buckets | [`buckets.md`](buckets.md) | describe-buckets, get-bucket-statistics, search-resources, get-classification-export-configuration, put-classification-export-configuration, get-classification-scope, list-classification-scopes, update-classification-scope |
| Automated Discovery | [`automated-discovery.md`](automated-discovery.md) | get-automated-discovery-configuration, update-automated-discovery-configuration, list-automated-discovery-accounts, batch-update-automated-discovery-accounts |
| Resource Profiles | [`resource-profiles.md`](resource-profiles.md) | get-resource-profile, list-resource-profile-artifacts, list-resource-profile-detections, update-resource-profile, update-resource-profile-detections |
| Sensitivity | [`sensitivity.md`](sensitivity.md) | get-reveal-configuration, update-reveal-configuration, get-sensitive-data-occurrences, get-sensitive-data-occurrences-availability, get-sensitivity-inspection-template, list-sensitivity-inspection-templates, update-sensitivity-inspection-template |
| Members | [`members.md`](members.md) | create-member, delete-member, get-member, list-members, disassociate-member, create-invitations, accept-invitation, decline-invitations, delete-invitations, list-invitations, get-invitations-count, disassociate-from-administrator-account, get-administrator-account, update-member-session |
| Organization | [`organization.md`](organization.md) | enable-organization-admin-account, disable-organization-admin-account, list-organization-admin-accounts, describe-organization-configuration, update-organization-configuration |
| Usage & Tags | [`usage-tags.md`](usage-tags.md) | get-usage-statistics, get-usage-totals, tag-resource, untag-resource, list-tags-for-resource |
| Wait | [`wait.md`](wait.md) | wait finding-revealed |
