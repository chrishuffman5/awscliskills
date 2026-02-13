# Tags & Policies

### 5.1 `add-tags-to-stream`

Adds or updates tags for a data stream. Max 50 tags per stream.

**Synopsis:**
```bash
aws kinesis add-tags-to-stream \
    [--stream-name <value>] \
    [--stream-arn <value>] \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stream-name` | No* | string | -- | Name of the stream |
| `--stream-arn` | No* | string | -- | ARN of the stream |
| `--tags` | **Yes** | map | -- | Key-value pairs. Shorthand: `KeyName1=string,KeyName2=string` |

*Either `--stream-name` or `--stream-arn` must be provided.

**Output:** None

---

### 5.2 `remove-tags-from-stream`

Removes tags from a data stream.

**Synopsis:**
```bash
aws kinesis remove-tags-from-stream \
    [--stream-name <value>] \
    [--stream-arn <value>] \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stream-name` | No* | string | -- | Name of the stream |
| `--stream-arn` | No* | string | -- | ARN of the stream |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove (1-10 keys) |

*Either `--stream-name` or `--stream-arn` must be provided.

**Output:** None

---

### 5.3 `list-tags-for-stream`

Lists the tags for a data stream.

**Synopsis:**
```bash
aws kinesis list-tags-for-stream \
    [--stream-name <value>] \
    [--stream-arn <value>] \
    [--exclusive-start-tag-key <value>] \
    [--limit <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stream-name` | No* | string | -- | Name of the stream |
| `--stream-arn` | No* | string | -- | ARN of the stream |
| `--exclusive-start-tag-key` | No | string | -- | Tag key to start listing after |
| `--limit` | No | integer | -- | Max tags to return |

*Either `--stream-name` or `--stream-arn` must be provided.

**Output Schema:**
```json
{
    "Tags": [
        {
            "Key": "string",
            "Value": "string"
        }
    ],
    "HasMoreTags": "boolean"
}
```

---

### 5.4 `tag-resource`

Adds or updates tags for a Kinesis resource using ARN-based tagging.

**Synopsis:**
```bash
aws kinesis tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |
| `--tags` | **Yes** | list | -- | Tags to add. Shorthand: `Key=string,Value=string ...` |

**Output:** None

---

### 5.5 `untag-resource`

Removes tags from a Kinesis resource using ARN-based tagging.

**Synopsis:**
```bash
aws kinesis untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output:** None

---

### 5.6 `list-tags-for-resource`

Lists tags for a Kinesis resource using ARN-based tagging.

**Synopsis:**
```bash
aws kinesis list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |

**Output Schema:**
```json
{
    "Tags": [
        {
            "Key": "string",
            "Value": "string"
        }
    ]
}
```

---

### 5.7 `put-resource-policy`

Attaches a resource-based policy to a stream or consumer.

**Synopsis:**
```bash
aws kinesis put-resource-policy \
    --resource-arn <value> \
    --policy <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the stream or consumer |
| `--policy` | **Yes** | string | -- | JSON resource policy document |

**Output:** None

---

### 5.8 `get-resource-policy`

Gets the resource-based policy for a stream or consumer.

**Synopsis:**
```bash
aws kinesis get-resource-policy \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the stream or consumer |

**Output Schema:**
```json
{
    "Policy": "string"
}
```

---

### 5.9 `delete-resource-policy`

Deletes the resource-based policy for a stream or consumer.

**Synopsis:**
```bash
aws kinesis delete-resource-policy \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the stream or consumer |

**Output:** None

---

### 5.10 `describe-limits`

Describes the shard limits and usage for the account.

**Synopsis:**
```bash
aws kinesis describe-limits \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output Schema:**
```json
{
    "ShardLimit": "integer",
    "OpenShardCount": "integer",
    "OnDemandStreamCount": "integer",
    "OnDemandStreamCountLimit": "integer"
}
```

---

### 5.11 `describe-account-settings`

Describes the account-level settings for Kinesis Data Streams.

**Synopsis:**
```bash
aws kinesis describe-account-settings \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output Schema:**
```json
{
    "AccountSettings": {
        "MaxRecordSizeInKiB": "integer",
        "MaxShardRetentionPeriodHours": "integer"
    }
}
```

---

### 5.12 `update-account-settings`

Updates the account-level settings for Kinesis Data Streams.

**Synopsis:**
```bash
aws kinesis update-account-settings \
    [--max-record-size-in-ki-b <value>] \
    [--max-shard-retention-period-hours <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--max-record-size-in-ki-b` | No | integer | -- | Max record size in KiB (1024-10240) |
| `--max-shard-retention-period-hours` | No | integer | -- | Max retention period in hours |

**Output Schema:**
```json
{
    "AccountSettings": {
        "MaxRecordSizeInKiB": "integer",
        "MaxShardRetentionPeriodHours": "integer"
    }
}
```
