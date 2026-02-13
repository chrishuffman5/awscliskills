# AWS CLI v2 — CloudTrail

## Overview

Complete reference for all `aws cloudtrail` subcommands in AWS CLI v2. Covers trail management, event selectors, insight selectors, event data stores (CloudTrail Lake), queries, channels, imports, tagging, and event lookup.

## Quick Reference — Common Workflows

### Create a trail
```bash
aws cloudtrail create-trail \
  --name my-trail \
  --s3-bucket-name my-cloudtrail-bucket \
  --is-multi-region-trail \
  --enable-log-file-validation
```

### Start logging for a trail
```bash
aws cloudtrail start-logging --name my-trail
```

### Get trail status
```bash
aws cloudtrail get-trail-status --name my-trail
```

### Look up recent events
```bash
aws cloudtrail lookup-events \
  --lookup-attributes AttributeKey=EventName,AttributeValue=RunInstances \
  --max-results 10
```

### Create an event data store (CloudTrail Lake)
```bash
aws cloudtrail create-event-data-store \
  --name my-lake-store \
  --retention-period 365 \
  --advanced-event-selectors '[{"Name":"Management","FieldSelectors":[{"Field":"eventCategory","Equals":["Management"]}]}]'
```

### Run a query on CloudTrail Lake
```bash
aws cloudtrail start-query \
  --query-statement "SELECT eventName, count(*) as cnt FROM my-eds-id WHERE eventTime > '2024-01-01' GROUP BY eventName ORDER BY cnt DESC"
```

### Put event selectors (data events)
```bash
aws cloudtrail put-event-selectors --trail-name my-trail \
  --advanced-event-selectors '[{"Name":"S3DataEvents","FieldSelectors":[{"Field":"eventCategory","Equals":["Data"]},{"Field":"resources.type","Equals":["AWS::S3::Object"]}]}]'
```

### Enable CloudTrail Insights
```bash
aws cloudtrail put-insight-selectors --trail-name my-trail \
  --insight-selectors '[{"InsightType":"ApiCallRateInsight"},{"InsightType":"ApiErrorRateInsight"}]'
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Trails | [`trails.md`](trails.md) | create-trail, delete-trail, describe-trails, get-trail, list-trails, update-trail, start-logging, stop-logging |
| Event Selectors | [`event-selectors.md`](event-selectors.md) | get-event-selectors, put-event-selectors, get-insight-selectors, put-insight-selectors |
| Event Data Stores | [`event-data-stores.md`](event-data-stores.md) | create-event-data-store, delete-event-data-store, describe-event-data-store, get-event-data-store, list-event-data-stores, update-event-data-store, restore-event-data-store, enable-federation, disable-federation |
| Queries | [`queries.md`](queries.md) | start-query, describe-query, get-query-results, list-queries, cancel-query |
| Channels | [`channels.md`](channels.md) | create-channel, delete-channel, get-channel, list-channels, update-channel |
| Imports | [`imports.md`](imports.md) | create-import, get-import, list-imports, start-import |
| Tags | [`tags.md`](tags.md) | add-tags, remove-tags, list-tags |
| Events | [`events.md`](events.md) | lookup-events, get-trail-status |
