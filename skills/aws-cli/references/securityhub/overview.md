# AWS CLI v2 — Security Hub

## Overview

Complete reference for all `aws securityhub` subcommands in AWS CLI v2. Covers hub management, security findings, custom insights, security standards, security controls, automation rules, configuration policies, finding aggregators, action targets, member account management, and organization configuration. Security Hub provides a comprehensive view of security state across AWS accounts, integrating findings from AWS services and third-party tools.

## Quick Reference — Common Workflows

### Enable Security Hub
```bash
aws securityhub enable-security-hub \
  --enable-default-standards \
  --control-finding-generator SECURITY_CONTROL \
  --tags '{"Department":"Security"}'
```

### Get findings with filters
```bash
aws securityhub get-findings \
  --filters '{"SeverityLabel":[{"Value":"CRITICAL","Comparison":"EQUALS"}],"WorkflowStatus":[{"Value":"NEW","Comparison":"EQUALS"}]}' \
  --sort-criteria '{"Field":"SeverityLabel","SortOrder":"desc"}' \
  --max-items 25
```

### Batch update findings (set workflow status)
```bash
aws securityhub batch-update-findings \
  --finding-identifiers '[{"Id":"arn:aws:securityhub:us-east-1:123456789012:finding/abc123","ProductArn":"arn:aws:securityhub:us-east-1::product/aws/securityhub"}]' \
  --workflow '{"Status":"RESOLVED"}'
```

### Create a custom insight
```bash
aws securityhub create-insight --name "Critical Findings by Resource" \
  --filters '{"SeverityLabel":[{"Value":"CRITICAL","Comparison":"EQUALS"}]}' \
  --group-by-attribute "ResourceType"
```

### Enable a security standard
```bash
aws securityhub batch-enable-standards \
  --standards-subscription-requests '[{"StandardsArn":"arn:aws:securityhub:::ruleset/cis-aws-foundations-benchmark/v/1.4.0"}]'
```

### Create an automation rule
```bash
aws securityhub create-automation-rule --rule-name "Auto-suppress informational" \
  --rule-order 1 --rule-status ENABLED \
  --criteria '{"SeverityLabel":[{"Value":"INFORMATIONAL","Comparison":"EQUALS"}]}' \
  --actions '[{"Type":"FINDING_FIELDS_UPDATE","FindingFieldsUpdate":{"Workflow":{"Status":"SUPPRESSED"}}}]'
```

### Set up cross-region aggregation
```bash
aws securityhub create-finding-aggregator --region-linking-mode ALL_REGIONS
```

### Invite and manage members
```bash
aws securityhub create-members \
  --account-details '[{"AccountId":"111122223333","Email":"member@example.com"}]'
aws securityhub invite-members --account-ids 111122223333
```

### Enable Security Hub for an organization
```bash
aws securityhub enable-organization-admin-account --admin-account-id 123456789012
aws securityhub update-organization-configuration --auto-enable --auto-enable-standards DEFAULT
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Hub | [`hub.md`](hub.md) | enable-security-hub, disable-security-hub, describe-hub, update-security-hub-configuration |
| Findings | [`findings.md`](findings.md) | get-findings, batch-import-findings, batch-update-findings, update-findings, get-finding-history |
| Insights | [`insights.md`](insights.md) | create-insight, delete-insight, get-insights, get-insight-results, update-insight |
| Standards | [`standards.md`](standards.md) | describe-standards, batch-enable-standards, batch-disable-standards, get-enabled-standards, describe-standards-controls, update-standards-control, batch-get-standards-control-associations, batch-update-standards-control-associations, list-standards-control-associations |
| Security Controls | [`security-controls.md`](security-controls.md) | list-security-control-definitions, get-security-control-definition, batch-get-security-controls, update-security-control |
| Automation Rules | [`automation-rules.md`](automation-rules.md) | create-automation-rule, list-automation-rules, batch-get-automation-rules, batch-update-automation-rules, batch-delete-automation-rules |
| Configuration Policies | [`configuration-policies.md`](configuration-policies.md) | create-configuration-policy, delete-configuration-policy, get-configuration-policy, list-configuration-policies, update-configuration-policy, get-configuration-policy-association, list-configuration-policy-associations, batch-get-configuration-policy-associations, start-configuration-policy-association, start-configuration-policy-disassociation |
| Finding Aggregators | [`finding-aggregators.md`](finding-aggregators.md) | create-finding-aggregator, delete-finding-aggregator, get-finding-aggregator, list-finding-aggregators, update-finding-aggregator |
| Aggregators v2 | [`aggregators-v2.md`](aggregators-v2.md) | create-aggregator-v2, delete-aggregator-v2, get-aggregator-v2, list-aggregators-v2, update-aggregator-v2 |
| Connectors v2 | [`connectors-v2.md`](connectors-v2.md) | create-connector-v2, delete-connector-v2, get-connector-v2, list-connectors-v2, update-connector-v2, register-connector-v2 |
| Action Targets | [`action-targets.md`](action-targets.md) | create-action-target, delete-action-target, describe-action-targets, update-action-target |
| Members | [`members.md`](members.md) | create-members, delete-members, get-members, invite-members, list-members, disassociate-members, accept-administrator-invitation, disassociate-from-administrator-account, get-administrator-account, get-invitations-count, list-invitations, decline-invitations, delete-invitations |
| Organization | [`organization.md`](organization.md) | enable-organization-admin-account, disable-organization-admin-account, list-organization-admin-accounts, describe-organization-configuration, update-organization-configuration |
| Products & Tags | [`products-tags.md`](products-tags.md) | describe-products, enable-import-findings-for-product, disable-import-findings-for-product, list-enabled-products-for-import, tag-resource, untag-resource, list-tags-for-resource |
