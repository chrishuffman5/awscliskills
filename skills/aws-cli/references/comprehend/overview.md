# AWS CLI v2 — Comprehend (Natural Language Processing)

## Overview

Complete reference for all `aws comprehend` subcommands in AWS CLI v2. Covers real-time text analysis (entity detection, sentiment, key phrases, syntax, PII, toxicity), batch operations, asynchronous detection jobs (entities, sentiment, key phrases, dominant language, PII, events, topics, targeted sentiment), custom document classifiers and entity recognizers, inference endpoints, flywheels for automated retraining, datasets, resource policies, and tagging.

## Quick Reference — Common Workflows

### Detect entities in text
```bash
aws comprehend detect-entities \
  --language-code en \
  --text "John moved to 123 Main St in Seattle last Friday."
```

### Detect sentiment
```bash
aws comprehend detect-sentiment \
  --language-code en \
  --text "The service was excellent and the food was amazing."
```

### Detect PII entities
```bash
aws comprehend detect-pii-entities \
  --language-code en \
  --text "His SSN is 123-45-6789 and email is john@example.com"
```

### Batch detect entities across multiple documents
```bash
aws comprehend batch-detect-entities \
  --language-code en \
  --text-list "John lives in Seattle." "AWS is based in Virginia."
```

### Start an asynchronous entities detection job
```bash
aws comprehend start-entities-detection-job \
  --job-name my-entities-job \
  --language-code en \
  --input-data-config "S3Uri=s3://my-bucket/input/" \
  --output-data-config "S3Uri=s3://my-bucket/output/" \
  --data-access-role-arn arn:aws:iam::111122223333:role/ComprehendRole
```

### Train a custom document classifier
```bash
aws comprehend create-document-classifier \
  --document-classifier-name my-classifier \
  --language-code en \
  --input-data-config "S3Uri=s3://my-bucket/training-data/" \
  --data-access-role-arn arn:aws:iam::111122223333:role/ComprehendRole
```

### Create an endpoint for real-time inference
```bash
aws comprehend create-endpoint \
  --endpoint-name my-endpoint \
  --model-arn arn:aws:comprehend:us-east-1:111122223333:document-classifier/my-classifier \
  --desired-inference-units 1
```

### Classify a document using a custom endpoint
```bash
aws comprehend classify-document \
  --endpoint-arn arn:aws:comprehend:us-east-1:111122223333:document-classifier-endpoint/my-endpoint \
  --text "URGENT: Your account has been compromised"
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Real-Time Analysis | [`real-time-analysis.md`](real-time-analysis.md) | detect-dominant-language, detect-entities, detect-key-phrases, detect-pii-entities, detect-sentiment, detect-syntax, detect-targeted-sentiment, detect-toxic-content, contains-pii-entities, classify-document |
| Batch Analysis | [`batch-analysis.md`](batch-analysis.md) | batch-detect-dominant-language, batch-detect-entities, batch-detect-key-phrases, batch-detect-sentiment, batch-detect-syntax, batch-detect-targeted-sentiment |
| Entity Detection Jobs | [`entity-detection-jobs.md`](entity-detection-jobs.md) | start-entities-detection-job, describe-entities-detection-job, list-entities-detection-jobs, stop-entities-detection-job |
| Classification Jobs | [`classification-jobs.md`](classification-jobs.md) | start-document-classification-job, describe-document-classification-job, list-document-classification-jobs |
| Other Jobs | [`other-jobs.md`](other-jobs.md) | start-dominant-language-detection-job, describe-dominant-language-detection-job, list-dominant-language-detection-jobs, stop-dominant-language-detection-job, start-key-phrases-detection-job, describe-key-phrases-detection-job, list-key-phrases-detection-jobs, stop-key-phrases-detection-job, start-sentiment-detection-job, describe-sentiment-detection-job, list-sentiment-detection-jobs, stop-sentiment-detection-job, start-targeted-sentiment-detection-job, describe-targeted-sentiment-detection-job, list-targeted-sentiment-detection-jobs, stop-targeted-sentiment-detection-job, start-pii-entities-detection-job, describe-pii-entities-detection-job, list-pii-entities-detection-jobs, stop-pii-entities-detection-job, start-events-detection-job, describe-events-detection-job, list-events-detection-jobs, stop-events-detection-job, start-topics-detection-job, describe-topics-detection-job, list-topics-detection-jobs |
| Document Classifiers | [`document-classifiers.md`](document-classifiers.md) | create-document-classifier, delete-document-classifier, describe-document-classifier, list-document-classifiers, list-document-classifier-summaries, stop-training-document-classifier |
| Entity Recognizers | [`entity-recognizers.md`](entity-recognizers.md) | create-entity-recognizer, delete-entity-recognizer, describe-entity-recognizer, list-entity-recognizers, list-entity-recognizer-summaries, stop-training-entity-recognizer |
| Endpoints | [`endpoints.md`](endpoints.md) | create-endpoint, delete-endpoint, describe-endpoint, list-endpoints, update-endpoint |
| Flywheels | [`flywheels.md`](flywheels.md) | create-flywheel, delete-flywheel, describe-flywheel, list-flywheels, update-flywheel, start-flywheel-iteration, describe-flywheel-iteration, list-flywheel-iteration-history |
| Datasets | [`datasets.md`](datasets.md) | create-dataset, describe-dataset, list-datasets |
| Resource Policies | [`resource-policies.md`](resource-policies.md) | put-resource-policy, delete-resource-policy, describe-resource-policy, import-model |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
