# AWS CLI v2 — Amazon Managed Service for Prometheus (AMP)

## Overview

Complete reference for all `aws amp` subcommands in AWS CLI v2. Covers workspace management, alert manager definitions, rule groups namespaces, scrapers, logging configuration, and resource policies for Amazon Managed Service for Prometheus.

## Quick Reference — Common Workflows

### Create a workspace
```bash
aws amp create-workspace --alias my-workspace \
  --tags Environment=production
```

### Describe and list workspaces
```bash
aws amp list-workspaces
aws amp describe-workspace --workspace-id ws-12345678-1234-1234-1234-123456789012
```

### Configure alert manager
```bash
aws amp create-alert-manager-definition \
  --workspace-id ws-12345678-1234-1234-1234-123456789012 \
  --data fileb://alertmanager.yaml
```

### Create rule groups namespace
```bash
aws amp create-rule-groups-namespace \
  --workspace-id ws-12345678-1234-1234-1234-123456789012 \
  --name my-rules --data fileb://rules.yaml
```

### Create a scraper
```bash
aws amp create-scraper --alias my-scraper \
  --source '{"eksConfiguration":{"clusterArn":"arn:aws:eks:us-east-1:123456789012:cluster/my-cluster","subnetIds":["subnet-abc123"],"securityGroupIds":["sg-abc123"]}}' \
  --destination '{"ampConfiguration":{"workspaceArn":"arn:aws:aps:us-east-1:123456789012:workspace/ws-12345"}}' \
  --scrape-configuration '{"configurationBlob":"..."}'
```

### Configure logging
```bash
aws amp create-logging-configuration \
  --workspace-id ws-12345678-1234-1234-1234-123456789012 \
  --log-group-arn arn:aws:logs:us-east-1:123456789012:log-group:/aws/amp/workspace
```

### Wait for workspace to be active
```bash
aws amp wait workspace-active \
  --workspace-id ws-12345678-1234-1234-1234-123456789012
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Workspaces | [`workspaces.md`](workspaces.md) | create-workspace, delete-workspace, describe-workspace, list-workspaces, update-workspace-alias |
| Alert Manager | [`alert-manager.md`](alert-manager.md) | create-alert-manager-definition, delete-alert-manager-definition, describe-alert-manager-definition, put-alert-manager-definition |
| Rule Groups | [`rule-groups.md`](rule-groups.md) | create-rule-groups-namespace, delete-rule-groups-namespace, describe-rule-groups-namespace, list-rule-groups-namespaces, put-rule-groups-namespace |
| Scrapers | [`scrapers.md`](scrapers.md) | create-scraper, delete-scraper, describe-scraper, list-scrapers, update-scraper, get-default-scraper-configuration |
| Logging | [`logging.md`](logging.md) | create-logging-configuration, delete-logging-configuration, describe-logging-configuration, update-logging-configuration |
| Resource Policies | [`resource-policies.md`](resource-policies.md) | describe-resource-policy, put-resource-policy, delete-resource-policy |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
| Wait | [`wait.md`](wait.md) | wait: workspace-active, workspace-deleted, scraper-active, scraper-deleted |
