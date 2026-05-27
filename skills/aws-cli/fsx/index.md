# Amazon FSx Quick Reference

## All Commands

| Command | Category | Description |
|---------|----------|-------------|
| `associate-file-system-aliases` | File Systems | Associate DNS aliases with a Windows file system |
| `cancel-data-repository-task` | Data Repository | Cancel a running data repository task |
| `copy-backup` | Backups | Copy a backup to another region or account |
| `copy-snapshot-and-update-volume` | Volumes | Copy snapshot and update volume with it |
| `create-and-attach-s3-access-point` | S3 Access Points | Create and attach an S3 access point |
| `create-backup` | Backups | Create an on-demand backup |
| `create-data-repository-association` | Data Repository | Link a file system path to an S3/NFS repository |
| `create-data-repository-task` | Data Repository | Export, import, or release data |
| `create-file-cache` | File Caches | Create a Lustre file cache |
| `create-file-system` | File Systems | Create a new file system |
| `create-file-system-from-backup` | Backups | Restore a file system from backup |
| `create-snapshot` | Snapshots | Create a volume snapshot (ONTAP/OpenZFS) |
| `create-storage-virtual-machine` | SVMs | Create an ONTAP storage virtual machine |
| `create-volume` | Volumes | Create an ONTAP or OpenZFS volume |
| `create-volume-from-backup` | Volumes | Create an ONTAP volume from backup |
| `delete-backup` | Backups | Delete a backup |
| `delete-data-repository-association` | Data Repository | Remove a data repository link |
| `delete-file-cache` | File Caches | Delete a file cache |
| `delete-file-system` | File Systems | Delete a file system |
| `delete-snapshot` | Snapshots | Delete a snapshot |
| `delete-storage-virtual-machine` | SVMs | Delete an ONTAP SVM |
| `delete-volume` | Volumes | Delete a volume |
| `describe-backups` | Backups | Describe one or more backups |
| `describe-data-repository-associations` | Data Repository | Describe data repository associations |
| `describe-data-repository-tasks` | Data Repository | Describe data repository tasks |
| `describe-file-caches` | File Caches | Describe file caches |
| `describe-file-system-aliases` | File Systems | Describe DNS aliases for a file system |
| `describe-file-systems` | File Systems | Describe one or more file systems |
| `describe-s3-access-point-attachments` | S3 Access Points | Describe S3 access point attachments |
| `describe-shared-vpc-configuration` | File Systems | Describe shared VPC configuration |
| `describe-snapshots` | Snapshots | Describe one or more snapshots |
| `describe-storage-virtual-machines` | SVMs | Describe one or more SVMs |
| `describe-volumes` | Volumes | Describe one or more volumes |
| `detach-and-delete-s3-access-point` | S3 Access Points | Detach and delete an S3 access point |
| `disassociate-file-system-aliases` | File Systems | Remove DNS aliases from a file system |
| `list-tags-for-resource` | Tags | List tags on a resource |
| `release-file-system-nfs-v3-locks` | File Systems | Release NFS v3 locks on a file system |
| `restore-volume-from-snapshot` | Volumes | Restore a volume to a snapshot point |
| `start-misconfigured-state-recovery` | File Systems | Recover a misconfigured file system |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `update-data-repository-association` | Data Repository | Update a data repository association |
| `update-file-cache` | File Caches | Update a file cache |
| `update-file-system` | File Systems | Update a file system configuration |
| `update-shared-vpc-configuration` | File Systems | Update shared VPC configuration |
| `update-snapshot` | Snapshots | Rename a snapshot |
| `update-storage-virtual-machine` | SVMs | Update an ONTAP SVM |
| `update-volume` | Volumes | Update a volume configuration |

---

## Global Options

| Option | Type | Description |
|--------|------|-------------|
| `--output` | string | `json`, `text`, `table`, `yaml`, `yaml-stream` |
| `--query` | string | JMESPath query for filtering |
| `--region` | string | AWS region |
| `--profile` | string | Named credential profile |
| `--no-paginate` | boolean | Disable auto-pagination |
| `--cli-input-json` | string | Read params from JSON |
| `--generate-cli-skeleton` | string | Print param skeleton |

---

## Common Patterns

**File System Types:**
- `WINDOWS` -- Windows File Server (SMB, AD integration)
- `LUSTRE` -- High-performance parallel file system (HPC, ML)
- `ONTAP` -- NetApp ONTAP (NFS, SMB, iSCSI, multi-protocol)
- `OPENZFS` -- OpenZFS (NFS, snapshots, clones)

**ID Formats:**
- File System: `fs-0123456789abcdef0`
- Volume: `fsvol-0123456789abcdef0`
- Snapshot: `fsvolsnap-0123456789abcdef0`
- Backup: `backup-0123456789abcdef0`
- SVM: `svm-0123456789abcdef0`
- File Cache: `fc-0123456789abcdef0`
- Data Repository Association: `dra-0123456789abcdef0`
- Data Repository Task: `task-0123456789abcdef0`

**File System Lifecycle States:**
`AVAILABLE` | `CREATING` | `DELETING` | `FAILED` | `MISCONFIGURED` | `UPDATING` | `MISCONFIGURED_UNAVAILABLE`

**Storage Types:** `SSD` | `HDD` | `INTELLIGENT_TIERING`

**Deployment Types (by FS type):**
- Windows: `SINGLE_AZ_1`, `SINGLE_AZ_2`, `MULTI_AZ_1`
- Lustre: `SCRATCH_1`, `SCRATCH_2`, `PERSISTENT_1`, `PERSISTENT_2`
- ONTAP: `SINGLE_AZ_1`, `SINGLE_AZ_2`, `MULTI_AZ_1`, `MULTI_AZ_2`
- OpenZFS: `SINGLE_AZ_1`, `SINGLE_AZ_2`, `SINGLE_AZ_HA_1`, `SINGLE_AZ_HA_2`, `MULTI_AZ_1`
- File Cache: `CACHE_1`
