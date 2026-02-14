# Launches

### 4.1 `create-launch`

Creates a launch for gradual feature rollout. Launches let you serve a feature variation to increasing percentages of users over scheduled steps.

**Synopsis:**
```bash
aws evidently create-launch \
    --project <value> \
    --name <value> \
    --groups <value> \
    [--description <value>] \
    [--metric-monitors <value>] \
    [--randomization-salt <value>] \
    [--scheduled-splits-config <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project` | **Yes** | string | -- | Project name or ARN (0-2048 chars) |
| `--name` | **Yes** | string | -- | Launch name (1-127 chars) |
| `--groups` | **Yes** | list | -- | Feature variation groups (1-5) |
| `--description` | No | string | None | Description (0-160 chars) |
| `--metric-monitors` | No | list | None | Metrics to monitor (max 3) |
| `--randomization-salt` | No | string | Launch name | Salt for randomization (0-127 chars) |
| `--scheduled-splits-config` | No | structure | None | Traffic allocation schedule |
| `--tags` | No | map | None | Tags (max 50) |

**Groups structure:**
```json
[
    {
        "name": "string",
        "feature": "string",
        "variation": "string",
        "description": "string"
    }
]
```

**MetricMonitors structure:**
```json
[
    {
        "metricDefinition": {
            "name": "string",
            "entityIdKey": "string",
            "valueKey": "string",
            "eventPattern": "string",
            "unitLabel": "string"
        }
    }
]
```

**ScheduledSplitsConfig structure:**
```json
{
    "steps": [
        {
            "startTime": "timestamp",
            "groupWeights": {
                "group-name": 50000
            },
            "segmentOverrides": [
                {
                    "segment": "string",
                    "evaluationOrder": "long",
                    "weights": {"group-name": 50000}
                }
            ]
        }
    ]
}
```

Group weights are in thousandths of percent (50000 = 50%).

**Output Schema:**
```json
{
    "launch": {
        "arn": "string",
        "name": "string",
        "project": "string",
        "description": "string",
        "createdTime": "timestamp",
        "lastUpdatedTime": "timestamp",
        "status": "CREATED|UPDATING|RUNNING|COMPLETED|CANCELLED",
        "statusReason": "string",
        "type": "aws.evidently.splits",
        "groups": [
            {
                "name": "string",
                "description": "string",
                "featureVariations": {}
            }
        ],
        "metricMonitors": [],
        "randomizationSalt": "string",
        "scheduledSplitsDefinition": {"steps": []},
        "execution": {"startedTime": "timestamp", "endedTime": "timestamp"},
        "tags": {}
    }
}
```

---

### 4.2 `get-launch`

Retrieves launch details.

**Synopsis:**
```bash
aws evidently get-launch \
    --project <value> \
    --launch <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project` | **Yes** | string | -- | Project name or ARN |
| `--launch` | **Yes** | string | -- | Launch name (1-127 chars) |

**Output Schema:**
```json
{
    "launch": {
        "arn": "string",
        "name": "string",
        "project": "string",
        "description": "string",
        "createdTime": "timestamp",
        "lastUpdatedTime": "timestamp",
        "status": "CREATED|UPDATING|RUNNING|COMPLETED|CANCELLED",
        "type": "aws.evidently.splits",
        "groups": [],
        "metricMonitors": [],
        "scheduledSplitsDefinition": {},
        "execution": {},
        "tags": {}
    }
}
```

---

### 4.3 `list-launches`

Lists launches in a project. **Paginated operation.**

**Synopsis:**
```bash
aws evidently list-launches \
    --project <value> \
    [--status <value>] \
    [--max-items <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project` | **Yes** | string | -- | Project name or ARN |
| `--status` | No | string | None | Filter: `CREATED`, `UPDATING`, `RUNNING`, `COMPLETED`, `CANCELLED` |
| `--max-items` | No | integer | None | Total items to return |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Size of each page |

**Output Schema:**
```json
{
    "nextToken": "string",
    "launches": [
        {
            "arn": "string",
            "name": "string",
            "project": "string",
            "status": "CREATED|UPDATING|RUNNING|COMPLETED|CANCELLED",
            "type": "aws.evidently.splits",
            "createdTime": "timestamp",
            "lastUpdatedTime": "timestamp",
            "tags": {}
        }
    ]
}
```

---

### 4.4 `update-launch`

Updates a launch.

**Synopsis:**
```bash
aws evidently update-launch \
    --project <value> \
    --launch <value> \
    [--description <value>] \
    [--groups <value>] \
    [--metric-monitors <value>] \
    [--randomization-salt <value>] \
    [--scheduled-splits-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project` | **Yes** | string | -- | Project name or ARN |
| `--launch` | **Yes** | string | -- | Launch name |
| `--description` | No | string | None | Updated description |
| `--groups` | No | list | None | Updated groups |
| `--metric-monitors` | No | list | None | Updated metric monitors |
| `--randomization-salt` | No | string | None | Updated salt |
| `--scheduled-splits-config` | No | structure | None | Updated schedule |

**Output Schema:**
```json
{
    "launch": {
        "arn": "string",
        "name": "string",
        "project": "string",
        "status": "CREATED|UPDATING|RUNNING|COMPLETED|CANCELLED",
        "type": "aws.evidently.splits",
        "groups": [],
        "metricMonitors": [],
        "scheduledSplitsDefinition": {},
        "tags": {}
    }
}
```

---

### 4.5 `delete-launch`

Deletes a launch. Must be in CREATED, COMPLETED, or CANCELLED state.

**Synopsis:**
```bash
aws evidently delete-launch \
    --project <value> \
    --launch <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project` | **Yes** | string | -- | Project name or ARN |
| `--launch` | **Yes** | string | -- | Launch name |

**Output:** None

---

### 4.6 `start-launch`

Starts a launch.

**Synopsis:**
```bash
aws evidently start-launch \
    --project <value> \
    --launch <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project` | **Yes** | string | -- | Project name or ARN |
| `--launch` | **Yes** | string | -- | Launch name (1-127 chars) |

**Output Schema:**
```json
{
    "launch": {
        "arn": "string",
        "name": "string",
        "project": "string",
        "status": "RUNNING",
        "type": "aws.evidently.splits",
        "createdTime": "timestamp",
        "lastUpdatedTime": "timestamp",
        "execution": {"startedTime": "timestamp"},
        "groups": [],
        "scheduledSplitsDefinition": {},
        "tags": {}
    }
}
```

---

### 4.7 `stop-launch`

Stops a running launch.

**Synopsis:**
```bash
aws evidently stop-launch \
    --project <value> \
    --launch <value> \
    [--desired-state <value>] \
    [--reason <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project` | **Yes** | string | -- | Project name or ARN |
| `--launch` | **Yes** | string | -- | Launch name (1-127 chars) |
| `--desired-state` | No | string | None | `COMPLETED` or `CANCELLED` |
| `--reason` | No | string | None | Reason for stopping (0-160 chars) |

**Output Schema:**
```json
{
    "endedTime": "timestamp"
}
```
