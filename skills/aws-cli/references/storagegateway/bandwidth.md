# Bandwidth

### 7.1 `update-bandwidth-rate-limit`

Updates the bandwidth rate limits for a gateway. Supported for stored volume, cached volume, and tape gateways. For S3 File Gateways, use `update-bandwidth-rate-limit-schedule` instead.

**Synopsis:**
```bash
aws storagegateway update-bandwidth-rate-limit \
    --gateway-arn <value> \
    [--average-upload-rate-limit-in-bits-per-sec <value>] \
    [--average-download-rate-limit-in-bits-per-sec <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | Gateway ARN (50-500 chars) |
| `--average-upload-rate-limit-in-bits-per-sec` | No | long | None | Upload rate limit in bps (min: 51200 = 50 Kbps) |
| `--average-download-rate-limit-in-bits-per-sec` | No | long | None | Download rate limit in bps (min: 102400 = 100 Kbps) |

**Output Schema:**
```json
{
    "GatewayARN": "string"
}
```

---

### 7.2 `describe-bandwidth-rate-limit`

Returns the bandwidth rate limits for a gateway.

**Synopsis:**
```bash
aws storagegateway describe-bandwidth-rate-limit \
    --gateway-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | Gateway ARN |

**Output Schema:**
```json
{
    "GatewayARN": "string",
    "AverageUploadRateLimitInBitsPerSec": "long",
    "AverageDownloadRateLimitInBitsPerSec": "long"
}
```

---

### 7.3 `delete-bandwidth-rate-limit`

Deletes the bandwidth rate limit for a gateway. Removes throttling so the gateway uses maximum available bandwidth.

**Synopsis:**
```bash
aws storagegateway delete-bandwidth-rate-limit \
    --gateway-arn <value> \
    --bandwidth-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | Gateway ARN |
| `--bandwidth-type` | **Yes** | string | -- | Which limit to delete: `UPLOAD`, `DOWNLOAD`, or `ALL` |

**Output Schema:**
```json
{
    "GatewayARN": "string"
}
```

---

### 7.4 `update-bandwidth-rate-limit-schedule`

Updates a gateway's bandwidth rate limit schedule. Allows time-based throttling with different limits at different times. Supported for all gateway types.

**Synopsis:**
```bash
aws storagegateway update-bandwidth-rate-limit-schedule \
    --gateway-arn <value> \
    --bandwidth-rate-limit-intervals <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | Gateway ARN |
| `--bandwidth-rate-limit-intervals` | **Yes** | list | -- | List of time-based rate limit intervals |

**Interval Structure:**
```json
[
    {
        "StartHourOfDay": "integer",
        "StartMinuteOfHour": "integer",
        "EndHourOfDay": "integer",
        "EndMinuteOfHour": "integer",
        "DaysOfWeek": ["integer"],
        "AverageUploadRateLimitInBitsPerSec": "long",
        "AverageDownloadRateLimitInBitsPerSec": "long"
    }
]
```

- `DaysOfWeek`: 0=Sunday to 6=Saturday
- Hours: 0-23, Minutes: 0-59
- Upload min: 51200 bps, Download min: 102400 bps

**Output Schema:**
```json
{
    "GatewayARN": "string"
}
```

---

### 7.5 `describe-bandwidth-rate-limit-schedule`

Returns the bandwidth rate limit schedule for a gateway.

**Synopsis:**
```bash
aws storagegateway describe-bandwidth-rate-limit-schedule \
    --gateway-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--gateway-arn` | **Yes** | string | -- | Gateway ARN |

**Output Schema:**
```json
{
    "GatewayARN": "string",
    "BandwidthRateLimitIntervals": [
        {
            "StartHourOfDay": "integer",
            "StartMinuteOfHour": "integer",
            "EndHourOfDay": "integer",
            "EndMinuteOfHour": "integer",
            "DaysOfWeek": ["integer"],
            "AverageUploadRateLimitInBitsPerSec": "long",
            "AverageDownloadRateLimitInBitsPerSec": "long"
        }
    ]
}
```
