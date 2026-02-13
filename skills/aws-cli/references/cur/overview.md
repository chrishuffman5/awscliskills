# AWS CLI v2 — Cost and Usage Report

## Overview

Complete reference for all `aws cur` subcommands in AWS CLI v2. Covers creating, describing, modifying, and deleting Cost and Usage Report (CUR) definitions that deliver detailed billing data to S3 buckets. Reports can be formatted as CSV or Parquet with optional integration for Amazon Redshift, QuickSight, or Athena.

## Quick Reference — Common Workflows

### Create a daily CUR with resource-level detail
```bash
aws cur put-report-definition \
  --report-definition '{
    "ReportName": "daily-cur",
    "TimeUnit": "DAILY",
    "Format": "Parquet",
    "Compression": "Parquet",
    "AdditionalSchemaElements": ["RESOURCES"],
    "S3Bucket": "my-cur-bucket",
    "S3Prefix": "reports/daily",
    "S3Region": "us-east-1",
    "AdditionalArtifacts": ["ATHENA"],
    "RefreshClosedReports": true,
    "ReportVersioning": "OVERWRITE_REPORT"
  }' --region us-east-1
```

### List all report definitions
```bash
aws cur describe-report-definitions --region us-east-1
```

### Modify an existing report
```bash
aws cur modify-report-definition \
  --report-name "daily-cur" \
  --report-definition file://updated-report.json \
  --region us-east-1
```

### Delete a report definition
```bash
aws cur delete-report-definition \
  --report-name "daily-cur" \
  --region us-east-1
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Reports | [`reports.md`](reports.md) | put-report-definition, delete-report-definition, describe-report-definitions, modify-report-definition |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
