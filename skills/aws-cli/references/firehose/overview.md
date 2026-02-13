# AWS CLI v2 — Firehose (Amazon Data Firehose)

## Overview

Complete reference for `aws firehose` subcommands in AWS CLI v2. Amazon Data Firehose (formerly Kinesis Data Firehose) is a fully managed service for delivering real-time streaming data to destinations including Amazon S3, Amazon Redshift, Amazon OpenSearch Service, Splunk, Snowflake, HTTP endpoints, and Apache Iceberg tables.

## Quick Reference — Common Workflows

### Create a delivery stream to S3
```bash
aws firehose create-delivery-stream \
  --delivery-stream-name my-stream \
  --extended-s3-destination-configuration '{
    "RoleARN": "arn:aws:iam::123456789012:role/firehose-role",
    "BucketARN": "arn:aws:s3:::my-bucket",
    "Prefix": "data/year=!{timestamp:yyyy}/month=!{timestamp:MM}/",
    "BufferingHints": {"SizeInMBs": 128, "IntervalInSeconds": 60},
    "CompressionFormat": "GZIP"
  }'
```

### Create a delivery stream from Kinesis to S3
```bash
aws firehose create-delivery-stream \
  --delivery-stream-name my-stream \
  --delivery-stream-type KinesisStreamAsSource \
  --kinesis-stream-source-configuration '{
    "KinesisStreamARN": "arn:aws:kinesis:us-east-1:123456789012:stream/my-kinesis-stream",
    "RoleARN": "arn:aws:iam::123456789012:role/firehose-role"
  }' \
  --extended-s3-destination-configuration '{
    "RoleARN": "arn:aws:iam::123456789012:role/firehose-role",
    "BucketARN": "arn:aws:s3:::my-bucket"
  }'
```

### Put a single record
```bash
aws firehose put-record \
  --delivery-stream-name my-stream \
  --record '{"Data":"eyJrZXkiOiJ2YWx1ZSJ9Cg=="}'
```

### Put a batch of records
```bash
aws firehose put-record-batch \
  --delivery-stream-name my-stream \
  --records '{"Data":"cmVjb3JkMQ=="}' '{"Data":"cmVjb3JkMg=="}'
```

### Describe a delivery stream
```bash
aws firehose describe-delivery-stream \
  --delivery-stream-name my-stream \
  --query 'DeliveryStreamDescription.{Status:DeliveryStreamStatus,Type:DeliveryStreamType}'
```

### Enable server-side encryption
```bash
aws firehose start-delivery-stream-encryption \
  --delivery-stream-name my-stream \
  --delivery-stream-encryption-configuration-input KeyType=AWS_OWNED_CMK
```

### Update destination buffering hints
```bash
aws firehose update-destination \
  --delivery-stream-name my-stream \
  --current-delivery-stream-version-id 1 \
  --destination-id destinationId-000000000001 \
  --extended-s3-destination-update '{"BufferingHints":{"SizeInMBs":64,"IntervalInSeconds":300}}'
```

### Tag a delivery stream
```bash
aws firehose tag-delivery-stream \
  --delivery-stream-name my-stream \
  --tags Key=Environment,Value=Production Key=Team,Value=DataEng
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Delivery Streams | [`delivery-streams.md`](delivery-streams.md) | create-delivery-stream, delete-delivery-stream, describe-delivery-stream, list-delivery-streams, update-destination, start-delivery-stream-encryption, stop-delivery-stream-encryption |
| Data Operations | [`data-operations.md`](data-operations.md) | put-record, put-record-batch |
| Tags | [`tags.md`](tags.md) | tag-delivery-stream, untag-delivery-stream, list-tags-for-delivery-stream |
