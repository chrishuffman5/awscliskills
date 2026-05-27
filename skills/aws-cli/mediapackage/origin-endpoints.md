# Origin Endpoints

### 3.1 `create-origin-endpoint`

Creates an origin endpoint for delivering live content from a channel. Supports HLS, Low-Latency HLS, DASH, and MSS manifests.

**Synopsis:**
```bash
aws mediapackagev2 create-origin-endpoint \
    --channel-group-name <value> \
    --channel-name <value> \
    --origin-endpoint-name <value> \
    --container-type <value> \
    [--segment <value>] \
    [--client-token <value>] \
    [--description <value>] \
    [--startover-window-seconds <value>] \
    [--hls-manifests <value>] \
    [--low-latency-hls-manifests <value>] \
    [--dash-manifests <value>] \
    [--mss-manifests <value>] \
    [--force-endpoint-error-configuration <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-group-name` | **Yes** | string | -- | Name of the channel group (1-256 chars) |
| `--channel-name` | **Yes** | string | -- | Name of the channel (1-256 chars) |
| `--origin-endpoint-name` | **Yes** | string | -- | Unique endpoint name (1-256 chars, `[a-zA-Z0-9_-]+`) |
| `--container-type` | **Yes** | string | -- | Container format: `TS`, `CMAF`, or `ISM` |
| `--segment` | No | structure | None | Segment configuration (duration, encryption, SCTE) |
| `--client-token` | No | string | Auto | Idempotency token |
| `--description` | No | string | None | Descriptive text (0-1024 chars) |
| `--startover-window-seconds` | No | integer | None | Live rewind window in seconds (60-1209600) |
| `--hls-manifests` | No | list | None | HLS manifest configurations |
| `--low-latency-hls-manifests` | No | list | None | Low-latency HLS manifest configurations |
| `--dash-manifests` | No | list | None | DASH manifest configurations |
| `--mss-manifests` | No | list | None | MSS manifest configurations |
| `--force-endpoint-error-configuration` | No | structure | None | Failover error condition settings |
| `--tags` | No | map | None | Key-value tag pairs |

**Segment Configuration:**
```json
{
    "SegmentDurationSeconds": 6,
    "SegmentName": "string",
    "TsUseAudioRenditionGroup": true,
    "IncludeIframeOnlyStreams": false,
    "TsIncludeDvbSubtitles": false,
    "Scte": {
        "ScteFilter": ["SPLICE_INSERT", "BREAK", "PROVIDER_ADVERTISEMENT"],
        "ScteInSegments": "NONE|ALL"
    },
    "Encryption": {
        "ConstantInitializationVector": "string",
        "EncryptionMethod": {
            "TsEncryptionMethod": "AES_128|SAMPLE_AES",
            "CmafEncryptionMethod": "CENC|CBCS"
        },
        "KeyRotationIntervalSeconds": 300,
        "SpekeKeyProvider": {
            "EncryptionContractConfiguration": {
                "PresetSpeke20Audio": "PRESET_AUDIO_1|SHARED|UNENCRYPTED",
                "PresetSpeke20Video": "PRESET_VIDEO_1|SHARED|UNENCRYPTED"
            },
            "ResourceId": "string",
            "DrmSystems": ["CLEAR_KEY_AES_128", "FAIRPLAY", "PLAYREADY", "WIDEVINE"],
            "RoleArn": "string",
            "Url": "string"
        }
    }
}
```

**HLS Manifest Configuration:**
```json
[
    {
        "ManifestName": "string",
        "ChildManifestName": "string",
        "ManifestWindowSeconds": 60,
        "ProgramDateTimeIntervalSeconds": 0,
        "ScteHls": {"AdMarkerHls": "DATERANGE|SCTE35_ENHANCED"},
        "FilterConfiguration": {
            "ManifestFilter": "string",
            "Start": "timestamp",
            "End": "timestamp",
            "TimeDelaySeconds": 0
        },
        "StartTag": {"TimeOffset": 0.0, "Precise": false},
        "UrlEncodeChildManifest": false
    }
]
```

