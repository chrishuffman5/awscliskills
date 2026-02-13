# Network Profiles

### 7.1 `create-network-profile`

Creates a network profile for simulating network conditions.

**Synopsis:**
```bash
aws devicefarm create-network-profile \
    --project-arn <value> \
    --name <value> \
    [--description <value>] \
    [--type <value>] \
    [--uplink-bandwidth-bits <value>] \
    [--downlink-bandwidth-bits <value>] \
    [--uplink-delay-ms <value>] \
    [--downlink-delay-ms <value>] \
    [--uplink-jitter-ms <value>] \
    [--downlink-jitter-ms <value>] \
    [--uplink-loss-percent <value>] \
    [--downlink-loss-percent <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project-arn` | **Yes** | string | -- | ARN of the project |
| `--name` | **Yes** | string | -- | Name of the network profile |
| `--description` | No | string | None | Description of the network profile |
| `--type` | No | string | `PRIVATE` | Type: `CURATED` or `PRIVATE` |
| `--uplink-bandwidth-bits` | No | long | None | Uplink bandwidth in bits per second |
| `--downlink-bandwidth-bits` | No | long | None | Downlink bandwidth in bits per second |
| `--uplink-delay-ms` | No | long | None | Uplink delay in milliseconds |
| `--downlink-delay-ms` | No | long | None | Downlink delay in milliseconds |
| `--uplink-jitter-ms` | No | long | None | Uplink jitter in milliseconds |
| `--downlink-jitter-ms` | No | long | None | Downlink jitter in milliseconds |
| `--uplink-loss-percent` | No | integer | 0 | Uplink packet loss percentage (0-100) |
| `--downlink-loss-percent` | No | integer | 0 | Downlink packet loss percentage (0-100) |

**Output Schema:**
```json
{
    "networkProfile": {
        "arn": "string",
        "name": "string",
        "description": "string",
        "type": "CURATED|PRIVATE",
        "uplinkBandwidthBits": "long",
        "downlinkBandwidthBits": "long",
        "uplinkDelayMs": "long",
        "downlinkDelayMs": "long",
        "uplinkJitterMs": "long",
        "downlinkJitterMs": "long",
        "uplinkLossPercent": "integer",
        "downlinkLossPercent": "integer"
    }
}
```

---

### 7.2 `delete-network-profile`

Deletes a network profile.

**Synopsis:**
```bash
aws devicefarm delete-network-profile \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the network profile to delete |

**Output Schema:**
```json
{}
```

---

### 7.3 `get-network-profile`

Returns information about a network profile.

**Synopsis:**
```bash
aws devicefarm get-network-profile \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the network profile |

**Output Schema:**
```json
{
    "networkProfile": {
        "arn": "string",
        "name": "string",
        "description": "string",
        "type": "CURATED|PRIVATE",
        "uplinkBandwidthBits": "long",
        "downlinkBandwidthBits": "long",
        "uplinkDelayMs": "long",
        "downlinkDelayMs": "long",
        "uplinkJitterMs": "long",
        "downlinkJitterMs": "long",
        "uplinkLossPercent": "integer",
        "downlinkLossPercent": "integer"
    }
}
```

---

### 7.4 `list-network-profiles`

Returns a list of network profiles. **Paginated operation.**

**Synopsis:**
```bash
aws devicefarm list-network-profiles \
    --arn <value> \
    [--type <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the project |
| `--type` | No | string | None | Filter by type: `CURATED` or `PRIVATE` |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "networkProfiles": [
        {
            "arn": "string",
            "name": "string",
            "description": "string",
            "type": "CURATED|PRIVATE",
            "uplinkBandwidthBits": "long",
            "downlinkBandwidthBits": "long",
            "uplinkDelayMs": "long",
            "downlinkDelayMs": "long",
            "uplinkJitterMs": "long",
            "downlinkJitterMs": "long",
            "uplinkLossPercent": "integer",
            "downlinkLossPercent": "integer"
        }
    ],
    "nextToken": "string"
}
```

---

### 7.5 `update-network-profile`

Updates a network profile.

**Synopsis:**
```bash
aws devicefarm update-network-profile \
    --arn <value> \
    [--name <value>] \
    [--description <value>] \
    [--type <value>] \
    [--uplink-bandwidth-bits <value>] \
    [--downlink-bandwidth-bits <value>] \
    [--uplink-delay-ms <value>] \
    [--downlink-delay-ms <value>] \
    [--uplink-jitter-ms <value>] \
    [--downlink-jitter-ms <value>] \
    [--uplink-loss-percent <value>] \
    [--downlink-loss-percent <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the network profile to update |
| `--name` | No | string | None | Updated name |
| `--description` | No | string | None | Updated description |
| `--type` | No | string | None | Updated type |
| `--uplink-bandwidth-bits` | No | long | None | Updated uplink bandwidth |
| `--downlink-bandwidth-bits` | No | long | None | Updated downlink bandwidth |
| `--uplink-delay-ms` | No | long | None | Updated uplink delay |
| `--downlink-delay-ms` | No | long | None | Updated downlink delay |
| `--uplink-jitter-ms` | No | long | None | Updated uplink jitter |
| `--downlink-jitter-ms` | No | long | None | Updated downlink jitter |
| `--uplink-loss-percent` | No | integer | None | Updated uplink loss percentage |
| `--downlink-loss-percent` | No | integer | None | Updated downlink loss percentage |

**Output Schema:**
```json
{
    "networkProfile": {
        "arn": "string",
        "name": "string",
        "description": "string",
        "type": "CURATED|PRIVATE",
        "uplinkBandwidthBits": "long",
        "downlinkBandwidthBits": "long",
        "uplinkDelayMs": "long",
        "downlinkDelayMs": "long",
        "uplinkJitterMs": "long",
        "downlinkJitterMs": "long",
        "uplinkLossPercent": "integer",
        "downlinkLossPercent": "integer"
    }
}
```
