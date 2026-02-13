# AWS CLI v2 — Lookout for Vision

## Overview

Complete reference for all `aws lookoutvision` subcommands in AWS CLI v2. Covers project management, ML model training and hosting, image anomaly detection, dataset management, model packaging for edge deployment, and resource tagging. Amazon Lookout for Vision uses computer vision to detect visual defects in manufactured products, identifying missing components, damage, and irregularities from images. **Note:** Amazon Lookout for Vision is no longer available to new customers (end of life October 31, 2025).

## Quick Reference — Common Workflows

### Create a project and dataset
```bash
aws lookoutvision create-project \
    --project-name my-defect-detection

aws lookoutvision create-dataset \
    --project-name my-defect-detection \
    --dataset-type train \
    --dataset-source '{"GroundTruthManifest":{"S3Object":{"Bucket":"my-bucket","Key":"manifests/train.manifest"}}}'
```

### Train a model
```bash
aws lookoutvision create-model \
    --project-name my-defect-detection \
    --output-config '{"S3Location":{"Bucket":"my-output-bucket","Prefix":"training-output/"}}' \
    --tags '[{"Key":"Environment","Value":"production"}]'
```

### Start model and detect anomalies
```bash
aws lookoutvision start-model \
    --project-name my-defect-detection \
    --model-version 1 \
    --min-inference-units 1

aws lookoutvision detect-anomalies \
    --project-name my-defect-detection \
    --model-version 1 \
    --content-type image/jpeg \
    --body test-image.jpg
```

### Package model for edge deployment
```bash
aws lookoutvision start-model-packaging-job \
    --project-name my-defect-detection \
    --model-version 1 \
    --configuration '{"Greengrass":{"CompilerOptions":"{}","TargetPlatform":{"Os":"LINUX","Arch":"ARM64","Accelerator":"NVIDIA"},"S3OutputLocation":{"Bucket":"my-output-bucket","Prefix":"packaging/"},"ComponentName":"MyDefectDetector","ComponentVersion":"1.0.0"}}'
```

### Stop model and clean up
```bash
aws lookoutvision stop-model \
    --project-name my-defect-detection \
    --model-version 1

aws lookoutvision delete-model \
    --project-name my-defect-detection \
    --model-version 1

aws lookoutvision delete-dataset \
    --project-name my-defect-detection \
    --dataset-type train

aws lookoutvision delete-project \
    --project-name my-defect-detection
```

## Command Reference

| Group | File | Commands |
|-------|------|----------|
| Projects | [projects.md](projects.md) | `create-project`, `delete-project`, `describe-project`, `list-projects` |
| Models | [models.md](models.md) | `create-model`, `delete-model`, `describe-model`, `list-models`, `start-model`, `stop-model`, `detect-anomalies` |
| Datasets | [datasets.md](datasets.md) | `create-dataset`, `delete-dataset`, `describe-dataset`, `list-dataset-entries`, `update-dataset-entries` |
| Packaging | [packaging.md](packaging.md) | `describe-model-packaging-job`, `list-model-packaging-jobs`, `start-model-packaging-job` |
| Tags | [tags.md](tags.md) | `tag-resource`, `untag-resource`, `list-tags-for-resource` |
