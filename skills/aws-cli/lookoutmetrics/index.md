# AWS CLI v2 -- Lookout for Metrics Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/lookoutmetrics/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `create-anomaly-detector` | Detectors | Create an anomaly detector |
| `describe-anomaly-detector` | Detectors | Describe an anomaly detector |
| `list-anomaly-detectors` | Detectors | List anomaly detectors |
| `update-anomaly-detector` | Detectors | Update an anomaly detector |
| `delete-anomaly-detector` | Detectors | Delete an anomaly detector |
| `activate-anomaly-detector` | Detectors | Activate an anomaly detector |
| `deactivate-anomaly-detector` | Detectors | Deactivate an anomaly detector |
| `back-test-anomaly-detector` | Detectors | Run a backtest on a detector |
| `describe-anomaly-detection-executions` | Detectors | Describe detection execution status |
| `create-metric-set` | Metric Sets | Create a metric set (dataset) |
| `describe-metric-set` | Metric Sets | Describe a metric set |
| `list-metric-sets` | Metric Sets | List metric sets |
| `update-metric-set` | Metric Sets | Update a metric set |
| `detect-metric-set-config` | Metric Sets | Auto-detect metric set configuration |
| `get-sample-data` | Metric Sets | Get sample records from a data source |
| `get-data-quality-metrics` | Metric Sets | Get data quality metrics |
| `create-alert` | Alerts | Create an alert |
| `describe-alert` | Alerts | Describe an alert |
| `list-alerts` | Alerts | List alerts for a detector |
| `update-alert` | Alerts | Update an alert |
| `delete-alert` | Alerts | Delete an alert |
| `get-anomaly-group` | Anomaly Groups | Get anomaly group details |
| `list-anomaly-group-summaries` | Anomaly Groups | List anomaly group summaries |
| `list-anomaly-group-time-series` | Anomaly Groups | List time series in an anomaly group |
| `list-anomaly-group-related-metrics` | Anomaly Groups | List related metrics for an anomaly group |
| `put-feedback` | Anomaly Groups | Submit feedback on an anomaly |
| `get-feedback` | Anomaly Groups | Get feedback for an anomaly group |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

---

## Global Options

These options are available on ALL `aws lookoutmetrics` commands.

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

---

## Common Patterns

### Detector Status Values
| Status | Description |
|--------|-------------|
| `ACTIVE` | Detector is actively running |
| `ACTIVATING` | Detector is being activated |
| `INACTIVE` | Detector is not running |
| `DEACTIVATED` | Detector has been deactivated |
| `DEACTIVATING` | Detector is being deactivated |
| `LEARNING` | Detector is in learning phase |
| `BACK_TEST_ACTIVATING` | Backtest is being activated |
| `BACK_TEST_ACTIVE` | Backtest is running |
| `BACK_TEST_COMPLETE` | Backtest is complete |
| `FAILED` | Detector failed |
| `DELETING` | Detector is being deleted |

### Frequency Values
| Frequency | Description |
|-----------|-------------|
| `P1D` | Once per day |
| `PT1H` | Once per hour |
| `PT10M` | Every 10 minutes |
| `PT5M` | Every 5 minutes |

### Aggregation Functions
| Function | Description |
|----------|-------------|
| `AVG` | Average of values |
| `SUM` | Sum of values |

### Execution Status Values
| Status | Description |
|--------|-------------|
| `PENDING` | Execution is pending |
| `IN_PROGRESS` | Execution is in progress |
| `COMPLETED` | Execution completed |
| `FAILED` | Execution failed |
| `FAILED_TO_SCHEDULE` | Execution failed to schedule |
