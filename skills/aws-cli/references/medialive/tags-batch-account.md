# Tags, Batch & Account

### 15.1 `create-tags`

Adds tags to a MediaLive resource.

**Synopsis:**
```bash
aws medialive create-tags \
    --resource-arn <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource to tag |
| `--tags` | No | map | None | Key-value tag pairs |

**Output:** None

---

### 15.2 `delete-tags`

Removes tags from a MediaLive resource.

**Synopsis:**
```bash
aws medialive delete-tags \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |
| `--tag-keys` | **Yes** | list | -- | Tag keys to remove |

**Output:** None

---

### 15.3 `list-tags-for-resource`

Lists tags for a MediaLive resource.

**Synopsis:**
```bash
aws medialive list-tags-for-resource \
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
    "Tags": {
        "key": "value"
    }
}
```

---

### 15.4 `batch-delete`

Deletes multiple resources (channels, inputs, input security groups, multiplexes) in a single call.

**Synopsis:**
```bash
aws medialive batch-delete \
    [--channel-ids <value>] \
    [--input-ids <value>] \
    [--input-security-group-ids <value>] \
    [--multiplex-ids <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-ids` | No | list | None | Channel IDs to delete |
| `--input-ids` | No | list | None | Input IDs to delete |
| `--input-security-group-ids` | No | list | None | Security group IDs to delete |
| `--multiplex-ids` | No | list | None | Multiplex IDs to delete |

**Output Schema:**
```json
{
    "Failed": [
        {
            "Arn": "string",
            "Code": "string",
            "Id": "string",
            "Message": "string"
        }
    ],
    "Successful": [
        {
            "Arn": "string",
            "Id": "string",
            "State": "string"
        }
    ]
}
```

---

### 15.5 `batch-start`

Starts multiple channels and/or multiplexes in a single call.

**Synopsis:**
```bash
aws medialive batch-start \
    [--channel-ids <value>] \
    [--multiplex-ids <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-ids` | No | list | None | Channel IDs to start |
| `--multiplex-ids` | No | list | None | Multiplex IDs to start |

**Output Schema:**
```json
{
    "Failed": [
        {
            "Arn": "string",
            "Code": "string",
            "Id": "string",
            "Message": "string"
        }
    ],
    "Successful": [
        {
            "Arn": "string",
            "Id": "string",
            "State": "string"
        }
    ]
}
```

---

### 15.6 `batch-stop`

Stops multiple channels and/or multiplexes in a single call.

**Synopsis:**
```bash
aws medialive batch-stop \
    [--channel-ids <value>] \
    [--multiplex-ids <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-ids` | No | list | None | Channel IDs to stop |
| `--multiplex-ids` | No | list | None | Multiplex IDs to stop |

**Output Schema:** Same as `batch-start` output.

---

### 15.7 `describe-account-configuration`

Describes account-level MediaLive configuration.

**Synopsis:**
```bash
aws medialive describe-account-configuration \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output Schema:**
```json
{
    "AccountConfiguration": {
        "KmsKeyId": "string"
    }
}
```

---

### 15.8 `update-account-configuration`

Updates account-level MediaLive configuration.

**Synopsis:**
```bash
aws medialive update-account-configuration \
    [--account-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-configuration` | No | structure | None | Account configuration with KmsKeyId |

**Output Schema:**
```json
{
    "AccountConfiguration": {
        "KmsKeyId": "string"
    }
}
```

---

### 15.9 `list-versions`

Lists available MediaLive channel engine versions.

**Synopsis:**
```bash
aws medialive list-versions \
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
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "NextToken": "string",
    "Versions": [
        {
            "EngineVersions": [
                {
                    "ExpirationDate": "timestamp",
                    "Version": "string"
                }
            ]
        }
    ]
}
```

---

### 15.10 `list-alerts`

Lists alerts for a resource (channel or input device). **Paginated operation.**

**Synopsis:**
```bash
aws medialive list-alerts \
    --resource-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN to list alerts for |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "NextToken": "string",
    "Alerts": [
        {
            "AlertId": "string",
            "AlertMessage": "string",
            "AlertType": "string",
            "FirstTimestamp": "timestamp",
            "LastTimestamp": "timestamp"
        }
    ]
}
```

---

### 15.11 `describe-thumbnails`

Gets thumbnail images for a channel's pipelines.

**Synopsis:**
```bash
aws medialive describe-thumbnails \
    --channel-id <value> \
    --pipeline-id <value> \
    --thumbnail-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-id` | **Yes** | string | -- | Channel ID |
| `--pipeline-id` | **Yes** | string | -- | `0` or `1` |
| `--thumbnail-type` | **Yes** | string | -- | `CURRENT_ACTIVE` |

**Output Schema:**
```json
{
    "ThumbnailDetails": [
        {
            "PipelineId": "string",
            "Thumbnails": [
                {
                    "Body": "string",
                    "ContentType": "string",
                    "ThumbnailType": "string",
                    "TimeStamp": "timestamp"
                }
            ]
        }
    ]
}
```

---

### 15.12 `claim-device`

Claims an unregistered input device to the current account.

**Synopsis:**
```bash
aws medialive claim-device \
    [--id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | No | string | None | Device ID to claim |

**Output:** None
