# AWS CLI v2 -- SageMaker A2I Runtime Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/sagemaker-a2i-runtime/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `start-human-loop` | Human Loops | Start a human review loop |
| `describe-human-loop` | Human Loops | Get details of a human loop |
| `list-human-loops` | Human Loops | List human loops for a flow definition |
| `stop-human-loop` | Human Loops | Stop an in-progress human loop |
| `delete-human-loop` | Human Loops | Delete a human loop |

---

## Global Options

These options are available on ALL `aws sagemaker-a2i-runtime` commands.

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

### Human Loop Status Values
| Status | Description |
|--------|-------------|
| `InProgress` | Loop is actively being reviewed |
| `Completed` | Loop review is complete |
| `Failed` | Loop failed |
| `Stopped` | Loop was stopped |
| `Stopping` | Loop is being stopped |

### Failure Codes
| Code | Description |
|------|-------------|
| `ValidationError` | Input validation error |
| `Expired` | Human loop expired |
| `InternalError` | Internal service error |

### Content Classifiers
| Classifier | Description |
|------------|-------------|
| `FreeOfPersonallyIdentifiableInformation` | Data does not contain PII |
| `FreeOfAdultContent` | Data does not contain adult content |
