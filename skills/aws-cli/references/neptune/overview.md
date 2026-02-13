# AWS CLI v2 — Neptune (Database + Analytics Graph)

## Overview

Complete reference for `aws neptune` and `aws neptune-graph` subcommands in AWS CLI v2. Covers Neptune Database (provisioned and serverless graph database clusters, instances, endpoints, snapshots, parameter groups, subnet groups, global clusters, events) and Neptune Analytics (graph creation, snapshots, import/export, queries, private endpoints).

## Quick Reference — Common Workflows

### Create a Neptune DB cluster
```bash
aws neptune create-db-cluster \
  --db-cluster-identifier my-cluster \
  --engine neptune \
  --engine-version 1.3.1.0 \
  --storage-encrypted \
  --deletion-protection \
  --backup-retention-period 7 \
  --vpc-security-group-ids sg-12345678 \
  --db-subnet-group-name my-subnet-group
```

### Create a Neptune DB instance
```bash
aws neptune create-db-instance \
  --db-instance-identifier my-instance \
  --db-cluster-identifier my-cluster \
  --db-instance-class db.r6g.large \
  --engine neptune

aws neptune wait db-instance-available \
  --db-instance-identifier my-instance
```

### Create a serverless cluster
```bash
aws neptune create-db-cluster \
  --db-cluster-identifier my-serverless-cluster \
  --engine neptune \
  --serverless-v2-scaling-configuration MinCapacity=1.0,MaxCapacity=128.0

aws neptune create-db-instance \
  --db-instance-identifier my-serverless-instance \
  --db-cluster-identifier my-serverless-cluster \
  --db-instance-class db.serverless \
  --engine neptune
```

### Create a cluster snapshot
```bash
aws neptune create-db-cluster-snapshot \
  --db-cluster-identifier my-cluster \
  --db-cluster-snapshot-identifier my-snapshot
```

### Restore from snapshot
```bash
aws neptune restore-db-cluster-from-snapshot \
  --db-cluster-identifier restored-cluster \
  --snapshot-identifier my-snapshot \
  --engine neptune
```

### Create a Neptune Analytics graph
```bash
aws neptune-graph create-graph \
  --graph-name my-graph \
  --provisioned-memory 128 \
  --public-connectivity \
  --replica-count 1

aws neptune-graph wait graph-available --graph-identifier g-abc1234567
```

### Import data into a graph
```bash
aws neptune-graph start-import-task \
  --graph-identifier g-abc1234567 \
  --source s3://my-bucket/data/ \
  --role-arn arn:aws:iam::123456789012:role/neptune-graph-role \
  --format CSV
```

### Execute a query on a graph
```bash
aws neptune-graph execute-query \
  --graph-identifier g-abc1234567 \
  --query-string "MATCH (n) RETURN n LIMIT 10" \
  --language OPEN_CYPHER \
  output.json
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Clusters | [`clusters.md`](clusters.md) | create-db-cluster, modify-db-cluster, delete-db-cluster, describe-db-clusters, start-db-cluster, stop-db-cluster, failover-db-cluster, promote-read-replica-db-cluster, add-role-to-db-cluster, remove-role-from-db-cluster |
| Instances | [`instances.md`](instances.md) | create-db-instance, modify-db-instance, delete-db-instance, describe-db-instances, reboot-db-instance, describe-orderable-db-instance-options, describe-valid-db-instance-modifications, describe-db-engine-versions |
| Cluster Endpoints | [`cluster-endpoints.md`](cluster-endpoints.md) | create-db-cluster-endpoint, modify-db-cluster-endpoint, delete-db-cluster-endpoint, describe-db-cluster-endpoints |
| Snapshots | [`snapshots.md`](snapshots.md) | create-db-cluster-snapshot, copy-db-cluster-snapshot, delete-db-cluster-snapshot, describe-db-cluster-snapshots, describe-db-cluster-snapshot-attributes, modify-db-cluster-snapshot-attribute, restore-db-cluster-from-snapshot, restore-db-cluster-to-point-in-time |
| Parameter Groups | [`parameter-groups.md`](parameter-groups.md) | create-db-cluster-parameter-group, modify-db-cluster-parameter-group, delete-db-cluster-parameter-group, describe-db-cluster-parameter-groups, describe-db-cluster-parameters, reset-db-cluster-parameter-group, describe-engine-default-cluster-parameters, create-db-parameter-group, modify-db-parameter-group, delete-db-parameter-group, describe-db-parameter-groups, describe-db-parameters, reset-db-parameter-group, describe-engine-default-parameters |
| Subnet Groups | [`subnet-groups.md`](subnet-groups.md) | create-db-subnet-group, modify-db-subnet-group, delete-db-subnet-group, describe-db-subnet-groups |
| Global Clusters | [`global-clusters.md`](global-clusters.md) | create-global-cluster, modify-global-cluster, delete-global-cluster, describe-global-clusters, failover-global-cluster, switchover-global-cluster, remove-from-global-cluster |
| Events & Tags | [`events-tags.md`](events-tags.md) | create-event-subscription, modify-event-subscription, delete-event-subscription, describe-event-subscriptions, describe-events, describe-event-categories, add-source-identifier-to-subscription, remove-source-identifier-from-subscription, add-tags-to-resource, remove-tags-from-resource, list-tags-for-resource, apply-pending-maintenance-action, describe-pending-maintenance-actions |
| Graph | [`graph.md`](graph.md) | create-graph, delete-graph, get-graph, list-graphs, update-graph, reset-graph, start-graph, stop-graph, get-graph-summary |
| Graph Snapshots | [`graph-snapshots.md`](graph-snapshots.md) | create-graph-snapshot, delete-graph-snapshot, get-graph-snapshot, list-graph-snapshots, restore-graph-from-snapshot |
| Graph Import/Export | [`graph-import-export.md`](graph-import-export.md) | start-import-task, cancel-import-task, get-import-task, list-import-tasks, start-export-task, cancel-export-task, get-export-task, list-export-tasks |
| Graph Endpoints | [`graph-endpoints.md`](graph-endpoints.md) | create-private-graph-endpoint, delete-private-graph-endpoint, get-private-graph-endpoint, list-private-graph-endpoints |
| Graph Queries & Tags | [`graph-queries-tags.md`](graph-queries-tags.md) | execute-query, cancel-query, get-query, list-queries, tag-resource, untag-resource, list-tags-for-resource |
| Wait | [`wait.md`](wait.md) | wait db-instance-available, wait db-instance-deleted, wait graph-available, wait graph-deleted, wait graph-snapshot-available, wait graph-snapshot-deleted, wait graph-stopped, wait import-task-successful, wait import-task-cancelled, wait export-task-successful, wait export-task-cancelled, wait private-graph-endpoint-available, wait private-graph-endpoint-deleted |
