# Landing Zones

### 1.1 `create-landing-zone`

Creates a new landing zone. This is an asynchronous operation that returns an `operationIdentifier`.

**Synopsis:**
```bash
aws controltower create-landing-zone \
    --landing-zone-version <value> \
    [--manifest <value>] \
    [--tags <value>] \
    [--remediation-types <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--landing-zone-version` | **Yes** | string | -- | Landing zone version (pattern: `\d+.\d+`, e.g., "3.0") |
| `--manifest` | No | document | None | JSON manifest describing AWS resources |
| `--tags` | No | map | None | Key-value pairs for tagging (max 200) |
| `--remediation-types` | No | list(string) | None | Remediation action types (e.g., `INHERITANCE_DRIFT`) |

**Output Schema:**
```json
{
    "arn": "string",
    "operationIdentifier": "string"
}
```

---

### 1.2 `get-landing-zone`

Returns details about a landing zone.

**Synopsis:**
```bash
aws controltower get-landing-zone \
    --landing-zone-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--landing-zone-identifier` | **Yes** | string | -- | The unique identifier (ARN) of the landing zone |

**Output Schema:**
```json
{
    "landingZone": {
        "version": "string",
        "remediationTypes": ["INHERITANCE_DRIFT"],
        "arn": "string",
        "status": "ACTIVE|PROCESSING|FAILED",
        "latestAvailableVersion": "string",
        "driftStatus": {
            "status": "DRIFTED|IN_SYNC"
        },
        "manifest": "document"
    }
}
```

---

### 1.3 `list-landing-zones`

Lists all landing zones. **Paginated operation.**

**Synopsis:**
```bash
aws controltower list-landing-zones \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "landingZones": [
        {
            "arn": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 1.4 `update-landing-zone`

Updates an existing landing zone. This is an asynchronous operation.

**Synopsis:**
```bash
aws controltower update-landing-zone \
    --landing-zone-identifier <value> \
    --landing-zone-version <value> \
    [--manifest <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--landing-zone-identifier` | **Yes** | string | -- | The ARN of the landing zone to update |
| `--landing-zone-version` | **Yes** | string | -- | Target landing zone version |
| `--manifest` | No | document | None | Updated JSON manifest |

**Output Schema:**
```json
{
    "operationIdentifier": "string"
}
```

---

### 1.5 `delete-landing-zone`

Decommissions a landing zone. This is an asynchronous operation.

**Synopsis:**
```bash
aws controltower delete-landing-zone \
    --landing-zone-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--landing-zone-identifier` | **Yes** | string | -- | The ARN of the landing zone to delete |

**Output Schema:**
```json
{
    "operationIdentifier": "string"
}
```

---

### 1.6 `reset-landing-zone`

Resets a landing zone. This is an asynchronous operation.

**Synopsis:**
```bash
aws controltower reset-landing-zone \
    --landing-zone-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--landing-zone-identifier` | **Yes** | string | -- | The ARN of the landing zone to reset |

**Output Schema:**
```json
{
    "operationIdentifier": "string"
}
```

---

### 1.7 `get-landing-zone-operation`

Returns details of a landing zone operation.

**Synopsis:**
```bash
aws controltower get-landing-zone-operation \
    --operation-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--operation-identifier` | **Yes** | string | -- | The operation UUID (36 chars) |

**Output Schema:**
```json
{
    "operationDetails": {
        "operationType": "CREATE|DELETE|UPDATE|RESET",
        "startTime": "timestamp",
        "endTime": "timestamp",
        "status": "SUCCEEDED|FAILED|IN_PROGRESS",
        "statusMessage": "string",
        "operationIdentifier": "string"
    }
}
```

---

### 1.8 `list-landing-zone-operations`

Lists all landing zone operations. **Paginated operation.**

**Synopsis:**
```bash
aws controltower list-landing-zone-operations \
    [--filter <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filter` | No | structure | None | Filter by operation types and statuses |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Filter Structure:**
```json
{
    "types": ["CREATE|DELETE|UPDATE|RESET"],
    "statuses": ["SUCCEEDED|FAILED|IN_PROGRESS"]
}
```

**Output Schema:**
```json
{
    "landingZoneOperations": [
        {
            "operationType": "CREATE|DELETE|UPDATE|RESET",
            "operationIdentifier": "string",
            "status": "SUCCEEDED|FAILED|IN_PROGRESS"
        }
    ],
    "nextToken": "string"
}
```
