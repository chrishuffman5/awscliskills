# Multiplexes

### 5.1 `create-multiplex`

Creates a multiplex for combining multiple channels into a single transport stream.

**Synopsis:**
```bash
aws medialive create-multiplex \
    --availability-zones <value> \
    --multiplex-settings <value> \
    --name <value> \
    [--request-id <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--availability-zones` | **Yes** | list | -- | Exactly two AZs |
| `--multiplex-settings` | **Yes** | structure | -- | Multiplex configuration |
| `--name` | **Yes** | string | -- | Multiplex name |
| `--request-id` | No | string | Auto | Idempotency token |
| `--tags` | No | map | None | Key-value tag pairs |

**MultiplexSettings:**
```json
{
    "TransportStreamBitrate": 10000000,
    "TransportStreamId": 1,
    "MaximumVideoBufferDelayMilliseconds": 1000,
    "TransportStreamReservedBitrate": 0
}
```

**Output Schema:**
```json
{
    "Multiplex": {
        "Arn": "string",
        "Id": "string",
        "Name": "string",
        "AvailabilityZones": ["string"],
        "MultiplexSettings": {},
        "Destinations": [{"MediaConnectSettings": {}}],
        "PipelinesRunningCount": "integer",
        "ProgramCount": "integer",
        "State": "CREATING|CREATE_FAILED|IDLE|STARTING|RUNNING|RECOVERING|STOPPING|DELETING|DELETED",
        "Tags": {}
    }
}
```

---

### 5.2 `describe-multiplex`

Describes a multiplex.

**Synopsis:**
```bash
aws medialive describe-multiplex \
    --multiplex-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--multiplex-id` | **Yes** | string | -- | Multiplex ID |

**Output Schema:** Same as `create-multiplex` output.

---

### 5.3 `update-multiplex`

Updates a multiplex's settings or name.

**Synopsis:**
```bash
aws medialive update-multiplex \
    --multiplex-id <value> \
    [--multiplex-settings <value>] \
    [--name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--multiplex-id` | **Yes** | string | -- | Multiplex ID to update |
| `--multiplex-settings` | No | structure | None | Updated settings |
| `--name` | No | string | None | Updated name |

**Output Schema:** Same as `create-multiplex` output.

---

### 5.4 `delete-multiplex`

Deletes a multiplex. Must be idle.

**Synopsis:**
```bash
aws medialive delete-multiplex \
    --multiplex-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--multiplex-id` | **Yes** | string | -- | Multiplex ID to delete |

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

### 5.5 `start-multiplex`

Starts a multiplex.

**Synopsis:**
```bash
aws medialive start-multiplex \
    --multiplex-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--multiplex-id` | **Yes** | string | -- | Multiplex ID to start |

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

### 5.6 `stop-multiplex`

Stops a running multiplex.

**Synopsis:**
```bash
aws medialive stop-multiplex \
    --multiplex-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--multiplex-id` | **Yes** | string | -- | Multiplex ID to stop |

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

### 5.7 `list-multiplexes`

Lists multiplexes. **Paginated operation.**

**Synopsis:**
```bash
aws medialive list-multiplexes \
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
    "Multiplexes": [
        {
            "Arn": "string",
            "Id": "string",
            "Name": "string",
            "AvailabilityZones": ["string"],
            "MultiplexSettings": {},
            "PipelinesRunningCount": "integer",
            "ProgramCount": "integer",
            "State": "string",
            "Tags": {}
        }
    ]
}
```

---

### 5.8 `create-multiplex-program`

Creates a program within a multiplex.

**Synopsis:**
```bash
aws medialive create-multiplex-program \
    --multiplex-id <value> \
    --multiplex-program-settings <value> \
    --program-name <value> \
    [--request-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--multiplex-id` | **Yes** | string | -- | Multiplex ID |
| `--multiplex-program-settings` | **Yes** | structure | -- | Program configuration |
| `--program-name` | **Yes** | string | -- | Program name |
| `--request-id` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "MultiplexProgram": {
        "ChannelId": "string",
        "MultiplexProgramSettings": {},
        "ProgramName": "string",
        "PacketIdentifiersMap": {},
        "PipelineDetails": []
    }
}
```

---

### 5.9 `describe-multiplex-program`

Describes a multiplex program.

**Synopsis:**
```bash
aws medialive describe-multiplex-program \
    --multiplex-id <value> \
    --program-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--multiplex-id` | **Yes** | string | -- | Multiplex ID |
| `--program-name` | **Yes** | string | -- | Program name |

**Output Schema:** Same as `create-multiplex-program` output.

---

### 5.10 `update-multiplex-program`

Updates a multiplex program's settings.

**Synopsis:**
```bash
aws medialive update-multiplex-program \
    --multiplex-id <value> \
    --program-name <value> \
    [--multiplex-program-settings <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--multiplex-id` | **Yes** | string | -- | Multiplex ID |
| `--program-name` | **Yes** | string | -- | Program name |
| `--multiplex-program-settings` | No | structure | None | Updated program settings |

**Output Schema:** Same as `create-multiplex-program` output.

---

### 5.11 `delete-multiplex-program`

Deletes a program from a multiplex.

**Synopsis:**
```bash
aws medialive delete-multiplex-program \
    --multiplex-id <value> \
    --program-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--multiplex-id` | **Yes** | string | -- | Multiplex ID |
| `--program-name` | **Yes** | string | -- | Program name to delete |

**Output Schema:**
```json
{
    "ChannelId": "string",
    "ProgramName": "string"
}
```

---

### 5.12 `list-multiplex-programs`

Lists programs in a multiplex. **Paginated operation.**

**Synopsis:**
```bash
aws medialive list-multiplex-programs \
    --multiplex-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--multiplex-id` | **Yes** | string | -- | Multiplex ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "NextToken": "string",
    "MultiplexPrograms": [
        {
            "ChannelId": "string",
            "ProgramName": "string"
        }
    ]
}
```

---

### 5.13 `list-multiplex-alerts`

Lists alerts for a multiplex. **Paginated operation.**

**Synopsis:**
```bash
aws medialive list-multiplex-alerts \
    --multiplex-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--multiplex-id` | **Yes** | string | -- | Multiplex ID |
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
