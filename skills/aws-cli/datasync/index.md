# AWS CLI v2 -- DataSync Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/datasync/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-agent` | Agent | Activate a DataSync agent |
| `delete-agent` | Agent | Delete an agent |
| `describe-agent` | Agent | Get agent details |
| `list-agents` | Agent | List all agents |
| `update-agent` | Agent | Update agent name |
| `create-task` | Task | Create a data transfer task |
| `delete-task` | Task | Delete a task |
| `describe-task` | Task | Get task details |
| `list-tasks` | Task | List all tasks |
| `update-task` | Task | Update task configuration |
| `start-task-execution` | Task Execution | Start a task execution |
| `cancel-task-execution` | Task Execution | Cancel a running execution |
| `describe-task-execution` | Task Execution | Get execution details |
| `list-task-executions` | Task Execution | List executions for a task |
| `update-task-execution` | Task Execution | Update a running execution |
| `create-location-s3` | Location (S3) | Create an S3 location |
| `describe-location-s3` | Location (S3) | Get S3 location details |
| `update-location-s3` | Location (S3) | Update S3 location |
| `create-location-efs` | Location (EFS) | Create an EFS location |
| `describe-location-efs` | Location (EFS) | Get EFS location details |
| `update-location-efs` | Location (EFS) | Update EFS location |
| `create-location-fsx-windows` | Location (FSx) | Create FSx Windows location |
| `create-location-fsx-lustre` | Location (FSx) | Create FSx Lustre location |
| `create-location-fsx-ontap` | Location (FSx) | Create FSx ONTAP location |
| `create-location-fsx-open-zfs` | Location (FSx) | Create FSx OpenZFS location |
| `describe-location-fsx-windows` | Location (FSx) | Get FSx Windows location details |
| `describe-location-fsx-lustre` | Location (FSx) | Get FSx Lustre location details |
| `describe-location-fsx-ontap` | Location (FSx) | Get FSx ONTAP location details |
| `describe-location-fsx-open-zfs` | Location (FSx) | Get FSx OpenZFS location details |
| `update-location-fsx-windows` | Location (FSx) | Update FSx Windows location |
| `update-location-fsx-lustre` | Location (FSx) | Update FSx Lustre location |
| `update-location-fsx-ontap` | Location (FSx) | Update FSx ONTAP location |
| `update-location-fsx-open-zfs` | Location (FSx) | Update FSx OpenZFS location |
| `create-location-nfs` | Location (Network) | Create an NFS location |
| `create-location-smb` | Location (Network) | Create an SMB location |
| `create-location-hdfs` | Location (Network) | Create an HDFS location |
| `describe-location-nfs` | Location (Network) | Get NFS location details |
| `describe-location-smb` | Location (Network) | Get SMB location details |
| `describe-location-hdfs` | Location (Network) | Get HDFS location details |
| `update-location-nfs` | Location (Network) | Update NFS location |
| `update-location-smb` | Location (Network) | Update SMB location |
| `update-location-hdfs` | Location (Network) | Update HDFS location |
| `create-location-object-storage` | Location (Other) | Create object storage location |
| `create-location-azure-blob` | Location (Other) | Create Azure Blob location |
| `describe-location-object-storage` | Location (Other) | Get object storage location details |
| `describe-location-azure-blob` | Location (Other) | Get Azure Blob location details |
| `update-location-object-storage` | Location (Other) | Update object storage location |
| `update-location-azure-blob` | Location (Other) | Update Azure Blob location |
| `delete-location` | Location | Delete any location |
| `list-locations` | Location | List all locations |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

---

## Global Options

These options are available on ALL `aws datasync` commands.

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

### Task Status Values
| Status | Description |
|--------|-------------|
| `AVAILABLE` | Task is ready to run |
| `CREATING` | Task is being created |
| `QUEUED` | Task execution is queued |
| `RUNNING` | Task is actively running |
| `UNAVAILABLE` | Task cannot be run |

### Task Execution Status Values
| Status | Description |
|--------|-------------|
| `QUEUED` | Execution is queued |
| `CANCELLING` | Execution is being cancelled |
| `LAUNCHING` | Execution is launching |
| `PREPARING` | Execution is preparing |
| `TRANSFERRING` | Execution is transferring data |
| `VERIFYING` | Execution is verifying transferred data |
| `SUCCESS` | Execution completed successfully |
| `ERROR` | Execution completed with errors |

### Agent Status Values
| Status | Description |
|--------|-------------|
| `ONLINE` | Agent is connected and available |
| `OFFLINE` | Agent is disconnected |

### Transfer Mode Options
| Mode | Description |
|------|-------------|
| `CHANGED` | Transfer only files that have changed (default) |
| `ALL` | Transfer all files regardless of changes |

### ARN Patterns
| Resource | Pattern |
|----------|---------|
| Agent | `arn:aws:datasync:region:account:agent/agent-[0-9a-z]{17}` |
| Location | `arn:aws:datasync:region:account:location/loc-[0-9a-z]{17}` |
| Task | `arn:aws:datasync:region:account:task/task-[0-9a-f]{17}` |
| Execution | `arn:aws:datasync:region:account:task/task-[0-9a-f]{17}/execution/exec-[0-9a-f]{17}` |
