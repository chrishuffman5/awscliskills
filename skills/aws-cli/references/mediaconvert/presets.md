# Presets

### 3.1 `create-preset`

Creates a reusable output preset with audio, video, caption, and container settings.

**Synopsis:**
```bash
aws mediaconvert create-preset \
    --name <value> \
    --settings <value> \
    [--category <value>] \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Preset name |
| `--settings` | **Yes** | structure | -- | PresetSettings with audio, video, caption, and container config |
| `--category` | No | string | None | Preset category |
| `--description` | No | string | None | Preset description |
| `--tags` | No | map | None | Key-value tag pairs |

**Settings structure contains:**
- `AudioDescriptions` — Audio codec, normalization, channel mapping settings
- `CaptionDescriptions` — Caption format and destination settings
- `ContainerSettings` — Container format (MP4, MKV, MOV, etc.)
- `VideoDescription` — Video codec, resolution, bitrate settings

**Output Schema:**
```json
{
    "Preset": {
        "Arn": "string",
        "Name": "string",
        "Description": "string",
        "Category": "string",
        "Type": "SYSTEM|CUSTOM",
        "CreatedAt": "timestamp",
        "LastUpdated": "timestamp",
        "Settings": {
            "AudioDescriptions": [
                {
                    "AudioSourceName": "string",
                    "AudioType": "integer",
                    "AudioTypeControl": "FOLLOW_INPUT|USE_CONFIGURED",
                    "CodecSettings": {
                        "Codec": "AAC|MP2|MP3|WAV|AIFF|AC3|EAC3|EAC3_ATMOS|VORBIS|OPUS|PASSTHROUGH|FLAC"
                    },
                    "LanguageCode": "string",
                    "LanguageCodeControl": "FOLLOW_INPUT|USE_CONFIGURED",
                    "RemixSettings": {},
                    "StreamName": "string"
                }
            ],
            "CaptionDescriptions": [
                {
                    "DestinationSettings": {
                        "DestinationType": "BURN_IN|DVB_SUB|EMBEDDED|SCC|SRT|TTML|WEBVTT"
                    },
                    "LanguageCode": "string"
                }
            ],
            "ContainerSettings": {
                "Container": "string"
            },
            "VideoDescription": {
                "CodecSettings": {},
                "Height": "integer",
                "Width": "integer"
            }
        }
    }
}
```

---

### 3.2 `get-preset`

Retrieves a preset by name.

**Synopsis:**
```bash
aws mediaconvert get-preset \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Preset name |

**Output Schema:**
```json
{
    "Preset": {
        "Arn": "string",
        "Name": "string",
        "Description": "string",
        "Category": "string",
        "Type": "SYSTEM|CUSTOM",
        "CreatedAt": "timestamp",
        "LastUpdated": "timestamp",
        "Settings": {
            "AudioDescriptions": [],
            "CaptionDescriptions": [],
            "ContainerSettings": {},
            "VideoDescription": {}
        }
    }
}
```

---

### 3.3 `update-preset`

Updates a preset's settings, category, or description.

**Synopsis:**
```bash
aws mediaconvert update-preset \
    --name <value> \
    [--category <value>] \
    [--description <value>] \
    [--settings <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Preset name to modify |
| `--category` | No | string | None | Updated category |
| `--description` | No | string | None | Updated description |
| `--settings` | No | structure | None | Updated PresetSettings |

**Output Schema:**
```json
{
    "Preset": {
        "Arn": "string",
        "Name": "string",
        "Description": "string",
        "Category": "string",
        "Type": "SYSTEM|CUSTOM",
        "CreatedAt": "timestamp",
        "LastUpdated": "timestamp",
        "Settings": {
            "AudioDescriptions": [],
            "CaptionDescriptions": [],
            "ContainerSettings": {},
            "VideoDescription": {}
        }
    }
}
```

---

### 3.4 `list-presets`

Lists output presets. **Paginated operation.**

**Synopsis:**
```bash
aws mediaconvert list-presets \
    [--category <value>] \
    [--list-by <value>] \
    [--order <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--category` | No | string | None | Filter by category |
| `--list-by` | No | string | NAME | `NAME`, `CREATION_DATE`, `SYSTEM` |
| `--order` | No | string | None | `ASCENDING` or `DESCENDING` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Max total items to return |

**Output Schema:**
```json
{
    "NextToken": "string",
    "Presets": [
        {
            "Arn": "string",
            "Name": "string",
            "Description": "string",
            "Category": "string",
            "Type": "SYSTEM|CUSTOM",
            "CreatedAt": "timestamp",
            "LastUpdated": "timestamp",
            "Settings": {
                "AudioDescriptions": [],
                "CaptionDescriptions": [],
                "ContainerSettings": {},
                "VideoDescription": {}
            }
        }
    ]
}
```

---

### 3.5 `delete-preset`

Deletes a preset by name.

**Synopsis:**
```bash
aws mediaconvert delete-preset \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the preset to delete |

**Output:** None
