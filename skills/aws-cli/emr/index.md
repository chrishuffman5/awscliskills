# AWS CLI v2 — EMR Command Reference Index

> Based on AWS CLI v2 documentation. Sources:
> - https://docs.aws.amazon.com/cli/latest/reference/emr/
> - https://docs.aws.amazon.com/cli/latest/reference/emr-containers/
> - https://docs.aws.amazon.com/cli/latest/reference/emr-serverless/

---

## Quick Reference — `aws emr`

| Command | Category | Description |
|---------|----------|-------------|
| `create-cluster` | Cluster | Create a new EMR cluster |
| `describe-cluster` | Cluster | Describe a cluster |
| `list-clusters` | Cluster | List clusters by status |
| `terminate-clusters` | Cluster | Terminate one or more clusters |
| `modify-cluster` | Cluster | Modify cluster step concurrency |
| `put-auto-termination-policy` | Cluster | Set auto-termination policy |
| `get-auto-termination-policy` | Cluster | Get auto-termination policy |
| `remove-auto-termination-policy` | Cluster | Remove auto-termination policy |
| `add-instance-groups` | Instance | Add instance groups to a cluster |
| `modify-instance-groups` | Instance | Modify instance groups |
| `list-instance-groups` | Instance | List instance groups |
| `add-instance-fleet` | Instance | Add an instance fleet |
| `modify-instance-fleet` | Instance | Modify an instance fleet |
| `list-instance-fleets` | Instance | List instance fleets |
| `list-instances` | Instance | List instances in a cluster |
| `add-steps` | Step | Add steps to a cluster |
| `cancel-steps` | Step | Cancel pending steps |
| `list-steps` | Step | List steps in a cluster |
| `describe-step` | Step | Describe a step |
| `put-auto-scaling-policy` | Scaling | Set auto scaling policy for instance group |
| `remove-auto-scaling-policy` | Scaling | Remove auto scaling policy |
| `put-managed-scaling-policy` | Scaling | Set managed scaling policy |
| `get-managed-scaling-policy` | Scaling | Get managed scaling policy |
| `remove-managed-scaling-policy` | Scaling | Remove managed scaling policy |
| `create-security-configuration` | Security | Create a security configuration |
| `delete-security-configuration` | Security | Delete a security configuration |
| `describe-security-configuration` | Security | Describe a security configuration |
| `list-security-configurations` | Security | List security configurations |
| `put-block-public-access-configuration` | Security | Set block public access configuration |
| `get-block-public-access-configuration` | Security | Get block public access configuration |
| `delete-block-public-access-configuration` | Security | Delete block public access |
| `create-studio` | Studio | Create an EMR Studio |
| `delete-studio` | Studio | Delete an EMR Studio |
| `describe-studio` | Studio | Describe an EMR Studio |
| `list-studios` | Studio | List EMR Studios |
| `update-studio` | Studio | Update an EMR Studio |
| `create-studio-session-mapping` | Studio | Map a user/group to a studio |
| `delete-studio-session-mapping` | Studio | Delete a session mapping |
| `get-studio-session-mapping` | Studio | Get a session mapping |
| `list-studio-session-mappings` | Studio | List session mappings |
| `update-studio-session-mapping` | Studio | Update a session mapping |
| `create-notebook-execution` | Notebook | Start a notebook execution |
| `describe-notebook-execution` | Notebook | Describe a notebook execution |
| `list-notebook-executions` | Notebook | List notebook executions |
| `start-notebook-execution` | Notebook | Start a notebook execution |
| `stop-notebook-execution` | Notebook | Stop a running notebook execution |
| `schedule-hbase-backup` | HBase | Schedule an HBase backup |
| `restore-hbase-backup` | HBase | Restore an HBase backup |
| `get-cluster-session-credentials` | App UI | Get session credentials for app UIs |
| `ssh` | Utility | SSH into the master node |
| `socks` | Utility | Create a SOCKS proxy to the master |
| `get` | Utility | Download a file from the master node |
| `put` | Utility | Upload a file to the master node |
| `add-tags` | Tags | Add tags to a resource |
| `remove-tags` | Tags | Remove tags from a resource |

## Quick Reference — `aws emr-containers`

