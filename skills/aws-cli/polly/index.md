# AWS CLI v2 -- Polly (Text-to-Speech) Command Reference Index

> Based on AWS CLI v2 documentation. Source: https://docs.aws.amazon.com/cli/latest/reference/polly/

---

## Quick Reference

| Command | Category | Description |
|---------|----------|-------------|
| `synthesize-speech` | Synthesis | Synthesize speech from text (real-time, returns audio stream) |
| `start-speech-synthesis-task` | Synthesis | Start an asynchronous speech synthesis task (output to S3) |
| `get-speech-synthesis-task` | Synthesis | Get details of a speech synthesis task |
| `list-speech-synthesis-tasks` | Synthesis | List speech synthesis tasks |
| `describe-voices` | Synthesis | List available voices and their properties |
| `put-lexicon` | Lexicon | Create or update a pronunciation lexicon |
| `get-lexicon` | Lexicon | Retrieve a pronunciation lexicon |
| `delete-lexicon` | Lexicon | Delete a pronunciation lexicon |
| `list-lexicons` | Lexicon | List all pronunciation lexicons |

---

## Global Options

These options are available on ALL `aws polly` commands.

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

### Speech Engines
| Engine | Description |
|--------|-------------|
| `standard` | Classic concatenative synthesis |
| `neural` | Neural text-to-speech (NTTS) with more natural prosody |
| `long-form` | Optimized for long-form content like articles |
| `generative` | Most expressive and human-like synthesis |

### Output Formats
| Format | MIME Type | Description |
|--------|-----------|-------------|
| `mp3` | audio/mpeg | Compressed audio, widely compatible |
| `ogg_vorbis` | audio/ogg | Open-source compressed format |
| `ogg_opus` | audio/ogg | Low-latency compressed format |
| `pcm` | audio/pcm | Uncompressed raw audio |
| `json` | application/x-json-stream | Speech marks (metadata only, no audio) |

### Speech Mark Types
| Type | Description |
|------|-------------|
| `sentence` | Marks beginning and end of each sentence |
| `word` | Marks beginning and end of each word |
| `viseme` | Describes face/mouth position for lip-syncing |
| `ssml` | Marks SSML tags in input |

### Task Status Values
| Status | Description |
|--------|-------------|
| `scheduled` | Task is queued |
| `inProgress` | Task is being processed |
| `completed` | Task completed successfully |
| `failed` | Task failed |
