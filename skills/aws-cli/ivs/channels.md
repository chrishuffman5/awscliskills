# Channels

### 1.1 `create-channel`

Creates a new IVS channel and an associated stream key.

**Synopsis:**
```bash
aws ivs create-channel \
    [--name <value>] \
    [--type <value>] \
    [--latency-mode <value>] \
    [--authorized | --no-authorized] \
    [--insecure-ingest | --no-insecure-ingest] \
    [--container-format <value>] \
    [--recording-configuration-arn <value>] \
    [--playback-restriction-policy-arn <value>] \
    [--preset <value>] \
    [--multitrack-input-configuration <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | No | string | None | Channel name (0-128 chars, `[a-zA-Z0-9-_]*`) |
| `--type` | No | string | `STANDARD` | `BASIC`, `STANDARD`, `ADVANCED_SD`, `ADVANCED_HD` |
| `--latency-mode` | No | string | `LOW` | `NORMAL` or `LOW` (near-real-time) |
| `--authorized` | No | boolean | false | Enable playback authorization |
| `--insecure-ingest` | No | boolean | false | Allow insecure RTMP/SRT ingest |
| `--container-format` | No | string | `TS` | `TS` or `FRAGMENTED_MP4` |
| `--recording-configuration-arn` | No | string | None | ARN of recording configuration |
| `--playback-restriction-policy-arn` | No | string | None | ARN of playback restriction policy |
| `--preset` | No | string | None | `HIGHER_BANDWIDTH_DELIVERY` or `CONSTRAINED_BANDWIDTH_DELIVERY` (ADVANCED types only) |
| `--multitrack-input-configuration` | No | structure | None | Multitrack input config (STANDARD only) |
| `--tags` | No | map | None | Key-value tag pairs (max 50) |

**MultitrackInputConfiguration:**
```json
{
    "enabled": true,
    "maximumResolution": "SD|HD|FULL_HD",
    "policy": "ALLOW|REQUIRE"
}
```

**Output Schema:**
```json
{
    "channel": {
        "arn": "string",
        "name": "string",
        "type": "BASIC|STANDARD|ADVANCED_SD|ADVANCED_HD",
        "latencyMode": "NORMAL|LOW",
        "authorized": "boolean",
        "insecureIngest": "boolean",
        "containerFormat": "TS|FRAGMENTED_MP4",
        "ingestEndpoint": "string",
        "playbackUrl": "string",
        "preset": "string",
        "recordingConfigurationArn": "string",
        "playbackRestrictionPolicyArn": "string",
        "srt": {"endpoint": "string", "passphrase": "string"},
        "multitrackInputConfiguration": {},
        "tags": {"string": "string"}
    },
    "streamKey": {
        "arn": "string",
        "channelArn": "string",
        "value": "string",
        "tags": {"string": "string"}
    }
}
```

---

### 1.2 `get-channel`

Gets details for a channel.

**Synopsis:**
```bash
aws ivs get-channel \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the channel |

**Output Schema:** `channel` object (same as in `create-channel` output, without `streamKey`).

---

### 1.3 `batch-get-channel`

Gets details for multiple channels in a single call.

**Synopsis:**
```bash
aws ivs batch-get-channel \
    --arns <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arns` | **Yes** | list | -- | List of channel ARNs (max 50) |

**Output Schema:**
```json
{
    "channels": [{}],
    "errors": [{"arn": "string", "code": "string", "message": "string"}]
}
```

---

### 1.4 `list-channels`

Lists all channels. **Paginated operation.**

**Synopsis:**
```bash
aws ivs list-channels \
    [--filter-by-name <value>] \
    [--filter-by-recording-configuration-arn <value>] \
    [--filter-by-playback-restriction-policy-arn <value>] \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filter-by-name` | No | string | None | Filter by channel name prefix |
| `--filter-by-recording-configuration-arn` | No | string | None | Filter by recording config ARN |
| `--filter-by-playback-restriction-policy-arn` | No | string | None | Filter by restriction policy ARN |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results per page (1-100) |

**Output Schema:**
```json
{
    "channels": [
        {
            "arn": "string",
            "name": "string",
            "latencyMode": "NORMAL|LOW",
            "authorized": "boolean",
            "recordingConfigurationArn": "string",
            "playbackRestrictionPolicyArn": "string",
            "tags": {"string": "string"}
        }
    ],
    "nextToken": "string"
}
```

---

### 1.5 `update-channel`

Updates a channel's configuration.

**Synopsis:**
```bash
aws ivs update-channel \
    --arn <value> \
    [--name <value>] \
    [--type <value>] \
    [--latency-mode <value>] \
    [--authorized | --no-authorized] \
    [--insecure-ingest | --no-insecure-ingest] \
    [--container-format <value>] \
    [--recording-configuration-arn <value>] \
    [--playback-restriction-policy-arn <value>] \
    [--preset <value>] \
    [--multitrack-input-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the channel to update |
| All other params | No | -- | -- | Same as `create-channel` (except `--tags`) |

**Output Schema:** `channel` object.

---

### 1.6 `delete-channel`

Deletes a channel and associated stream keys. The stream must be stopped first.

**Synopsis:**
```bash
aws ivs delete-channel \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the channel to delete |

**Output:** None
