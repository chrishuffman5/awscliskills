# AWS CLI v2 -- Storage Gateway Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/storagegateway/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `activate-gateway` | Gateway | Activate a Storage Gateway appliance |
| `describe-gateway-information` | Gateway | Get gateway metadata and configuration |
| `update-gateway-information` | Gateway | Update gateway name, timezone, or CloudWatch logs |
| `update-gateway-software-now` | Gateway | Trigger immediate gateway software update |
| `shutdown-gateway` | Gateway | Shut down a gateway |
| `start-gateway` | Gateway | Start a previously shut down gateway |
| `disable-gateway` | Gateway | Disable a gateway (tape gateway only) |
| `delete-gateway` | Gateway | Delete a gateway and its resources |
| `list-gateways` | Gateway | List all gateways in the account |
| `list-local-disks` | Gateway | List local disks on a gateway |
| `describe-maintenance-start-time` | Gateway | Get maintenance window schedule |
| `update-maintenance-start-time` | Gateway | Update maintenance window schedule |
| `start-availability-monitor-test` | Gateway | Start an availability monitor test |
| `describe-availability-monitor-test` | Gateway | Describe availability monitor test status |
| `set-local-console-password` | Gateway | Set the local console password |
| `create-nfs-file-share` | File Share | Create an NFS file share on S3 File Gateway |
| `update-nfs-file-share` | File Share | Update NFS file share settings |
| `describe-nfs-file-shares` | File Share | Describe NFS file shares |
| `create-smb-file-share` | File Share | Create an SMB file share on S3 File Gateway |
| `update-smb-file-share` | File Share | Update SMB file share settings |
| `describe-smb-file-shares` | File Share | Describe SMB file shares |
| `delete-file-share` | File Share | Delete a file share |
| `list-file-shares` | File Share | List file shares on a gateway |
| `refresh-cache` | File Share | Refresh the file share cache from S3 |
| `notify-when-uploaded` | File Share | Get notified when file upload completes |
| `evict-files-failing-upload` | File Share | Evict files that are failing to upload |
| `start-cache-report` | File Share | Start a cache report for a file share |
| `describe-cache-report` | File Share | Describe a cache report |
| `list-cache-reports` | File Share | List cache reports |
| `cancel-cache-report` | File Share | Cancel a running cache report |
| `delete-cache-report` | File Share | Delete a cache report |
| `describe-smb-settings` | SMB | Describe SMB settings for a gateway |
| `join-domain` | SMB | Join a gateway to an Active Directory domain |
| `set-smb-guest-password` | SMB | Set the SMB guest access password |
| `update-smb-security-strategy` | SMB | Update the SMB security strategy |
| `update-smb-file-share-visibility` | SMB | Toggle file share visibility |
| `update-smb-local-groups` | SMB | Update SMB local group membership |
| `create-cached-iscsi-volume` | Volume | Create a cached iSCSI volume |
| `create-stored-iscsi-volume` | Volume | Create a stored iSCSI volume |
| `describe-cached-iscsi-volumes` | Volume | Describe cached iSCSI volumes |
| `describe-stored-iscsi-volumes` | Volume | Describe stored iSCSI volumes |
| `attach-volume` | Volume | Attach a volume to a gateway |
| `detach-volume` | Volume | Detach a volume from a gateway |
| `delete-volume` | Volume | Delete a volume |
| `list-volumes` | Volume | List volumes on a gateway |
| `list-volume-initiators` | Volume | List iSCSI initiators connected to a volume |
| `list-volume-recovery-points` | Volume | List volume recovery points |
| `create-snapshot` | Volume | Create a snapshot of a volume |
| `create-snapshot-from-volume-recovery-point` | Volume | Create a snapshot from a recovery point |
| `describe-snapshot-schedule` | Volume | Describe a volume snapshot schedule |
| `update-snapshot-schedule` | Volume | Update a volume snapshot schedule |
| `delete-snapshot-schedule` | Volume | Delete a volume snapshot schedule |
| `add-upload-buffer` | Volume | Add upload buffer to a gateway |
| `describe-upload-buffer` | Volume | Describe upload buffer on a gateway |
| `add-working-storage` | Volume | Add working storage to a stored volume gateway |
| `describe-working-storage` | Volume | Describe working storage on a gateway |
| `create-tapes` | Tape | Create virtual tapes |
| `create-tape-with-barcode` | Tape | Create a virtual tape with a specific barcode |
| `describe-tapes` | Tape | Describe virtual tapes on a gateway |
| `list-tapes` | Tape | List virtual tapes |
| `delete-tape` | Tape | Delete a virtual tape |
| `delete-tape-archive` | Tape | Delete a tape from the archive |
| `describe-tape-archives` | Tape | Describe tape archives |
| `describe-tape-recovery-points` | Tape | Describe tape recovery points |
| `retrieve-tape-archive` | Tape | Retrieve a tape from archive |
| `retrieve-tape-recovery-point` | Tape | Retrieve a tape recovery point |
| `assign-tape-pool` | Tape | Assign a tape to a pool |
| `cancel-archival` | Tape | Cancel tape archival |
| `cancel-retrieval` | Tape | Cancel tape retrieval |
| `create-tape-pool` | Tape | Create a custom tape pool |
| `delete-tape-pool` | Tape | Delete a custom tape pool |
| `list-tape-pools` | Tape | List tape pools |
| `list-automatic-tape-creation-policies` | Tape | List automatic tape creation policies |
| `update-automatic-tape-creation-policy` | Tape | Update automatic tape creation policy |
| `delete-automatic-tape-creation-policy` | Tape | Delete automatic tape creation policy |
| `describe-vtl-devices` | Tape | Describe VTL devices on a tape gateway |
| `update-vtl-device-type` | Tape | Update VTL device type |
| `add-cache` | Cache | Add cache disks to a gateway |
| `describe-cache` | Cache | Describe cache on a gateway |
| `reset-cache` | Cache | Reset cache on a gateway |
| `update-bandwidth-rate-limit` | Bandwidth | Set bandwidth rate limits |
| `describe-bandwidth-rate-limit` | Bandwidth | Describe bandwidth rate limits |
| `delete-bandwidth-rate-limit` | Bandwidth | Delete bandwidth rate limits |
| `update-bandwidth-rate-limit-schedule` | Bandwidth | Set bandwidth rate limit schedule |
| `describe-bandwidth-rate-limit-schedule` | Bandwidth | Describe bandwidth rate limit schedule |
| `associate-file-system` | FSx Association | Associate an FSx file system with a gateway |
| `disassociate-file-system` | FSx Association | Disassociate an FSx file system |
| `describe-file-system-associations` | FSx Association | Describe file system associations |
| `list-file-system-associations` | FSx Association | List file system associations |
| `update-file-system-association` | FSx Association | Update a file system association |
| `update-chap-credentials` | CHAP | Update CHAP credentials for iSCSI |
| `describe-chap-credentials` | CHAP | Describe CHAP credentials |
| `delete-chap-credentials` | CHAP | Delete CHAP credentials |
| `add-tags-to-resource` | Tags | Add tags to a resource |
| `remove-tags-from-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

---

## Global Options

These options are available on ALL `aws storagegateway` commands.

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `--debug` | boolean | false | Enable debug logging to stderr |
| `--endpoint-url` | string | -- | Override the default service endpoint URL |
| `--no-verify-ssl` | boolean | false | Disable SSL certificate verification |
| `--no-paginate` | boolean | false | Disable automatic pagination |
| `--output` | string | `json` | Output format: `json`, `text`, `table`, `yaml`, `yaml-stream` |
| `--query` | string | -- | JMESPath query to filter output |
| `--profile` | string | `default` | Named AWS credential profile |
| `--region` | string | from config | AWS region to send requests to |
| `--version` | string | -- | Display the CLI version |
| `--color` | string | `auto` | Toggle color output: `on`, `off`, `auto` |
| `--no-sign-request` | boolean | false | Do not sign requests |
| `--ca-bundle` | string | -- | Path to custom CA certificate bundle for SSL |
| `--cli-read-timeout` | integer | 60 | Socket read timeout in seconds |
| `--cli-connect-timeout` | integer | 60 | Socket connect timeout in seconds |
| `--cli-binary-format` | string | `base64` | Format for binary blob input: `base64`, `raw-in-base64-out` |
| `--no-cli-pager` | boolean | false | Disable the output pager |
| `--cli-auto-prompt` | boolean | false | Auto-prompt for missing parameters |
| `--no-cli-auto-prompt` | boolean | false | Disable auto-prompt |
| `--cli-input-json` | string | -- | Read arguments from a JSON string or `file://` path |
| `--cli-input-yaml` | string | -- | Read arguments from a YAML string or `file://` path |
| `--generate-cli-skeleton` | string | -- | Print input/output skeleton: `input`, `yaml-input`, `output` |

