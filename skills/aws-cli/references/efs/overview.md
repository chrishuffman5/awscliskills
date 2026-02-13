# AWS CLI v2 — EFS (Elastic File System)

## Overview

Complete reference for all `aws efs` subcommands in AWS CLI v2. Covers file system management, mount targets, access points, replication configurations, lifecycle policies, backup policies, and tagging.

## Quick Reference — Common Workflows

### Create a file system
```bash
aws efs create-file-system --performance-mode generalPurpose \
  --throughput-mode bursting --encrypted \
  --tags Key=Name,Value=my-efs
```

### Create a mount target
```bash
aws efs create-mount-target --file-system-id fs-12345678 \
  --subnet-id subnet-abcdef12 \
  --security-groups sg-01234567
```

### Create an access point
```bash
aws efs create-access-point --file-system-id fs-12345678 \
  --posix-user Uid=1000,Gid=1000 \
  --root-directory "Path=/data,CreationInfo={OwnerUid=1000,OwnerGid=1000,Permissions=755}"
```

### Set lifecycle policy (transition to IA after 30 days)
```bash
aws efs put-lifecycle-configuration --file-system-id fs-12345678 \
  --lifecycle-policies TransitionToIA=AFTER_30_DAYS TransitionToPrimaryStorageClass=AFTER_1_ACCESS
```

### Enable automatic backups
```bash
aws efs put-backup-policy --file-system-id fs-12345678 \
  --backup-policy Status=ENABLED
```

### Create replication to another region
```bash
aws efs create-replication-configuration --source-file-system-id fs-12345678 \
  --destinations Region=us-west-2
```

### Describe file systems
```bash
aws efs describe-file-systems --query 'FileSystems[*].[FileSystemId,LifeCycleState,SizeInBytes.Value]'
```

### Mount using EFS mount helper (on EC2)
```bash
# Using file system ID
sudo mount -t efs fs-12345678:/ /mnt/efs
# Using access point
sudo mount -t efs -o tls,accesspoint=fsap-12345678 fs-12345678:/ /mnt/efs
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| File Systems | [`file-systems.md`](file-systems.md) | create-file-system, delete-file-system, describe-file-systems, update-file-system, put-lifecycle-configuration, describe-lifecycle-configuration, put-backup-policy, describe-backup-policy, put-file-system-policy, describe-file-system-policy, delete-file-system-policy |
| Mount Targets | [`mount-targets.md`](mount-targets.md) | create-mount-target, delete-mount-target, describe-mount-targets, describe-mount-target-security-groups, modify-mount-target-security-groups |
| Access Points | [`access-points.md`](access-points.md) | create-access-point, delete-access-point, describe-access-points |
| Replication | [`replication.md`](replication.md) | create-replication-configuration, delete-replication-configuration, describe-replication-configurations |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
