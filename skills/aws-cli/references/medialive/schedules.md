# Schedules

### 6.1 `batch-update-schedule`

Creates and deletes schedule actions for a channel. Schedule actions control input switches, SCTE-35 messages, static image overlays, and more.

**Synopsis:**
```bash
aws medialive batch-update-schedule \
    --channel-id <value> \
    [--creates <value>] \
    [--deletes <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-id` | **Yes** | string | -- | Channel ID |
| `--creates` | No | structure | None | Schedule actions to create |
| `--deletes` | No | structure | None | Schedule actions to delete |

**Creates structure:**
```json
{
    "ScheduleActions": [
        {
            "ActionName": "string",
            "ScheduleActionStartSettings": {
                "FixedModeScheduleActionStartSettings": {
                    "Time": "2025-06-01T12:00:00Z"
                },
                "FollowModeScheduleActionStartSettings": {
                    "FollowPoint": "END|START",
                    "ReferenceActionName": "string"
                },
                "ImmediateModeScheduleActionStartSettings": {}
            },
            "ScheduleActionSettings": {
                "InputSwitchSettings": {"InputAttachmentNameReference": "string"},
                "Scte35SpliceInsertSettings": {},
                "Scte35TimeSignalSettings": {},
                "StaticImageActivateSettings": {},
                "StaticImageDeactivateSettings": {},
                "HlsTimedMetadataSettings": {},
                "PauseStateSettings": {},
                "MotionGraphicsImageActivateSettings": {},
                "MotionGraphicsImageDeactivateSettings": {}
            }
        }
    ]
}
```

**Deletes structure:**
```json
{
    "ActionNames": ["string"]
}
```

**Output Schema:**
```json
{
    "Creates": {
        "ScheduleActions": [
            {
                "ActionName": "string",
                "ScheduleActionStartSettings": {},
                "ScheduleActionSettings": {}
            }
        ]
    },
    "Deletes": {
        "ScheduleActions": [
            {
                "ActionName": "string",
                "ScheduleActionStartSettings": {},
                "ScheduleActionSettings": {}
            }
        ]
    }
}
```

---

### 6.2 `describe-schedule`

Describes the schedule actions for a channel. **Paginated operation.**

**Synopsis:**
```bash
aws medialive describe-schedule \
    --channel-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-id` | **Yes** | string | -- | Channel ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "NextToken": "string",
    "ScheduleActions": [
        {
            "ActionName": "string",
            "ScheduleActionStartSettings": {},
            "ScheduleActionSettings": {}
        }
    ]
}
```

---

### 6.3 `delete-schedule`

Deletes all schedule actions for a channel.

**Synopsis:**
```bash
aws medialive delete-schedule \
    --channel-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--channel-id` | **Yes** | string | -- | Channel ID |

**Output:** None
