# AWS CLI v2 — MediaStore

## Overview

Complete reference for `aws mediastore` and `aws mediastore-data` subcommands in AWS CLI v2. Covers container management, access policies, CORS policies, lifecycle policies, metric policies, access logging, and object data operations. AWS Elemental MediaStore is an AWS storage service optimized for media, providing consistent low-latency performance for live and on-demand video workloads.

## Quick Reference — Common Workflows

### Create a container
```bash
aws mediastore create-container \
    --container-name my-media-container \
    --tags Key=environment,Value=production
```

### Set a container access policy
```bash
aws mediastore put-container-policy \
    --container-name my-media-container \
    --policy file://container-policy.json
```

### Configure CORS for browser-based playback
```bash
aws mediastore put-cors-policy \
    --container-name my-media-container \
    --cors-policy '[{"AllowedOrigins":["*"],"AllowedMethods":["GET","HEAD"],"AllowedHeaders":["*"],"MaxAgeSeconds":3000}]'
```

### Set a lifecycle policy to expire old objects
```bash
aws mediastore put-lifecycle-policy \
    --container-name my-media-container \
    --lifecycle-policy file://lifecycle-policy.json
```

### Enable access logging
```bash
aws mediastore start-access-logging \
    --container-name my-media-container
```

### Upload an object to a container
```bash
aws mediastore-data put-object \
    --endpoint https://aaabbbcccdddee.data.mediastore.us-west-2.amazonaws.com \
    --body video.mp4 \
    --path media/video.mp4 \
    --content-type video/mp4
```

### Download an object from a container
```bash
aws mediastore-data get-object \
    --endpoint https://aaabbbcccdddee.data.mediastore.us-west-2.amazonaws.com \
    --path media/video.mp4 \
    video.mp4
```

## Command Reference

| Group | File | Commands |
|-------|------|----------|
| Containers | [containers.md](containers.md) | `mediastore create-container`, `describe-container`, `list-containers`, `delete-container` |
| Policies | [policies.md](policies.md) | `mediastore put-container-policy`, `get-container-policy`, `delete-container-policy`, `put-cors-policy`, `get-cors-policy`, `delete-cors-policy`, `put-lifecycle-policy`, `get-lifecycle-policy`, `delete-lifecycle-policy`, `put-metric-policy`, `get-metric-policy`, `delete-metric-policy` |
| Access Logging | [logging.md](logging.md) | `mediastore start-access-logging`, `stop-access-logging` |
| Objects | [objects.md](objects.md) | `mediastore-data put-object`, `get-object`, `describe-object`, `list-items`, `delete-object` |
| Tags | [tags.md](tags.md) | `mediastore tag-resource`, `untag-resource`, `list-tags-for-resource` |
