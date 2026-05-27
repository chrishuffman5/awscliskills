# AWS CLI v2 -- Transcribe (Speech-to-Text) Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/transcribe/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `start-transcription-job` | Transcription Job | Start a standard transcription job |
| `get-transcription-job` | Transcription Job | Get transcription job details |
| `list-transcription-jobs` | Transcription Job | List transcription jobs |
| `delete-transcription-job` | Transcription Job | Delete a transcription job |
| `start-call-analytics-job` | Call Analytics | Start a call analytics transcription job |
| `get-call-analytics-job` | Call Analytics | Get call analytics job details |
| `list-call-analytics-jobs` | Call Analytics | List call analytics jobs |
| `delete-call-analytics-job` | Call Analytics | Delete a call analytics job |
| `create-call-analytics-category` | Call Analytics | Create a call analytics category |
| `get-call-analytics-category` | Call Analytics | Get a call analytics category |
| `list-call-analytics-categories` | Call Analytics | List call analytics categories |
| `update-call-analytics-category` | Call Analytics | Update a call analytics category |
| `delete-call-analytics-category` | Call Analytics | Delete a call analytics category |
| `start-medical-transcription-job` | Medical | Start a medical transcription job |
| `get-medical-transcription-job` | Medical | Get medical transcription job details |
| `list-medical-transcription-jobs` | Medical | List medical transcription jobs |
| `delete-medical-transcription-job` | Medical | Delete a medical transcription job |
| `start-medical-scribe-job` | Medical | Start a medical scribe job |
| `get-medical-scribe-job` | Medical | Get medical scribe job details |
| `list-medical-scribe-jobs` | Medical | List medical scribe jobs |
| `delete-medical-scribe-job` | Medical | Delete a medical scribe job |
| `create-medical-vocabulary` | Medical | Create a medical vocabulary |
| `get-medical-vocabulary` | Medical | Get medical vocabulary details |
| `list-medical-vocabularies` | Medical | List medical vocabularies |
| `update-medical-vocabulary` | Medical | Update a medical vocabulary |
| `delete-medical-vocabulary` | Medical | Delete a medical vocabulary |
| `create-vocabulary` | Vocabulary | Create a custom vocabulary |
| `get-vocabulary` | Vocabulary | Get vocabulary details |
| `list-vocabularies` | Vocabulary | List vocabularies |
| `update-vocabulary` | Vocabulary | Update a vocabulary |
| `delete-vocabulary` | Vocabulary | Delete a vocabulary |
| `create-vocabulary-filter` | Vocabulary | Create a vocabulary filter |
| `get-vocabulary-filter` | Vocabulary | Get vocabulary filter details |
| `list-vocabulary-filters` | Vocabulary | List vocabulary filters |
| `update-vocabulary-filter` | Vocabulary | Update a vocabulary filter |
| `delete-vocabulary-filter` | Vocabulary | Delete a vocabulary filter |
| `create-language-model` | Language Model | Create a custom language model |
| `describe-language-model` | Language Model | Describe a language model |
| `list-language-models` | Language Model | List language models |
| `delete-language-model` | Language Model | Delete a language model |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |
| `wait` | Wait | Wait for a resource state change |

---

## Global Options

These options are available on ALL `aws transcribe` commands.

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

### Job Status Values
| Status | Description |
|--------|-------------|
| `QUEUED` | Job is queued for processing |
| `IN_PROGRESS` | Job is being processed |
| `COMPLETED` | Job completed successfully |
| `FAILED` | Job failed |

### Vocabulary State Values
| State | Description |
|-------|-------------|
| `PENDING` | Vocabulary is being processed |
| `READY` | Vocabulary is ready for use |
| `FAILED` | Vocabulary creation/update failed |

### Supported Media Formats
`mp3`, `mp4`, `wav`, `flac`, `ogg`, `amr`, `webm`, `m4a`

### Vocabulary Filter Methods
| Method | Description |
|--------|-------------|
| `remove` | Remove filtered words from transcript |
| `mask` | Replace filtered words with `***` |
| `tag` | Tag filtered words in the transcript |
