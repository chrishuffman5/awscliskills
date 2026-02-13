# AWS CLI v2 — FinSpace

## Overview

Complete reference for all `aws finspace` subcommands in AWS CLI v2. Covers FinSpace environment management, KX (kdb+) environments, clusters, databases, dataviews, changesets, scaling groups, volumes, and user management.

Amazon FinSpace is a data management and analytics service purpose-built for the financial services industry. It provides managed kdb+ environments (branded as "Managed kdb Insights") for high-performance analytics on time-series and relational data. The service includes both legacy FinSpace environments and the newer KX-based architecture.

## Quick Reference — Common Workflows

### Create a KX environment

```bash
aws finspace create-kx-environment \
  --name my-kx-env \
  --kms-key-id arn:aws:kms:us-east-1:123456789012:key/my-key-id
```

### Create a KX database

```bash
aws finspace create-kx-database \
  --environment-id env-abc123 \
  --database-name mydb \
  --description "Trading data database"
```

### Create a changeset (load data into a database)

```bash
aws finspace create-kx-changeset \
  --environment-id env-abc123 \
  --database-name mydb \
  --change-requests '[{"changeType":"PUT","s3Path":"s3://my-bucket/data/","dbPath":"/"}]'
```

### Create a KX cluster

```bash
aws finspace create-kx-cluster \
  --environment-id env-abc123 \
  --cluster-name my-cluster \
  --cluster-type HDB \
  --release-label 1.0 \
  --az-mode SINGLE \
  --availability-zone-id use1-az1 \
  --capacity-configuration '{"nodeType":"kx.s.xlarge","nodeCount":2}' \
  --databases '[{"databaseName":"mydb","cacheConfigurations":[{"cacheType":"CACHE_1000","dbPaths":["/"]}]}]'
```

### Create a dataview

```bash
aws finspace create-kx-dataview \
  --environment-id env-abc123 \
  --database-name mydb \
  --dataview-name my-dataview \
  --az-mode SINGLE \
  --availability-zone-id use1-az1 \
  --segment-configurations '[{"dbPaths":["/"],"volumeName":"my-volume"}]'
```

### List KX clusters

```bash
aws finspace list-kx-clusters \
  --environment-id env-abc123 \
  --query 'kxClusterSummaries[].{Name:clusterName,Type:clusterType,Status:status}'
```

### Create a KX user

```bash
aws finspace create-kx-user \
  --environment-id env-abc123 \
  --user-name analyst1 \
  --iam-role arn:aws:iam::123456789012:role/FinSpaceUserRole
```

### Create a scaling group

```bash
aws finspace create-kx-scaling-group \
  --environment-id env-abc123 \
  --scaling-group-name my-scaling-group \
  --host-type kx.sg.large \
  --availability-zone-id use1-az1
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Environments | [`environments.md`](environments.md) | create-environment, delete-environment, get-environment, list-environments, update-environment, create-kx-environment, delete-kx-environment, get-kx-environment, list-kx-environments, update-kx-environment, update-kx-environment-network |
| Databases | [`databases.md`](databases.md) | create-kx-database, delete-kx-database, get-kx-database, list-kx-databases, update-kx-database |
| Clusters | [`clusters.md`](clusters.md) | create-kx-cluster, delete-kx-cluster, get-kx-cluster, list-kx-clusters, update-kx-cluster-code-configuration, update-kx-cluster-databases, delete-kx-cluster-node, list-kx-cluster-nodes, get-kx-connection-string |
| Dataviews | [`dataviews.md`](dataviews.md) | create-kx-dataview, delete-kx-dataview, get-kx-dataview, list-kx-dataviews, update-kx-dataview |
| Changesets | [`changesets.md`](changesets.md) | create-kx-changeset, get-kx-changeset, list-kx-changesets |
| Scaling Groups | [`scaling-groups.md`](scaling-groups.md) | create-kx-scaling-group, delete-kx-scaling-group, get-kx-scaling-group, list-kx-scaling-groups |
| Volumes | [`volumes.md`](volumes.md) | create-kx-volume, delete-kx-volume, get-kx-volume, list-kx-volumes, update-kx-volume |
| Users & Tags | [`users-tags.md`](users-tags.md) | create-kx-user, delete-kx-user, get-kx-user, list-kx-users, update-kx-user, tag-resource, untag-resource, list-tags-for-resource |
