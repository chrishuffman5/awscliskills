# Inputs

### 2.1 `create-input`

Creates an input source for a channel. Supports various input types including RTMP, RTP, URL pull, MediaConnect, and hardware devices.

**Synopsis:**
```bash
aws medialive create-input \
    [--name <value>] \
    [--type <value>] \
    [--sources <value>] \
    [--destinations <value>] \
    [--input-security-groups <value>] \
    [--input-devices <value>] \
    [--media-connect-flows <value>] \
    [--role-arn <value>] \
    [--vpc <value>] \
    [--tags <value>] \
    [--srt-settings <value>] \
    [--input-network-location <value>] \
    [--multicast-settings <value>] \
    [--sdi-sources <value>] \
    [--request-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | No | string | None | Input name |
| `--type` | No | string | None | `UDP_PUSH`, `RTP_PUSH`, `RTMP_PUSH`, `RTMP_PULL`, `URL_PULL`, `MP4_FILE`, `MEDIACONNECT`, `INPUT_DEVICE`, `AWS_CDI`, `TS_FILE`, `SRT_CALLER`, `MULTICAST`, `SDI`, `SRT_LISTENER` |
| `--sources` | No | list | None | Source URLs for PULL inputs (2 for redundancy) |
| `--destinations` | No | list | None | Destination settings for PUSH inputs |
| `--input-security-groups` | No | list | None | Security group IDs |
| `--input-devices` | No | list | None | Input device settings |
| `--media-connect-flows` | No | list | None | MediaConnect flow ARNs |
| `--role-arn` | No | string | None | IAM role ARN |
| `--vpc` | No | structure | None | VPC configuration |
| `--tags` | No | map | None | Key-value tag pairs |
| `--srt-settings` | No | structure | None | SRT input settings |
| `--input-network-location` | No | string | None | `AWS` or `ON_PREMISES` |
| `--multicast-settings` | No | structure | None | Multicast settings |
| `--sdi-sources` | No | list | None | SDI source IDs |
| `--request-id` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "Input": {
        "Arn": "string",
        "Id": "string",
        "Name": "string",
        "Type": "string",
        "InputClass": "STANDARD|SINGLE_PIPELINE",
        "InputSourceType": "STATIC|DYNAMIC",
        "State": "CREATING|DETACHED|ATTACHED|DELETING|DELETED",
        "AttachedChannels": ["string"],
        "Sources": [{"Url": "string"}],
        "Destinations": [{"Ip": "string", "Port": "string", "Url": "string"}],
        "SecurityGroups": ["string"],
        "InputDevices": [],
        "MediaConnectFlows": [],
        "InputPartnerIds": ["string"],
        "RoleArn": "string",
        "Tags": {}
    }
}
```

---

### 2.2 `describe-input`

Describes an input.

**Synopsis:**
```bash
aws medialive describe-input \
    --input-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--input-id` | **Yes** | string | -- | Input ID |

**Output Schema:** Same as `create-input` output.

---

### 2.3 `update-input`

Updates an input's configuration.

**Synopsis:**
```bash
aws medialive update-input \
    --input-id <value> \
    [--name <value>] \
    [--sources <value>] \
    [--destinations <value>] \
    [--input-security-groups <value>] \
    [--input-devices <value>] \
    [--media-connect-flows <value>] \
    [--role-arn <value>] \
    [--srt-settings <value>] \
    [--multicast-settings <value>] \
    [--sdi-sources <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--input-id` | **Yes** | string | -- | Input ID to update |
| `--name` | No | string | None | Updated name |
| `--sources` | No | list | None | Updated sources |
| `--destinations` | No | list | None | Updated destinations |
| `--input-security-groups` | No | list | None | Updated security groups |
| `--input-devices` | No | list | None | Updated devices |
| `--media-connect-flows` | No | list | None | Updated flows |
| `--role-arn` | No | string | None | Updated role |
| `--srt-settings` | No | structure | None | Updated SRT settings |
| `--multicast-settings` | No | structure | None | Updated multicast settings |
| `--sdi-sources` | No | list | None | Updated SDI sources |

**Output Schema:**
```json
{
    "Input": {
        "Arn": "string",
        "Id": "string",
        "Name": "string",
        "Type": "string",
        "State": "string"
    }
}
```

---

### 2.4 `delete-input`

Deletes an input. Input must be detached from all channels.

**Synopsis:**
```bash
aws medialive delete-input \
    --input-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--input-id` | **Yes** | string | -- | Input ID to delete |

**Output:** None

---

### 2.5 `list-inputs`

Lists inputs. **Paginated operation.**

**Synopsis:**
```bash
aws medialive list-inputs \
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
    "Inputs": [
        {
            "Arn": "string",
            "Id": "string",
            "Name": "string",
            "Type": "string",
            "InputClass": "string",
            "State": "string",
            "AttachedChannels": ["string"],
            "Sources": [],
            "Destinations": [],
            "SecurityGroups": ["string"],
            "Tags": {}
        }
    ]
}
```

---

### 2.6 `create-partner-input`

Creates a partner input from an existing input, allowing two channels to share the same source.

**Synopsis:**
```bash
aws medialive create-partner-input \
    --input-id <value> \
    [--request-id <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--input-id` | **Yes** | string | -- | ID of the existing input |
| `--request-id` | No | string | Auto | Idempotency token |
| `--tags` | No | map | None | Key-value tag pairs |

**Output Schema:**
```json
{
    "Input": {
        "Arn": "string",
        "Id": "string",
        "Name": "string",
        "Type": "string",
        "State": "string",
        "InputPartnerIds": ["string"]
    }
}
```
