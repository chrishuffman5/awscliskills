# AWS CLI v2 — Amazon Translate

## Overview

Complete reference for all `aws translate` subcommands in AWS CLI v2. Covers real-time and batch text translation, document translation, custom terminology management, parallel data resources for Active Custom Translation, and supported language listing.

## Quick Reference — Common Workflows

### Translate text in real time
```bash
aws translate translate-text \
  --text "Hello, how are you?" \
  --source-language-code en \
  --target-language-code es
```

### Translate text with auto-detected source language
```bash
aws translate translate-text \
  --text "Bonjour le monde" \
  --source-language-code auto \
  --target-language-code en
```

### Translate a document
```bash
aws translate translate-document \
  --document ContentType=text/plain \
  --document-content fileb://document.txt \
  --source-language-code en \
  --target-language-code fr
```

### Import custom terminology
```bash
aws translate import-terminology \
  --name my-terminology \
  --merge-strategy OVERWRITE \
  --data-file fileb://terms.csv \
  --terminology-data Format=CSV
```

### Start a batch translation job
```bash
aws translate start-text-translation-job \
  --job-name my-batch-job \
  --input-data-config S3Uri=s3://my-bucket/input/,ContentType=text/plain \
  --output-data-config S3Uri=s3://my-bucket/output/ \
  --data-access-role-arn arn:aws:iam::123456789012:role/TranslateRole \
  --source-language-code en \
  --target-language-codes fr es de
```

### Check batch job status
```bash
aws translate describe-text-translation-job --job-id abc123def456
```

### Create parallel data for Active Custom Translation
```bash
aws translate create-parallel-data \
  --name my-parallel-data \
  --parallel-data-config S3Uri=s3://my-bucket/parallel/,Format=CSV
```

### List supported languages
```bash
aws translate list-languages --display-language-code en
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Translation | [`translation.md`](translation.md) | translate-text, translate-document, start-text-translation-job, describe-text-translation-job, list-text-translation-jobs, stop-text-translation-job, list-languages |
| Terminologies | [`terminologies.md`](terminologies.md) | import-terminology, get-terminology, list-terminologies, delete-terminology |
| Parallel Data | [`parallel-data.md`](parallel-data.md) | create-parallel-data, get-parallel-data, list-parallel-data, update-parallel-data, delete-parallel-data |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
