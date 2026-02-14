# AWS CLI v2 — MediaPackage

## Overview

Complete reference for `aws mediapackagev2` and `aws mediapackage-vod` subcommands in AWS CLI v2. Covers live packaging (MediaPackage v2) with channel groups, channels, origin endpoints, and harvest jobs, as well as video-on-demand packaging (MediaPackage VOD) with assets, packaging configurations, and packaging groups. MediaPackage prepares and protects video for delivery over the internet using just-in-time format conversion and DRM encryption.

## Quick Reference — Common Workflows

### Create a live channel group and channel (v2)
```bash
aws mediapackagev2 create-channel-group \
    --channel-group-name my-channel-group \
    --description "Production live channels"

aws mediapackagev2 create-channel \
    --channel-group-name my-channel-group \
    --channel-name my-live-channel \
    --input-type HLS
```

### Create an HLS origin endpoint (v2)
```bash
aws mediapackagev2 create-origin-endpoint \
    --channel-group-name my-channel-group \
    --channel-name my-live-channel \
    --origin-endpoint-name my-hls-endpoint \
    --container-type TS \
    --hls-manifests '[{"ManifestName":"index","ChildManifestName":"child","ManifestWindowSeconds":60}]' \
    --startover-window-seconds 86400
```

### Create a harvest job to clip live content (v2)
```bash
aws mediapackagev2 create-harvest-job \
    --channel-group-name my-channel-group \
    --channel-name my-live-channel \
    --origin-endpoint-name my-hls-endpoint \
    --harvested-manifests '{"HlsManifests":[{"ManifestName":"index"}]}' \
    --schedule-configuration '{"StartTime":"2025-01-01T00:00:00Z","EndTime":"2025-01-01T01:00:00Z"}' \
    --destination '{"S3Destination":{"BucketName":"my-harvest-bucket","DestinationPath":"clips/"}}'
```

### Create a VOD packaging group and configuration
```bash
aws mediapackage-vod create-packaging-group \
    --id my-vod-group

aws mediapackage-vod create-packaging-configuration \
    --id hls-config \
    --packaging-group-id my-vod-group \
    --hls-package '{"HlsManifests":[{"AdMarkers":"NONE","ManifestName":"index","ProgramDateTimeIntervalSeconds":0}],"SegmentDurationSeconds":6}'
```

### Ingest a VOD asset
```bash
aws mediapackage-vod create-asset \
    --id my-video-asset \
    --packaging-group-id my-vod-group \
    --source-arn arn:aws:s3:::my-bucket/video.smil \
    --source-role-arn arn:aws:iam::123456789012:role/MediaPackageVODRole
```

## Command Reference

| Group | File | Commands |
|-------|------|----------|
| Channel Groups | [channel-groups.md](channel-groups.md) | `mediapackagev2 create-channel-group`, `get-channel-group`, `list-channel-groups`, `update-channel-group`, `delete-channel-group` |
| Channels | [channels.md](channels.md) | `mediapackagev2 create-channel`, `get-channel`, `list-channels`, `update-channel`, `delete-channel`, `put-channel-policy`, `get-channel-policy`, `delete-channel-policy`, `reset-channel-state` |
| Origin Endpoints | [origin-endpoints.md](origin-endpoints.md) | `mediapackagev2 create-origin-endpoint`, `get-origin-endpoint`, `list-origin-endpoints`, `update-origin-endpoint`, `delete-origin-endpoint`, `put-origin-endpoint-policy`, `get-origin-endpoint-policy`, `delete-origin-endpoint-policy`, `reset-origin-endpoint-state` |
| Harvest Jobs | [harvest-jobs.md](harvest-jobs.md) | `mediapackagev2 create-harvest-job`, `get-harvest-job`, `list-harvest-jobs`, `cancel-harvest-job` |
| Packaging Groups | [packaging-groups.md](packaging-groups.md) | `mediapackage-vod create-packaging-group`, `describe-packaging-group`, `list-packaging-groups`, `update-packaging-group`, `delete-packaging-group`, `configure-logs` |
| Packaging Configurations | [packaging-configurations.md](packaging-configurations.md) | `mediapackage-vod create-packaging-configuration`, `describe-packaging-configuration`, `list-packaging-configurations`, `delete-packaging-configuration` |
| Assets | [assets.md](assets.md) | `mediapackage-vod create-asset`, `describe-asset`, `list-assets`, `delete-asset` |
| Tags | [tags.md](tags.md) | `mediapackagev2 tag-resource`, `untag-resource`, `list-tags-for-resource`, `mediapackage-vod tag-resource`, `untag-resource`, `list-tags-for-resource` |
