# Waves & Applications

## Waves

### 5.1 `create-wave`

Creates a migration wave for grouping applications.

**Synopsis:**
```bash
aws mgn create-wave \
    --name <value> \
    [--description <value>] \
    [--account-id <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Wave name (1-256 chars) |
| `--description` | No | string | None | Description (max 600 chars) |
| `--account-id` | No | string | None | Account ID |
| `--tags` | No | map | None | Tags |

**Output Schema:**
```json
{
    "waveID": "string",
    "arn": "string",
    "name": "string",
    "description": "string",
    "isArchived": true|false,
    "waveAggregatedStatus": {
        "lastUpdateDateTime": "string",
        "replicationStartedDateTime": "string",
        "healthStatus": "HEALTHY|LAGGING|STALLED|ERROR",
        "progressStatus": "NOT_STARTED|IN_PROGRESS|COMPLETED",
        "totalApplications": "long"
    },
    "creationDateTime": "string",
    "lastModifiedDateTime": "string",
    "tags": {"key": "value"}
}
```

---

### 5.2 `delete-wave`

Deletes a wave. All applications must be disassociated first.

**Synopsis:**
```bash
aws mgn delete-wave \
    --wave-id <value> \
    [--account-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--wave-id` | **Yes** | string | -- | Wave ID |
| `--account-id` | No | string | None | Account ID |

**Output:** None

---

### 5.3 `list-waves`

Lists migration waves. **Paginated.**

**Synopsis:**
```bash
aws mgn list-waves \
    [--filters <value>] \
    [--account-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | structure | None | Filters: `waveIDs=["string"],isArchived=true\|false` |
| `--account-id` | No | string | None | Account ID |

**Output Schema:**
```json
{
    "items": [{"waveID": "string", "...": "..."}],
    "nextToken": "string"
}
```

---

### 5.4 `update-wave`

Updates a wave's name or description.

**Synopsis:**
```bash
aws mgn update-wave \
    --wave-id <value> \
    [--name <value>] \
    [--description <value>] \
    [--account-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Output Schema:** Same as create-wave.

---

### 5.5 `archive-wave` / 5.6 `unarchive-wave`

Archives or unarchives a wave.

**Synopsis:**
```bash
aws mgn archive-wave --wave-id <value> [--account-id <value>]
aws mgn unarchive-wave --wave-id <value> [--account-id <value>]
```

**Output Schema:** Same as create-wave.

---

## Applications

### 5.7 `create-application`

Creates a migration application for grouping source servers.

**Synopsis:**
```bash
aws mgn create-application \
    --name <value> \
    [--description <value>] \
    [--account-id <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Application name (1-256 chars) |
| `--description` | No | string | None | Description (max 600 chars) |
| `--account-id` | No | string | None | Account ID |
| `--tags` | No | map | None | Tags |

**Output Schema:**
```json
{
    "applicationID": "string",
    "arn": "string",
    "name": "string",
    "description": "string",
    "isArchived": true|false,
    "applicationAggregatedStatus": {
        "lastUpdateDateTime": "string",
        "healthStatus": "HEALTHY|LAGGING|STALLED|ERROR",
        "progressStatus": "NOT_STARTED|IN_PROGRESS|COMPLETED",
        "totalSourceServers": "long"
    },
    "creationDateTime": "string",
    "lastModifiedDateTime": "string",
    "waveID": "string",
    "tags": {"key": "value"}
}
```

---

### 5.8 `delete-application`

Deletes an application. All source servers must be disassociated first.

**Synopsis:**
```bash
aws mgn delete-application \
    --application-id <value> \
    [--account-id <value>]
```

**Output:** None

---

### 5.9 `list-applications`

Lists applications. **Paginated.**

**Synopsis:**
```bash
aws mgn list-applications \
    [--filters <value>] \
    [--account-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Filters:** `applicationIDs=["string"],isArchived=true|false,waveIDs=["string"]`

**Output Schema:**
```json
{
    "items": [{"applicationID": "string", "...": "..."}],
    "nextToken": "string"
}
```

---

### 5.10-5.11 `archive-application` / `unarchive-application`

Archives or unarchives an application.

```bash
aws mgn archive-application --application-id <value> [--account-id <value>]
aws mgn unarchive-application --application-id <value> [--account-id <value>]
```

**Output Schema:** Same as create-application.

---

### 5.12-5.13 `update-application`

Updates an application.

```bash
aws mgn update-application --application-id <value> [--name <value>] [--description <value>] [--account-id <value>]
```

**Output Schema:** Same as create-application.

---

## Associations

### 5.14 `associate-applications`

Associates applications with a wave.

**Synopsis:**
```bash
aws mgn associate-applications \
    --wave-id <value> \
    --application-ids <value> \
    [--account-id <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--wave-id` | **Yes** | string | -- | Wave ID |
| `--application-ids` | **Yes** | list(string) | -- | Application IDs (1-50) |
| `--account-id` | No | string | None | Account ID |

**Output:** None

---

### 5.15 `disassociate-applications`

Disassociates applications from a wave.

```bash
aws mgn disassociate-applications --wave-id <value> --application-ids <value> [--account-id <value>]
```

**Output:** None

---

### 5.16 `associate-source-servers`

Associates source servers with an application.

**Synopsis:**
```bash
aws mgn associate-source-servers \
    --application-id <value> \
    --source-server-ids <value> \
    [--account-id <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application ID |
| `--source-server-ids` | **Yes** | list(string) | -- | Source server IDs (1-50) |
| `--account-id` | No | string | None | Account ID |

**Output:** None

---

### 5.17 `disassociate-source-servers`

Disassociates source servers from an application.

```bash
aws mgn disassociate-source-servers --application-id <value> --source-server-ids <value> [--account-id <value>]
```

**Output:** None
