# AWS CLI v2 — MediaConvert

## Overview

Complete reference for all `aws mediaconvert` subcommands in AWS CLI v2. Covers transcoding job creation and management, job templates, output presets, processing queues, input policies, DRM certificate management, media file probing, job engine versions, advanced job queries, and resource tagging. AWS Elemental MediaConvert is a file-based video transcoding service that converts media files into formats required for broadcast and internet streaming.

## Quick Reference — Common Workflows

### Create a transcoding job
```bash
aws mediaconvert create-job \
    --role arn:aws:iam::123456789012:role/MediaConvertRole \
    --settings file://job-settings.json \
    --queue arn:aws:mediaconvert:us-east-1:123456789012:queues/Default \
    --priority 0
```

### Check job status
```bash
aws mediaconvert get-job \
    --id 1234567890123-abcdef

aws mediaconvert list-jobs \
    --status PROGRESSING \
    --query 'Jobs[].{Id:Id,Status:Status,Percent:JobPercentComplete}'
```

### Create a job template and preset
```bash
aws mediaconvert create-preset \
    --name "HD-H264-AAC" \
    --settings file://preset-settings.json

aws mediaconvert create-job-template \
    --name "StandardHLS" \
    --settings file://template-settings.json \
    --queue arn:aws:mediaconvert:us-east-1:123456789012:queues/Default
```

### Manage queues
```bash
aws mediaconvert create-queue \
    --name "HighPriority" \
    --description "Queue for high-priority jobs" \
    --status ACTIVE

aws mediaconvert list-queues \
    --query 'Queues[].{Name:Name,Status:Status,Progressing:ProgressingJobsCount}'
```

### Probe a media file
```bash
aws mediaconvert probe \
    --input-files '[{"FileUrl":"s3://my-bucket/input/video.mp4"}]'
```

### Search jobs with advanced filtering
```bash
aws mediaconvert start-jobs-query \
    --filter-list '[{"Key":"status","Values":["COMPLETE"]},{"Key":"videoCodec","Values":["H_264"]}]' \
    --max-results 20

aws mediaconvert get-jobs-query-results --id <query-id>
```

## Command Reference

| Group | File | Commands |
|-------|------|----------|
| Jobs | [jobs.md](jobs.md) | `create-job`, `get-job`, `cancel-job`, `list-jobs`, `search-jobs` |
| Job Templates | [job-templates.md](job-templates.md) | `create-job-template`, `get-job-template`, `update-job-template`, `list-job-templates`, `delete-job-template` |
| Presets | [presets.md](presets.md) | `create-preset`, `get-preset`, `update-preset`, `list-presets`, `delete-preset` |
| Queues | [queues.md](queues.md) | `create-queue`, `get-queue`, `update-queue`, `list-queues`, `delete-queue` |
| Policies | [policies.md](policies.md) | `put-policy`, `get-policy`, `delete-policy` |
| Certificates | [certificates.md](certificates.md) | `associate-certificate`, `disassociate-certificate` |
| Versions & Probe | [versions-probe.md](versions-probe.md) | `list-versions`, `probe` |
| Jobs Query & Resource Share | [jobs-query.md](jobs-query.md) | `start-jobs-query`, `get-jobs-query-results`, `create-resource-share` |
| Tags | [tags.md](tags.md) | `tag-resource`, `untag-resource`, `list-tags-for-resource` |