| Command | Category | Description |
|---------|----------|-------------|
| `create-virtual-cluster` | Virtual Cluster | Create a virtual cluster on EKS |
| `delete-virtual-cluster` | Virtual Cluster | Delete a virtual cluster |
| `describe-virtual-cluster` | Virtual Cluster | Describe a virtual cluster |
| `list-virtual-clusters` | Virtual Cluster | List virtual clusters |
| `start-job-run` | Job Run | Start a job run |
| `cancel-job-run` | Job Run | Cancel a running job |
| `describe-job-run` | Job Run | Describe a job run |
| `list-job-runs` | Job Run | List job runs |
| `get-managed-endpoint-session-credentials` | Session | Get managed endpoint credentials |
| `create-managed-endpoint` | Managed Endpoint | Create a managed endpoint |
| `delete-managed-endpoint` | Managed Endpoint | Delete a managed endpoint |
| `describe-managed-endpoint` | Managed Endpoint | Describe a managed endpoint |
| `list-managed-endpoints` | Managed Endpoint | List managed endpoints |
| `create-security-configuration` | Security | Create a security configuration |
| `delete-security-configuration` | Security | Delete a security configuration |
| `describe-security-configuration` | Security | Describe a security configuration |
| `list-security-configurations` | Security | List security configurations |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags on a resource |

## Quick Reference — `aws emr-serverless`

| Command | Category | Description |
|---------|----------|-------------|
| `create-application` | Application | Create a serverless application |
| `delete-application` | Application | Delete a serverless application |
| `get-application` | Application | Get application details |
| `list-applications` | Application | List applications |
| `update-application` | Application | Update an application |
| `start-application` | Application | Start (pre-initialize) an application |
| `stop-application` | Application | Stop an application |
| `start-job-run` | Job Run | Start a job run |
| `cancel-job-run` | Job Run | Cancel a job run |
| `get-job-run` | Job Run | Get job run details |
| `list-job-runs` | Job Run | List job runs |
| `get-dashboard-for-job-run` | Job Run | Get Spark/Tez dashboard URL |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags on a resource |

---

## Global Options

These options are available on ALL `aws emr`, `aws emr-containers`, and `aws emr-serverless` commands.

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
| `--ca-bundle` | string | -- | Path to custom CA certificate bundle |
| `--cli-read-timeout` | integer | 60 | Socket read timeout in seconds |
| `--cli-connect-timeout` | integer | 60 | Socket connect timeout in seconds |
| `--cli-binary-format` | string | `base64` | Format for binary blob input |
| `--no-cli-pager` | boolean | false | Disable the output pager |
| `--cli-auto-prompt` | boolean | false | Auto-prompt for missing parameters |
| `--no-cli-auto-prompt` | boolean | false | Disable auto-prompt |
| `--cli-input-json` | string | -- | Read arguments from a JSON string or `file://` path |
| `--cli-input-yaml` | string | -- | Read arguments from a YAML string or `file://` path |
| `--generate-cli-skeleton` | string | -- | Print input/output skeleton |

---

## Common Patterns

### Cluster State Values
| State | Description |
|-------|-------------|
| `STARTING` | Cluster is provisioning resources |
| `BOOTSTRAPPING` | Bootstrap actions are running |
| `RUNNING` | Cluster is running and accepting steps |
| `WAITING` | Cluster is idle, waiting for steps |
| `TERMINATING` | Cluster is shutting down |
| `TERMINATED` | Cluster has been terminated |
| `TERMINATED_WITH_ERRORS` | Cluster terminated with errors |

### Step State Values
| State | Description |
|-------|-------------|
| `PENDING` | Step is waiting to run |
| `CANCEL_PENDING` | Step cancellation is pending |
| `RUNNING` | Step is running |
| `COMPLETED` | Step completed successfully |
| `CANCELLED` | Step was cancelled |
| `FAILED` | Step failed |
| `INTERRUPTED` | Step was interrupted |

### Instance Group Types
| Type | Description |
|------|-------------|
| `MASTER` | Master instance group (exactly 1) |
| `CORE` | Core instance group |
| `TASK` | Task instance group (no HDFS) |

### Wait Commands
| Waiter | Description |
|--------|-------------|
| `cluster-running` | Wait until cluster is running |
| `cluster-terminated` | Wait until cluster is terminated |
| `step-complete` | Wait until a step completes |

```bash
aws emr wait cluster-running --cluster-id j-XXXXXXXXXXXXX
aws emr wait step-complete --cluster-id j-XXXXXXXXXXXXX --step-id s-XXXXXXXXXXXXX
```
