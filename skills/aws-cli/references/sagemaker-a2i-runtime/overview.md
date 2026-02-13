# AWS CLI v2 -- SageMaker A2I Runtime (Augmented AI)

## Overview

Complete reference for all `aws sagemaker-a2i-runtime` subcommands in AWS CLI v2. Amazon Augmented AI (A2I) enables human review workflows for ML predictions. The A2I Runtime API manages human loops -- the individual review tasks that route data to human workers when ML models cannot evaluate with high confidence.

## Quick Reference -- Common Workflows

### Start a human loop
```bash
aws sagemaker-a2i-runtime start-human-loop \
  --human-loop-name my-review-loop \
  --flow-definition-arn arn:aws:sagemaker:us-east-1:111122223333:flow-definition/my-flow \
  --human-loop-input InputContent='{"taskObject":"s3://bucket/image.png"}'
```

### Start a human loop with data attributes
```bash
aws sagemaker-a2i-runtime start-human-loop \
  --human-loop-name my-review-loop \
  --flow-definition-arn arn:aws:sagemaker:us-east-1:111122223333:flow-definition/my-flow \
  --human-loop-input InputContent='{"taskObject":"s3://bucket/document.pdf"}' \
  --data-attributes ContentClassifiers=FreeOfPersonallyIdentifiableInformation,FreeOfAdultContent
```

### Check human loop status
```bash
aws sagemaker-a2i-runtime describe-human-loop \
  --human-loop-name my-review-loop \
  --query 'HumanLoopStatus'
```

### List human loops for a flow definition
```bash
aws sagemaker-a2i-runtime list-human-loops \
  --flow-definition-arn arn:aws:sagemaker:us-east-1:111122223333:flow-definition/my-flow \
  --sort-order Descending
```

### Stop an in-progress human loop
```bash
aws sagemaker-a2i-runtime stop-human-loop \
  --human-loop-name my-review-loop
```

### Delete a human loop
```bash
aws sagemaker-a2i-runtime delete-human-loop \
  --human-loop-name my-review-loop
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Human Loops | [`human-loops.md`](human-loops.md) | start-human-loop, describe-human-loop, list-human-loops, stop-human-loop, delete-human-loop |
