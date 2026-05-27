# Projects

### 1.1 `create-project`

Creates an Evidently project. A project groups features, experiments, and launches together.

**Synopsis:**
```bash
aws evidently create-project \
    --name <value> \
    [--description <value>] \
    [--app-config-resource <value>] \
    [--data-delivery <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Project name (1-127 chars, pattern: `^[-a-zA-Z0-9._]*$`) |
| `--description` | No | string | None | Project description (0-160 chars) |
| `--app-config-resource` | No | structure | None | AppConfig integration for client-side evaluation |
| `--data-delivery` | No | structure | None | Where to store evaluation events |
| `--tags` | No | map | None | Tags (max 50) |

**AppConfigResource structure:**
```json
{
    "applicationId": "string",
    "environmentId": "string"
}
```

**DataDelivery structure:**
```json
{
    "cloudWatchLogs": {
        "logGroup": "string"
    },
    "s3Destination": {
        "bucket": "string",
        "prefix": "string"
    }
}
```

**Output Schema:**
```json
{
    "project": {
        "arn": "string",
        "name": "string",
        "description": "string",
        "status": "AVAILABLE|UPDATING",
        "createdTime": "timestamp",
        "lastUpdatedTime": "timestamp",
        "activeExperimentCount": "long",
        "activeLaunchCount": "long",
        "experimentCount": "long",
        "featureCount": "long",
        "launchCount": "long",
        "appConfigResource": {
            "applicationId": "string",
            "environmentId": "string",
            "configurationProfileId": "string"
        },
        "dataDelivery": {
            "cloudWatchLogs": {"logGroup": "string"},
            "s3Destination": {"bucket": "string", "prefix": "string"}
        },
        "tags": {}
    }
}
```

---

### 1.2 `get-project`

Retrieves project details.

**Synopsis:**
```bash
aws evidently get-project \
    --project <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project` | **Yes** | string | -- | Project name or ARN (0-2048 chars) |

**Output Schema:**
```json
{
    "project": {
        "arn": "string",
        "name": "string",
        "description": "string",
        "status": "AVAILABLE|UPDATING",
        "createdTime": "timestamp",
        "lastUpdatedTime": "timestamp",
        "activeExperimentCount": "long",
        "activeLaunchCount": "long",
        "experimentCount": "long",
        "featureCount": "long",
        "launchCount": "long",
        "appConfigResource": {},
        "dataDelivery": {},
        "tags": {}
    }
}
```

---

### 1.3 `list-projects`

Lists all projects. **Paginated operation.**

**Synopsis:**
```bash
aws evidently list-projects \
    [--max-items <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--max-items` | No | integer | None | Total number of items to return |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Size of each page |

**Output Schema:**
```json
{
    "nextToken": "string",
    "projects": [
        {
            "arn": "string",
            "name": "string",
            "description": "string",
            "status": "AVAILABLE|UPDATING",
            "createdTime": "timestamp",
            "lastUpdatedTime": "timestamp",
            "activeExperimentCount": "long",
            "activeLaunchCount": "long",
            "experimentCount": "long",
            "featureCount": "long",
            "launchCount": "long",
            "tags": {}
        }
    ]
}
```

---

### 1.4 `update-project`

Updates a project.

**Synopsis:**
```bash
aws evidently update-project \
    --project <value> \
    [--description <value>] \
    [--app-config-resource <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project` | **Yes** | string | -- | Project name or ARN |
| `--description` | No | string | None | Updated description (0-160 chars) |
| `--app-config-resource` | No | structure | None | Updated AppConfig integration |

**Output Schema:**
```json
{
    "project": {
        "arn": "string",
        "name": "string",
        "description": "string",
        "status": "AVAILABLE|UPDATING",
        "createdTime": "timestamp",
        "lastUpdatedTime": "timestamp"
    }
}
```

---

### 1.5 `delete-project`

Deletes an Evidently project. All features, experiments, and launches in the project must be deleted first.

**Synopsis:**
```bash
aws evidently delete-project \
    --project <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project` | **Yes** | string | -- | Project name or ARN |

**Output:** None

---

### 1.6 `put-project-events`

Sends evaluation or custom events to Evidently. Used for custom metric tracking.

**Synopsis:**
```bash
aws evidently put-project-events \
    --project <value> \
    --events <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project` | **Yes** | string | -- | Project name or ARN (0-2048 chars) |
| `--events` | **Yes** | list | -- | Array of event structures (max 50) |

**Events structure:**
```json
[
    {
        "data": "string",
        "timestamp": "timestamp",
        "type": "aws.evidently.evaluation|aws.evidently.custom"
    }
]
```

**Output Schema:**
```json
{
    "eventResults": [
        {
            "eventId": "string",
            "errorCode": "string",
            "errorMessage": "string"
        }
    ],
    "failedEventCount": "integer"
}
```
