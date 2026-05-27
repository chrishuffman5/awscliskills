# AWS CLI v2 -- Amazon Translate Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/translate/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `translate-text` | Translation | Translate text from source to target language in real time |
| `translate-document` | Translation | Translate a document from source to target language |
| `start-text-translation-job` | Translation | Start an asynchronous batch translation job |
| `describe-text-translation-job` | Translation | Get properties of an asynchronous batch translation job |
| `list-text-translation-jobs` | Translation | List batch translation jobs with optional filtering |
| `stop-text-translation-job` | Translation | Stop an asynchronous batch translation job |
| `list-languages` | Translation | List all supported languages for translation |
| `import-terminology` | Terminology | Import a custom terminology resource |
| `get-terminology` | Terminology | Retrieve a custom terminology resource |
| `list-terminologies` | Terminology | List all custom terminologies in the account |
| `delete-terminology` | Terminology | Delete a custom terminology resource |
| `create-parallel-data` | Parallel Data | Create a parallel data resource |
| `get-parallel-data` | Parallel Data | Retrieve a parallel data resource |
| `list-parallel-data` | Parallel Data | List all parallel data resources in the account |
| `update-parallel-data` | Parallel Data | Update an existing parallel data resource |
| `delete-parallel-data` | Parallel Data | Delete a parallel data resource |
| `tag-resource` | Tags | Add tags to a resource |
| `untag-resource` | Tags | Remove tags from a resource |
| `list-tags-for-resource` | Tags | List tags for a resource |

---

## Global Options

These options are available on ALL `aws translate` commands.

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

### Language Codes
Language codes follow RFC-5646 format (2-5 characters). Common examples:
- `en` — English
- `es` — Spanish
- `fr` — French
- `de` — German
- `ja` — Japanese
- `zh` — Chinese (Simplified)
- `zh-TW` — Chinese (Traditional)
- `ko` — Korean
- `pt` — Portuguese
- `it` — Italian
- `ar` — Arabic
- `auto` — Auto-detect (source only)

Use `aws translate list-languages` to get the full list of supported languages.

### Translation Settings
Translation settings control output formality, profanity masking, and brevity:
```json
{
    "Formality": "FORMAL|INFORMAL",
    "Profanity": "MASK",
    "Brevity": "ON"
}
```

### Batch Job Statuses
| Status | Description |
|--------|-------------|
| `SUBMITTED` | Job is queued for processing |
| `IN_PROGRESS` | Job is being processed |
| `COMPLETED` | Job completed successfully |
| `COMPLETED_WITH_ERROR` | Job completed with some errors |
| `FAILED` | Job failed |
| `STOP_REQUESTED` | Stop has been requested |
| `STOPPED` | Job was stopped |

### Parallel Data Statuses
| Status | Description |
|--------|-------------|
| `CREATING` | Resource is being created |
| `UPDATING` | Resource is being updated |
| `ACTIVE` | Resource is ready for use |
| `DELETING` | Resource is being deleted |
| `FAILED` | Resource creation/update failed |

### Custom Terminology Formats
| Format | Description |
|--------|-------------|
| `CSV` | Comma-separated values |
| `TSV` | Tab-separated values |
| `TMX` | Translation Memory eXchange (XML) |

### Encryption Key Structure
```json
{
    "Type": "KMS",
    "Id": "arn:aws:kms:region:account-id:key/key-id"
}
```
