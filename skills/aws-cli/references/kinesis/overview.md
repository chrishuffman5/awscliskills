# AWS CLI v2 — Kinesis (Data Streams + Data Analytics)

## Overview

Complete reference for `aws kinesis` and `aws kinesisanalyticsv2` subcommands in AWS CLI v2. Covers Kinesis Data Streams management (stream creation, shard operations, data ingestion/retrieval, enhanced fan-out consumers, encryption, monitoring) and Kinesis Data Analytics for Apache Flink (application lifecycle, input/output configuration, snapshots, VPC settings).

## Quick Reference — Common Workflows

### Create a data stream (provisioned mode)
```bash
aws kinesis create-stream --stream-name my-stream --shard-count 4
aws kinesis wait stream-exists --stream-name my-stream
```

### Create a data stream (on-demand mode)
```bash
aws kinesis create-stream --stream-name my-stream \
  --stream-mode-details StreamMode=ON_DEMAND
```

### Put a single record
```bash
aws kinesis put-record --stream-name my-stream \
  --data "Hello, Kinesis" \
  --partition-key user-123
```

### Put multiple records in a batch
```bash
aws kinesis put-records --stream-name my-stream \
  --records Data=dGVzdDE=,PartitionKey=key1 Data=dGVzdDI=,PartitionKey=key2
```

### Read records from a shard
```bash
SHARD_ITERATOR=$(aws kinesis get-shard-iterator \
  --stream-name my-stream \
  --shard-id shardId-000000000000 \
  --shard-iterator-type TRIM_HORIZON \
  --query 'ShardIterator' --output text)

aws kinesis get-records --shard-iterator "$SHARD_ITERATOR" --limit 100
```

### Register an enhanced fan-out consumer
```bash
aws kinesis register-stream-consumer \
  --stream-arn arn:aws:kinesis:us-east-1:123456789012:stream/my-stream \
  --consumer-name my-consumer
```

### Enable server-side encryption
```bash
aws kinesis start-stream-encryption \
  --stream-name my-stream \
  --encryption-type KMS \
  --key-id alias/aws/kinesis
```

### Enable enhanced monitoring
```bash
aws kinesis enable-enhanced-monitoring \
  --stream-name my-stream \
  --shard-level-metrics ALL
```

### Scale a provisioned stream
```bash
aws kinesis update-shard-count --stream-name my-stream \
  --target-shard-count 8 \
  --scaling-type UNIFORM_SCALING
```

### Create a Flink analytics application
```bash
aws kinesisanalyticsv2 create-application \
  --application-name my-flink-app \
  --runtime-environment FLINK-1_20 \
  --service-execution-role arn:aws:iam::123456789012:role/flink-role \
  --application-mode STREAMING
```

### Start / stop a Flink application
```bash
aws kinesisanalyticsv2 start-application --application-name my-flink-app

aws kinesisanalyticsv2 stop-application --application-name my-flink-app
```

### Add input source to analytics application
```bash
aws kinesisanalyticsv2 add-application-input \
  --application-name my-flink-app \
  --current-application-version-id 1 \
  --input '{"NamePrefix":"SOURCE_SQL_STREAM","KinesisStreamsInput":{"ResourceARN":"arn:aws:kinesis:us-east-1:123456789012:stream/my-stream"},"InputSchema":{"RecordFormat":{"RecordFormatType":"JSON"},"RecordColumns":[{"Name":"col1","SqlType":"VARCHAR(64)","Mapping":"$.col1"}]}}'
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Streams | [`streams.md`](streams.md) | create-stream, delete-stream, describe-stream, describe-stream-summary, list-streams, update-stream-mode, increase-stream-retention-period, decrease-stream-retention-period, update-stream-warm-throughput, update-max-record-size |
| Shards & Records | [`shards-records.md`](shards-records.md) | list-shards, split-shard, merge-shards, update-shard-count, get-shard-iterator, get-records, put-record, put-records |
| Consumers | [`consumers.md`](consumers.md) | register-stream-consumer, deregister-stream-consumer, describe-stream-consumer, list-stream-consumers |
| Monitoring | [`monitoring.md`](monitoring.md) | enable-enhanced-monitoring, disable-enhanced-monitoring, start-stream-encryption, stop-stream-encryption |
| Tags & Policies | [`tags-policies.md`](tags-policies.md) | add-tags-to-stream, remove-tags-from-stream, list-tags-for-stream, tag-resource, untag-resource, list-tags-for-resource, put-resource-policy, get-resource-policy, delete-resource-policy, describe-limits, describe-account-settings, update-account-settings |
| Analytics Applications | [`analytics-applications.md`](analytics-applications.md) | create-application, delete-application, describe-application, list-applications, update-application, start-application, stop-application, rollback-application, describe-application-version, list-application-versions, describe-application-operation, list-application-operations |
| Analytics I/O | [`analytics-io.md`](analytics-io.md) | add-application-input, add-application-output, delete-application-output, add-application-input-processing-configuration, delete-application-input-processing-configuration, discover-input-schema, add-application-reference-data-source, delete-application-reference-data-source, add-application-vpc-configuration, delete-application-vpc-configuration |
| Analytics Config | [`analytics-config.md`](analytics-config.md) | add-application-cloud-watch-logging-option, delete-application-cloud-watch-logging-option, create-application-snapshot, delete-application-snapshot, describe-application-snapshot, list-application-snapshots, create-application-presigned-url, update-application-maintenance-configuration, tag-resource, untag-resource, list-tags-for-resource |
| Wait | [`wait.md`](wait.md) | wait stream-exists, wait stream-not-exists |
