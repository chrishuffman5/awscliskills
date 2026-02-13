# AWS CLI v2 — ElastiCache

## Overview

Complete reference for all `aws elasticache` subcommands in AWS CLI v2. Covers cache cluster management, replication groups (Redis/Valkey), parameter groups, subnet groups, snapshots, users and user groups, serverless caches, global replication groups, service updates, and tagging.

## Quick Reference — Common Workflows

### Create a Redis replication group with cluster mode
```bash
aws elasticache create-replication-group \
  --replication-group-id my-redis \
  --replication-group-description "My Redis cluster" \
  --engine redis --engine-version 7.1 \
  --cache-node-type cache.r7g.large \
  --num-node-groups 2 --replicas-per-node-group 1 \
  --cache-subnet-group-name my-subnet-group \
  --security-group-ids sg-12345678 \
  --at-rest-encryption-enabled --transit-encryption-enabled
```

### Create a Memcached cluster
```bash
aws elasticache create-cache-cluster \
  --cache-cluster-id my-memcached \
  --engine memcached --engine-version 1.6.22 \
  --cache-node-type cache.r7g.large \
  --num-cache-nodes 3 \
  --cache-subnet-group-name my-subnet-group \
  --security-group-ids sg-12345678
```

### Create a subnet group
```bash
aws elasticache create-cache-subnet-group \
  --cache-subnet-group-name my-subnet-group \
  --cache-subnet-group-description "My subnet group" \
  --subnet-ids subnet-111 subnet-222 subnet-333
```

### Create a snapshot (backup)
```bash
aws elasticache create-snapshot --replication-group-id my-redis \
  --snapshot-name my-redis-backup
```

### Scale out (add shards)
```bash
aws elasticache modify-replication-group-shard-configuration \
  --replication-group-id my-redis \
  --node-group-count 4 --apply-immediately
```

### Create a serverless cache
```bash
aws elasticache create-serverless-cache \
  --serverless-cache-name my-serverless \
  --engine redis \
  --cache-usage-limits "DataStorage={Maximum=10,Unit=GB},ECPUPerSecond={Maximum=5000}" \
  --subnet-ids subnet-111 subnet-222 \
  --security-group-ids sg-12345678
```

### Failover a replication group
```bash
aws elasticache test-failover --replication-group-id my-redis \
  --node-group-id 0001
```

### Apply service updates
```bash
aws elasticache batch-apply-update-action \
  --replication-group-ids my-redis \
  --service-update-name elc-xxxxx
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Clusters | [`clusters.md`](clusters.md) | create-cache-cluster, delete-cache-cluster, describe-cache-clusters, modify-cache-cluster, reboot-cache-cluster |
| Replication Groups | [`replication-groups.md`](replication-groups.md) | create-replication-group, delete-replication-group, describe-replication-groups, modify-replication-group, modify-replication-group-shard-configuration, increase-replica-count, decrease-replica-count, test-failover, start-migration, complete-migration |
| Parameter Groups | [`parameter-groups.md`](parameter-groups.md) | create-cache-parameter-group, delete-cache-parameter-group, describe-cache-parameter-groups, describe-cache-parameters, modify-cache-parameter-group, reset-cache-parameter-group, describe-engine-default-parameters |
| Subnet Groups | [`subnet-groups.md`](subnet-groups.md) | create-cache-subnet-group, delete-cache-subnet-group, describe-cache-subnet-groups, modify-cache-subnet-group |
| Snapshots | [`snapshots.md`](snapshots.md) | create-snapshot, delete-snapshot, describe-snapshots, copy-snapshot, export-serverless-cache-snapshot |
| Users | [`users.md`](users.md) | create-user, delete-user, describe-users, modify-user, create-user-group, delete-user-group, describe-user-groups, modify-user-group |
| Serverless | [`serverless.md`](serverless.md) | create-serverless-cache, delete-serverless-cache, describe-serverless-caches, modify-serverless-cache, create-serverless-cache-snapshot, delete-serverless-cache-snapshot, describe-serverless-cache-snapshots |
| Global Replication | [`global-replication.md`](global-replication.md) | create-global-replication-group, delete-global-replication-group, describe-global-replication-groups, modify-global-replication-group, failover-global-replication-group, increase-node-groups-in-global-replication-group, decrease-node-groups-in-global-replication-group, disassociate-global-replication-group, rebalance-slots-in-global-replication-group |
| Service Updates | [`service-updates.md`](service-updates.md) | describe-service-updates, describe-update-actions, batch-apply-update-action, batch-stop-update-action |
| Tags | [`tags.md`](tags.md) | add-tags-to-resource, remove-tags-from-resource, list-tags-for-resource |
