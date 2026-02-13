# AWS CLI v2 — Textract

## Overview

Complete reference for all `aws textract` subcommands in AWS CLI v2. Amazon Textract automatically extracts text, handwriting, and structured data from scanned documents. It supports document text detection, form and table analysis, expense (invoice/receipt) analysis, identity document analysis, and lending document analysis. Textract also provides custom adapters to fine-tune extraction for specific document types.

## Quick Reference — Common Workflows

### Detect text in a document (synchronous)
```bash
aws textract detect-document-text \
  --document '{"S3Object":{"Bucket":"my-bucket","Name":"document.pdf"}}'
```

### Analyze a document for tables and forms (synchronous)
```bash
aws textract analyze-document \
  --document '{"S3Object":{"Bucket":"my-bucket","Name":"document.pdf"}}' \
  --feature-types '["TABLES","FORMS"]'
```

### Analyze a document with queries (synchronous)
```bash
aws textract analyze-document \
  --document '{"S3Object":{"Bucket":"my-bucket","Name":"form.png"}}' \
  --feature-types '["QUERIES"]' \
  --queries-config '{"Queries":[{"Text":"What is the patient name?","Alias":"PATIENT_NAME"}]}'
```

### Analyze an expense document (synchronous)
```bash
aws textract analyze-expense \
  --document '{"S3Object":{"Bucket":"my-bucket","Name":"receipt.jpg"}}'
```

### Analyze an identity document (synchronous)
```bash
aws textract analyze-id \
  --document-pages '[{"S3Object":{"Bucket":"my-bucket","Name":"id-front.jpg"}},{"S3Object":{"Bucket":"my-bucket","Name":"id-back.jpg"}}]'
```

### Start async document analysis and retrieve results
```bash
aws textract start-document-analysis \
  --document-location '{"S3Object":{"Bucket":"my-bucket","Name":"large-doc.pdf"}}' \
  --feature-types '["TABLES","FORMS"]' \
  --notification-channel "SNSTopicArn=arn:aws:sns:us-east-1:123456789012:textract-topic,RoleArn=arn:aws:iam::123456789012:role/TextractRole"

# Poll for results using the returned JobId
aws textract get-document-analysis --job-id <job-id>
```

### Start async text detection
```bash
aws textract start-document-text-detection \
  --document-location '{"S3Object":{"Bucket":"my-bucket","Name":"large-doc.pdf"}}' \
  --output-config '{"S3Bucket":"output-bucket","S3Prefix":"textract-output"}'
```

### Create and use a custom adapter
```bash
# Create adapter
aws textract create-adapter \
  --adapter-name my-adapter \
  --feature-types '["QUERIES"]' \
  --auto-update ENABLED

# Create adapter version with training data
aws textract create-adapter-version \
  --adapter-id <adapter-id> \
  --dataset-config '{"ManifestS3Object":{"Bucket":"my-bucket","Name":"manifest.jsonl"}}' \
  --output-config '{"S3Bucket":"output-bucket"}'

# Use adapter in analysis
aws textract analyze-document \
  --document '{"S3Object":{"Bucket":"my-bucket","Name":"doc.pdf"}}' \
  --feature-types '["QUERIES"]' \
  --adapters-config '{"Adapters":[{"AdapterId":"<adapter-id>","Version":"1"}]}'
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Synchronous | [`synchronous.md`](synchronous.md) | detect-document-text, analyze-document, analyze-expense, analyze-id |
| Asynchronous | [`asynchronous.md`](asynchronous.md) | start-document-analysis, start-document-text-detection, start-expense-analysis, start-lending-analysis, get-document-analysis, get-document-text-detection, get-expense-analysis, get-lending-analysis, get-lending-analysis-summary |
| Adapters | [`adapters.md`](adapters.md) | create-adapter, create-adapter-version, delete-adapter, delete-adapter-version, get-adapter, get-adapter-version, list-adapters, list-adapter-versions, update-adapter |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
