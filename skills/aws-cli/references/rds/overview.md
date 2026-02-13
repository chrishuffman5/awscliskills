
# AWS CLI v2 — RDS (Relational Database Service)

## Overview

Complete reference for all `aws rds` subcommands in AWS CLI v2. Covers DB instance lifecycle, Aurora clusters, snapshots, parameter groups, subnet groups, read replicas, automated backups, security, monitoring, and event subscriptions.

## Quick Reference — Common Workflows

### Create a DB instance
```bash
aws rds create-db-instance --db-instance-identifier my-db \
  --db-instance-class db.t3.medium --engine postgres \
  --master-username admin --master-user-password secret \
  --allocated-storage 20 --vpc-security-group-ids sg-xxx \
  --db-subnet-group-name my-subnet-group
```

### Create an Aurora cluster
```bash
aws rds create-db-cluster --db-cluster-identifier my-aurora \
  --engine aurora-postgresql --master-username admin \
  --master-user-password secret --vpc-security-group-ids sg-xxx \
  --db-subnet-group-name my-subnet-group
aws rds create-db-instance --db-instance-identifier my-aurora-instance-1 \
  --db-cluster-identifier my-aurora --db-instance-class db.r6g.large \
  --engine aurora-postgresql
```

### Take a snapshot
```bash
aws rds create-db-snapshot --db-instance-identifier my-db --db-snapshot-identifier my-snap
aws rds wait db-snapshot-available --db-snapshot-identifier my-snap
```

### Create read replica
```bash
aws rds create-db-instance-read-replica --db-instance-identifier my-replica \
  --source-db-instance-identifier my-db --db-instance-class db.t3.medium
```

### Modify instance (apply immediately)
```bash
aws rds modify-db-instance --db-instance-identifier my-db \
  --db-instance-class db.t3.large --apply-immediately
aws rds wait db-instance-available --db-instance-identifier my-db
```

## Covered Command Groups

| Group | Commands | Description |
|-------|----------|-------------|
| DB Instances | create, delete, describe, modify, reboot, start, stop | Instance lifecycle |
| DB Clusters | create, delete, describe, modify, failover, start, stop | Aurora clusters |
| Snapshots | create, delete, describe, copy, restore, share | Instance & cluster snapshots |
| Parameter Groups | create, delete, describe, modify, reset | Engine configuration |
| Subnet Groups | create, delete, describe, modify | VPC networking |
| Option Groups | create, delete, describe, modify, copy | Engine-specific features |
| Event Subscriptions | create, delete, describe, modify | SNS notifications |
| Automated Backups | describe, delete, start/stop replication | Backup management |
| Proxies | create, delete, describe, modify | RDS Proxy |

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| DB Instances | [`db-instances.md`](db-instances.md) | create-db-instance, delete-db-instance, describe-db-instances, modify-db-instance, reboot-db-instance, start-db-instance, stop-db-instance, create-db-instance-read-replica, promote-read-replica |
| DB Clusters (Aurora) | [`db-clusters.md`](db-clusters.md) | create-db-cluster, delete-db-cluster, describe-db-clusters, modify-db-cluster, failover-db-cluster, start-db-cluster, stop-db-cluster, create-db-cluster-endpoint, describe-db-cluster-endpoints, modify-db-cluster-endpoint, delete-db-cluster-endpoint |
| Snapshots | [`snapshots.md`](snapshots.md) | create-db-snapshot, delete-db-snapshot, describe-db-snapshots, copy-db-snapshot, restore-db-instance-from-db-snapshot, modify-db-snapshot, create-db-cluster-snapshot, delete-db-cluster-snapshot, describe-db-cluster-snapshots, copy-db-cluster-snapshot, restore-db-cluster-from-snapshot |
| Parameter Groups | [`parameter-groups.md`](parameter-groups.md) | create-db-parameter-group, delete-db-parameter-group, describe-db-parameter-groups, describe-db-parameters, modify-db-parameter-group, reset-db-parameter-group, create-db-cluster-parameter-group, delete-db-cluster-parameter-group, describe-db-cluster-parameter-groups, describe-db-cluster-parameters, modify-db-cluster-parameter-group, reset-db-cluster-parameter-group |
| Subnet Groups | [`subnet-groups.md`](subnet-groups.md) | create-db-subnet-group, delete-db-subnet-group, describe-db-subnet-groups, modify-db-subnet-group |
| Option Groups | [`option-groups.md`](option-groups.md) | create-option-group, delete-option-group, describe-option-groups, describe-option-group-options, modify-option-group, copy-option-group |
| Event Subscriptions | [`event-subscriptions.md`](event-subscriptions.md) | create-event-subscription, delete-event-subscription, describe-event-subscriptions, modify-event-subscription, describe-events, describe-event-categories |
| Automated Backups | [`automated-backups.md`](automated-backups.md) | describe-db-instance-automated-backups, delete-db-instance-automated-backup, start-db-instance-automated-backups-replication, stop-db-instance-automated-backups-replication |
| RDS Proxy | [`rds-proxy.md`](rds-proxy.md) | create-db-proxy, delete-db-proxy, describe-db-proxies, modify-db-proxy, register-db-proxy-targets, deregister-db-proxy-targets, describe-db-proxy-targets, describe-db-proxy-target-groups |
| Tags | [`tags.md`](tags.md) | add-tags-to-resource, remove-tags-from-resource, list-tags-for-resource |
| Maintenance & Engine Info | [`maintenance-engine-info.md`](maintenance-engine-info.md) | describe-pending-maintenance-actions, apply-pending-maintenance-action, describe-db-engine-versions, describe-orderable-db-instance-options, describe-certificates |
