# AWS CLI v2 — CloudWatch Evidently

## Overview

Complete reference for all `aws evidently` subcommands in AWS CLI v2. Covers project management, feature flags with variations, experiments (A/B testing), launches (gradual rollouts), audience segments, feature evaluation, and event ingestion. CloudWatch Evidently lets you safely validate new features by serving them to a percentage of your users while you roll out the feature, and monitor the impact through experiment metrics.

## Quick Reference — Common Workflows

### Create a project with data delivery to S3
```bash
aws evidently create-project \
    --name my-project \
    --description "Feature testing project" \
    --data-delivery '{"s3Destination":{"bucket":"my-evidently-bucket","prefix":"events/"}}'
```

### Create a feature with variations
```bash
aws evidently create-feature \
    --project my-project \
    --name new-checkout \
    --variations '[{"name":"control","value":{"boolValue":false}},{"name":"treatment","value":{"boolValue":true}}]' \
    --default-variation control \
    --evaluation-strategy ALL_RULES
```

### Run an A/B experiment
```bash
aws evidently create-experiment \
    --project my-project \
    --name checkout-experiment \
    --treatments '[{"name":"control","feature":"new-checkout","variation":"control"},{"name":"treatment","feature":"new-checkout","variation":"treatment"}]' \
    --metric-goals '[{"desiredChange":"INCREASE","metricDefinition":{"name":"conversion","entityIdKey":"userDetails.userId","valueKey":"details.conversion"}}]' \
    --online-ab-config '{"controlTreatmentName":"control","treatmentWeights":{"control":50000,"treatment":50000}}'

aws evidently start-experiment \
    --project my-project \
    --experiment checkout-experiment \
    --analysis-complete-time 2026-03-15T00:00:00Z
```

### Create a gradual launch
```bash
aws evidently create-launch \
    --project my-project \
    --name checkout-launch \
    --groups '[{"name":"treatment","feature":"new-checkout","variation":"treatment"}]' \
    --scheduled-splits-config '{"steps":[{"startTime":"2026-02-15T00:00:00Z","groupWeights":{"treatment":10000}},{"startTime":"2026-02-22T00:00:00Z","groupWeights":{"treatment":50000}},{"startTime":"2026-03-01T00:00:00Z","groupWeights":{"treatment":100000}}]}'

aws evidently start-launch \
    --project my-project \
    --launch checkout-launch
```

### Evaluate a feature for a user
```bash
aws evidently evaluate-feature \
    --project my-project \
    --feature new-checkout \
    --entity-id user-12345

aws evidently batch-evaluate-feature \
    --project my-project \
    --requests '[{"entityId":"user-12345","feature":"new-checkout"},{"entityId":"user-67890","feature":"new-checkout"}]'
```

## Command Reference

| Group | File | Commands |
|-------|------|----------|
| Projects | [projects.md](projects.md) | `create-project`, `get-project`, `list-projects`, `update-project`, `delete-project`, `put-project-events` |
| Features | [features.md](features.md) | `create-feature`, `get-feature`, `list-features`, `update-feature`, `delete-feature`, `evaluate-feature`, `batch-evaluate-feature` |
| Experiments | [experiments.md](experiments.md) | `create-experiment`, `get-experiment`, `list-experiments`, `update-experiment`, `delete-experiment`, `start-experiment`, `stop-experiment`, `get-experiment-results` |
| Launches | [launches.md](launches.md) | `create-launch`, `get-launch`, `list-launches`, `update-launch`, `delete-launch`, `start-launch`, `stop-launch` |
| Segments | [segments.md](segments.md) | `create-segment`, `get-segment`, `list-segments`, `delete-segment`, `test-segment-pattern` |
| Tags | [tags.md](tags.md) | `tag-resource`, `untag-resource`, `list-tags-for-resource` |
