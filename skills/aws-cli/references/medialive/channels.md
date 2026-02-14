# Channels

### 1.1 `create-channel`

Creates a live encoding channel with encoder settings, input attachments, and output destinations.

**Synopsis:**
```bash
aws medialive create-channel \
    [--name <value>] \
    [--channel-class <value>] \
    --encoder-settings <value> \
    [--input-attachments <value>] \
    [--destinations <value>] \
    [--input-specification <value>] \
    [--cdi-input-specification <value>] \
    [--log-level <value>] \
    [--maintenance <value>] \
    [--role-arn <value>] \
    [--tags <value>] \
    [--vpc <value>] \
    [--anywhere-settings <value>] \
    [--channel-engine-version <value>] \
    [--dry-run | --no-dry-run] \
    [--request-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--encoder-settings` | **Yes** | structure | -- | Encoder configuration (audio, video, output groups) |
| `--name` | No | string | None | Channel name |
| `--channel-class` | No | string | STANDARD | `STANDARD` or `SINGLE_PIPELINE` |
| `--input-attachments` | No | list | None | Input sources attached to channel |
| `--destinations` | No | list | None | Output destination settings |
| `--input-specification` | No | structure | None | Input codec/resolution spec |
| `--cdi-input-specification` | No | structure | None | CDI input resolution: `SD`, `HD`, `FHD`, `UHD` |
| `--log-level` | No | string | None | `ERROR`, `WARNING`, `INFO`, `DEBUG`, `DISABLED` |
| `--maintenance` | No | structure | None | Maintenance window settings |
| `--role-arn` | No | string | None | IAM role for channel permissions |
| `--tags` | No | map | None | Key-value tag pairs |
| `--vpc` | No | structure | None | VPC settings for on-premises |
| `--anywhere-settings` | No | structure | None | Anywhere configuration |
| `--channel-engine-version` | No | string | None | Engine version |
| `--dry-run` | No | boolean | false | Validate without creating |
| `--request-id` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "Channel": {
        "Arn": "string",
        "Id": "string",
        "Name": "string",
        "ChannelClass": "STANDARD|SINGLE_PIPELINE",
        "State": "CREATING|CREATE_FAILED|IDLE|STARTING|RUNNING|RECOVERING|STOPPING|DELETING|DELETED|UPDATING|UPDATE_FAILED",
        "EncoderSettings": {},
        "InputAttachments": [],
        "Destinations": [],
        "EgressEndpoints": [{"SourceIp": "string"}],
        "InputSpecification": {},
        "LogLevel": "string",
        "Maintenance": {},
        "PipelineDetails": [],
        "RoleArn": "string",
        "Tags": {},
        "Vpc": {}
    }
}
```

---

### 1.2 `describe-channel`

Describes a channel's configuration and current state.

**Synopsis:**
```bash
aws medialive describe-channel \
    --channel-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-id` | **Yes** | string | -- | Channel ID |

**Output Schema:** Same as `create-channel` output.

---

### 1.3 `update-channel`

Updates a channel's configuration. Channel must be idle or running.

**Synopsis:**
```bash
aws medialive update-channel \
    --channel-id <value> \
    [--name <value>] \
    [--encoder-settings <value>] \
    [--input-attachments <value>] \
    [--destinations <value>] \
    [--input-specification <value>] \
    [--cdi-input-specification <value>] \
    [--log-level <value>] \
    [--maintenance <value>] \
    [--role-arn <value>] \
    [--anywhere-settings <value>] \
    [--channel-engine-version <value>] \
    [--dry-run | --no-dry-run] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-id` | **Yes** | string | -- | Channel ID to update |
| `--name` | No | string | None | Updated name |
| `--encoder-settings` | No | structure | None | Updated encoder settings |
| `--input-attachments` | No | list | None | Updated input attachments |
| `--destinations` | No | list | None | Updated destinations |
| `--input-specification` | No | structure | None | Updated input spec |
| `--cdi-input-specification` | No | structure | None | Updated CDI spec |
| `--log-level` | No | string | None | Updated log level |
| `--maintenance` | No | structure | None | Updated maintenance window |
| `--role-arn` | No | string | None | Updated IAM role |
| `--channel-engine-version` | No | string | None | Updated engine version |
| `--dry-run` | No | boolean | false | Validate without applying |

**Output Schema:**
```json
{
    "Channel": {
        "Arn": "string",
        "Id": "string",
        "Name": "string",
        "State": "string",
        "ChannelClass": "string",
        "EncoderSettings": {},
        "InputAttachments": [],
        "Destinations": []
    }
}
```

---

### 1.4 `update-channel-class`

Changes a channel between STANDARD (two pipelines) and SINGLE_PIPELINE.

**Synopsis:**
```bash
aws medialive update-channel-class \
    --channel-class <value> \
    --channel-id <value> \
    [--destinations <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-class` | **Yes** | string | -- | `STANDARD` or `SINGLE_PIPELINE` |
| `--channel-id` | **Yes** | string | -- | Channel ID |
| `--destinations` | No | list | None | Updated destinations for new class |

**Output Schema:**
```json
{
    "Channel": {
        "Arn": "string",
        "Id": "string",
        "ChannelClass": "STANDARD|SINGLE_PIPELINE",
        "State": "string"
    }
}
```

---

### 1.5 `delete-channel`

Deletes a channel. Channel must be idle.

**Synopsis:**
```bash
aws medialive delete-channel \
    --channel-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-id` | **Yes** | string | -- | Channel ID to delete |

**Output Schema:**
```json
{
    "Arn": "string",
    "Id": "string",
    "Name": "string",
    "State": "DELETING"
}
```

---

### 1.6 `start-channel`

Starts a channel to begin encoding and output.

**Synopsis:**
```bash
aws medialive start-channel \
    --channel-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-id` | **Yes** | string | -- | Channel ID to start |

**Output Schema:**
```json
{
    "Arn": "string",
    "Id": "string",
    "Name": "string",
    "State": "STARTING"
}
```

---

### 1.7 `stop-channel`

Stops a running channel.

**Synopsis:**
```bash
aws medialive stop-channel \
    --channel-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-id` | **Yes** | string | -- | Channel ID to stop |

**Output Schema:**
```json
{
    "Arn": "string",
    "Id": "string",
    "Name": "string",
    "State": "STOPPING"
}
```

---

### 1.8 `restart-channel-pipelines`

Restarts one or both pipelines of a running channel.

**Synopsis:**
```bash
aws medialive restart-channel-pipelines \
    --channel-id <value> \
    [--pipeline-ids <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-id` | **Yes** | string | -- | Channel ID |
| `--pipeline-ids` | No | list | None | Pipeline IDs to restart: `PIPELINE_0`, `PIPELINE_1` |

**Output Schema:**
```json
{
    "Arn": "string",
    "Id": "string",
    "Name": "string",
    "State": "string",
    "PipelineDetails": []
}
```

---

### 1.9 `list-channels`

Lists channels. **Paginated operation.**

**Synopsis:**
```bash
aws medialive list-channels \
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
    "Channels": [
        {
            "Arn": "string",
            "Id": "string",
            "Name": "string",
            "ChannelClass": "STANDARD|SINGLE_PIPELINE",
            "State": "string",
            "InputAttachments": [],
            "Destinations": [],
            "EgressEndpoints": [],
            "InputSpecification": {},
            "LogLevel": "string",
            "Maintenance": {},
            "RoleArn": "string",
            "Tags": {},
            "Vpc": {}
        }
    ]
}
```
