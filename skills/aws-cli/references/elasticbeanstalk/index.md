# AWS CLI v2 -- Elastic Beanstalk Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/elasticbeanstalk/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-application` | Application | Create a new Elastic Beanstalk application |
| `describe-applications` | Application | Describe one or more applications |
| `update-application` | Application | Update application properties |
| `delete-application` | Application | Delete an application and all versions |
| `create-application-version` | Application Version | Create an application version |
| `describe-application-versions` | Application Version | Describe application versions |
| `update-application-version` | Application Version | Update an application version |
| `delete-application-version` | Application Version | Delete an application version |
| `create-environment` | Environment | Create a new environment |
| `describe-environments` | Environment | Describe one or more environments |
| `update-environment` | Environment | Update environment configuration or version |
| `terminate-environment` | Environment | Terminate an environment |
| `rebuild-environment` | Environment | Rebuild an environment |
| `restart-app-server` | Environment | Restart application servers |
| `describe-environment-health` | Environment | Get enhanced health for an environment |
| `describe-instances-health` | Environment | Get health for individual instances |
| `compose-environments` | Environment | Create or update environments for a group |
| `swap-environment-cnames` | Environment | Swap CNAMEs between two environments |
| `abort-environment-update` | Environment | Abort an in-progress environment update |
| `describe-environment-resources` | Environment | Describe environment resources |
| `list-available-solution-stacks` | Environment | List available solution stacks |
| `describe-environment-managed-actions` | Managed Action | List pending managed actions |
| `describe-environment-managed-action-history` | Managed Action | List managed action history |
| `apply-environment-managed-action` | Managed Action | Apply a pending managed action |
| `create-configuration-template` | Configuration | Create a configuration template |
| `describe-configuration-settings` | Configuration | Describe configuration settings |
| `update-configuration-template` | Configuration | Update a configuration template |
| `delete-configuration-template` | Configuration | Delete a configuration template |
| `describe-configuration-options` | Configuration | Describe available configuration options |
| `validate-configuration-settings` | Configuration | Validate configuration settings |
| `create-platform-version` | Platform | Create a custom platform version |
| `describe-platform-version` | Platform | Describe a platform version |
| `list-platform-versions` | Platform | List platform versions |
| `list-platform-branches` | Platform | List platform branches |
| `delete-platform-version` | Platform | Delete a custom platform version |
| `describe-events` | Operations | List events for an environment |
| `describe-account-attributes` | Operations | Describe account quota limits |
| `create-storage-location` | Operations | Create an S3 storage bucket |
| `associate-environment-operations-role` | Operations | Associate an operations role |
| `disassociate-environment-operations-role` | Operations | Disassociate an operations role |
| `check-dns-availability` | Utility | Check if a CNAME is available |
| `request-environment-info` | Utility | Request environment info (logs) |
| `retrieve-environment-info` | Utility | Retrieve environment info (logs) |
| `list-tags-for-resource` | Utility | List tags for a resource |
| `update-tags-for-resource` | Utility | Update tags for a resource |

---

## Global Options

These options are available on ALL `aws elasticbeanstalk` commands.

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
| `--no-sign-request` | boolean | false | Do not sign requests (for anonymous access) |
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

### Environment Health Statuses
| Status | Description |
|--------|-------------|
| `Green` | Environment is healthy |
| `Yellow` | Health of one or more instances is degraded |
| `Red` | Environment is unhealthy; requests are failing |
| `Grey` | Health information is not available |

### Environment Statuses
| Status | Description |
|--------|-------------|
| `Launching` | Environment is being created |
| `Updating` | Environment is being updated |
| `Ready` | Environment is available |
| `Terminating` | Environment is being terminated |
| `Terminated` | Environment has been terminated |
| `Aborting` | An update is being aborted |
| `LinkingFrom` | Being linked from another environment |
| `LinkingTo` | Linking to another environment |

### Deployment Policies
| Policy | Description |
|--------|-------------|
| `AllAtOnce` | Deploy to all instances simultaneously |
| `Rolling` | Deploy in batches |
| `RollingWithAdditionalBatch` | Launch new batch before removing old |
| `Immutable` | Launch a full set of new instances |
| `TrafficSplitting` | Canary deployment with traffic splitting |

### Common Option Namespaces
| Namespace | Description |
|-----------|-------------|
| `aws:autoscaling:asg` | Auto Scaling group settings |
| `aws:autoscaling:launchconfiguration` | Launch configuration (instance type, etc.) |
| `aws:autoscaling:trigger` | Scaling triggers |
| `aws:ec2:vpc` | VPC settings |
| `aws:elasticbeanstalk:application` | Application settings |
| `aws:elasticbeanstalk:environment` | Environment type, service role |
| `aws:elasticbeanstalk:healthreporting:system` | Health reporting |
| `aws:elb:loadbalancer` | Classic Load Balancer settings |
| `aws:elbv2:loadbalancer` | Application Load Balancer settings |
