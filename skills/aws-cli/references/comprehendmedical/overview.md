# AWS CLI v2 — Comprehend Medical

## Overview

Complete reference for all `aws comprehendmedical` subcommands in AWS CLI v2. Amazon Comprehend Medical is a HIPAA-eligible NLP service that extracts health data from unstructured clinical text. It detects medical entities (medications, conditions, procedures), protected health information (PHI), and maps entities to standard medical codes (ICD-10-CM, RxNorm, SNOMED CT). Supports both real-time (synchronous) and batch (asynchronous) processing.

## Quick Reference — Common Workflows

### Detect medical entities in text (real-time)
```bash
aws comprehendmedical detect-entities-v2 \
  --text "Patient has a history of type 2 diabetes treated with Metformin 500mg twice daily."
```

### Detect protected health information (real-time)
```bash
aws comprehendmedical detect-phi \
  --text "Patient John Smith, DOB 01/15/1980, lives at 123 Main St, Anytown USA."
```

### Infer ICD-10-CM codes from clinical text
```bash
aws comprehendmedical infer-icd10-cm \
  --text "The patient complains of abdominal pain and nausea."
```

### Infer RxNorm medication codes
```bash
aws comprehendmedical infer-rx-norm \
  --text "Patient is prescribed Lisinopril 10mg once daily for hypertension."
```

### Infer SNOMED CT codes
```bash
aws comprehendmedical infer-snomedct \
  --text "Patient presents with acute bronchitis and productive cough."
```

### Run batch entity detection job
```bash
aws comprehendmedical start-entities-detection-v2-job \
  --input-data-config "S3Bucket=my-input-bucket,S3Key=clinical-notes/" \
  --output-data-config "S3Bucket=my-output-bucket,S3Key=results/" \
  --data-access-role-arn arn:aws:iam::123456789012:role/ComprehendMedicalRole \
  --language-code en

# Check job status
aws comprehendmedical describe-entities-detection-v2-job --job-id <job-id>
```

### Run batch PHI detection job
```bash
aws comprehendmedical start-phi-detection-job \
  --input-data-config "S3Bucket=my-input-bucket,S3Key=clinical-notes/" \
  --output-data-config "S3Bucket=my-output-bucket,S3Key=results/" \
  --data-access-role-arn arn:aws:iam::123456789012:role/ComprehendMedicalRole \
  --language-code en
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Real-Time | [`real-time.md`](real-time.md) | detect-entities-v2, detect-phi, infer-icd10-cm, infer-rx-norm, infer-snomedct |
| Entity Detection Jobs | [`entity-detection-jobs.md`](entity-detection-jobs.md) | start-entities-detection-v2-job, describe-entities-detection-v2-job, list-entities-detection-v2-jobs, stop-entities-detection-v2-job |
| PHI Detection Jobs | [`phi-detection-jobs.md`](phi-detection-jobs.md) | start-phi-detection-job, describe-phi-detection-job, list-phi-detection-jobs, stop-phi-detection-job |
| Medical Code Jobs | [`medical-code-jobs.md`](medical-code-jobs.md) | start-icd10-cm-inference-job, describe-icd10-cm-inference-job, list-icd10-cm-inference-jobs, stop-icd10-cm-inference-job, start-rx-norm-inference-job, describe-rx-norm-inference-job, list-rx-norm-inference-jobs, stop-rx-norm-inference-job, start-snomedct-inference-job, describe-snomedct-inference-job, list-snomedct-inference-jobs, stop-snomedct-inference-job |
