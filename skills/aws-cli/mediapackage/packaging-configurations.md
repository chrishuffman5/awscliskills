# Packaging Configurations (VOD)

### 6.1 `create-packaging-configuration`

Creates a packaging configuration that defines output format (HLS, DASH, CMAF, or MSS) for VOD assets.

**Synopsis:**
```bash
aws mediapackage-vod create-packaging-configuration \
    --id <value> \
    --packaging-group-id <value> \
    [--cmaf-package <value>] \
    [--dash-package <value>] \
    [--hls-package <value>] \
    [--mss-package <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Unique ID for the packaging configuration |
| `--packaging-group-id` | **Yes** | string | -- | ID of the packaging group |
| `--cmaf-package` | No | structure | None | CMAF packaging configuration |
| `--dash-package` | No | structure | None | DASH packaging configuration |
| `--hls-package` | No | structure | None | HLS packaging configuration |
| `--mss-package` | No | structure | None | MSS packaging configuration |
| `--tags` | No | map | None | Key-value tag pairs |

**HlsPackage:**
```json
{
    "HlsManifests": [
        {
            "AdMarkers": "NONE|SCTE35_ENHANCED|PASSTHROUGH",
            "IncludeIframeOnlyStream": false,
            "ManifestName": "index",
            "ProgramDateTimeIntervalSeconds": 0,
            "RepeatExtXKey": true,
            "StreamSelection": {
                "MaxVideoBitsPerSecond": 2147483647,
                "MinVideoBitsPerSecond": 0,
                "StreamOrder": "ORIGINAL|VIDEO_BITRATE_ASCENDING|VIDEO_BITRATE_DESCENDING"
            }
        }
    ],
    "SegmentDurationSeconds": 6,
    "UseAudioRenditionGroup": false,
    "IncludeDvbSubtitles": false,
    "Encryption": {
        "ConstantInitializationVector": "string",
        "EncryptionMethod": "AES_128|SAMPLE_AES",
        "SpekeKeyProvider": {
            "RoleArn": "string",
            "SystemIds": ["string"],
            "Url": "string",
            "EncryptionContractConfiguration": {
                "PresetSpeke20Audio": "PRESET-AUDIO-1|PRESET-AUDIO-2|PRESET-AUDIO-3|SHARED|UNENCRYPTED",
                "PresetSpeke20Video": "PRESET-VIDEO-1|PRESET-VIDEO-2|...|SHARED|UNENCRYPTED"
            }
        }
    }
}
```

**DashPackage:**
```json
{
    "DashManifests": [
        {
            "ManifestLayout": "FULL|COMPACT",
            "ManifestName": "index",
            "MinBufferTimeSeconds": 30,
            "Profile": "NONE|HBBTV_1_5",
            "ScteMarkersSource": "SEGMENTS|MANIFEST",
            "StreamSelection": {}
        }
    ],
    "SegmentDurationSeconds": 6,
    "SegmentTemplateFormat": "NUMBER_WITH_TIMELINE|TIME_WITH_TIMELINE|NUMBER_WITH_DURATION",
    "PeriodTriggers": ["ADS"],
    "IncludeEncoderConfigurationInSegments": false,
    "IncludeIframeOnlyStream": false,
    "Encryption": {}
}
```

**CmafPackage:**
```json
{
    "HlsManifests": [
        {
            "AdMarkers": "NONE|SCTE35_ENHANCED|PASSTHROUGH",
            "IncludeIframeOnlyStream": false,
            "ManifestName": "index",
            "ProgramDateTimeIntervalSeconds": 0,
            "RepeatExtXKey": true,
            "StreamSelection": {}
        }
    ],
    "SegmentDurationSeconds": 6,
    "IncludeEncoderConfigurationInSegments": false,
    "Encryption": {
        "SpekeKeyProvider": {
            "RoleArn": "string",
            "SystemIds": ["string"],
            "Url": "string"
        }
    }
}
```

**MssPackage:**
```json
{
    "MssManifests": [
        {
            "ManifestName": "index",
            "StreamSelection": {}
        }
    ],
    "SegmentDurationSeconds": 6,
    "Encryption": {
        "SpekeKeyProvider": {
            "RoleArn": "string",
            "SystemIds": ["string"],
            "Url": "string"
        }
    }
}
```

**Output Schema:**
```json
{
    "Arn": "string",
    "Id": "string",
    "PackagingGroupId": "string",
    "CreatedAt": "string",
    "Tags": {"string": "string"},
    "CmafPackage": {},
    "DashPackage": {},
    "HlsPackage": {},
    "MssPackage": {}
}
```

---

### 6.2 `describe-packaging-configuration`

Describes a packaging configuration.

**Synopsis:**
```bash
aws mediapackage-vod describe-packaging-configuration \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | ID of the packaging configuration |

**Output Schema:**
```json
{
    "Arn": "string",
    "Id": "string",
    "PackagingGroupId": "string",
    "CreatedAt": "string",
    "Tags": {"string": "string"},
    "CmafPackage": {},
    "DashPackage": {},
    "HlsPackage": {},
    "MssPackage": {}
}
```

---

### 6.3 `list-packaging-configurations`

Lists packaging configurations, optionally filtered by packaging group. **Paginated operation.**

**Synopsis:**
```bash
aws mediapackage-vod list-packaging-configurations \
    [--max-results <value>] \
    [--next-token <value>] \
    [--packaging-group-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--max-results` | No | integer | None | Maximum number of results per page |
| `--next-token` | No | string | None | Pagination token |
| `--packaging-group-id` | No | string | None | Filter by packaging group ID |

**Output Schema:**
```json
{
    "PackagingConfigurations": [
        {
            "Arn": "string",
            "Id": "string",
            "PackagingGroupId": "string",
            "CreatedAt": "string",
            "Tags": {"string": "string"},
            "CmafPackage": {},
            "DashPackage": {},
            "HlsPackage": {},
            "MssPackage": {}
        }
    ],
    "NextToken": "string"
}
```

---

### 6.4 `delete-packaging-configuration`

Deletes a packaging configuration.

**Synopsis:**
```bash
aws mediapackage-vod delete-packaging-configuration \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | ID of the packaging configuration to delete |

**Output:** None
