# AWS CLI v2 — Lookout for Equipment

## Overview

Complete reference for all `aws lookoutequipment` subcommands in AWS CLI v2. Covers dataset management, ML model training and versioning, inference scheduling, label management, retraining schedulers, sensor statistics, and resource policies. Lookout for Equipment uses sensor data from industrial equipment to detect abnormal behavior and enable predictive maintenance.

## Quick Reference — Common Workflows

### Create a dataset and ingest data
```bash
aws lookoutequipment create-dataset \
    --dataset-name my-equipment-dataset

aws lookoutequipment start-data-ingestion-job \
    --dataset-name my-equipment-dataset \
    --ingestion-input-configuration '{"S3InputConfiguration":{"Bucket":"my-bucket","Prefix":"sensor-data/","KeyPattern":"{prefix}/{component_name}_*"}}' \
    --role-arn arn:aws:iam::123456789012:role/LookoutRole
```

### Create and train a model
```bash
aws lookoutequipment create-model \
    --model-name my-equipment-model \
    --dataset-name my-equipment-dataset \
    --training-data-start-time 2024-01-01T00:00:00Z \
    --training-data-end-time 2024-06-30T23:59:59Z \
    --evaluation-data-start-time 2024-07-01T00:00:00Z \
    --evaluation-data-end-time 2024-09-30T23:59:59Z \
    --role-arn arn:aws:iam::123456789012:role/LookoutRole
```

### Create an inference scheduler
```bash
aws lookoutequipment create-inference-scheduler \
    --inference-scheduler-name my-scheduler \
    --model-name my-equipment-model \
    --data-upload-frequency PT5M \
    --data-input-configuration '{"S3InputConfiguration":{"Bucket":"my-input-bucket","Prefix":"inference/"}}' \
    --data-output-configuration '{"S3OutputConfiguration":{"Bucket":"my-output-bucket","Prefix":"results/"}}' \
    --role-arn arn:aws:iam::123456789012:role/LookoutRole

aws lookoutequipment start-inference-scheduler \
    --inference-scheduler-name my-scheduler
```

### Set up automatic retraining
```bash
aws lookoutequipment create-retraining-scheduler \
    --model-name my-equipment-model \
    --retraining-frequency P30D \
    --lookback-window P180D \
    --promote-mode MANAGED
```

### Create labels for anomalies
```bash
aws lookoutequipment create-label-group \
    --label-group-name my-labels \
    --fault-codes "bearing_failure" "motor_overheating"

aws lookoutequipment create-label \
    --label-group-name my-labels \
    --start-time 2024-06-15T10:00:00Z \
    --end-time 2024-06-15T11:00:00Z \
    --rating ANOMALY \
    --fault-code bearing_failure \
    --equipment pump-01
```

## Command Reference

| Group | File | Commands |
|-------|------|----------|
| Datasets | [datasets.md](datasets.md) | `create-dataset`, `describe-dataset`, `list-datasets`, `delete-dataset`, `import-dataset`, `start-data-ingestion-job`, `describe-data-ingestion-job`, `list-data-ingestion-jobs` |
| Models | [models.md](models.md) | `create-model`, `describe-model`, `list-models`, `update-model`, `delete-model`, `describe-model-version`, `list-model-versions`, `update-active-model-version`, `import-model-version` |
| Inference | [inference.md](inference.md) | `create-inference-scheduler`, `describe-inference-scheduler`, `list-inference-schedulers`, `update-inference-scheduler`, `delete-inference-scheduler`, `start-inference-scheduler`, `stop-inference-scheduler`, `list-inference-executions`, `list-inference-events` |
| Labels | [labels.md](labels.md) | `create-label-group`, `describe-label-group`, `list-label-groups`, `update-label-group`, `delete-label-group`, `create-label`, `describe-label`, `list-labels`, `delete-label` |
| Retraining | [retraining.md](retraining.md) | `create-retraining-scheduler`, `describe-retraining-scheduler`, `list-retraining-schedulers`, `update-retraining-scheduler`, `delete-retraining-scheduler`, `start-retraining-scheduler`, `stop-retraining-scheduler` |
| Sensor Statistics | [sensor-statistics.md](sensor-statistics.md) | `list-sensor-statistics` |
| Resource Policies & Tags | [resource-policies-tags.md](resource-policies-tags.md) | `put-resource-policy`, `describe-resource-policy`, `delete-resource-policy`, `tag-resource`, `untag-resource`, `list-tags-for-resource` |
