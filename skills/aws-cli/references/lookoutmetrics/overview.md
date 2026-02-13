# AWS CLI v2 -- Lookout for Metrics

> **Note:** Amazon Lookout for Metrics was discontinued on September 12, 2025. This reference is provided for existing deployments.

## Overview

Complete reference for all `aws lookoutmetrics` subcommands in AWS CLI v2. Covers anomaly detectors, metric sets (datasets), alerts, anomaly groups, feedback, and tagging.

## Quick Reference -- Common Workflows

### Create an anomaly detector
```bash
aws lookoutmetrics create-anomaly-detector \
  --anomaly-detector-name my-detector \
  --anomaly-detector-config AnomalyDetectorFrequency=PT1H
```

### Create a metric set
```bash
aws lookoutmetrics create-metric-set \
  --anomaly-detector-arn arn:aws:lookoutmetrics:us-east-1:111122223333:AnomalyDetector:my-detector \
  --metric-set-name my-metric-set \
  --metric-list MetricName=revenue,AggregationFunction=SUM \
  --metric-source '{"S3SourceConfig":{"RoleArn":"arn:aws:iam::111122223333:role/LookoutRole","TemplatedPathList":["s3://bucket/data/"],"FileFormatDescriptor":{"CsvFormatDescriptor":{"FileCompression":"NONE","Charset":"UTF-8","ContainsHeader":true,"Delimiter":",","QuoteSymbol":"\""}}}}'
```

### Create an alert
```bash
aws lookoutmetrics create-alert \
  --alert-name my-alert \
  --anomaly-detector-arn arn:aws:lookoutmetrics:us-east-1:111122223333:AnomalyDetector:my-detector \
  --action '{"SNSConfiguration":{"RoleArn":"arn:aws:iam::111122223333:role/LookoutRole","SnsTopicArn":"arn:aws:sns:us-east-1:111122223333:my-topic","SnsFormat":"JSON"}}'
```

### Activate an anomaly detector
```bash
aws lookoutmetrics activate-anomaly-detector \
  --anomaly-detector-arn arn:aws:lookoutmetrics:us-east-1:111122223333:AnomalyDetector:my-detector
```

### Check detector status
```bash
aws lookoutmetrics describe-anomaly-detector \
  --anomaly-detector-arn arn:aws:lookoutmetrics:us-east-1:111122223333:AnomalyDetector:my-detector \
  --query 'Status'
```

### List anomaly group summaries
```bash
aws lookoutmetrics list-anomaly-group-summaries \
  --anomaly-detector-arn arn:aws:lookoutmetrics:us-east-1:111122223333:AnomalyDetector:my-detector \
  --sensitivity-threshold 50
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Detectors | [`detectors.md`](detectors.md) | create-anomaly-detector, describe-anomaly-detector, list-anomaly-detectors, update-anomaly-detector, delete-anomaly-detector, activate-anomaly-detector, deactivate-anomaly-detector, back-test-anomaly-detector, describe-anomaly-detection-executions |
| Metric Sets | [`metric-sets.md`](metric-sets.md) | create-metric-set, describe-metric-set, list-metric-sets, update-metric-set, detect-metric-set-config, get-sample-data, get-data-quality-metrics |
| Alerts | [`alerts.md`](alerts.md) | create-alert, describe-alert, list-alerts, update-alert, delete-alert |
| Anomaly Groups | [`anomaly-groups.md`](anomaly-groups.md) | get-anomaly-group, list-anomaly-group-summaries, list-anomaly-group-time-series, list-anomaly-group-related-metrics, put-feedback, get-feedback |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
