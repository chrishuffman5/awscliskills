# AWS CLI v2 -- Application Insights Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/application-insights/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-application` | Application | Create a monitoring application |
| `delete-application` | Application | Delete a monitoring application |
| `describe-application` | Application | Describe a monitoring application |
| `list-applications` | Application | List monitoring applications |
| `update-application` | Application | Update a monitoring application |
| `create-component` | Component | Create a custom component grouping |
| `delete-component` | Component | Delete a custom component |
| `describe-component` | Component | Describe a component |
| `list-components` | Component | List components in an application |
| `update-component` | Component | Update a custom component |
| `describe-component-configuration` | Component | Describe component monitoring configuration |
| `describe-component-configuration-recommendation` | Component | Get recommended configuration |
| `update-component-configuration` | Component | Update component monitoring configuration |
| `create-log-pattern` | Log Pattern | Create a log pattern |
| `delete-log-pattern` | Log Pattern | Delete a log pattern |
| `describe-log-pattern` | Log Pattern | Describe a log pattern |
| `list-log-patterns` | Log Pattern | List log patterns |
| `update-log-pattern` | Log Pattern | Update a log pattern |
| `list-log-pattern-sets` | Log Pattern | List log pattern sets |
| `describe-problem` | Problem | Describe a detected problem |
| `list-problems` | Problem | List detected problems |
| `update-problem` | Problem | Update a problem status |
| `describe-problem-observations` | Problem | Describe observations for a problem |
| `describe-observation` | Problem | Describe a specific observation |
| `list-configuration-history` | Problem | List configuration change history |
| `add-workload` | Workload | Add a workload to a component |
| `remove-workload` | Workload | Remove a workload from a component |
| `describe-workload` | Workload | Describe a workload |
| `list-workloads` | Workload | List workloads for a component |
| `update-workload` | Workload | Update a workload |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

---

## Global Options

These options are available on ALL `aws application-insights` commands.

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

### Supported Tiers
| Tier | Description |
|------|-------------|
| `CUSTOM` | Custom tier |
| `DEFAULT` | Default tier |
| `DOT_NET_CORE` | .NET Core application |
| `DOT_NET_WORKER` | .NET Worker Service |
| `DOT_NET_WEB_TIER` | .NET Web tier |
| `DOT_NET_WEB` | .NET Web application |
| `SQL_SERVER` | SQL Server |
| `SQL_SERVER_ALWAYSON_AVAILABILITY_GROUP` | SQL Server Always On AG |
| `MYSQL` | MySQL |
| `POSTGRESQL` | PostgreSQL |
| `JAVA_JMX` | Java JMX |
| `ORACLE` | Oracle |
| `SAP_HANA_MULTI_NODE` | SAP HANA Multi-Node |
| `SAP_HANA_SINGLE_NODE` | SAP HANA Single-Node |
| `SAP_HANA_HIGH_AVAILABILITY` | SAP HANA High Availability |
| `ACTIVE_DIRECTORY` | Active Directory |
| `SHAREPOINT` | SharePoint |

### Problem Severity Levels
| Severity | Description |
|----------|-------------|
| `Informative` | Informational finding |
| `Low` | Low severity |
| `Medium` | Medium severity |
| `High` | High severity |

### Problem Status
| Status | Description |
|--------|-------------|
| `IGNORE` | Problem is ignored |
| `RESOLVED` | Problem has been resolved |
| `PENDING` | Problem is pending |
| `RECURRING` | Problem is recurring |
| `RECOVERING` | Problem is recovering |
