# Rotations

### 11.1 `create-rotation`

Creates an on-call rotation in an on-call schedule.

**Synopsis:**
```bash
aws ssm-contacts create-rotation \
    --name <value> \
    --contact-ids <value> \
    --time-zone-id <value> \
    --recurrence <value> \
    [--start-time <value>] \
    [--tags <value>] \
    [--idempotency-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Rotation name |
| `--contact-ids` | **Yes** | list(string) | -- | Contact ARNs in the rotation |
| `--time-zone-id` | **Yes** | string | -- | Time zone ID (e.g., `America/New_York`) |
| `--recurrence` | **Yes** | structure | -- | Recurrence schedule |
| `--start-time` | No | timestamp | None | Start time for the rotation |
| `--tags` | No | list | None | Tags |
| `--idempotency-token` | No | string | None | Idempotency token |

**Recurrence Structure:**
```json
{
    "MonthlySettings": [
        {
            "DayOfMonth": "integer",
            "HandOffTime": {
                "HourOfDay": "integer",
                "MinuteOfHour": "integer"
            }
        }
    ],
    "WeeklySettings": [
        {
            "DayOfWeek": "MON|TUE|WED|THU|FRI|SAT|SUN",
            "HandOffTime": {
                "HourOfDay": "integer",
                "MinuteOfHour": "integer"
            }
        }
    ],
    "DailySettings": [
        {
            "HourOfDay": "integer",
            "MinuteOfHour": "integer"
        }
    ],
    "NumberOfOnCalls": "integer",
    "RecurrenceMultiplier": "integer",
    "ShiftCoverages": {
        "MON": [
            {
                "Start": {
                    "HourOfDay": "integer",
                    "MinuteOfHour": "integer"
                },
                "End": {
                    "HourOfDay": "integer",
                    "MinuteOfHour": "integer"
                }
            }
        ]
    }
}
```

**Output Schema:**
```json
{
    "RotationArn": "string"
}
```

---

### 11.2 `delete-rotation`

Deletes a rotation from the system.

**Synopsis:**
```bash
aws ssm-contacts delete-rotation \
    --rotation-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rotation-id` | **Yes** | string | -- | Rotation ARN |

**Output Schema:**
```json
{}
```

---

### 11.3 `get-rotation`

Retrieves information about an on-call rotation.

**Synopsis:**
```bash
aws ssm-contacts get-rotation \
    --rotation-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rotation-id` | **Yes** | string | -- | Rotation ARN |

**Output Schema:**
```json
{
    "RotationArn": "string",
    "Name": "string",
    "ContactIds": ["string"],
    "StartTime": "timestamp",
    "TimeZoneId": "string",
    "Recurrence": {
        "MonthlySettings": [],
        "WeeklySettings": [],
        "DailySettings": [],
        "NumberOfOnCalls": "integer",
        "RecurrenceMultiplier": "integer",
        "ShiftCoverages": {}
    }
}
```

---

### 11.4 `list-rotations`

Retrieves a list of on-call rotations. **Paginated operation.**

**Synopsis:**
```bash
aws ssm-contacts list-rotations \
    [--rotation-name-prefix <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rotation-name-prefix` | No | string | None | Filter by rotation name prefix |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Maximum items |

**Output Schema:**
```json
{
    "Rotations": [
        {
            "RotationArn": "string",
            "Name": "string",
            "ContactIds": ["string"],
            "StartTime": "timestamp",
            "TimeZoneId": "string",
            "Recurrence": {}
        }
    ],
    "NextToken": "string"
}
```

---

### 11.5 `update-rotation`

Updates the information specified for an on-call rotation.

**Synopsis:**
```bash
aws ssm-contacts update-rotation \
    --rotation-id <value> \
    --recurrence <value> \
    [--contact-ids <value>] \
    [--start-time <value>] \
    [--time-zone-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rotation-id` | **Yes** | string | -- | Rotation ARN |
| `--recurrence` | **Yes** | structure | -- | Updated recurrence |
| `--contact-ids` | No | list(string) | None | Updated contact ARNs |
| `--start-time` | No | timestamp | None | Updated start time |
| `--time-zone-id` | No | string | None | Updated time zone |

**Output Schema:**
```json
{}
```

---

### 11.6 `create-rotation-override`

Creates an override for a rotation in an on-call schedule.

**Synopsis:**
```bash
aws ssm-contacts create-rotation-override \
    --rotation-id <value> \
    --new-contact-ids <value> \
    --start-time <value> \
    --end-time <value> \
    [--idempotency-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rotation-id` | **Yes** | string | -- | Rotation ARN |
| `--new-contact-ids` | **Yes** | list(string) | -- | Contact ARNs for the override period |
| `--start-time` | **Yes** | timestamp | -- | Override start time |
| `--end-time` | **Yes** | timestamp | -- | Override end time |
| `--idempotency-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "RotationOverrideId": "string"
}
```

---

### 11.7 `delete-rotation-override`

Deletes an existing override for an on-call rotation.

**Synopsis:**
```bash
aws ssm-contacts delete-rotation-override \
    --rotation-id <value> \
    --rotation-override-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rotation-id` | **Yes** | string | -- | Rotation ARN |
| `--rotation-override-id` | **Yes** | string | -- | Override ID |

**Output Schema:**
```json
{}
```

---

### 11.8 `get-rotation-override`

Retrieves information about an override to an on-call rotation.

**Synopsis:**
```bash
aws ssm-contacts get-rotation-override \
    --rotation-id <value> \
    --rotation-override-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rotation-id` | **Yes** | string | -- | Rotation ARN |
| `--rotation-override-id` | **Yes** | string | -- | Override ID |

**Output Schema:**
```json
{
    "RotationOverrideId": "string",
    "RotationArn": "string",
    "NewContactIds": ["string"],
    "StartTime": "timestamp",
    "EndTime": "timestamp",
    "CreateTime": "timestamp"
}
```

---

### 11.9 `list-rotation-overrides`

Retrieves a list of overrides currently specified for an on-call rotation. **Paginated operation.**

**Synopsis:**
```bash
aws ssm-contacts list-rotation-overrides \
    --rotation-id <value> \
    --start-time <value> \
    --end-time <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rotation-id` | **Yes** | string | -- | Rotation ARN |
| `--start-time` | **Yes** | timestamp | -- | Start of time range |
| `--end-time` | **Yes** | timestamp | -- | End of time range |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Maximum items |

**Output Schema:**
```json
{
    "RotationOverrides": [
        {
            "RotationOverrideId": "string",
            "NewContactIds": ["string"],
            "StartTime": "timestamp",
            "EndTime": "timestamp",
            "CreateTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 11.10 `list-rotation-shifts`

Returns a list of shifts generated by an existing rotation in the system. **Paginated operation.**

**Synopsis:**
```bash
aws ssm-contacts list-rotation-shifts \
    --rotation-id <value> \
    --end-time <value> \
    [--start-time <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--rotation-id` | **Yes** | string | -- | Rotation ARN |
| `--end-time` | **Yes** | timestamp | -- | End of time range |
| `--start-time` | No | timestamp | None | Start of time range |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Maximum items |

**Output Schema:**
```json
{
    "RotationShifts": [
        {
            "ContactIds": ["string"],
            "StartTime": "timestamp",
            "EndTime": "timestamp",
            "Type": "REGULAR|OVERRIDDEN",
            "ShiftDetails": {
                "OverriddenContactIds": ["string"]
            }
        }
    ],
    "NextToken": "string"
}
```

---

### 11.11 `list-preview-rotation-shifts`

Returns a list of shifts based on rotation configuration parameters. This is a preview that does not require an existing rotation. **Paginated operation.**

**Synopsis:**
```bash
aws ssm-contacts list-preview-rotation-shifts \
    --end-time <value> \
    --members <value> \
    --time-zone-id <value> \
    --recurrence <value> \
    [--rotation-start-time <value>] \
    [--start-time <value>] \
    [--overrides <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--end-time` | **Yes** | timestamp | -- | End of preview range |
| `--members` | **Yes** | list(string) | -- | Contact ARNs for the preview |
| `--time-zone-id` | **Yes** | string | -- | Time zone ID |
| `--recurrence` | **Yes** | structure | -- | Recurrence configuration |
| `--rotation-start-time` | No | timestamp | None | When the rotation starts |
| `--start-time` | No | timestamp | None | Start of preview range |
| `--overrides` | No | list | None | Override configurations |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Maximum items |

**Output Schema:**
```json
{
    "RotationShifts": [
        {
            "ContactIds": ["string"],
            "StartTime": "timestamp",
            "EndTime": "timestamp",
            "Type": "REGULAR|OVERRIDDEN",
            "ShiftDetails": {
                "OverriddenContactIds": ["string"]
            }
        }
    ],
    "NextToken": "string"
}
```
