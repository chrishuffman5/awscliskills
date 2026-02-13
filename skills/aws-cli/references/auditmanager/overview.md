# AWS CLI v2 — Audit Manager

## Overview

Complete reference for all `aws auditmanager` subcommands in AWS CLI v2. Covers assessment creation and management, framework customization, control definition, assessment reports, evidence collection, audit delegations, compliance insights, and account settings.

## Quick Reference — Common Workflows

### Register Audit Manager account
```bash
aws auditmanager register-account
```

### Create an assessment from a framework
```bash
aws auditmanager create-assessment \
  --name "SOC2-Assessment" \
  --framework-id a1b2c3d4-5678-90ab-cdef-EXAMPLE11111 \
  --assessment-reports-destination 'destinationType=S3,destination=s3://my-audit-bucket' \
  --scope 'awsAccounts=[{id=123456789012}]' \
  --roles 'roleType=PROCESS_OWNER,roleArn=arn:aws:iam::123456789012:role/AuditRole'
```

### List all assessments
```bash
aws auditmanager list-assessments
```

### Create a custom framework
```bash
aws auditmanager create-assessment-framework \
  --name "Custom-Framework" \
  --control-sets '[{"name":"ControlSet1","controls":[{"id":"control-uuid"}]}]'
```

### Create a custom control
```bash
aws auditmanager create-control \
  --name "Custom-Access-Control" \
  --control-mapping-sources '[{"sourceName":"CloudTrail","sourceSetUpOption":"System_Controls_Mapping","sourceType":"AWS_Cloudtrail","sourceKeyword":{"keywordInputType":"SELECT_FROM_LIST","keywordValue":"IAM"}}]'
```

### Generate an assessment report
```bash
aws auditmanager create-assessment-report \
  --name "Q1-2024-Report" \
  --assessment-id a1b2c3d4-5678-90ab-cdef-EXAMPLE11111
```

### Get compliance insights
```bash
aws auditmanager get-insights
```

### Get account settings
```bash
aws auditmanager get-settings --attribute ALL
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Assessments | [`assessments.md`](assessments.md) | create-assessment, get-assessment, update-assessment, delete-assessment, list-assessments, update-assessment-status, update-assessment-control, update-assessment-control-set-status, get-change-logs |
| Assessment Frameworks | [`assessment-frameworks.md`](assessment-frameworks.md) | create-assessment-framework, get-assessment-framework, update-assessment-framework, delete-assessment-framework, list-assessment-frameworks, start-assessment-framework-share, update-assessment-framework-share, delete-assessment-framework-share, list-assessment-framework-share-requests |
| Controls | [`controls.md`](controls.md) | create-control, get-control, update-control, delete-control, list-controls, get-services-in-scope, list-keywords-for-data-source |
| Assessment Reports | [`assessment-reports.md`](assessment-reports.md) | create-assessment-report, delete-assessment-report, list-assessment-reports, get-assessment-report-url, associate-assessment-report-evidence-folder, disassociate-assessment-report-evidence-folder, batch-associate-assessment-report-evidence, batch-disassociate-assessment-report-evidence, validate-assessment-report-integrity |
| Evidence | [`evidence.md`](evidence.md) | get-evidence, get-evidence-by-evidence-folder, get-evidence-folder, get-evidence-folders-by-assessment, get-evidence-folders-by-assessment-control, batch-import-evidence-to-assessment-control, get-evidence-file-upload-url |
| Delegations | [`delegations.md`](delegations.md) | get-delegations, batch-create-delegation-by-assessment, batch-delete-delegation-by-assessment |
| Insights | [`insights.md`](insights.md) | get-insights, get-insights-by-assessment, list-assessment-control-insights-by-control-domain, list-control-domain-insights, list-control-domain-insights-by-assessment, list-control-insights-by-control-domain |
| Account Settings | [`account-settings.md`](account-settings.md) | register-account, deregister-account, get-account-status, get-settings, update-settings, register-organization-admin-account, deregister-organization-admin-account, get-organization-admin-account, list-notifications, list-tags-for-resource, tag-resource, untag-resource |
