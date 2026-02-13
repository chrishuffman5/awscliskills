# AWS CLI v2 — Transcribe (Speech-to-Text)

## Overview

Complete reference for all `aws transcribe` subcommands in AWS CLI v2. Covers standard transcription jobs, call analytics transcription with speaker role assignment, medical transcription (primary care dictation and conversations), medical scribe jobs, custom vocabularies and vocabulary filters, custom language models, and tagging.

## Quick Reference — Common Workflows

### Start a standard transcription job
```bash
aws transcribe start-transcription-job \
  --transcription-job-name my-job \
  --language-code en-US \
  --media MediaFileUri=s3://my-bucket/audio.mp3 \
  --output-bucket-name my-output-bucket
```

### Start transcription with speaker identification
```bash
aws transcribe start-transcription-job \
  --transcription-job-name speaker-job \
  --language-code en-US \
  --media MediaFileUri=s3://my-bucket/meeting.mp3 \
  --settings ShowSpeakerLabels=true,MaxSpeakerLabels=4
```

### Start a call analytics job
```bash
aws transcribe start-call-analytics-job \
  --call-analytics-job-name my-call-job \
  --media MediaFileUri=s3://my-bucket/call.mp3 \
  --output-location s3://my-bucket/output/ \
  --data-access-role-arn arn:aws:iam::111122223333:role/TranscribeRole \
  --channel-definitions ChannelId=0,ParticipantRole=AGENT ChannelId=1,ParticipantRole=CUSTOMER
```

### Start a medical transcription job
```bash
aws transcribe start-medical-transcription-job \
  --medical-transcription-job-name my-medical-job \
  --language-code en-US \
  --specialty PRIMARYCARE \
  --type DICTATION \
  --media MediaFileUri=s3://my-bucket/recording.wav \
  --output-bucket-name my-output-bucket
```

### Create a custom vocabulary
```bash
aws transcribe create-vocabulary \
  --vocabulary-name my-vocab \
  --language-code en-US \
  --vocabulary-file-uri s3://my-bucket/vocab.txt
```

### Create a custom language model
```bash
aws transcribe create-language-model \
  --language-code en-US \
  --base-model-name WideBand \
  --model-name my-model \
  --input-data-config S3Uri=s3://my-bucket/training/,DataAccessRoleArn=arn:aws:iam::111122223333:role/TranscribeRole
```

### Check job status
```bash
aws transcribe get-transcription-job \
  --transcription-job-name my-job \
  --query 'TranscriptionJob.TranscriptionJobStatus'
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Transcription Jobs | [`transcription-jobs.md`](transcription-jobs.md) | start-transcription-job, get-transcription-job, list-transcription-jobs, delete-transcription-job |
| Call Analytics | [`call-analytics.md`](call-analytics.md) | start-call-analytics-job, get-call-analytics-job, list-call-analytics-jobs, delete-call-analytics-job, create-call-analytics-category, get-call-analytics-category, list-call-analytics-categories, update-call-analytics-category, delete-call-analytics-category |
| Medical | [`medical.md`](medical.md) | start-medical-transcription-job, get-medical-transcription-job, list-medical-transcription-jobs, delete-medical-transcription-job, start-medical-scribe-job, get-medical-scribe-job, list-medical-scribe-jobs, delete-medical-scribe-job, create-medical-vocabulary, get-medical-vocabulary, list-medical-vocabularies, update-medical-vocabulary, delete-medical-vocabulary |
| Vocabularies | [`vocabularies.md`](vocabularies.md) | create-vocabulary, get-vocabulary, list-vocabularies, update-vocabulary, delete-vocabulary, create-vocabulary-filter, get-vocabulary-filter, list-vocabulary-filters, update-vocabulary-filter, delete-vocabulary-filter |
| Language Models | [`language-models.md`](language-models.md) | create-language-model, describe-language-model, list-language-models, delete-language-model |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
| Wait | [`wait.md`](wait.md) | wait vocabulary-ready |
