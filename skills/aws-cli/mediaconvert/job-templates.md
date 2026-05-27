# Job Templates

### 2.1 `create-job-template`

Creates a reusable job template with predefined transcoding settings.

**Synopsis:**
```bash
aws mediaconvert create-job-template \
    --name <value> \
    --settings <value> \
    [--acceleration-settings <value>] \
    [--category <value>] \
    [--description <value>] \
    [--hop-destinations <value>] \
    [--priority <value>] \
    [--queue <value>] \
    [--status-update-interval <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Template name |
| `--settings` | **Yes** | structure | -- | JobTemplateSettings with transcode configuration |
| `--acceleration-settings` | No | structure | None | Accelerated transcoding mode |
| `--category` | No | string | None | Template category |
| `--description` | No | string | None | Template description |
| `--hop-destinations` | No | list | None | Queue hopping configuration |
| `--priority` | No | integer | 0 | Job priority (-50 to 50) |
| `--queue` | No | string | None | Queue assignment |
| `--status-update-interval` | No | string | None | Status update interval |
| `--tags` | No | map | None | Key-value tag pairs |

**Output Schema:**
```json
{
    "JobTemplate": {
        "Arn": "string",
        "Name": "string",
        "Description": "string",
        "Category": "string",
        "Queue": "string",
        "Priority": "integer",
        "Type": "SYSTEM|CUSTOM",
        "Status": "ACTIVE|INACTIVE",
        "CreatedAt": "timestamp",
        "LastUpdated": "timestamp",
        "AccelerationSettings": {
            "Mode": "DISABLED|ENABLED|PREFERRED"
        },
        "HopDestinations": [
            {
                "Priority": "integer",
                "Queue": "string",
                "WaitMinutes": "integer"
            }
        ],
        "Settings": {
            "AdAvailOffset": "integer",
            "AvailBlanking": {},
            "Esam": {},
            "ExtendedDataServices": {},
            "Inputs": [],
            "OutputGroups": [],
            "TimecodeConfig": {}
        },
        "StatusUpdateInterval": "string",
        "Tags": {}
    }
}
```

---

### 2.2 `get-job-template`

Retrieves a job template by name.

**Synopsis:**
```bash
aws mediaconvert get-job-template \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Job template name |

**Output Schema:**
```json
{
    "JobTemplate": {
        "Arn": "string",
        "Name": "string",
        "Description": "string",
        "Category": "string",
        "Queue": "string",
        "Priority": "integer",
        "Type": "SYSTEM|CUSTOM",
        "CreatedAt": "timestamp",
        "LastUpdated": "timestamp",
        "AccelerationSettings": {
            "Mode": "DISABLED|ENABLED|PREFERRED"
        },
        "HopDestinations": [],
        "Settings": {
            "Inputs": [],
            "OutputGroups": [],
            "TimecodeConfig": {}
        },
        "StatusUpdateInterval": "string"
    }
}
```

---

### 2.3 `update-job-template`

Updates a job template's settings, priority, queue, or metadata.

**Synopsis:**
```bash
aws mediaconvert update-job-template \
    --name <value> \
    [--acceleration-settings <value>] \
    [--category <value>] \
    [--description <value>] \
    [--hop-destinations <value>] \
    [--priority <value>] \
    [--queue <value>] \
    [--settings <value>] \
    [--status-update-interval <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Template name to modify |
| `--acceleration-settings` | No | structure | None | Updated acceleration settings |
| `--category` | No | string | None | Updated category |
| `--description` | No | string | None | Updated description |
| `--hop-destinations` | No | list | None | Updated queue hopping config |
| `--priority` | No | integer | None | Updated priority (-50 to 50) |
| `--queue` | No | string | None | Updated queue assignment |
| `--settings` | No | structure | None | Updated JobTemplateSettings |
| `--status-update-interval` | No | string | None | Updated interval |

**Output Schema:**
```json
{
    "JobTemplate": {
        "Arn": "string",
        "Name": "string",
        "Description": "string",
        "Category": "string",
        "Queue": "string",
        "Priority": "integer",
        "Type": "SYSTEM|CUSTOM",
        "CreatedAt": "timestamp",
        "LastUpdated": "timestamp",
        "AccelerationSettings": {},
        "HopDestinations": [],
        "Settings": {},
        "StatusUpdateInterval": "string"
    }
}
```

---

### 2.4 `list-job-templates`

Lists job templates. **Paginated operation.**

**Synopsis:**
```bash
aws mediaconvert list-job-templates \
    [--category <value>] \
    [--list-by <value>] \
    [--order <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--category` | No | string | None | Filter by category |
| `--list-by` | No | string | NAME | `NAME`, `CREATION_DATE`, `SYSTEM` |
| `--order` | No | string | None | `ASCENDING` or `DESCENDING` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Max total items to return |

**Output Schema:**
```json
{
    "NextToken": "string",
    "JobTemplates": [
        {
            "Arn": "string",
            "Name": "string",
            "Description": "string",
            "Category": "string",
            "Queue": "string",
            "Priority": "integer",
            "Type": "SYSTEM|CUSTOM",
            "CreatedAt": "timestamp",
            "LastUpdated": "timestamp",
            "AccelerationSettings": {},
            "HopDestinations": [],
            "Settings": {},
            "StatusUpdateInterval": "string"
        }
    ]
}
```

---

### 2.5 `delete-job-template`

Deletes a job template by name.

**Synopsis:**
```bash
aws mediaconvert delete-job-template \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the job template to delete |

**Output:** None
