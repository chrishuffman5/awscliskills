# Amazon FSx CLI Reference

> **Service:** Amazon FSx (`aws fsx`)

Amazon FSx provides fully managed file systems optimized for a variety of workloads. It supports four file system types: **Windows File Server**, **Lustre**, **NetApp ONTAP**, and **OpenZFS**.

## Common Workflows

### 1. Create a Windows File Server File System
```bash
aws fsx create-file-system \
    --file-system-type WINDOWS \
    --storage-capacity 300 \
    --subnet-ids subnet-0123456789abcdef0 \
    --security-group-ids sg-0123456789abcdef0 \
    --windows-configuration \
        ThroughputCapacity=32,DeploymentType=SINGLE_AZ_2,\
ActiveDirectoryId=d-0123456789

# Monitor creation
aws fsx describe-file-systems --file-system-ids fs-0123456789abcdef0
```

### 2. Create an ONTAP File System with SVM and Volume
```bash
# Create file system
aws fsx create-file-system \
    --file-system-type ONTAP \
    --storage-capacity 1024 \
    --subnet-ids subnet-aaa subnet-bbb \
    --ontap-configuration \
        DeploymentType=MULTI_AZ_1,ThroughputCapacity=512,\
PreferredSubnetId=subnet-aaa

# Create storage virtual machine
aws fsx create-storage-virtual-machine \
    --file-system-id fs-0123456789abcdef0 \
    --name svm1 \
    --root-volume-security-style UNIX

# Create volume on the SVM
aws fsx create-volume \
    --volume-type ONTAP \
    --name vol1 \
    --ontap-configuration \
        JunctionPath=/vol1,StorageVirtualMachineId=svm-0123456789abcdef0,\
SizeInMegabytes=102400,StorageEfficiencyEnabled=true
```

### 3. Create a Lustre File System Linked to S3
```bash
aws fsx create-file-system \
    --file-system-type LUSTRE \
    --storage-capacity 1200 \
    --subnet-ids subnet-0123456789abcdef0 \
    --lustre-configuration \
        DeploymentType=PERSISTENT_2,PerUnitStorageThroughput=250

# Link to S3 data repository
aws fsx create-data-repository-association \
    --file-system-id fs-0123456789abcdef0 \
    --file-system-path /ns1/ \
    --data-repository-path s3://my-bucket/prefix/ \
    --s3 '{"AutoImportPolicy":{"Events":["NEW","CHANGED","DELETED"]},"AutoExportPolicy":{"Events":["NEW","CHANGED","DELETED"]}}'
```

### 4. Back Up and Restore a File System
```bash
# Create backup
aws fsx create-backup --file-system-id fs-0123456789abcdef0 \
    --tags Key=Purpose,Value=weekly-backup

# List backups
aws fsx describe-backups

# Restore from backup
aws fsx create-file-system-from-backup \
    --backup-id backup-0123456789abcdef0 \
    --subnet-ids subnet-0123456789abcdef0 \
    --security-group-ids sg-0123456789abcdef0
```

### 5. Manage OpenZFS Snapshots and Volumes
```bash
# Create snapshot
aws fsx create-snapshot --name daily-snap \
    --volume-id fsvol-0123456789abcdef0

# Create volume from snapshot (clone)
aws fsx create-volume --volume-type OPENZFS --name cloned-vol \
    --open-zfs-configuration \
        ParentVolumeId=fsvol-0123456789abcdef0,\
OriginSnapshot={SnapshotARN=arn:aws:fsx:us-east-1:123456789012:snapshot/fsvolsnap-0123456789abcdef0,CopyStrategy=CLONE}
```

### 6. Create a Lustre File Cache
```bash
aws fsx create-file-cache \
    --file-cache-type LUSTRE \
    --file-cache-type-version "2.12" \
    --storage-capacity 1200 \
    --subnet-ids subnet-0123456789abcdef0 \
    --lustre-configuration \
        DeploymentType=CACHE_1,PerUnitStorageThroughput=1000,\
MetadataConfiguration={StorageCapacity=2400}
```

### 7. Run a Data Repository Task
```bash
# Export data to S3
aws fsx create-data-repository-task \
    --type EXPORT_TO_REPOSITORY \
    --file-system-id fs-0123456789abcdef0 \
    --paths /ns1/dir1/ \
    --report Enabled=true,Path=s3://my-bucket/reports/,Format=REPORT_CSV_20191124,Scope=FAILED_FILES_ONLY

# Check task status
aws fsx describe-data-repository-tasks \
    --filters Name=task-id,Values=task-0123456789abcdef0
```

---

## Command Reference

| Group | File | Commands | Description |
|-------|------|----------|-------------|
| 1. File Systems | [file-systems.md](file-systems.md) | 8 | Create, describe, update, delete file systems; aliases; shared VPC; NFS locks; misconfigured recovery |
| 2. Backups | [backups.md](backups.md) | 4 | Create, copy, describe, delete backups; restore from backup |
| 3. Volumes | [volumes.md](volumes.md) | 7 | Create, describe, update, delete volumes; create from backup; snapshot copy; restore |
| 4. Snapshots | [snapshots.md](snapshots.md) | 4 | Create, describe, update, delete snapshots |
| 5. Storage Virtual Machines | [storage-virtual-machines.md](storage-virtual-machines.md) | 4 | Create, describe, update, delete SVMs (ONTAP) |
| 6. Data Repository | [data-repository.md](data-repository.md) | 7 | Associations and tasks for Lustre-S3/NFS data linking |
| 7. File Caches | [file-caches.md](file-caches.md) | 4 | Create, describe, update, delete Lustre file caches |
| 8. S3 Access Points | [s3-access-points.md](s3-access-points.md) | 3 | Create, describe, detach S3 access point attachments |
| 9. Tags | [tags.md](tags.md) | 3 | Tag, untag, list tags for FSx resources |
