# Labels

### 4.1 `create-label-group`

Creates a label group for organizing anomaly labels with optional fault codes.

**Synopsis:**
```bash
aws lookoutequipment create-label-group \
    --label-group-name <value> \
    [--fault-codes <value>] \
    [--client-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--label-group-name` | **Yes** | string | -- | Label group name (1-200 chars) |
| `--fault-codes` | No | list(string) | None | Acceptable fault codes (max 50, each 1-100 chars) |
| `--client-token` | No | string | Auto | Idempotency token |
| `--tags` | No | list | None | Tags (max 200) |

**Output Schema:**
```json
{
    "LabelGroupName": "string",
    "LabelGroupArn": "string"
}
```

---

### 4.2 `describe-label-group`

Describes a label group.

**Synopsis:**
```bash
aws lookoutequipment describe-label-group \
    --label-group-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--label-group-name` | **Yes** | string | -- | Name of the label group |

**Output Schema:**
```json
{
    "LabelGroupName": "string",
    "LabelGroupArn": "string",
    "FaultCodes": ["string"],
    "CreatedAt": "timestamp",
    "UpdatedAt": "timestamp"
}
```

---

### 4.3 `list-label-groups`

Lists label groups. **Paginated operation.**

**Synopsis:**
```bash
aws lookoutequipment list-label-groups \
    [--label-group-name-begins-with <value>] \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--label-group-name-begins-with` | No | string | None | Filter by name prefix |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results per page (1-500) |

**Output Schema:**
```json
{
    "NextToken": "string",
    "LabelGroupSummaries": [
        {
            "LabelGroupName": "string",
            "LabelGroupArn": "string",
            "CreatedAt": "timestamp",
            "UpdatedAt": "timestamp"
        }
    ]
}
```

---

### 4.4 `update-label-group`

Updates a label group's fault codes.

**Synopsis:**
```bash
aws lookoutequipment update-label-group \
    --label-group-name <value> \
    [--fault-codes <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--label-group-name` | **Yes** | string | -- | Name of the label group |
| `--fault-codes` | No | list(string) | None | Updated fault codes (max 50) |

**Output:** None

---

### 4.5 `delete-label-group`

Deletes a label group.

**Synopsis:**
```bash
aws lookoutequipment delete-label-group \
    --label-group-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--label-group-name` | **Yes** | string | -- | Name of the label group to delete |

**Output:** None

---

### 4.6 `create-label`

Creates a label (anomaly annotation) within a label group for a specific time range.

**Synopsis:**
```bash
aws lookoutequipment create-label \
    --label-group-name <value> \
    --start-time <value> \
    --end-time <value> \
    --rating <value> \
    [--fault-code <value>] \
    [--notes <value>] \
    [--equipment <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--label-group-name` | **Yes** | string | -- | Label group name |
| `--start-time` | **Yes** | timestamp | -- | Start of the labeled event |
| `--end-time` | **Yes** | timestamp | -- | End of the labeled event |
| `--rating` | **Yes** | string | -- | `ANOMALY`, `NO_ANOMALY`, or `NEUTRAL` |
| `--fault-code` | No | string | None | Fault code (must be in label group's fault codes) |
| `--notes` | No | string | None | Additional notes (1-2560 chars) |
| `--equipment` | No | string | None | Equipment identifier (1-200 chars) |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "LabelId": "string"
}
```

---

### 4.7 `describe-label`

Describes a label.

**Synopsis:**
```bash
aws lookoutequipment describe-label \
    --label-group-name <value> \
    --label-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--label-group-name` | **Yes** | string | -- | Name of the label group |
| `--label-id` | **Yes** | string | -- | The label ID |

**Output Schema:**
```json
{
    "LabelGroupName": "string",
    "LabelGroupArn": "string",
    "LabelId": "string",
    "StartTime": "timestamp",
    "EndTime": "timestamp",
    "Rating": "ANOMALY|NO_ANOMALY|NEUTRAL",
    "FaultCode": "string",
    "Notes": "string",
    "Equipment": "string",
    "CreatedAt": "timestamp"
}
```

---

### 4.8 `list-labels`

Lists labels in a label group. **Paginated operation.**

**Synopsis:**
```bash
aws lookoutequipment list-labels \
    --label-group-name <value> \
    [--interval-start-time <value>] \
    [--interval-end-time <value>] \
    [--fault-code <value>] \
    [--equipment <value>] \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--label-group-name` | **Yes** | string | -- | Name of the label group |
| `--interval-start-time` | No | timestamp | None | Filter by start time |
| `--interval-end-time` | No | timestamp | None | Filter by end time |
| `--fault-code` | No | string | None | Filter by fault code |
| `--equipment` | No | string | None | Filter by equipment |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results per page (1-500) |

**Output Schema:**
```json
{
    "NextToken": "string",
    "LabelSummaries": [
        {
            "LabelGroupName": "string",
            "LabelId": "string",
            "LabelGroupArn": "string",
            "StartTime": "timestamp",
            "EndTime": "timestamp",
            "Rating": "ANOMALY|NO_ANOMALY|NEUTRAL",
            "FaultCode": "string",
            "Equipment": "string",
            "CreatedAt": "timestamp"
        }
    ]
}
```

---

### 4.9 `delete-label`

Deletes a label.

**Synopsis:**
```bash
aws lookoutequipment delete-label \
    --label-group-name <value> \
    --label-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--label-group-name` | **Yes** | string | -- | Name of the label group |
| `--label-id` | **Yes** | string | -- | ID of the label to delete |

**Output:** None
