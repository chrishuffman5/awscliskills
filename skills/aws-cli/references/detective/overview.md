# AWS CLI v2 — Detective

## Overview

Complete reference for all `aws detective` subcommands in AWS CLI v2. Covers behavior graph management, member account management, investigations, data source packages, and organization configuration. Amazon Detective automatically collects log data from your AWS resources and uses machine learning, statistical analysis, and graph theory to build visualizations that help you investigate potential security issues.

## Quick Reference — Common Workflows

### Create a behavior graph
```bash
aws detective create-graph \
  --tags '{"Environment":"Production"}'
```

### Add members to a behavior graph
```bash
aws detective create-members --graph-arn arn:aws:detective:us-east-1:123456789012:graph:abc123 \
  --accounts '[{"AccountId":"111122223333","EmailAddress":"member@example.com"}]'
```

### List behavior graphs
```bash
aws detective list-graphs --max-results 10
```

### Start an investigation
```bash
aws detective start-investigation \
  --graph-arn arn:aws:detective:us-east-1:123456789012:graph:abc123 \
  --entity-arn arn:aws:iam::111122223333:user/suspicious-user \
  --scope-start-time 2024-01-01T00:00:00Z \
  --scope-end-time 2024-01-02T00:00:00Z
```

### Get investigation details
```bash
aws detective get-investigation \
  --graph-arn arn:aws:detective:us-east-1:123456789012:graph:abc123 \
  --investigation-id inv-abc123
```

### List available data source packages
```bash
aws detective list-datasource-packages \
  --graph-arn arn:aws:detective:us-east-1:123456789012:graph:abc123
```

### Enable Detective for an organization
```bash
aws detective enable-organization-admin-account --account-id 123456789012
aws detective update-organization-configuration \
  --graph-arn arn:aws:detective:us-east-1:123456789012:graph:abc123 \
  --auto-enable
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Graphs | [`graphs.md`](graphs.md) | create-graph, delete-graph, list-graphs |
| Members | [`members.md`](members.md) | create-members, delete-members, get-members, list-members, accept-invitation, reject-invitation, disassociate-membership, list-invitations, start-monitoring-member |
| Investigations | [`investigations.md`](investigations.md) | start-investigation, get-investigation, list-investigations, update-investigation-state, list-indicators |
| Data Sources | [`datasources.md`](datasources.md) | list-datasource-packages, update-datasource-packages, batch-get-graph-member-datasources, batch-get-membership-datasources |
| Organization & Tags | [`organization-tags.md`](organization-tags.md) | enable-organization-admin-account, disable-organization-admin-account, list-organization-admin-accounts, describe-organization-configuration, update-organization-configuration, tag-resource, untag-resource, list-tags-for-resource |
