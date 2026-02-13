# AWS CLI v2 — DataSync

## Overview

Complete reference for all `aws datasync` subcommands in AWS CLI v2. AWS DataSync is an online data movement service that automates transferring data between on-premises storage, AWS storage services, and other cloud storage. Supports NFS, SMB, HDFS, object storage, Amazon S3, Amazon EFS, Amazon FSx, and Azure Blob Storage as source/destination locations.

## Quick Reference — Common Workflows

### Activate an agent and create an NFS-to-S3 transfer task
```bash
aws datasync create-agent \
  --activation-key AAAAA-BBBBB-CCCCC-DDDDD-EEEEE \
  --agent-name my-agent

aws datasync create-location-nfs \
  --server-hostname nfs.example.com \
  --subdirectory /export/data \
  --on-prem-config AgentArns=arn:aws:datasync:us-east-1:123456789012:agent/agent-0123456789abcdef0

aws datasync create-location-s3 \
  --s3-bucket-arn arn:aws:s3:::my-destination-bucket \
  --s3-config BucketAccessRoleArn=arn:aws:iam::123456789012:role/DataSyncS3Role \
  --subdirectory /synced-data

aws datasync create-task \
  --source-location-arn arn:aws:datasync:us-east-1:123456789012:location/loc-0123456789abcdef0 \
  --destination-location-arn arn:aws:datasync:us-east-1:123456789012:location/loc-abcdef0123456789a \
  --name nfs-to-s3-sync \
  --options VerifyMode=ONLY_FILES_TRANSFERRED,OverwriteMode=ALWAYS
```

### Start a task execution and monitor it
```bash
aws datasync start-task-execution \
  --task-arn arn:aws:datasync:us-east-1:123456789012:task/task-0123456789abcdef0

aws datasync describe-task-execution \
  --task-execution-arn arn:aws:datasync:us-east-1:123456789012:task/task-0123456789abcdef0/execution/exec-0123456789abcdef0
```

### Create an EFS location
```bash
aws datasync create-location-efs \
  --efs-filesystem-arn arn:aws:elasticfilesystem:us-east-1:123456789012:file-system/fs-0123abcd \
  --ec2-config SubnetArn=arn:aws:ec2:us-east-1:123456789012:subnet/subnet-abc123,SecurityGroupArns=arn:aws:ec2:us-east-1:123456789012:security-group/sg-def456 \
  --subdirectory /data
```

### Create an FSx for Windows location
```bash
aws datasync create-location-fsx-windows \
  --fsx-filesystem-arn arn:aws:fsx:us-east-1:123456789012:file-system/fs-0123abcd \
  --security-group-arns arn:aws:ec2:us-east-1:123456789012:security-group/sg-def456 \
  --user Admin \
  --password MyPassword123 \
  --subdirectory /share
```

### Create a scheduled task with bandwidth limit
```bash
aws datasync create-task \
  --source-location-arn arn:aws:datasync:us-east-1:123456789012:location/loc-src123 \
  --destination-location-arn arn:aws:datasync:us-east-1:123456789012:location/loc-dst456 \
  --name nightly-sync \
  --schedule ScheduleExpression="cron(0 1 * * ? *)" \
  --options BytesPerSecond=10485760,TransferMode=CHANGED,LogLevel=BASIC \
  --cloud-watch-log-group-arn arn:aws:logs:us-east-1:123456789012:log-group:/aws/datasync:*
```

## Command Reference

See [`index.md`](index.md) for the quick reference table and global options.

| Group | File | Commands |
|-------|------|----------|
| Agents | [`agents.md`](agents.md) | create-agent, delete-agent, describe-agent, list-agents, update-agent |
| Tasks | [`tasks.md`](tasks.md) | create-task, delete-task, describe-task, list-tasks, update-task, start-task-execution, cancel-task-execution, describe-task-execution, list-task-executions, update-task-execution |
| Locations (S3 & EFS) | [`locations-s3-efs.md`](locations-s3-efs.md) | create-location-s3, describe-location-s3, update-location-s3, create-location-efs, describe-location-efs, update-location-efs |
| Locations (FSx) | [`locations-fsx.md`](locations-fsx.md) | create-location-fsx-windows, create-location-fsx-lustre, create-location-fsx-ontap, create-location-fsx-open-zfs, describe-location-fsx-*, update-location-fsx-* |
| Locations (Network) | [`locations-network.md`](locations-network.md) | create-location-nfs, create-location-smb, create-location-hdfs, describe-location-nfs, describe-location-smb, describe-location-hdfs, update-location-nfs, update-location-smb, update-location-hdfs |
| Locations (Common) | [`locations-common.md`](locations-common.md) | create-location-object-storage, create-location-azure-blob, describe-location-object-storage, describe-location-azure-blob, update-location-object-storage, update-location-azure-blob, delete-location, list-locations |
| Tags | [`tags.md`](tags.md) | tag-resource, untag-resource, list-tags-for-resource |
