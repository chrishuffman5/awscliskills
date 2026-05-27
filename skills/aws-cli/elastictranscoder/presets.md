# Presets

### 3.1 `create-preset`

Creates a custom transcoding preset with audio, video, and thumbnail settings.

**Synopsis:**
```bash
aws elastictranscoder create-preset \
    --name <value> \
    --container <value> \
    [--description <value>] \
    [--video <value>] \
    [--audio <value>] \
    [--thumbnails <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Preset name |
| `--container` | **Yes** | string | -- | `fmp4`, `flv`, `fmp4`, `gif`, `mp2`, `mp3`, `mp4`, `mpg`, `mxf`, `oga`, `ogg`, `ts`, `wav`, `webm` |
| `--description` | No | string | None | Preset description |
| `--video` | No | structure | None | Video encoding settings |
| `--audio` | No | structure | None | Audio encoding settings |
| `--thumbnails` | No | structure | None | Thumbnail generation settings |

**Video settings:**
```json
{
    "Codec": "gif|H.264|mpeg2|vp8|vp9",
    "CodecOptions": {
        "Profile": "baseline|main|high|0|1|2|3",
        "Level": "1|1b|1.1|1.2|...|5.1",
        "MaxReferenceFrames": "string",
        "MaxBitRate": "string",
        "BufferSize": "string",
        "InterlacedMode": "Progressive|TopFirst|BottomFirst|Auto",
        "ColorSpaceConversionMode": "None|Bt709ToBt601|Bt601ToBt709|Auto"
    },
    "KeyframesMaxDist": "string",
    "FixedGOP": "string",
    "BitRate": "string",
    "FrameRate": "auto|10|15|23.97|24|25|29.97|30|50|60",
    "MaxFrameRate": "string",
    "Resolution": "auto|widthxheight",
    "AspectRatio": "auto|1:1|4:3|3:2|16:9",
    "MaxWidth": "string",
    "MaxHeight": "string",
    "DisplayAspectRatio": "auto|1:1|4:3|3:2|16:9",
    "SizingPolicy": "Fit|Fill|Stretch|Keep|ShrinkToFit|ShrinkToFill",
    "PaddingPolicy": "Pad|NoPad",
    "Watermarks": []
}
```

**Audio settings:**
```json
{
    "Codec": "AAC|flac|mp2|mp3|pcm|vorbis",
    "SampleRate": "auto|22050|32000|44100|48000|96000",
    "BitRate": "string",
    "Channels": "auto|0|1|2",
    "AudioPackingMode": "SingleTrack|OneChannelPerTrack|OneChannelPerTrackWithMosTo8Tracks",
    "CodecOptions": {
        "Profile": "auto|AAC-LC|HE-AAC|HE-AACv2",
        "BitDepth": "8|16|24|32",
        "BitOrder": "LittlEndian",
        "Signed": "Signed|Unsigned"
    }
}
```

**Thumbnails settings:**
```json
{
    "Format": "jpg|png",
    "Interval": "string",
    "Resolution": "widthxheight",
    "AspectRatio": "auto|1:1|4:3|3:2|16:9",
    "MaxWidth": "string",
    "MaxHeight": "string",
    "SizingPolicy": "Fit|Fill|Stretch|Keep|ShrinkToFit|ShrinkToFill",
    "PaddingPolicy": "Pad|NoPad"
}
```

**Output Schema:**
```json
{
    "Preset": {
        "Id": "string",
        "Arn": "string",
        "Name": "string",
        "Description": "string",
        "Container": "string",
        "Type": "Custom",
        "Video": {},
        "Audio": {},
        "Thumbnails": {}
    },
    "Warning": "string"
}
```

---

### 3.2 `read-preset`

Reads the settings for a preset.

**Synopsis:**
```bash
aws elastictranscoder read-preset \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Preset ID |

**Output Schema:**
```json
{
    "Preset": {
        "Id": "string",
        "Arn": "string",
        "Name": "string",
        "Description": "string",
        "Container": "string",
        "Type": "System|Custom",
        "Video": {},
        "Audio": {},
        "Thumbnails": {}
    }
}
```

---

### 3.3 `delete-preset`

Deletes a custom preset. Cannot delete system presets.

**Synopsis:**
```bash
aws elastictranscoder delete-preset \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Preset ID to delete |

**Output:** None

---

### 3.4 `list-presets`

Lists all presets (system and custom). **Paginated operation.**

**Synopsis:**
```bash
aws elastictranscoder list-presets \
    [--ascending <value>] \
    [--page-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--ascending` | No | string | None | `true` for ascending, `false` for descending |
| `--page-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "NextPageToken": "string",
    "Presets": [
        {
            "Id": "string",
            "Arn": "string",
            "Name": "string",
            "Description": "string",
            "Container": "string",
            "Type": "System|Custom",
            "Video": {},
            "Audio": {},
            "Thumbnails": {}
        }
    ]
}
```
