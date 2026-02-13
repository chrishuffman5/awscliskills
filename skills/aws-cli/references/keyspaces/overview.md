# AWS CLI v2 — Amazon Keyspaces (for Apache Cassandra)

## Overview

Complete reference for `aws keyspaces` subcommands in AWS CLI v2. Amazon Keyspaces is a scalable, highly available, and managed Apache Cassandra-compatible database service. Covers keyspace management, table creation and configuration, custom types, point-in-time recovery, auto-scaling, encryption, CDC, and resource tagging.

## Quick Reference — Common Workflows

### Create a keyspace
```bash
aws keyspaces create-keyspace --keyspace-name my_keyspace
```

### Create a multi-region keyspace
```bash
aws keyspaces create-keyspace \
  --keyspace-name my_global_keyspace \
  --replication-specification replicationStrategy=MULTI_REGION,regionList=us-east-1,eu-west-1
```

### Create a table with schema
```bash
aws keyspaces create-table \
  --keyspace-name my_keyspace \
  --table-name users \
  --schema-definition '{
    "allColumns": [
      {"name":"user_id","type":"uuid"},
      {"name":"email","type":"text"},
      {"name":"created_at","type":"timestamp"},
      {"name":"status","type":"text"}
    ],
    "partitionKeys": [{"name":"user_id"}],
    "clusteringKeys": [{"name":"created_at","orderBy":"DESC"}]
  }'
```

### Create a provisioned table with auto-scaling
```bash
aws keyspaces create-table \
  --keyspace-name my_keyspace \
  --table-name events \
  --schema-definition file://schema.json \
  --capacity-specification throughputMode=PROVISIONED,readCapacityUnits=100,writeCapacityUnits=100 \
  --auto-scaling-specification file://autoscaling.json
```

### Enable point-in-time recovery
```bash
aws keyspaces update-table \
  --keyspace-name my_keyspace \
  --table-name users \
  --point-in-time-recovery status=ENABLED
```

### Restore a table to a point in time
```bash
aws keyspaces restore-table \
  --source-keyspace-name my_keyspace \
  --source-table-name users \
  --target-keyspace-name my_keyspace \
  --target-table-name users_restored \
  --restore-timestamp 2026-01-15T12:00:00Z
```

### Enable TTL on a table
```bash
aws keyspaces update-table \
  --keyspace-name my_keyspace \
  --table-name sessions \
  --ttl status=ENABLED \
  --default-time-to-live 86400
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Keyspaces | [`keyspaces.md`](keyspaces.md) | create-keyspace, delete-keyspace, get-keyspace, list-keyspaces, update-keyspace |
| Tables | [`tables.md`](tables.md) | create-table, delete-table, get-table, list-tables, update-table, restore-table, get-table-auto-scaling-settings |
| Types & Tags | [`types-tags.md`](types-tags.md) | create-type, delete-type, get-type, list-types, tag-resource, untag-resource, list-tags-for-resource |
