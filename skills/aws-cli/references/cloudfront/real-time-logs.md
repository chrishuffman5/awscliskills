# Real-Time Logs

### 12.1 `create-realtime-log-config`

Creates a real-time log configuration that streams CloudFront access logs to Amazon Kinesis Data Streams.

**Synopsis:**
```bash
aws cloudfront create-realtime-log-config \
    --end-points <value> \
    --fields <value> \
    --name <value> \
    --sampling-rate <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--end-points` | **Yes** | list | Kinesis data stream endpoint(s) |
| `--fields` | **Yes** | list(string) | Fields to include in log records |
| `--name` | **Yes** | string | Unique name |
| `--sampling-rate` | **Yes** | long | Sampling rate (1-100 inclusive) |

**EndPoints structure:**
```json
[
    {
        "StreamType": "Kinesis",
        "KinesisStreamConfig": {
            "RoleARN": "string",
            "StreamARN": "string"
        }
    }
]
```

**Common fields:** `timestamp`, `c-ip`, `sc-status`, `cs-uri-stem`, `cs-bytes`, `sc-bytes`, `time-taken`, `cs-method`, `cs-protocol`, `cs-host`, `cs-uri-query`, `cs-referer`, `cs-user-agent`, `x-edge-result-type`, `x-edge-response-result-type`, `x-edge-location`

**Output Schema:**
```json
{
    "RealtimeLogConfig": {
        "ARN": "string",
        "Name": "string",
        "SamplingRate": "long",
        "EndPoints": [
            {
                "StreamType": "string",
                "KinesisStreamConfig": {
                    "RoleARN": "string",
                    "StreamARN": "string"
                }
            }
        ],
        "Fields": ["string"]
    }
}
```

---

### 12.2 `get-realtime-log-config`

Gets a real-time log configuration.

**Synopsis:**
```bash
aws cloudfront get-realtime-log-config \
    [--name <value>] \
    [--arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--name` | No* | string | Config name (*one of name or ARN required) |
| `--arn` | No* | string | Config ARN |

**Output Schema:**
```json
{
    "RealtimeLogConfig": {
        "ARN": "string",
        "Name": "string",
        "SamplingRate": "long",
        "EndPoints": [{ "..." }],
        "Fields": ["string"]
    }
}
```

---

### 12.3 `list-realtime-log-configs`

Lists real-time log configurations.

**Synopsis:**
```bash
aws cloudfront list-realtime-log-configs \
    [--max-items <value>] \
    [--marker <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--max-items` | No | string | None | Maximum items to return |
| `--marker` | No | string | None | Pagination marker |

**Output Schema:**
```json
{
    "RealtimeLogConfigs": {
        "MaxItems": "integer",
        "NextMarker": "string",
        "Items": [
            {
                "ARN": "string",
                "Name": "string",
                "SamplingRate": "long",
                "EndPoints": [{ "..." }],
                "Fields": ["string"]
            }
        ]
    }
}
```

---

### 12.4 `update-realtime-log-config`

Updates a real-time log configuration.

**Synopsis:**
```bash
aws cloudfront update-realtime-log-config \
    [--end-points <value>] \
    [--fields <value>] \
    [--name <value>] \
    [--arn <value>] \
    [--sampling-rate <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--name` | No* | string | Config name (*one of name or ARN required) |
| `--arn` | No* | string | Config ARN |
| `--end-points` | No | list | Updated Kinesis endpoints |
| `--fields` | No | list(string) | Updated log fields |
| `--sampling-rate` | No | long | Updated sampling rate (1-100) |

**Output Schema:** Same as `get-realtime-log-config`.

---

### 12.5 `delete-realtime-log-config`

Deletes a real-time log configuration. Must not be attached to any distribution.

**Synopsis:**
```bash
aws cloudfront delete-realtime-log-config \
    [--name <value>] \
    [--arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--name` | No* | string | Config name (*one of name or ARN required) |
| `--arn` | No* | string | Config ARN |

**Output:** None.

---
