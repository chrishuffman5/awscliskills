# AWS CLI v2 — Amazon Personalize

## Overview

Complete reference for all `aws personalize`, `aws personalize-runtime`, and `aws personalize-events` subcommands in AWS CLI v2. Covers dataset groups, datasets, schemas, solutions, campaigns, recommenders, batch jobs, event trackers, filters, metric attributions, runtime recommendations, real-time event ingestion, and tagging.

## Quick Reference — Common Workflows

### Create a dataset group
```bash
aws personalize create-dataset-group \
  --name my-dataset-group \
  --domain ECOMMERCE
```

### Create a schema
```bash
aws personalize create-schema \
  --name my-interactions-schema \
  --schema '{"type":"record","name":"Interactions","namespace":"com.amazonaws.personalize.schema","fields":[{"name":"USER_ID","type":"string"},{"name":"ITEM_ID","type":"string"},{"name":"TIMESTAMP","type":"long"}],"version":"1.0"}'
```

### Create a dataset and import data
```bash
aws personalize create-dataset \
  --name my-interactions \
  --dataset-group-arn arn:aws:personalize:us-east-1:123456789012:dataset-group/my-dataset-group \
  --dataset-type Interactions \
  --schema-arn arn:aws:personalize:us-east-1:123456789012:schema/my-interactions-schema

aws personalize create-dataset-import-job \
  --job-name my-import \
  --dataset-arn arn:aws:personalize:us-east-1:123456789012:dataset/my-dataset-group/INTERACTIONS \
  --data-source dataLocation=s3://my-bucket/interactions.csv \
  --role-arn arn:aws:iam::123456789012:role/PersonalizeRole
```

### Create a solution and solution version
```bash
aws personalize create-solution \
  --name my-solution \
  --dataset-group-arn arn:aws:personalize:us-east-1:123456789012:dataset-group/my-dataset-group \
  --recipe-arn arn:aws:personalize:::recipe/aws-user-personalization

aws personalize create-solution-version \
  --solution-arn arn:aws:personalize:us-east-1:123456789012:solution/my-solution
```

### Create a campaign and get recommendations
```bash
aws personalize create-campaign \
  --name my-campaign \
  --solution-version-arn arn:aws:personalize:us-east-1:123456789012:solution/my-solution/version-id

aws personalize-runtime get-recommendations \
  --campaign-arn arn:aws:personalize:us-east-1:123456789012:campaign/my-campaign \
  --user-id user123 \
  --num-results 10
```

### Record real-time events
```bash
aws personalize-events put-events \
  --tracking-id tracking-id-12345 \
  --session-id session-123 \
  --user-id user123 \
  --event-list '[{"eventType":"click","itemId":"item456","sentAt":1630703537}]'
```

### Create a recommender (Domain dataset groups)
```bash
aws personalize create-recommender \
  --name my-recommender \
  --dataset-group-arn arn:aws:personalize:us-east-1:123456789012:dataset-group/my-dataset-group \
  --recipe-arn arn:aws:personalize:::recipe/aws-ecomm-popular-items-by-views
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Dataset Groups | [`dataset-groups.md`](dataset-groups.md) | create-dataset-group, describe-dataset-group, list-dataset-groups, delete-dataset-group |
| Datasets | [`datasets.md`](datasets.md) | create-dataset, describe-dataset, list-datasets, update-dataset, delete-dataset, create-dataset-import-job, describe-dataset-import-job, list-dataset-import-jobs, create-dataset-export-job, describe-dataset-export-job, list-dataset-export-jobs, create-data-deletion-job, describe-data-deletion-job, list-data-deletion-jobs |
| Schemas | [`schemas.md`](schemas.md) | create-schema, describe-schema, list-schemas, delete-schema |
| Solutions | [`solutions.md`](solutions.md) | create-solution, describe-solution, list-solutions, update-solution, delete-solution, create-solution-version, describe-solution-version, list-solution-versions, get-solution-metrics, stop-solution-version-creation |
| Campaigns | [`campaigns.md`](campaigns.md) | create-campaign, describe-campaign, list-campaigns, update-campaign, delete-campaign |
| Recommenders | [`recommenders.md`](recommenders.md) | create-recommender, describe-recommender, list-recommenders, update-recommender, delete-recommender, start-recommender, stop-recommender |
| Batch Jobs | [`batch-jobs.md`](batch-jobs.md) | create-batch-inference-job, describe-batch-inference-job, list-batch-inference-jobs, create-batch-segment-job, describe-batch-segment-job, list-batch-segment-jobs |
| Event Trackers | [`event-trackers.md`](event-trackers.md) | create-event-tracker, describe-event-tracker, list-event-trackers, delete-event-tracker |
| Filters & Metrics | [`filters-metrics.md`](filters-metrics.md) | create-filter, describe-filter, list-filters, delete-filter, create-metric-attribution, describe-metric-attribution, list-metric-attributions, list-metric-attribution-metrics, update-metric-attribution, delete-metric-attribution, describe-algorithm, describe-feature-transformation, describe-recipe, list-recipes |
| Runtime | [`runtime.md`](runtime.md) | get-recommendations, get-personalized-ranking, get-action-recommendations |
| Events | [`events.md`](events.md) | put-events, put-items, put-users, put-actions, put-action-interactions |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