---

## Common Patterns

### Gateway Types
| Type | Description |
|------|-------------|
| `FILE_S3` | S3 File Gateway — NFS/SMB file interface to S3 |
| `FILE_FSX_SMB` | FSx File Gateway — SMB interface to FSx for Windows |
| `CACHED` | Volume Gateway (Cached) — iSCSI volumes with S3 backing |
| `STORED` | Volume Gateway (Stored) — iSCSI volumes with local storage |
| `VTL` | Tape Gateway — Virtual tape library backed by S3/Glacier |

### Gateway ARN Format
```
arn:aws:storagegateway:<region>:<account-id>:gateway/sgw-<id>
```

### Host Environments
| Environment | Description |
|-------------|-------------|
| `VMWARE` | VMware ESXi |
| `HYPER-V` | Microsoft Hyper-V |
| `EC2` | Amazon EC2 |
| `KVM` | Linux KVM |
| `SNOWBALL` | AWS Snowball Edge |
| `OTHER` | Other environment |

### Active Directory Status Values
| Status | Description |
|--------|-------------|
| `JOINED` | Gateway is joined to the AD domain |
| `JOINING` | Gateway is joining the AD domain |
| `DETACHED` | Gateway is not joined to any domain |
| `ACCESS_DENIED` | Access was denied when joining |
| `NETWORK_ERROR` | Network error occurred during join |
| `TIMEOUT` | Join operation timed out |
| `UNKNOWN_ERROR` | An unknown error occurred |
| `INSUFFICIENT_PERMISSIONS` | Insufficient permissions to join |