**DASH Manifest Configuration:**
```json
[
    {
        "ManifestName": "string",
        "ManifestWindowSeconds": 60,
        "MinUpdatePeriodSeconds": 2,
        "MinBufferTimeSeconds": 6,
        "SuggestedPresentationDelaySeconds": 0,
        "SegmentTemplateFormat": "NUMBER_WITH_TIMELINE",
        "PeriodTriggers": ["AVAILS", "DRM_KEY_ROTATION", "SOURCE_CHANGES"],
        "ScteDash": {"AdMarkerDash": "BINARY|XML"},
        "DrmSignaling": "INDIVIDUAL|REFERENCED",
        "UtcTiming": {
            "TimingMode": "HTTP_HEAD|HTTP_ISO|HTTP_XSDATE|UTC_DIRECT",
            "TimingSource": "string"
        }
    }
]
```

**ForceEndpointErrorConfiguration:**
```json
{
    "EndpointErrorConditions": [
        "STALE_MANIFEST",
        "INCOMPLETE_MANIFEST",
        "MISSING_DRM_KEY",
        "SLATE_INPUT"
    ]
}
```

**Output Schema:**
```json
{
    "Arn": "string",
    "ChannelGroupName": "string",
    "ChannelName": "string",
    "OriginEndpointName": "string",
    "ContainerType": "TS|CMAF|ISM",
    "Segment": {},
    "CreatedAt": "timestamp",
    "ModifiedAt": "timestamp",
    "Description": "string",
    "StartoverWindowSeconds": "integer",
    "HlsManifests": [
        {"ManifestName": "string", "Url": "string", "ChildManifestName": "string"}
    ],
    "LowLatencyHlsManifests": [
        {"ManifestName": "string", "Url": "string", "ChildManifestName": "string"}
    ],
    "DashManifests": [
        {"ManifestName": "string", "Url": "string"}
    ],
    "MssManifests": [
        {"ManifestName": "string", "Url": "string"}
    ],
    "ForceEndpointErrorConfiguration": {
        "EndpointErrorConditions": ["string"]
    },
    "ETag": "string",
    "Tags": {"string": "string"}
}
```

---

### 3.2 `get-origin-endpoint`

Retrieves details for an origin endpoint including manifest URLs.

**Synopsis:**
```bash
aws mediapackagev2 get-origin-endpoint \
    --channel-group-name <value> \
    --channel-name <value> \
    --origin-endpoint-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-group-name` | **Yes** | string | -- | Name of the channel group |
| `--channel-name` | **Yes** | string | -- | Name of the channel |
| `--origin-endpoint-name` | **Yes** | string | -- | Name of the origin endpoint |

**Output Schema:** Same as `create-origin-endpoint` output with additional `ResetAt` timestamp field.

---

### 3.3 `list-origin-endpoints`

Lists origin endpoints in a channel. **Paginated operation.**

**Synopsis:**
```bash
aws mediapackagev2 list-origin-endpoints \
    --channel-group-name <value> \
    --channel-name <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-group-name` | **Yes** | string | -- | Name of the channel group |
| `--channel-name` | **Yes** | string | -- | Name of the channel |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Number of items per API call |
| `--max-items` | No | integer | None | Total number of items to return |

**Output Schema:**
```json
{
    "Items": [
        {
            "Arn": "string",
            "ChannelGroupName": "string",
            "ChannelName": "string",
            "OriginEndpointName": "string",
            "ContainerType": "TS|CMAF|ISM",
            "Description": "string",
            "CreatedAt": "timestamp",
            "ModifiedAt": "timestamp",
            "HlsManifests": [{"ManifestName": "string", "ChildManifestName": "string", "Url": "string"}],
            "LowLatencyHlsManifests": [{"ManifestName": "string", "ChildManifestName": "string", "Url": "string"}],
            "DashManifests": [{"ManifestName": "string", "Url": "string"}],
            "MssManifests": [{"ManifestName": "string", "Url": "string"}],
            "ForceEndpointErrorConfiguration": {
                "EndpointErrorConditions": ["string"]
            }
        }
    ],
    "NextToken": "string"
}
```

---

### 3.4 `update-origin-endpoint`

Updates an origin endpoint's configuration.

