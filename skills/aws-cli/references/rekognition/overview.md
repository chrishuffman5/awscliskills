# AWS CLI v2 — Rekognition (Image and Video Analysis)

## Overview

Complete reference for all `aws rekognition` subcommands in AWS CLI v2. Covers image analysis (label detection, face detection, text detection, moderation, celebrity recognition, protective equipment), face collections and user management, face liveness detection, stored video analysis, streaming video processing, media analysis jobs, Custom Labels projects, and tagging.

## Quick Reference — Common Workflows

### Detect labels (objects/scenes) in an image
```bash
aws rekognition detect-labels \
  --image '{"S3Object":{"Bucket":"my-bucket","Name":"photo.jpg"}}' \
  --max-labels 20 --min-confidence 75
```

### Detect faces in an image
```bash
aws rekognition detect-faces \
  --image '{"S3Object":{"Bucket":"my-bucket","Name":"photo.jpg"}}' \
  --attributes ALL
```

### Compare faces between two images
```bash
aws rekognition compare-faces \
  --source-image '{"S3Object":{"Bucket":"my-bucket","Name":"source.jpg"}}' \
  --target-image '{"S3Object":{"Bucket":"my-bucket","Name":"target.jpg"}}' \
  --similarity-threshold 90
```

### Create a face collection and index faces
```bash
aws rekognition create-collection --collection-id my-faces
aws rekognition index-faces \
  --collection-id my-faces \
  --image '{"S3Object":{"Bucket":"my-bucket","Name":"person.jpg"}}' \
  --external-image-id "person-001"
```

### Search for matching faces by image
```bash
aws rekognition search-faces-by-image \
  --collection-id my-faces \
  --image '{"S3Object":{"Bucket":"my-bucket","Name":"query.jpg"}}' \
  --face-match-threshold 85
```

### Start video label detection
```bash
aws rekognition start-label-detection \
  --video '{"S3Object":{"Bucket":"my-bucket","Name":"video.mp4"}}' \
  --min-confidence 70 \
  --notification-channel "SNSTopicArn=arn:aws:sns:us-east-1:111122223333:my-topic,RoleArn=arn:aws:iam::111122223333:role/RekRole"
```

### Detect moderation labels (inappropriate content)
```bash
aws rekognition detect-moderation-labels \
  --image '{"S3Object":{"Bucket":"my-bucket","Name":"image.jpg"}}' \
  --min-confidence 60
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Image Analysis | [`image-analysis.md`](image-analysis.md) | detect-labels, detect-faces, detect-text, detect-moderation-labels, detect-protective-equipment, compare-faces, recognize-celebrities, get-celebrity-info |
| Collections | [`collections.md`](collections.md) | create-collection, delete-collection, describe-collection, list-collections, index-faces, delete-faces, list-faces, search-faces, search-faces-by-image |
| Users | [`users.md`](users.md) | create-user, delete-user, list-users, associate-faces, disassociate-faces, search-users, search-users-by-image |
| Face Liveness | [`face-liveness.md`](face-liveness.md) | create-face-liveness-session, get-face-liveness-session-results |
| Video Analysis | [`video-analysis.md`](video-analysis.md) | start-label-detection, get-label-detection, start-face-detection, get-face-detection, start-face-search, get-face-search, start-celebrity-recognition, get-celebrity-recognition, start-content-moderation, get-content-moderation, start-person-tracking, get-person-tracking, start-segment-detection, get-segment-detection, start-text-detection, get-text-detection |
| Media Analysis | [`media-analysis.md`](media-analysis.md) | start-media-analysis-job, get-media-analysis-job, list-media-analysis-jobs |
| Stream Processors | [`stream-processors.md`](stream-processors.md) | create-stream-processor, delete-stream-processor, describe-stream-processor, list-stream-processors, start-stream-processor, stop-stream-processor, update-stream-processor |
| Projects | [`projects.md`](projects.md) | create-project, delete-project, describe-projects, create-project-version, delete-project-version, describe-project-versions, copy-project-version, start-project-version, stop-project-version, detect-custom-labels, put-project-policy, delete-project-policy, list-project-policies |
| Datasets | [`datasets.md`](datasets.md) | create-dataset, delete-dataset, describe-dataset, list-dataset-entries, list-dataset-labels, update-dataset-entries, distribute-dataset-entries |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
| Wait | [`wait.md`](wait.md) | wait project-version-running, wait project-version-training-completed |
