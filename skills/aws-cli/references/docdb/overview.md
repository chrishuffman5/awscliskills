# AWS CLI v2 — DocumentDB (Amazon DocumentDB with MongoDB Compatibility)

## Overview

Complete reference for all `aws docdb` and `aws docdb-elastic` subcommands in AWS CLI v2. Covers cluster management, instance management, snapshots, parameter groups, subnet groups, global clusters, event subscriptions, tagging, and DocumentDB Elastic Clusters.

Amazon DocumentDB is a fully managed, MongoDB-compatible document database service. The `aws docdb` namespace covers instance-based (provisioned) clusters, while `aws docdb-elastic` covers elastic clusters that automatically scale storage and compute.

## Quick Reference — Common Workflows

### Create a cluster

```bash
aws docdb create-db-cluster \
  --db-cluster-identifier my-docdb-cluster \
  --engine docdb \
  --master-username admin \
  --master-user-password 'MySecurePass123!' \
  --db-subnet-group-name my-subnet-group \
  --vpc-security-group-ids sg-0123456789abcdef0
```

### Create an instance in the cluster

```bash
aws docdb create-db-instance \
  --db-instance-identifier my-docdb-instance-1 \
  --db-instance-class db.r6g.large \
  --db-cluster-identifier my-docdb-cluster \
  --engine docdb
```

### Describe clusters

```bash
aws docdb describe-db-clusters \
  --db-cluster-identifier my-docdb-cluster \
  --query 'DBClusters[0].{Status:Status,Endpoint:Endpoint,Reader:ReaderEndpoint}'
```

### Create a cluster snapshot

```bash
aws docdb create-db-cluster-snapshot \
  --db-cluster-identifier my-docdb-cluster \
  --db-cluster-snapshot-identifier my-snapshot
```

### Restore cluster from snapshot

```bash
aws docdb restore-db-cluster-from-snapshot \
  --db-cluster-identifier my-restored-cluster \
  --snapshot-identifier my-snapshot \
  --engine docdb \
  --db-subnet-group-name my-subnet-group
```

### Create an elastic cluster

```bash
aws docdb-elastic create-cluster \
  --cluster-name my-elastic-cluster \
  --auth-type PLAIN_TEXT \
  --admin-user-name admin \
  --admin-user-password 'MySecurePass123!' \
  --shard-capacity 8 \
  --shard-count 2
```

### Create a global cluster

```bash
aws docdb create-global-cluster \
  --global-cluster-identifier my-global-cluster \
  --source-db-cluster-identifier arn:aws:rds:us-east-1:123456789012:cluster:my-docdb-cluster
```

### Stop and start a cluster

```bash
aws docdb stop-db-cluster --db-cluster-identifier my-docdb-cluster
aws docdb start-db-cluster --db-cluster-identifier my-docdb-cluster
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Clusters | [`clusters.md`](clusters.md) | create-db-cluster, delete-db-cluster, describe-db-clusters, modify-db-cluster, start-db-cluster, stop-db-cluster, failover-db-cluster |
| Instances | [`instances.md`](instances.md) | create-db-instance, delete-db-instance, describe-db-instances, modify-db-instance, reboot-db-instance |
| Snapshots | [`snapshots.md`](snapshots.md) | create-db-cluster-snapshot, delete-db-cluster-snapshot, describe-db-cluster-snapshots, describe-db-cluster-snapshot-attributes, modify-db-cluster-snapshot-attribute, copy-db-cluster-snapshot, restore-db-cluster-from-snapshot, restore-db-cluster-to-point-in-time |
| Parameter Groups | [`parameter-groups.md`](parameter-groups.md) | create-db-cluster-parameter-group, delete-db-cluster-parameter-group, describe-db-cluster-parameter-groups, describe-db-cluster-parameters, modify-db-cluster-parameter-group, reset-db-cluster-parameter-group, copy-db-cluster-parameter-group |
| Subnet Groups | [`subnet-groups.md`](subnet-groups.md) | create-db-subnet-group, delete-db-subnet-group, describe-db-subnet-groups, modify-db-subnet-group |
| Global Clusters | [`global-clusters.md`](global-clusters.md) | create-global-cluster, delete-global-cluster, describe-global-clusters, modify-global-cluster, remove-from-global-cluster, failover-global-cluster, switchover-global-cluster |
| Events & Tags | [`events-tags.md`](events-tags.md) | describe-events, describe-event-categories, create-event-subscription, delete-event-subscription, describe-event-subscriptions, modify-event-subscription, add-source-identifier-to-subscription, remove-source-identifier-from-subscription, add-tags-to-resource, remove-tags-from-resource, list-tags-for-resource, apply-pending-maintenance-action, describe-pending-maintenance-actions, describe-certificates, describe-db-engine-versions, describe-orderable-db-instance-options |
| Elastic Clusters | [`elastic-clusters.md`](elastic-clusters.md) | create-cluster, delete-cluster, get-cluster, list-clusters, update-cluster, start-cluster, stop-cluster, restore-cluster-from-snapshot |
| Elastic Snapshots | [`elastic-snapshots.md`](elastic-snapshots.md) | create-cluster-snapshot, delete-cluster-snapshot, get-cluster-snapshot, list-cluster-snapshots, copy-cluster-snapshot |
| Elastic Maintenance & Tags | [`elastic-maintenance-tags.md`](elastic-maintenance-tags.md) | apply-pending-maintenance-action, get-pending-maintenance-action, list-pending-maintenance-actions, tag-resource, untag-resource, list-tags-for-resource |
| Wait | [`wait.md`](wait.md) | wait db-instance-available, wait db-instance-deleted |
