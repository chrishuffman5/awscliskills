# AWS CLI v2 — Backup (AWS Backup + Backup Gateway)

## Overview

Complete reference for all `aws backup` and `aws backup-gateway` subcommands in AWS CLI v2. Covers backup plans and selections, backup vaults (including logically air-gapped vaults), backup jobs, copy jobs, restore jobs, recovery points, protected resources, compliance frameworks, report plans, restore testing, legal holds, tiering and scanning, global/region settings, and Backup Gateway for VM backup.

## Quick Reference — Common Workflows

### Create a backup vault
```bash
aws backup create-backup-vault \
  --backup-vault-name my-vault \
  --encryption-key-arn arn:aws:kms:us-east-1:123456789012:key/key-id
```

### Create a backup plan with daily backups
```bash
aws backup create-backup-plan --backup-plan '{
  "BackupPlanName": "DailyPlan",
  "Rules": [{
    "RuleName": "DailyRule",
    "TargetBackupVaultName": "my-vault",
    "ScheduleExpression": "cron(0 5 ? * * *)",
    "StartWindowMinutes": 480,
    "Lifecycle": {"DeleteAfterDays": 35}
  }]
}'
```

### Assign resources to a backup plan
```bash
aws backup create-backup-selection \
  --backup-plan-id my-plan-id \
  --backup-selection '{
    "SelectionName": "AllEBS",
    "IamRoleArn": "arn:aws:iam::123456789012:role/BackupRole",
    "Resources": ["arn:aws:ec2:*:*:volume/*"]
  }'
```

### Start an on-demand backup
```bash
aws backup start-backup-job \
  --backup-vault-name my-vault \
  --resource-arn arn:aws:ec2:us-east-1:123456789012:volume/vol-12345 \
  --iam-role-arn arn:aws:iam::123456789012:role/BackupRole
```

### Restore from a recovery point
```bash
aws backup start-restore-job \
  --recovery-point-arn arn:aws:backup:us-east-1:123456789012:recovery-point:rp-id \
  --metadata '{"availabilityZone":"us-east-1a"}' \
  --iam-role-arn arn:aws:iam::123456789012:role/RestoreRole \
  --resource-type EBS
```

### Copy a recovery point to another vault/region
```bash
aws backup start-copy-job \
  --recovery-point-arn arn:aws:backup:us-east-1:123456789012:recovery-point:rp-id \
  --source-backup-vault-name my-vault \
  --destination-backup-vault-arn arn:aws:backup:us-west-2:123456789012:backup-vault:dr-vault \
  --iam-role-arn arn:aws:iam::123456789012:role/BackupRole
```

### Lock a backup vault
```bash
aws backup put-backup-vault-lock-configuration \
  --backup-vault-name my-vault \
  --min-retention-days 7 \
  --max-retention-days 365
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Backup Plans | [`backup-plans.md`](backup-plans.md) | create-backup-plan, update-backup-plan, delete-backup-plan, get-backup-plan, list-backup-plans, list-backup-plan-versions, list-backup-plan-templates, get-backup-plan-from-template, get-backup-plan-from-json, export-backup-plan-template, create-backup-selection, delete-backup-selection, get-backup-selection, list-backup-selections |
| Backup Vaults | [`backup-vaults.md`](backup-vaults.md) | create-backup-vault, delete-backup-vault, describe-backup-vault, list-backup-vaults, create-logically-air-gapped-backup-vault, put-backup-vault-access-policy, get-backup-vault-access-policy, delete-backup-vault-access-policy, put-backup-vault-lock-configuration, delete-backup-vault-lock-configuration, put-backup-vault-notifications, get-backup-vault-notifications, delete-backup-vault-notifications, create-restore-access-backup-vault, list-restore-access-backup-vaults, revoke-restore-access-backup-vault |
| Backup Jobs | [`backup-jobs.md`](backup-jobs.md) | start-backup-job, describe-backup-job, list-backup-jobs, list-backup-job-summaries, stop-backup-job |
| Copy Jobs | [`copy-jobs.md`](copy-jobs.md) | start-copy-job, describe-copy-job, list-copy-jobs, list-copy-job-summaries |
| Restore Jobs | [`restore-jobs.md`](restore-jobs.md) | start-restore-job, describe-restore-job, list-restore-jobs, list-restore-job-summaries, list-restore-jobs-by-protected-resource, get-restore-job-metadata, put-restore-validation-result |
| Recovery Points | [`recovery-points.md`](recovery-points.md) | describe-recovery-point, list-recovery-points-by-backup-vault, list-recovery-points-by-resource, list-recovery-points-by-legal-hold, list-indexed-recovery-points, delete-recovery-point, disassociate-recovery-point, disassociate-recovery-point-from-parent, update-recovery-point-lifecycle, update-recovery-point-index-settings, get-recovery-point-restore-metadata, get-recovery-point-index-details |
| Protected Resources | [`protected-resources.md`](protected-resources.md) | describe-protected-resource, list-protected-resources, list-protected-resources-by-backup-vault, get-supported-resource-types |
| Frameworks | [`frameworks.md`](frameworks.md) | create-framework, update-framework, delete-framework, describe-framework, list-frameworks |
| Report Plans | [`report-plans.md`](report-plans.md) | create-report-plan, update-report-plan, delete-report-plan, describe-report-plan, list-report-plans, describe-report-job, list-report-jobs, start-report-job |
| Restore Testing | [`restore-testing.md`](restore-testing.md) | create-restore-testing-plan, update-restore-testing-plan, delete-restore-testing-plan, get-restore-testing-plan, list-restore-testing-plans, create-restore-testing-selection, update-restore-testing-selection, delete-restore-testing-selection, get-restore-testing-selection, list-restore-testing-selections, get-restore-testing-inferred-metadata |
| Legal Holds | [`legal-holds.md`](legal-holds.md) | create-legal-hold, cancel-legal-hold, get-legal-hold, list-legal-holds |
| Tiering & Scanning | [`tiering-scanning.md`](tiering-scanning.md) | create-tiering-configuration, update-tiering-configuration, delete-tiering-configuration, get-tiering-configuration, list-tiering-configurations, start-scan-job, describe-scan-job, list-scan-jobs, list-scan-job-summaries |
| Settings | [`settings.md`](settings.md) | describe-global-settings, update-global-settings, describe-region-settings, update-region-settings |
| Backup Gateway | [`backup-gateway.md`](backup-gateway.md) | create-gateway, delete-gateway, get-gateway, list-gateways, update-gateway-information, update-gateway-software-now, associate-gateway-to-server, disassociate-gateway-from-server, import-hypervisor-configuration, get-hypervisor, list-hypervisors, update-hypervisor, delete-hypervisor, get-virtual-machine, list-virtual-machines, test-hypervisor-configuration, put-maintenance-start-time, get-bandwidth-rate-limit-schedule, put-bandwidth-rate-limit-schedule, get-hypervisor-property-mappings, put-hypervisor-property-mappings, start-virtual-machines-metadata-sync |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags |
