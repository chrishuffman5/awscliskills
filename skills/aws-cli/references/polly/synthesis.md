# Synthesis

### 1.1 `synthesize-speech`

Synthesizes speech from text and returns the audio stream directly. For texts longer than 3000 characters (6000 for SSML), use `start-speech-synthesis-task` instead.

**Synopsis:**
```bash
aws polly synthesize-speech \
    --output-format <value> \
    --text <value> \
    --voice-id <value> \
    [--engine <value>] \
    [--language-code <value>] \
    [--lexicon-names <value>] \
    [--sample-rate <value>] \
    [--speech-mark-types <value>] \
    [--text-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>] \
    <outfile>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--output-format` | **Yes** | string | -- | Audio format: `json`, `mp3`, `ogg_opus`, `ogg_vorbis`, `pcm` |
| `--text` | **Yes** | string | -- | Input text to synthesize (plain text or SSML) |
| `--voice-id` | **Yes** | string | -- | Voice ID (e.g., `Joanna`, `Matthew`, `Amy`, `Brian`) |
| `<outfile>` | **Yes** | string | -- | Output file path for the audio |
| `--engine` | No | string | `standard` | Engine: `standard`, `neural`, `long-form`, `generative` |
| `--language-code` | No | string | -- | Language code (required for bilingual voices). E.g., `en-US`, `fr-FR`, `ja-JP` |
| `--lexicon-names` | No | list(string) | -- | Pronunciation lexicons to apply (max 5) |
| `--sample-rate` | No | string | -- | Audio frequency in Hz. MP3/OGG: `8000`-`48000`; PCM: `8000`, `16000` |
| `--speech-mark-types` | No | list(string) | -- | Speech mark types: `sentence`, `ssml`, `viseme`, `word` (max 4) |
| `--text-type` | No | string | `text` | Input type: `text` or `ssml` |

**Output:**
The audio is written to `<outfile>`. Response metadata includes:
```json
{
    "ContentType": "string",
    "RequestCharacters": "integer"
}
```

---

### 1.2 `start-speech-synthesis-task`

Starts an asynchronous speech synthesis task. The output is stored in an S3 bucket. Supports longer text (up to 100,000 characters for standard, 200,000 for SSML).

**Synopsis:**
```bash
aws polly start-speech-synthesis-task \
    --output-format <value> \
    --output-s3-bucket-name <value> \
    --text <value> \
    --voice-id <value> \
    [--engine <value>] \
    [--language-code <value>] \
    [--lexicon-names <value>] \
    [--output-s3-key-prefix <value>] \
    [--sample-rate <value>] \
    [--sns-topic-arn <value>] \
    [--speech-mark-types <value>] \
    [--text-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--output-format` | **Yes** | string | -- | Audio format: `json`, `mp3`, `ogg_opus`, `ogg_vorbis`, `pcm` |
| `--output-s3-bucket-name` | **Yes** | string | -- | S3 bucket for output audio |
| `--text` | **Yes** | string | -- | Input text (or `file://` path) |
| `--voice-id` | **Yes** | string | -- | Voice ID |
| `--engine` | No | string | `standard` | Engine: `standard`, `neural`, `long-form`, `generative` |
| `--language-code` | No | string | -- | Language code |
| `--lexicon-names` | No | list(string) | -- | Pronunciation lexicons (max 5) |
| `--output-s3-key-prefix` | No | string | -- | S3 key prefix for output file |
| `--sample-rate` | No | string | -- | Audio frequency in Hz |
| `--sns-topic-arn` | No | string | -- | SNS topic ARN for status notifications |
| `--speech-mark-types` | No | list(string) | -- | Speech mark types (max 4) |
| `--text-type` | No | string | `text` | Input type: `text` or `ssml` |

**Output Schema:**
```json
{
    "SynthesisTask": {
        "Engine": "standard|neural|long-form|generative",
        "TaskId": "string",
        "TaskStatus": "scheduled|inProgress|completed|failed",
        "TaskStatusReason": "string",
        "OutputUri": "string",
        "CreationTime": "timestamp",
        "RequestCharacters": "integer",
        "SnsTopicArn": "string",
        "LexiconNames": ["string"],
        "OutputFormat": "json|mp3|ogg_opus|ogg_vorbis|pcm",
        "SampleRate": "string",
        "SpeechMarkTypes": ["sentence|ssml|viseme|word"],
        "TextType": "text|ssml",
        "VoiceId": "string",
        "LanguageCode": "string"
    }
}
```

---

### 1.3 `get-speech-synthesis-task`

Gets details and status of a speech synthesis task.

**Synopsis:**
```bash
aws polly get-speech-synthesis-task \
    --task-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--task-id` | **Yes** | string | -- | Task ID from start-speech-synthesis-task |

**Output Schema:**
```json
{
    "SynthesisTask": {
        "Engine": "string",
        "TaskId": "string",
        "TaskStatus": "scheduled|inProgress|completed|failed",
        "TaskStatusReason": "string",
        "OutputUri": "string",
        "CreationTime": "timestamp",
        "RequestCharacters": "integer",
        "SnsTopicArn": "string",
        "LexiconNames": ["string"],
        "OutputFormat": "string",
        "SampleRate": "string",
        "SpeechMarkTypes": ["string"],
        "TextType": "string",
        "VoiceId": "string",
        "LanguageCode": "string"
    }
}
```

---

### 1.4 `list-speech-synthesis-tasks`

Lists speech synthesis tasks. **Paginated operation.**

**Synopsis:**
```bash
aws polly list-speech-synthesis-tasks \
    [--status <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--status` | No | string | -- | Filter by status: `scheduled`, `inProgress`, `completed`, `failed` |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "NextToken": "string",
    "SynthesisTasks": [
        {
            "Engine": "string",
            "TaskId": "string",
            "TaskStatus": "string",
            "TaskStatusReason": "string",
            "OutputUri": "string",
            "CreationTime": "timestamp",
            "RequestCharacters": "integer",
            "OutputFormat": "string",
            "VoiceId": "string",
            "LanguageCode": "string"
        }
    ]
}
```

---

### 1.5 `describe-voices`

Returns the list of voices available for use in speech synthesis. Supports filtering by language and engine.

**Synopsis:**
```bash
aws polly describe-voices \
    [--engine <value>] \
    [--language-code <value>] \
    [--include-additional-language-codes | --no-include-additional-language-codes] \
    [--cli-input-json | --cli-input-yaml] \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--engine` | No | string | -- | Filter by engine: `standard`, `neural`, `long-form`, `generative` |
| `--language-code` | No | string | -- | Filter by language code (e.g., `en-US`, `fr-FR`) |
| `--include-additional-language-codes` | No | boolean | false | Include bilingual voices |
| `--starting-token` | No | string | -- | Pagination token |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "Voices": [
        {
            "Gender": "Female|Male",
            "Id": "string",
            "LanguageCode": "string",
            "LanguageName": "string",
            "Name": "string",
            "AdditionalLanguageCodes": ["string"],
            "SupportedEngines": ["standard", "neural", "long-form", "generative"]
        }
    ],
    "NextToken": "string"
}
```
