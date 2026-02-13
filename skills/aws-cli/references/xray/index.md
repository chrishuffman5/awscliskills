# AWS CLI v2 -- X-Ray Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/xray/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `batch-get-traces` | Trace | Retrieve full traces by ID |
| `get-trace-summaries` | Trace | Search and retrieve trace summaries |
| `get-trace-graph` | Trace | Get the service graph for specific traces |
| `put-trace-segments` | Trace | Upload trace segment documents |
| `start-trace-retrieval` | Trace | Start retrieval of traces from storage |
| `cancel-trace-retrieval` | Trace | Cancel an ongoing trace retrieval |
| `list-retrieved-traces` | Trace | List traces from a retrieval operation |
| `get-retrieved-traces-graph` | Trace | Get service graph from retrieved traces |
| `get-trace-segment-destination` | Trace | Get trace segment destination configuration |
| `update-trace-segment-destination` | Trace | Update trace segment destination |
| `get-service-graph` | Service Graph | Get the service graph for a time period |
| `get-time-series-service-statistics` | Service Graph | Get time series service statistics |
| `create-sampling-rule` | Sampling | Create a sampling rule |
| `delete-sampling-rule` | Sampling | Delete a sampling rule |
| `get-sampling-rules` | Sampling | List all sampling rules |
| `update-sampling-rule` | Sampling | Update a sampling rule |
| `get-sampling-statistic-summaries` | Sampling | Get sampling statistic summaries |
| `get-sampling-targets` | Sampling | Get sampling targets for instrumentation |
| `create-group` | Group | Create a trace group |
| `delete-group` | Group | Delete a trace group |
| `get-group` | Group | Get details of a group |
| `get-groups` | Group | List all groups |
| `update-group` | Group | Update a group |
| `get-insight` | Insight | Get details of an insight |
| `get-insight-events` | Insight | Get events for an insight |
| `get-insight-impact-graph` | Insight | Get impact graph for an insight |
| `get-insight-summaries` | Insight | Get insight summaries for a time period |
| `get-indexing-rules` | Indexing | Get indexing rules |
| `update-indexing-rule` | Indexing | Update an indexing rule |
| `get-encryption-config` | Encryption | Get encryption configuration |
| `put-encryption-config` | Encryption | Set encryption configuration |
| `list-resource-policies` | Policy | List resource policies |
| `put-resource-policy` | Policy | Set a resource policy |
| `delete-resource-policy` | Policy | Delete a resource policy |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

---

## Global Options

These options are available on ALL `aws xray` commands.

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
| `--cli-binary-format` | string | `base64` | Format for binary blob input: `base64`, `raw-in-base64-out` |
| `--no-cli-pager` | boolean | false | Disable the output pager |
| `--cli-auto-prompt` | boolean | false | Auto-prompt for missing parameters |
| `--no-cli-auto-prompt` | boolean | false | Disable auto-prompt |
| `--cli-input-json` | string | -- | Read arguments from a JSON string or `file://` path |
| `--cli-input-yaml` | string | -- | Read arguments from a YAML string or `file://` path |
| `--generate-cli-skeleton` | string | -- | Print input/output skeleton: `input`, `yaml-input`, `output` |

---

## Common Patterns

### Trace ID Format
- Format: `1-XXXXXXXX-YYYYYYYYYYYYYYYYYYYYYYYY`
- First part after `1-` is an 8-hex-digit epoch timestamp
- Second part is a 24-hex-digit unique identifier

### Filter Expressions
Filter expressions are used with `get-trace-summaries` and group definitions:
```
service("my-service")
service("my-service") { fault = true }
responsetime > 5
annotation.user_id = "12345"
http.url CONTAINS "/api/"
```

### Insight States
| State | Description |
|-------|-------------|
| `ACTIVE` | Insight is currently active |
| `CLOSED` | Insight has been resolved |

### Encryption Types
| Type | Description |
|------|-------------|
| `NONE` | Default encryption (AWS-owned key) |
| `KMS` | Encryption using customer-managed KMS key |

### Sampling Rule Defaults
| Field | Default |
|-------|---------|
| `Version` | 1 (required) |
| `Priority` | Lower number = higher priority |
| `FixedRate` | 0.0 to 1.0 (fraction of requests sampled) |
| `ReservoirSize` | Number of requests per second to sample before applying fixed rate |
