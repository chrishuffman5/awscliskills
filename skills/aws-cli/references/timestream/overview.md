# AWS CLI v2 — Timestream (Time-Series Database)

## Overview

Complete reference for all `aws timestream-write` and `aws timestream-query` subcommands in AWS CLI v2. Covers database and table management, time-series data ingestion (single and batch), ad-hoc queries, scheduled queries, and resource tagging. Amazon Timestream is a fast, scalable, serverless time-series database for IoT and operational applications.

## Quick Reference — Common Workflows

### Create a database
```bash
aws timestream-write create-database --database-name my-ts-db
```

### Create a table with retention policies
```bash
aws timestream-write create-table --database-name my-ts-db --table-name my-ts-table \
  --retention-properties MemoryStoreRetentionPeriodInHours=24,MagneticStoreRetentionPeriodInDays=365
```

### Write records
```bash
aws timestream-write write-records --database-name my-ts-db --table-name my-ts-table \
  --common-attributes '{"Dimensions":[{"Name":"region","Value":"us-east-1"}],"MeasureName":"cpu","MeasureValueType":"DOUBLE","TimeUnit":"SECONDS"}' \
  --records '[{"MeasureValue":"80.5","Time":"'$(date +%s)'"}]'
```

### Query data
```bash
aws timestream-query query \
  --query-string "SELECT * FROM \"my-ts-db\".\"my-ts-table\" WHERE time > ago(1h) ORDER BY time DESC LIMIT 10"
```

### Create a batch load task from S3
```bash
aws timestream-write create-batch-load-task \
  --target-database-name my-ts-db --target-table-name my-ts-table \
  --data-source-configuration '{"DataSourceS3Configuration":{"BucketName":"my-bucket","ObjectKeyPrefix":"data/"},"DataFormat":"CSV"}' \
  --report-configuration '{"ReportS3Configuration":{"BucketName":"my-bucket","ObjectKeyPrefix":"reports/"}}'
```

### Create a scheduled query
```bash
aws timestream-query create-scheduled-query --name my-hourly-agg \
  --query-string "SELECT region, bin(time, 1h) as hour, avg(measure_value::double) as avg_cpu FROM \"my-ts-db\".\"my-ts-table\" WHERE time > @scheduled_runtime - 1h GROUP BY region, bin(time, 1h)" \
  --schedule-configuration '{"ScheduleExpression":"rate(1 hour)"}' \
  --notification-configuration '{"SnsConfiguration":{"TopicArn":"arn:aws:sns:us-east-1:123456789012:my-topic"}}' \
  --scheduled-query-execution-role-arn arn:aws:iam::123456789012:role/TimestreamRole \
  --error-report-configuration '{"S3Configuration":{"BucketName":"my-bucket","ObjectKeyPrefix":"errors/"}}' \
  --target-configuration '{"TimestreamConfiguration":{"DatabaseName":"my-ts-db","TableName":"agg-table","TimeColumn":"hour","DimensionMappings":[{"Name":"region","DimensionValueType":"VARCHAR"}]}}'
```

### Update table retention
```bash
aws timestream-write update-table --database-name my-ts-db --table-name my-ts-table \
  --retention-properties MemoryStoreRetentionPeriodInHours=48,MagneticStoreRetentionPeriodInDays=730
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Databases & Tables | [`databases-tables.md`](databases-tables.md) | create-database, describe-database, update-database, delete-database, list-databases, create-table, describe-table, update-table, delete-table, list-tables |
| Data Ingestion | [`data-ingestion.md`](data-ingestion.md) | write-records, create-batch-load-task, describe-batch-load-task, list-batch-load-tasks, resume-batch-load-task |
| Queries | [`queries.md`](queries.md) | query, cancel-query, prepare-query, describe-endpoints, describe-account-settings, update-account-settings |
| Scheduled Queries | [`scheduled-queries.md`](scheduled-queries.md) | create-scheduled-query, describe-scheduled-query, update-scheduled-query, delete-scheduled-query, execute-scheduled-query, list-scheduled-queries |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource (both timestream-write and timestream-query) |
