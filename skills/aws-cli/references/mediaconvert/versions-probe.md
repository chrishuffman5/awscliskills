# Versions & Probe

### 7.1 `list-versions`

Lists available MediaConvert job engine versions. **Paginated operation.**

**Synopsis:**
```bash
aws mediaconvert list-versions \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Max total items to return |

**Output Schema:**
```json
{
    "NextToken": "string",
    "Versions": [
        {
            "Version": "string",
            "ExpirationDate": "timestamp"
        }
    ]
}
```

---

### 7.2 `probe`

Probes media files to retrieve track, codec, and format information without starting a transcoding job.

**Synopsis:**
```bash
aws mediaconvert probe \
    [--input-files <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--input-files` | No | list | None | Media files to probe |

**InputFiles structure:**
```json
[
    {
        "FileUrl": "string"
    }
]
```

The `FileUrl` accepts S3, HTTP, or HTTPS URLs.

**Output Schema:**
```json
{
    "ProbeResults": [
        {
            "Container": {
                "Duration": "double",
                "Format": "mp4|quicktime|matroska|webm|mxf|wave",
                "Tracks": [
                    {
                        "Index": "integer",
                        "TrackType": "video|audio|data",
                        "Duration": "double",
                        "Codec": "AAC|AC3|EAC3|FLAC|MP3|OPUS|PCM|VORBIS|AV1|AVC|HEVC|JPEG2000|MJPEG|MPEG2|PRORES|VP8|VP9|UNKNOWN",
                        "VideoProperties": {
                            "BitRate": "long",
                            "BitDepth": "integer",
                            "Width": "integer",
                            "Height": "integer",
                            "FrameRate": {
                                "Numerator": "integer",
                                "Denominator": "integer"
                            },
                            "ColorPrimaries": "string",
                            "MatrixCoefficients": "string",
                            "TransferCharacteristics": "string",
                            "CodecMetadata": {
                                "BitDepth": "integer",
                                "ChromaSubsampling": "string",
                                "CodedFrameRate": {},
                                "Height": "integer",
                                "Width": "integer",
                                "Level": "string",
                                "Profile": "string",
                                "ScanType": "string"
                            }
                        },
                        "AudioProperties": {
                            "BitRate": "long",
                            "BitDepth": "integer",
                            "Channels": "integer",
                            "SampleRate": "integer",
                            "LanguageCode": "string",
                            "FrameRate": {}
                        },
                        "DataProperties": {
                            "LanguageCode": "string"
                        }
                    }
                ]
            },
            "Metadata": {
                "FileSize": "long",
                "LastModified": "timestamp",
                "MimeType": "string",
                "ETag": "string"
            },
            "TrackMappings": [
                {
                    "VideoTrackIndexes": ["integer"],
                    "AudioTrackIndexes": ["integer"],
                    "DataTrackIndexes": ["integer"]
                }
            ]
        }
    ]
}
```
