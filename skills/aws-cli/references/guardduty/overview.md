# AWS CLI v2 — GuardDuty

## Overview

Complete reference for all `aws guardduty` subcommands in AWS CLI v2. Covers detector management, security findings, filtering, IP sets, threat intelligence sets, malware protection, publishing destinations, member account management, and organization configuration. GuardDuty is a threat detection service that continuously monitors for malicious activity and unauthorized behavior across your AWS accounts, workloads, and data.

## Quick Reference — Common Workflows

### Enable GuardDuty (create a detector)
```bash
aws guardduty create-detector --enable \
  --finding-publishing-frequency FIFTEEN_MINUTES \
  --features '[{"Name":"S3_DATA_EVENTS","Status":"ENABLED"},{"Name":"EKS_AUDIT_LOGS","Status":"ENABLED"},{"Name":"RUNTIME_MONITORING","Status":"ENABLED","AdditionalConfiguration":[{"Name":"ECS_FARGATE_AGENT_MANAGEMENT","Status":"ENABLED"}]}]'
```

### Get detector details
```bash
aws guardduty get-detector --detector-id 12abc34d567e8fa901bc2d34eexample
```

### List and retrieve findings
```bash
aws guardduty list-findings --detector-id 12abc34d567e8fa901bc2d34eexample \
  --finding-criteria '{"Criterion":{"severity":{"Gte":7}}}'
aws guardduty get-findings --detector-id 12abc34d567e8fa901bc2d34eexample \
  --finding-ids 1ab92989eaf0e742df4a014d5example
```

### Archive findings
```bash
aws guardduty archive-findings --detector-id 12abc34d567e8fa901bc2d34eexample \
  --finding-ids 1ab92989eaf0e742df4a014d5example
```

### Create a finding filter
```bash
aws guardduty create-filter --detector-id 12abc34d567e8fa901bc2d34eexample \
  --name HighSeverityFindings --action NOOP --rank 1 \
  --finding-criteria '{"Criterion":{"severity":{"Gte":7}}}'
```

### Create a trusted IP set
```bash
aws guardduty create-ip-set --detector-id 12abc34d567e8fa901bc2d34eexample \
  --name TrustedIPs --format TXT \
  --location s3://my-bucket/trusted-ips.txt --activate
```

### Create a threat intel set
```bash
aws guardduty create-threat-intel-set --detector-id 12abc34d567e8fa901bc2d34eexample \
  --name MyThreatIntel --format TXT \
  --location s3://my-bucket/threat-list.txt --activate
```

### Set up publishing destination (S3)
```bash
aws guardduty create-publishing-destination --detector-id 12abc34d567e8fa901bc2d34eexample \
  --destination-type S3 \
  --destination-properties DestinationArn=arn:aws:s3:::my-findings-bucket,KmsKeyArn=arn:aws:kms:us-east-1:123456789012:key/my-key
```

### Invite and manage member accounts
```bash
aws guardduty create-members --detector-id 12abc34d567e8fa901bc2d34eexample \
  --account-details '[{"AccountId":"111122223333","Email":"member@example.com"}]'
aws guardduty invite-members --detector-id 12abc34d567e8fa901bc2d34eexample \
  --account-ids 111122223333
```

### Enable GuardDuty for an organization
```bash
aws guardduty enable-organization-admin-account --admin-account-id 123456789012
aws guardduty update-organization-configuration --detector-id 12abc34d567e8fa901bc2d34eexample \
  --auto-enable-organization-members ALL \
  --features '[{"Name":"S3_DATA_EVENTS","AutoEnable":"ALL"}]'
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Detectors | [`detectors.md`](detectors.md) | create-detector, delete-detector, get-detector, list-detectors, update-detector |
| Findings | [`findings.md`](findings.md) | get-findings, list-findings, get-findings-statistics, archive-findings, unarchive-findings, update-findings-feedback, create-sample-findings |
| Filters | [`filters.md`](filters.md) | create-filter, delete-filter, get-filter, list-filters, update-filter |
| IP Sets | [`ip-sets.md`](ip-sets.md) | create-ip-set, delete-ip-set, get-ip-set, list-ip-sets, update-ip-set |
| Threat Intel Sets | [`threat-intel-sets.md`](threat-intel-sets.md) | create-threat-intel-set, delete-threat-intel-set, get-threat-intel-set, list-threat-intel-sets, update-threat-intel-set |
| Threat Entity Sets | [`threat-entity-sets.md`](threat-entity-sets.md) | create-threat-entity-set, delete-threat-entity-set, get-threat-entity-set, list-threat-entity-sets, update-threat-entity-set |
| Trusted Entity Sets | [`trusted-entity-sets.md`](trusted-entity-sets.md) | create-trusted-entity-set, delete-trusted-entity-set, get-trusted-entity-set, list-trusted-entity-sets, update-trusted-entity-set |
| Malware Protection | [`malware-protection.md`](malware-protection.md) | create-malware-protection-plan, delete-malware-protection-plan, get-malware-protection-plan, list-malware-protection-plans, update-malware-protection-plan, start-malware-scan, get-malware-scan, get-malware-scan-settings, update-malware-scan-settings, describe-malware-scans, list-malware-scans, send-object-malware-scan |
| Publishing | [`publishing.md`](publishing.md) | create-publishing-destination, delete-publishing-destination, describe-publishing-destination, list-publishing-destinations, update-publishing-destination |
| Members | [`members.md`](members.md) | create-members, delete-members, get-members, invite-members, list-members, disassociate-members, start-monitoring-members, stop-monitoring-members, accept-administrator-invitation, disassociate-from-administrator-account, get-administrator-account, get-invitations-count, list-invitations, decline-invitations, delete-invitations, get-member-detectors, update-member-detectors, get-remaining-free-trial-days |
| Organization | [`organization.md`](organization.md) | enable-organization-admin-account, disable-organization-admin-account, list-organization-admin-accounts, describe-organization-configuration, update-organization-configuration, get-organization-statistics |
| Coverage & Tags | [`coverage-tags.md`](coverage-tags.md) | list-coverage, get-coverage-statistics, get-usage-statistics, tag-resource, untag-resource, list-tags-for-resource |
