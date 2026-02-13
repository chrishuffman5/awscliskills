# AWS CLI v2 — X-Ray

## Overview

Complete reference for all `aws xray` subcommands in AWS CLI v2. Covers distributed tracing, service graphs, sampling rules, groups, insights, indexing rules, encryption configuration, and resource policies.

## Quick Reference — Common Workflows

### Get trace summaries for the last hour
```bash
aws xray get-trace-summaries \
  --start-time $(date -u -d '1 hour ago' +%s) \
  --end-time $(date -u +%s)
```

### Get a service graph
```bash
aws xray get-service-graph \
  --start-time $(date -u -d '1 hour ago' +%s) \
  --end-time $(date -u +%s)
```

### Batch get specific traces
```bash
aws xray batch-get-traces \
  --trace-ids 1-67890abc-def012345678 1-67890abc-def012345679
```

### Create a sampling rule
```bash
aws xray create-sampling-rule --sampling-rule '{
  "RuleName": "my-rule",
  "Priority": 100,
  "FixedRate": 0.05,
  "ReservoirSize": 1,
  "ServiceName": "*",
  "ServiceType": "*",
  "Host": "*",
  "ResourceARN": "*",
  "HTTPMethod": "*",
  "URLPath": "*",
  "Version": 1
}'
```

### Create a group
```bash
aws xray create-group --group-name my-group \
  --filter-expression 'service("my-service")'
```

### Enable encryption with KMS
```bash
aws xray put-encryption-config --type KMS \
  --key-id arn:aws:kms:us-east-1:123456789012:key/my-key-id
```

### Get insight summaries
```bash
aws xray get-insight-summaries \
  --start-time $(date -u -d '24 hours ago' +%s) \
  --end-time $(date -u +%s)
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Traces | [`traces.md`](traces.md) | batch-get-traces, get-trace-summaries, get-trace-graph, put-trace-segments, start-trace-retrieval, cancel-trace-retrieval, list-retrieved-traces, get-retrieved-traces-graph, get-trace-segment-destination, update-trace-segment-destination |
| Service Graph | [`service-graph.md`](service-graph.md) | get-service-graph, get-time-series-service-statistics |
| Sampling | [`sampling.md`](sampling.md) | create-sampling-rule, delete-sampling-rule, get-sampling-rules, update-sampling-rule, get-sampling-statistic-summaries, get-sampling-targets |
| Groups | [`groups.md`](groups.md) | create-group, delete-group, get-group, get-groups, update-group |
| Insights | [`insights.md`](insights.md) | get-insight, get-insight-events, get-insight-impact-graph, get-insight-summaries |
| Indexing | [`indexing.md`](indexing.md) | get-indexing-rules, update-indexing-rule |
| Encryption & Policies | [`encryption-policies.md`](encryption-policies.md) | get-encryption-config, put-encryption-config, list-resource-policies, put-resource-policy, delete-resource-policy |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