**Synopsis:**
```bash
aws mediapackagev2 update-origin-endpoint \
    --channel-group-name <value> \
    --channel-name <value> \
    --origin-endpoint-name <value> \
    --container-type <value> \
    [--segment <value>] \
    [--description <value>] \
    [--startover-window-seconds <value>] \
    [--hls-manifests <value>] \
    [--low-latency-hls-manifests <value>] \
    [--dash-manifests <value>] \
    [--mss-manifests <value>] \
    [--force-endpoint-error-configuration <value>] \
    [--e-tag <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-group-name` | **Yes** | string | -- | Name of the channel group |
| `--channel-name` | **Yes** | string | -- | Name of the channel |
| `--origin-endpoint-name` | **Yes** | string | -- | Name of the origin endpoint |
| `--container-type` | **Yes** | string | -- | Container format: `TS`, `CMAF`, or `ISM` |
| `--segment` | No | structure | None | Updated segment configuration |
| `--description` | No | string | None | Updated description |
| `--startover-window-seconds` | No | integer | None | Updated rewind window (60-1209600) |
| `--hls-manifests` | No | list | None | Updated HLS manifests |
| `--low-latency-hls-manifests` | No | list | None | Updated LL-HLS manifests |
| `--dash-manifests` | No | list | None | Updated DASH manifests |
| `--mss-manifests` | No | list | None | Updated MSS manifests |
| `--force-endpoint-error-configuration` | No | structure | None | Updated failover config |
| `--e-tag` | No | string | None | Expected ETag for concurrent update safety |

**Output Schema:** Same as `create-origin-endpoint` output.

---

### 3.5 `delete-origin-endpoint`

Deletes an origin endpoint.

**Synopsis:**
```bash
aws mediapackagev2 delete-origin-endpoint \
    --channel-group-name <value> \
    --channel-name <value> \
    --origin-endpoint-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-group-name` | **Yes** | string | -- | Name of the channel group |
| `--channel-name` | **Yes** | string | -- | Name of the channel |
| `--origin-endpoint-name` | **Yes** | string | -- | Name of the origin endpoint to delete |

**Output:** None

---

### 3.6 `put-origin-endpoint-policy`

Attaches or updates an IAM policy on an origin endpoint.

**Synopsis:**
```bash
aws mediapackagev2 put-origin-endpoint-policy \
    --channel-group-name <value> \
    --channel-name <value> \
    --origin-endpoint-name <value> \
    --policy <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-group-name` | **Yes** | string | -- | Name of the channel group |
| `--channel-name` | **Yes** | string | -- | Name of the channel |
| `--origin-endpoint-name` | **Yes** | string | -- | Name of the origin endpoint |
| `--policy` | **Yes** | string | -- | JSON policy document |

**Output:** None

---

### 3.7 `get-origin-endpoint-policy`

Retrieves the IAM policy attached to an origin endpoint.

**Synopsis:**
```bash
aws mediapackagev2 get-origin-endpoint-policy \
    --channel-group-name <value> \
    --channel-name <value> \
    --origin-endpoint-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-group-name` | **Yes** | string | -- | Name of the channel group |
| `--channel-name` | **Yes** | string | -- | Name of the channel |
| `--origin-endpoint-name` | **Yes** | string | -- | Name of the origin endpoint |

**Output Schema:**
```json
{
    "ChannelGroupName": "string",
    "ChannelName": "string",
    "OriginEndpointName": "string",
    "Policy": "string"
}
```

---

### 3.8 `delete-origin-endpoint-policy`

Deletes the IAM policy from an origin endpoint.

**Synopsis:**
```bash
aws mediapackagev2 delete-origin-endpoint-policy \
    --channel-group-name <value> \
    --channel-name <value> \
    --origin-endpoint-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-group-name` | **Yes** | string | -- | Name of the channel group |
| `--channel-name` | **Yes** | string | -- | Name of the channel |
| `--origin-endpoint-name` | **Yes** | string | -- | Name of the origin endpoint |

**Output:** None

---

### 3.9 `reset-origin-endpoint-state`

Resets an origin endpoint's state, clearing any error conditions.

**Synopsis:**
```bash
aws mediapackagev2 reset-origin-endpoint-state \
    --channel-group-name <value> \
    --channel-name <value> \
    --origin-endpoint-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-group-name` | **Yes** | string | -- | Name of the channel group |
| `--channel-name` | **Yes** | string | -- | Name of the channel |
| `--origin-endpoint-name` | **Yes** | string | -- | Name of the origin endpoint |

**Output:** None
