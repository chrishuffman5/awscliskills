# Hours of Operation

### 9.1 `create-hours-of-operation`

Creates hours of operation for the specified instance.

**Synopsis:**
```bash
aws connect create-hours-of-operation \
    --instance-id <value> \
    --name <value> \
    --time-zone <value> \
    --config <value> \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--name` | **Yes** | string | -- | Name (1-127 chars) |
| `--time-zone` | **Yes** | string | -- | IANA time zone |
| `--config` | **Yes** | list | -- | Day/time config (0-100 items) |
| `--description` | No | string | None | Description (1-250 chars) |
| `--tags` | No | map | None | Tags (max 50) |

**Config:**
```json
[
    {
        "Day": "SUNDAY|MONDAY|TUESDAY|WEDNESDAY|THURSDAY|FRIDAY|SATURDAY",
        "StartTime": { "Hours": "integer (0-23)", "Minutes": "integer (0-59)" },
        "EndTime": { "Hours": "integer (0-23)", "Minutes": "integer (0-59)" }
    }
]
```

**Output Schema:**
```json
{
    "HoursOfOperationId": "string",
    "HoursOfOperationArn": "string"
}
```

---

### 9.2 `describe-hours-of-operation`

Describes hours of operation.

**Synopsis:**
```bash
aws connect describe-hours-of-operation \
    --instance-id <value> \
    --hours-of-operation-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--hours-of-operation-id` | **Yes** | string | -- | Hours of operation ID |

**Output Schema:**
```json
{
    "HoursOfOperation": {
        "HoursOfOperationId": "string",
        "HoursOfOperationArn": "string",
        "Name": "string",
        "Description": "string",
        "TimeZone": "string",
        "Config": [],
        "Tags": { "key": "value" },
        "LastModifiedTime": "timestamp",
        "LastModifiedRegion": "string"
    }
}
```

---

### 9.3 `list-hours-of-operations`

Lists hours of operations. **Paginated operation.**

**Synopsis:**
```bash
aws connect list-hours-of-operations \
    --instance-id <value> \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-1000) |

**Output Schema:**
```json
{
    "HoursOfOperationSummaryList": [ { "Id": "string", "Arn": "string", "Name": "string", "LastModifiedTime": "timestamp", "LastModifiedRegion": "string" } ],
    "NextToken": "string"
}
```

---

### 9.4 `update-hours-of-operation`

Updates hours of operation.

**Synopsis:**
```bash
aws connect update-hours-of-operation \
    --instance-id <value> \
    --hours-of-operation-id <value> \
    [--name <value>] \
    [--description <value>] \
    [--time-zone <value>] \
    [--config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--hours-of-operation-id` | **Yes** | string | -- | Hours of operation ID |
| `--name` | No | string | None | Updated name |
| `--description` | No | string | None | Updated description |
| `--time-zone` | No | string | None | Updated time zone |
| `--config` | No | list | None | Updated config |

**Output:** None

---

### 9.5 `delete-hours-of-operation`

Deletes hours of operation.

**Synopsis:**
```bash
aws connect delete-hours-of-operation \
    --instance-id <value> \
    --hours-of-operation-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--hours-of-operation-id` | **Yes** | string | -- | Hours of operation ID |

**Output:** None

---

### 9.6-9.10 Override Commands

`create-hours-of-operation-override`, `describe-hours-of-operation-override`, `list-hours-of-operation-overrides`, `update-hours-of-operation-override`, `delete-hours-of-operation-override` manage temporary overrides to hours of operation (e.g., holiday hours). All require `--instance-id` and `--hours-of-operation-id`.

**create-hours-of-operation-override:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--hours-of-operation-id` | **Yes** | string | -- | Hours of operation ID |
| `--name` | **Yes** | string | -- | Override name |
| `--config` | **Yes** | list | -- | Override config |
| `--effective-from` | **Yes** | string | -- | Start date |
| `--effective-till` | **Yes** | string | -- | End date |
| `--description` | No | string | None | Description |

**Output Schema:**
```json
{
    "HoursOfOperationOverrideId": "string"
}
```

---

### 9.11-9.16 Search & Association Commands

`search-hours-of-operations`, `search-hours-of-operation-overrides`, `get-effective-hours-of-operations`, `list-child-hours-of-operations`, `associate-hours-of-operations`, `disassociate-hours-of-operations` provide search, effective hours calculation, and parent-child association capabilities. All require `--instance-id`.
