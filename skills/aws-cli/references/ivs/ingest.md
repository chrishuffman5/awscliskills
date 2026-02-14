# Ingest Configurations (Real-Time)

### 9.1 `create-ingest-configuration`

Creates an ingest configuration for RTMP/RTMPS publishing to a stage.

**Synopsis:**
```bash
aws ivs-realtime create-ingest-configuration \
    --ingest-protocol <value> \
    [--name <value>] \
    [--stage-arn <value>] \
    [--user-id <value>] \
    [--attributes <value>] \
    [--insecure-ingest | --no-insecure-ingest] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--ingest-protocol` | **Yes** | string | -- | `RTMP` or `RTMPS` |
| `--name` | No | string | None | Name (0-128 chars) |
| `--stage-arn` | No | string | None | ARN of the stage to associate |
| `--user-id` | No | string | None | User identifier |
| `--attributes` | No | map | None | Custom attributes |
| `--insecure-ingest` | No | boolean | false | Allow insecure ingest |
| `--tags` | No | map | None | Key-value tag pairs |

**Output Schema:**
```json
{
    "ingestConfiguration": {
        "arn": "string",
        "name": "string",
        "stageArn": "string",
        "participantId": "string",
        "state": "ACTIVE|INACTIVE",
        "userId": "string",
        "attributes": {"string": "string"},
        "ingestProtocol": "RTMP|RTMPS",
        "streamKey": "string",
        "tags": {"string": "string"}
    }
}
```

---

### 9.2 `get-ingest-configuration`

Gets details for an ingest configuration.

**Synopsis:**
```bash
aws ivs-realtime get-ingest-configuration \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the ingest configuration |

---

### 9.3 `list-ingest-configurations`

Lists ingest configurations. **Paginated operation.**

**Synopsis:**
```bash
aws ivs-realtime list-ingest-configurations \
    [--filter-by-stage-arn <value>] \
    [--filter-by-state <value>] \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filter-by-stage-arn` | No | string | None | Filter by stage ARN |
| `--filter-by-state` | No | string | None | Filter: `ACTIVE` or `INACTIVE` |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results per page |

---

### 9.4 `update-ingest-configuration`

Updates an ingest configuration's stage association.

**Synopsis:**
```bash
aws ivs-realtime update-ingest-configuration \
    --arn <value> \
    [--stage-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the ingest configuration |
| `--stage-arn` | No | string | None | Updated stage ARN (empty string to disassociate) |

---

### 9.5 `delete-ingest-configuration`

Deletes an ingest configuration.

**Synopsis:**
```bash
aws ivs-realtime delete-ingest-configuration \
    --arn <value> \
    [--force | --no-force] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the ingest configuration |
| `--force` | No | boolean | false | Force deletion even if associated with a stage |

**Output:** None
