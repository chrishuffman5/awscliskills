
# AWS CLI v2 — DynamoDB (NoSQL Database)

## Overview

Complete reference for all `aws dynamodb` subcommands in AWS CLI v2. Covers table management, item CRUD operations, queries and scans, secondary indexes (GSI/LSI), DynamoDB Streams, on-demand and provisioned capacity, backups and restore, global tables, TTL, transactions, and batch operations.

## Quick Reference — Common Workflows

### Create a table
```bash
aws dynamodb create-table --table-name my-table \
  --attribute-definitions AttributeName=pk,AttributeType=S AttributeName=sk,AttributeType=S \
  --key-schema AttributeName=pk,KeyType=HASH AttributeName=sk,KeyType=RANGE \
  --billing-mode PAY_PER_REQUEST
aws dynamodb wait table-exists --table-name my-table
```

### Put and get an item
```bash
aws dynamodb put-item --table-name my-table \
  --item '{"pk":{"S":"user#123"},"sk":{"S":"profile"},"name":{"S":"Alice"}}'
aws dynamodb get-item --table-name my-table \
  --key '{"pk":{"S":"user#123"},"sk":{"S":"profile"}}'
```

### Query by partition key
```bash
aws dynamodb query --table-name my-table \
  --key-condition-expression "pk = :pk AND begins_with(sk, :prefix)" \
  --expression-attribute-values '{":pk":{"S":"user#123"},":prefix":{"S":"order#"}}'
```

### Batch write
```bash
aws dynamodb batch-write-item --request-items file://batch.json
```

### Enable TTL
```bash
aws dynamodb update-time-to-live --table-name my-table \
  --time-to-live-specification Enabled=true,AttributeName=ttl
```

## Covered Command Groups

| Group | Commands | Description |
|-------|----------|-------------|
| Tables | create, delete, describe, list, update | Table lifecycle |
| Items | put, get, update, delete | Single-item CRUD |
| Query & Scan | query, scan | Read operations |
| Batch | batch-write-item, batch-get-item | Multi-item operations |
| Transactions | transact-write-items, transact-get-items | ACID transactions |
| Indexes | update-table (GSI changes), describe-table | Secondary indexes |
| Streams | describe-stream, get-records, get-shard-iterator, list-streams | Change data capture |
| Backups | create-backup, delete-backup, describe-backup, list-backups, restore-table-from-backup | Point-in-time |
| PITR | describe/update-continuous-backups, restore-table-to-point-in-time | Continuous backups |
| Global Tables | create, describe, list, update global-table | Multi-region |
| TTL | describe/update-time-to-live | Item expiration |
| Import/Export | import-table, describe-import, list-imports, export-table-to-point-in-time, describe-export, list-exports | S3 integration |
| Tags | tag-resource, untag-resource, list-tags-of-resource | Resource tagging |

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Table Management | [`table-management.md`](table-management.md) | create-table, delete-table, describe-table, list-tables, update-table, describe-table-replica-auto-scaling, update-table-replica-auto-scaling |
| Item Operations | [`item-operations.md`](item-operations.md) | put-item, get-item, update-item, delete-item |
| Query & Scan | [`query-scan.md`](query-scan.md) | query, scan |
| Batch Operations | [`batch-operations.md`](batch-operations.md) | batch-get-item, batch-write-item |
| Transactions | [`transactions.md`](transactions.md) | transact-get-items, transact-write-items |
| PartiQL | [`partiql.md`](partiql.md) | execute-statement, batch-execute-statement, execute-transaction |
| DynamoDB Streams | [`dynamodb-streams.md`](dynamodb-streams.md) | describe-stream, get-records, get-shard-iterator, list-streams |
| Backups | [`backups.md`](backups.md) | create-backup, delete-backup, describe-backup, list-backups, restore-table-from-backup |
| Continuous Backups / PITR | [`continuous-backups-pitr.md`](continuous-backups-pitr.md) | describe-continuous-backups, update-continuous-backups, restore-table-to-point-in-time |
| Global Tables | [`global-tables.md`](global-tables.md) | create-global-table, describe-global-table, describe-global-table-settings, list-global-tables, update-global-table, update-global-table-settings |
| TTL | [`ttl.md`](ttl.md) | describe-time-to-live, update-time-to-live |
| Import / Export | [`import-export.md`](import-export.md) | import-table, describe-import, list-imports, export-table-to-point-in-time, describe-export, list-exports |
| Contributor Insights | [`contributor-insights.md`](contributor-insights.md) | describe-contributor-insights, list-contributor-insights, update-contributor-insights |
| Kinesis Streaming Destination | [`kinesis-streaming-destination.md`](kinesis-streaming-destination.md) | describe-kinesis-streaming-destination, enable-kinesis-streaming-destination, disable-kinesis-streaming-destination, update-kinesis-streaming-destination |
| Resource Policies | [`resource-policies.md`](resource-policies.md) | get-resource-policy, put-resource-policy, delete-resource-policy |
| Endpoints & Limits | [`endpoints-limits.md`](endpoints-limits.md) | describe-endpoints, describe-limits |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-of-resource |
| Wait Commands | [`wait-commands.md`](wait-commands.md) | wait table-exists, wait table-not-exists |
