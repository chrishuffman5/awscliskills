# AWS CLI v2 — CodeStar Connections & Notifications

## Overview

Combined reference for `aws codestar-connections` and `aws codestar-notifications` subcommands in AWS CLI v2. Covers third-party source provider connections (GitHub, Bitbucket, GitLab), hosts, repository links, sync configurations, notification rules, and notification targets.

## Quick Reference — Common Workflows

### Create a connection to GitHub
```bash
aws codestar-connections create-connection \
  --provider-type GitHub --connection-name my-github-conn
```

### List connections
```bash
aws codestar-connections list-connections \
  --provider-type-filter GitHub
```

### Create a repository link
```bash
aws codestar-connections create-repository-link \
  --connection-arn arn:aws:codestar-connections:us-east-1:123456789012:connection/abc-123 \
  --owner-id my-org --repository-name my-repo
```

### Create a sync configuration
```bash
aws codestar-connections create-sync-configuration \
  --branch main --config-file .sync-config.yaml \
  --repository-link-id abc-123 --resource-name my-resource \
  --role-arn arn:aws:iam::123456789012:role/SyncRole \
  --sync-type CFN_STACK_SYNC
```

### Create a notification rule
```bash
aws codestar-notifications create-notification-rule \
  --name my-rule --detail-type FULL \
  --resource arn:aws:codecommit:us-east-1:123456789012:my-repo \
  --event-type-ids codecommit-repository-comments-on-commits \
  --targets TargetType=SNS,TargetAddress=arn:aws:sns:us-east-1:123456789012:my-topic
```

### Subscribe a target to notifications
```bash
aws codestar-notifications subscribe \
  --arn arn:aws:codestar-notifications:us-east-1:123456789012:notificationrule/abc123 \
  --target TargetType=SNS,TargetAddress=arn:aws:sns:us-east-1:123456789012:my-topic
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Connections | [`connections.md`](connections.md) | create-connection, delete-connection, get-connection, list-connections |
| Hosts | [`hosts.md`](hosts.md) | create-host, delete-host, get-host, list-hosts, update-host |
| Repository Links | [`repository-links.md`](repository-links.md) | create-repository-link, delete-repository-link, get-repository-link, list-repository-links, update-repository-link, get-repository-sync-status, list-repository-sync-definitions |
| Sync | [`sync.md`](sync.md) | create-sync-configuration, delete-sync-configuration, get-sync-configuration, list-sync-configurations, update-sync-configuration, get-resource-sync-status, get-sync-blocker-summary, update-sync-blocker |
| Notifications | [`notifications.md`](notifications.md) | create-notification-rule, delete-notification-rule, describe-notification-rule, list-notification-rules, update-notification-rule, list-event-types |
| Notification Targets | [`notification-targets.md`](notification-targets.md) | subscribe, unsubscribe, list-targets, delete-target |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
