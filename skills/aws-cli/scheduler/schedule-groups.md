# Schedule Groups

### 2.1 `create-schedule-group`

Creates a schedule group for organizing schedules.

**Synopsis:**
```bash
aws scheduler create-schedule-group \
    --name <value> \
    [--client-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Group name (1-64 chars, alphanumeric, `-`, `_`, `.`) |
| `--client-token` | No | string | Auto | Idempotency token |
| `--tags` | No | list | None | Tags (Key/Value pairs, max 200) |

**Tags structure:**
```json
[
    {"Key": "string", "Value": "string"}
]
```

**Output Schema:**
```json
{
    "ScheduleGroupArn": "string"
}
```

---

### 2.2 `get-schedule-group`

Gets details about a schedule group.

**Synopsis:**
```bash
aws scheduler get-schedule-group \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Schedule group name |

**Output Schema:**
```json
{
    "Arn": "string",
    "Name": "string",
    "State": "ACTIVE|DELETING",
    "CreationDate": "timestamp",
    "LastModificationDate": "timestamp"
}
```

---

### 2.3 `list-schedule-groups`

Lists schedule groups. **Paginated operation.**

**Synopsis:**
```bash
aws scheduler list-schedule-groups \
    [--name-prefix <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name-prefix` | No | string | None | Filter by name prefix |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Size of each page |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "ScheduleGroups": [
        {
            "Arn": "string",
            "Name": "string",
            "State": "ACTIVE|DELETING",
            "CreationDate": "timestamp",
            "LastModificationDate": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.4 `delete-schedule-group`

Deletes a schedule group and all schedules within it.

**Synopsis:**
```bash
aws scheduler delete-schedule-group \
    --name <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Group name to delete |
| `--client-token` | No | string | Auto | Idempotency token |

**Output:** None
