# AWS CLI v2 — DRS (Elastic Disaster Recovery)

## Overview

Complete reference for all `aws drs` subcommands in AWS CLI v2. Covers source server management, recovery instances, replication configuration, launch configuration, recovery operations (failover, failback, reverse replication), source networks, jobs, and tagging.

## Quick Reference — Common Workflows

### Initialize the DRS service
```bash
aws drs initialize-service
```

### Describe source servers
```bash
aws drs describe-source-servers \
  --filters '{"sourceServerIDs":["s-1234567890abcdef0"]}'
```

### Start replication for a source server
```bash
aws drs start-replication --source-server-id s-1234567890abcdef0
```

### Start a recovery (failover)
```bash
aws drs start-recovery \
  --source-servers sourceServerID=s-1234567890abcdef0
```

### Describe recovery instances
```bash
aws drs describe-recovery-instances \
  --filters '{"recoveryInstanceIDs":["i-0123456789abcdef0"]}'
```

### Start failback
```bash
aws drs start-failback-launch \
  --recovery-instance-ids i-0123456789abcdef0
```

### Reverse replication after failback
```bash
aws drs reverse-replication --recovery-instance-id i-0123456789abcdef0
```

### Describe jobs
```bash
aws drs describe-jobs --filters '{"jobIDs":["drs-job-1234567890abcdef0"]}'
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Source Servers | [`source-servers.md`](source-servers.md) | describe-source-servers, delete-source-server, disconnect-source-server, create-extended-source-server, list-extensible-source-servers, start-replication, stop-replication |
| Recovery Instances | [`recovery-instances.md`](recovery-instances.md) | describe-recovery-instances, delete-recovery-instance, disconnect-recovery-instance, terminate-recovery-instances, describe-recovery-snapshots |
| Replication Config | [`replication-config.md`](replication-config.md) | create-replication-configuration-template, delete-replication-configuration-template, describe-replication-configuration-templates, update-replication-configuration-template, get-replication-configuration, update-replication-configuration |
| Launch Config | [`launch-config.md`](launch-config.md) | create-launch-configuration-template, delete-launch-configuration-template, describe-launch-configuration-templates, update-launch-configuration-template, get-launch-configuration, update-launch-configuration, put-launch-action, delete-launch-action, list-launch-actions |
| Recovery Operations | [`recovery-operations.md`](recovery-operations.md) | start-recovery, start-failback-launch, stop-failback, reverse-replication, get-failback-replication-configuration, update-failback-replication-configuration, initialize-service |
| Source Networks | [`source-networks.md`](source-networks.md) | create-source-network, delete-source-network, describe-source-networks, start-source-network-recovery, start-source-network-replication, stop-source-network-replication, associate-source-network-stack, export-source-network-cfn-template |
| Jobs | [`jobs.md`](jobs.md) | describe-jobs, delete-job, describe-job-log-items, list-staging-accounts |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
