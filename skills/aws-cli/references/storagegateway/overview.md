# AWS CLI v2 — Storage Gateway

## Overview

Complete reference for all `aws storagegateway` subcommands in AWS CLI v2. Covers gateway lifecycle management, NFS and SMB file shares, SMB settings and Active Directory, cached and stored iSCSI volumes, virtual tapes, cache and upload buffer management, bandwidth rate limits, FSx file system associations, and CHAP authentication and tags. Storage Gateway supports File Gateway (S3 and FSx), Volume Gateway (cached and stored), and Tape Gateway types.

## Quick Reference — Common Workflows

### Activate a gateway
```bash
aws storagegateway activate-gateway \
  --activation-key ABCDE12345 \
  --gateway-name my-gateway \
  --gateway-timezone GMT-5:00 \
  --gateway-region us-east-1 \
  --gateway-type FILE_S3
```

### Create an NFS file share
```bash
aws storagegateway create-nfs-file-share \
  --client-token unique-token-123 \
  --gateway-arn arn:aws:storagegateway:us-east-1:123456789012:gateway/sgw-12345678 \
  --role arn:aws:iam::123456789012:role/StorageGatewayRole \
  --location-arn arn:aws:s3:::my-bucket/ \
  --default-storage-class S3_STANDARD \
  --squash RootSquash
```

### Create an SMB file share
```bash
aws storagegateway create-smb-file-share \
  --client-token unique-token-456 \
  --gateway-arn arn:aws:storagegateway:us-east-1:123456789012:gateway/sgw-12345678 \
  --role arn:aws:iam::123456789012:role/StorageGatewayRole \
  --location-arn arn:aws:s3:::my-bucket/ \
  --authentication ActiveDirectory
```

### Create a cached iSCSI volume
```bash
aws storagegateway create-cached-iscsi-volume \
  --gateway-arn arn:aws:storagegateway:us-east-1:123456789012:gateway/sgw-12345678 \
  --volume-size-in-bytes 107374182400 \
  --target-name my-volume \
  --network-interface-id 10.0.0.1 \
  --client-token unique-token-789
```

### Create virtual tapes
```bash
aws storagegateway create-tapes \
  --gateway-arn arn:aws:storagegateway:us-east-1:123456789012:gateway/sgw-12345678 \
  --tape-size-in-bytes 107374182400 \
  --client-token unique-token-abc \
  --num-tapes-to-create 5 \
  --tape-barcode-prefix ABC
```

### Set bandwidth rate limits
```bash
aws storagegateway update-bandwidth-rate-limit \
  --gateway-arn arn:aws:storagegateway:us-east-1:123456789012:gateway/sgw-12345678 \
  --average-upload-rate-limit-in-bits-per-sec 51200 \
  --average-download-rate-limit-in-bits-per-sec 102400
```

### Add cache disks to a gateway
```bash
aws storagegateway add-cache \
  --gateway-arn arn:aws:storagegateway:us-east-1:123456789012:gateway/sgw-12345678 \
  --disk-ids disk-id-1 disk-id-2
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Gateways | [`gateways.md`](gateways.md) | activate-gateway, describe-gateway-information, update-gateway-information, update-gateway-software-now, shutdown-gateway, start-gateway, disable-gateway, delete-gateway, list-gateways, list-local-disks, describe-maintenance-start-time, update-maintenance-start-time, start-availability-monitor-test, describe-availability-monitor-test, set-local-console-password |
| File Shares | [`file-shares.md`](file-shares.md) | create-nfs-file-share, update-nfs-file-share, describe-nfs-file-shares, create-smb-file-share, update-smb-file-share, describe-smb-file-shares, delete-file-share, list-file-shares, refresh-cache, notify-when-uploaded, evict-files-failing-upload, start-cache-report, describe-cache-report, list-cache-reports, cancel-cache-report, delete-cache-report |
| SMB Settings | [`smb-settings.md`](smb-settings.md) | describe-smb-settings, join-domain, set-smb-guest-password, update-smb-security-strategy, update-smb-file-share-visibility, update-smb-local-groups |
| Volumes | [`volumes.md`](volumes.md) | create-cached-iscsi-volume, create-stored-iscsi-volume, describe-cached-iscsi-volumes, describe-stored-iscsi-volumes, attach-volume, detach-volume, delete-volume, list-volumes, list-volume-initiators, list-volume-recovery-points, create-snapshot, create-snapshot-from-volume-recovery-point, describe-snapshot-schedule, update-snapshot-schedule, delete-snapshot-schedule, add-upload-buffer, describe-upload-buffer, add-working-storage, describe-working-storage |
| Tapes | [`tapes.md`](tapes.md) | create-tapes, create-tape-with-barcode, describe-tapes, list-tapes, delete-tape, delete-tape-archive, describe-tape-archives, describe-tape-recovery-points, retrieve-tape-archive, retrieve-tape-recovery-point, assign-tape-pool, cancel-archival, cancel-retrieval, create-tape-pool, delete-tape-pool, list-tape-pools, list-automatic-tape-creation-policies, update-automatic-tape-creation-policy, delete-automatic-tape-creation-policy, describe-vtl-devices, update-vtl-device-type |
| Cache | [`cache.md`](cache.md) | add-cache, describe-cache, reset-cache |
| Bandwidth | [`bandwidth.md`](bandwidth.md) | update-bandwidth-rate-limit, describe-bandwidth-rate-limit, delete-bandwidth-rate-limit, update-bandwidth-rate-limit-schedule, describe-bandwidth-rate-limit-schedule |
| File System Associations | [`file-system-associations.md`](file-system-associations.md) | associate-file-system, disassociate-file-system, describe-file-system-associations, list-file-system-associations, update-file-system-association |
| CHAP & Tags | [`chap-tags.md`](chap-tags.md) | update-chap-credentials, describe-chap-credentials, delete-chap-credentials, add-tags-to-resource, remove-tags-from-resource, list-tags-for-resource |
