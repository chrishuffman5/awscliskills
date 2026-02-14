# AWS CLI v2 — Elastic Transcoder

## Overview

Complete reference for all `aws elastictranscoder` subcommands in AWS CLI v2. Covers transcoding pipelines, jobs, and presets. Amazon Elastic Transcoder is a legacy media transcoding service in the cloud. For new workloads, AWS recommends using AWS Elemental MediaConvert instead.

**Note:** Elastic Transcoder is a legacy service. AWS Elemental MediaConvert provides more features, broader codec support, and is recommended for all new video transcoding workloads.

## Quick Reference — Common Workflows

### Create a pipeline
```bash
aws elastictranscoder create-pipeline \
    --name "my-pipeline" \
    --input-bucket my-input-bucket \
    --output-bucket my-output-bucket \
    --role arn:aws:iam::123456789012:role/ElasticTranscoderRole
```

### Create a transcoding job
```bash
aws elastictranscoder create-job \
    --pipeline-id 1234567890123-abcdef \
    --inputs '[{"Key":"input/video.mp4"}]' \
    --outputs '[{"Key":"output/video.mp4","PresetId":"1351620000001-000010"}]' \
    --output-key-prefix "output/"
```

### List pipelines and check status
```bash
aws elastictranscoder list-pipelines \
    --query 'Pipelines[].{Id:Id,Name:Name,Status:Status}'

aws elastictranscoder read-pipeline \
    --id 1234567890123-abcdef
```

### List jobs by pipeline or status
```bash
aws elastictranscoder list-jobs-by-pipeline \
    --pipeline-id 1234567890123-abcdef \
    --query 'Jobs[].{Id:Id,Status:Status}'

aws elastictranscoder list-jobs-by-status \
    --status Complete
```

### Create a custom preset
```bash
aws elastictranscoder create-preset \
    --name "720p-H264" \
    --container mp4 \
    --video file://video-settings.json \
    --audio file://audio-settings.json \
    --thumbnails file://thumbnail-settings.json
```

## Command Reference

| Group | File | Commands |
|-------|------|----------|
| Pipelines | [pipelines.md](pipelines.md) | `create-pipeline`, `read-pipeline`, `update-pipeline`, `update-pipeline-notifications`, `update-pipeline-status`, `delete-pipeline`, `list-pipelines` |
| Jobs | [jobs.md](jobs.md) | `create-job`, `read-job`, `cancel-job`, `list-jobs-by-pipeline`, `list-jobs-by-status` |
| Presets | [presets.md](presets.md) | `create-preset`, `read-preset`, `delete-preset`, `list-presets` |
