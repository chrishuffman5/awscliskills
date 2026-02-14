# Media Streams

### 5.1 `add-flow-media-streams`

Adds media streams to a flow for ST 2110 JPEG XS or CDI transport.

**Synopsis:**
```bash
aws mediaconnect add-flow-media-streams \
    --flow-arn <value> \
    --media-streams <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--flow-arn` | **Yes** | string | -- | ARN of the flow |
| `--media-streams` | **Yes** | list | -- | Media stream configurations |

**MediaStream Structure:**

| Field | Required | Type | Description |
|-------|----------|------|-------------|
| `MediaStreamId` | **Yes** | integer | Unique identifier for the stream |
| `MediaStreamName` | **Yes** | string | Stream name |
| `MediaStreamType` | **Yes** | string | `video`, `audio`, or `ancillary-data` |
| `ClockRate` | No | integer | Sample rate (90000 for video, 48000/96000 for audio) |
| `Description` | No | string | Stream description |
| `Attributes` | No | structure | Format attributes (Fmtp with color encoding, scan mode, etc.) |
| `VideoFormat` | No | string | Video resolution/format shorthand |

**Attributes.Fmtp Structure:**
```json
{
    "ChannelOrder": "string",
    "Colorimetry": "BT601|BT709|BT2020|BT2100|ST2065-1|ST2065-3|XYZ",
    "ExactFramerate": "string",
    "Par": "string",
    "Range": "NARROW|FULL|FULLPROTECT",
    "ScanMode": "progressive|interlace|progressive-segmented-frame",
    "Tcs": "SDR|PQ|HLG|LINEAR|BT2100LINPQ|BT2100LINHLG|ST2065-1|ST428-1|DENSITY"
}
```

**Output Schema:**
```json
{
    "FlowArn": "string",
    "MediaStreams": [
        {
            "MediaStreamId": "integer",
            "MediaStreamName": "string",
            "MediaStreamType": "video|audio|ancillary-data",
            "ClockRate": "integer",
            "Description": "string",
            "Fmt": "integer",
            "Attributes": {"Fmtp": {}}
        }
    ]
}
```

---

### 5.2 `update-flow-media-stream`

Updates a media stream on a flow.

**Synopsis:**
```bash
aws mediaconnect update-flow-media-stream \
    --flow-arn <value> \
    --media-stream-name <value> \
    [--media-stream-type <value>] \
    [--clock-rate <value>] \
    [--description <value>] \
    [--attributes <value>] \
    [--video-format <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--flow-arn` | **Yes** | string | -- | ARN of the flow |
| `--media-stream-name` | **Yes** | string | -- | Name of the media stream to update |
| `--media-stream-type` | No | string | None | Updated type |
| `--clock-rate` | No | integer | None | Updated clock rate |
| `--description` | No | string | None | Updated description |
| `--attributes` | No | structure | None | Updated format attributes |
| `--video-format` | No | string | None | Updated video format |

**Output Schema:**
```json
{
    "FlowArn": "string",
    "MediaStream": { "..." }
}
```

---

### 5.3 `remove-flow-media-stream`

Removes a media stream from a flow.

**Synopsis:**
```bash
aws mediaconnect remove-flow-media-stream \
    --flow-arn <value> \
    --media-stream-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--flow-arn` | **Yes** | string | -- | ARN of the flow |
| `--media-stream-name` | **Yes** | string | -- | Name of the media stream to remove |

**Output Schema:**
```json
{
    "FlowArn": "string",
    "MediaStreamName": "string"
}
```
