# AWS CLI v2 — QLDB (Quantum Ledger Database)

> **DEPRECATION NOTICE:** Amazon QLDB reached end of support on July 31, 2025. You can no longer create new QLDB ledgers. Existing ledgers became read-only before that date, and all QLDB resources have since been deleted. For new workloads requiring immutable, cryptographically verifiable transaction logs, consider Amazon Aurora PostgreSQL with the `pgaudit` extension, Amazon Timestream, or a custom solution using Amazon DynamoDB with S3 for audit trails.

## Overview

Complete reference for all `aws qldb` and `aws qldb-session` subcommands in AWS CLI v2. Covers ledger management, journal exports to S3, journal streaming to Kinesis, block and revision verification, and the low-level session data plane.

QLDB provided a fully managed ledger database with a transparent, immutable, and cryptographically verifiable transaction log. The `aws qldb` namespace covers the control plane (management API), while `aws qldb-session` covers the data plane (transaction execution via `send-command`).

## Quick Reference — Common Workflows

### Create a ledger

```bash
aws qldb create-ledger --name my-ledger \
  --permissions-mode STANDARD \
  --deletion-protection \
  --tags Project=MyApp,Environment=prod
```

### Describe a ledger

```bash
aws qldb describe-ledger --name my-ledger
```

### List all ledgers

```bash
aws qldb list-ledgers --query 'Ledgers[].Name' --output table
```

### Update ledger (disable deletion protection)

```bash
aws qldb update-ledger --name my-ledger --no-deletion-protection
```

### Export journal to S3

```bash
aws qldb export-journal-to-s3 --name my-ledger \
  --inclusive-start-time 2024-01-01T00:00:00Z \
  --exclusive-end-time 2024-02-01T00:00:00Z \
  --s3-export-configuration '{
    "Bucket": "my-journal-exports",
    "Prefix": "qldb/my-ledger/",
    "EncryptionConfiguration": {
      "ObjectEncryptionType": "SSE_S3"
    }
  }' \
  --role-arn arn:aws:iam::123456789012:role/qldb-s3-export-role
```

### Stream journal to Kinesis

```bash
aws qldb stream-journal-to-kinesis --ledger-name my-ledger \
  --role-arn arn:aws:iam::123456789012:role/qldb-kinesis-role \
  --inclusive-start-time 2024-01-01T00:00:00Z \
  --kinesis-configuration StreamArn=arn:aws:kinesis:us-east-1:123456789012:stream/my-stream,AggregationEnabled=true \
  --stream-name my-qldb-stream
```

### Get ledger digest for verification

```bash
aws qldb get-digest --name my-ledger
```

### Cancel a Kinesis stream

```bash
aws qldb cancel-journal-kinesis-stream --ledger-name my-ledger \
  --stream-id abc123def456
```

### Tag a QLDB resource

```bash
aws qldb tag-resource \
  --resource-arn arn:aws:qldb:us-east-1:123456789012:ledger/my-ledger \
  --tags Project=MyApp,CostCenter=12345
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Ledgers | [`ledgers.md`](ledgers.md) | create-ledger, delete-ledger, describe-ledger, list-ledgers, update-ledger, update-ledger-permissions-mode |
| Journal | [`journal.md`](journal.md) | export-journal-to-s3, describe-journal-s3-export, list-journal-s3-exports, list-journal-s3-exports-for-ledger, get-block, get-digest, get-revision |
| Streams | [`streams.md`](streams.md) | stream-journal-to-kinesis, describe-journal-kinesis-stream, list-journal-kinesis-streams-for-ledger, cancel-journal-kinesis-stream |
| Tags & Session | [`tags-session.md`](tags-session.md) | tag-resource, untag-resource, list-tags-for-resource, qldb-session send-command |
