# Experiments

### 2.1 `start-experiment`

Starts an experiment from the specified experiment template.

**Synopsis:**
```bash
aws fis start-experiment \
    --experiment-template-id <value> \
    [--client-token <value>] \
    [--tags <value>] \
    [--experiment-options <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--experiment-template-id` | **Yes** | string | -- | ID of the experiment template to use |
| `--client-token` | No | string | Auto-generated | Idempotency token |
| `--tags` | No | map | None | Tags for the experiment. JSON: `{"key":"value"}` |
| `--experiment-options` | No | structure | None | Override experiment options. Shorthand: `actionsMode=run-all\|skip-all` |

**Output Schema:**
```json
{
    "experiment": {
        "id": "string",
        "experimentTemplateId": "string",
        "roleArn": "string",
        "state": {
            "status": "pending|initiating|running|completed|stopping|stopped|failed",
            "reason": "string"
        },
        "targets": {
            "string": {
                "resourceType": "string",
                "selectionMode": "string",
                "resourceArns": ["string"],
                "resourceTags": {},
                "filters": [],
                "parameters": {}
            }
        },
        "actions": {
            "string": {
                "actionId": "string",
                "description": "string",
                "parameters": {},
                "targets": {},
                "startAfter": ["string"],
                "state": {
                    "status": "pending|initiating|running|completed|cancelled|skipped|stopped|failed",
                    "reason": "string"
                },
                "startTime": "timestamp",
                "endTime": "timestamp"
            }
        },
        "stopConditions": [
            {
                "source": "string",
                "value": "string"
            }
        ],
        "creationTime": "timestamp",
        "startTime": "timestamp",
        "endTime": "timestamp",
        "tags": {},
        "logConfiguration": {
            "cloudWatchLogsConfiguration": {
                "logGroupArn": "string"
            },
            "s3Configuration": {
                "bucketName": "string",
                "prefix": "string"
            },
            "logSchemaVersion": "integer"
        },
        "experimentOptions": {
            "accountTargeting": "single-account|multi-account",
            "emptyTargetResolutionMode": "fail|skip",
            "actionsMode": "run-all|skip-all"
        },
        "targetAccountConfigurationsCount": "long"
    }
}
```

---

### 2.2 `stop-experiment`

Stops a running experiment.

**Synopsis:**
```bash
aws fis stop-experiment \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | ID of the experiment to stop |

**Output Schema:**
```json
{
    "experiment": {
        "id": "string",
        "experimentTemplateId": "string",
        "roleArn": "string",
        "state": {
            "status": "stopping",
            "reason": "string"
        },
        "targets": {},
        "actions": {},
        "stopConditions": [],
        "creationTime": "timestamp",
        "startTime": "timestamp",
        "endTime": "timestamp",
        "tags": {},
        "logConfiguration": {},
        "experimentOptions": {},
        "targetAccountConfigurationsCount": "long"
    }
}
```

---

### 2.3 `get-experiment`

Returns details of a specific experiment.

**Synopsis:**
```bash
aws fis get-experiment \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | ID of the experiment |

**Output Schema:**
```json
{
    "experiment": {
        "id": "string",
        "experimentTemplateId": "string",
        "roleArn": "string",
        "state": {
            "status": "pending|initiating|running|completed|stopping|stopped|failed",
            "reason": "string"
        },
        "targets": {
            "string": {
                "resourceType": "string",
                "selectionMode": "string",
                "resourceArns": ["string"],
                "resourceTags": {},
                "filters": [],
                "parameters": {}
            }
        },
        "actions": {
            "string": {
                "actionId": "string",
                "description": "string",
                "parameters": {},
                "targets": {},
                "startAfter": ["string"],
                "state": {
                    "status": "string",
                    "reason": "string"
                },
                "startTime": "timestamp",
                "endTime": "timestamp"
            }
        },
        "stopConditions": [],
        "creationTime": "timestamp",
        "startTime": "timestamp",
        "endTime": "timestamp",
        "tags": {},
        "logConfiguration": {},
        "experimentOptions": {
            "accountTargeting": "single-account|multi-account",
            "emptyTargetResolutionMode": "fail|skip",
            "actionsMode": "run-all|skip-all"
        },
        "targetAccountConfigurationsCount": "long"
    }
}
```

---

### 2.4 `list-experiments`

Lists experiments in the account. **Paginated operation.**

**Synopsis:**
```bash
aws fis list-experiments \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--experiment-template-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |
| `--experiment-template-id` | No | string | None | Filter by experiment template ID |

**Output Schema:**
```json
{
    "experiments": [
        {
            "id": "string",
            "experimentTemplateId": "string",
            "state": {
                "status": "pending|initiating|running|completed|stopping|stopped|failed",
                "reason": "string"
            },
            "creationTime": "timestamp",
            "tags": {},
            "experimentOptions": {
                "accountTargeting": "string",
                "emptyTargetResolutionMode": "string",
                "actionsMode": "string"
            }
        }
    ],
    "nextToken": "string"
}
```

---

### 2.5 `list-experiment-resolved-targets`

Lists the resolved targets for a running or completed experiment. **Paginated operation.**

**Synopsis:**
```bash
aws fis list-experiment-resolved-targets \
    --experiment-id <value> \
    [--target-name <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--experiment-id` | **Yes** | string | -- | ID of the experiment |
| `--target-name` | No | string | None | Filter by target name |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "resolvedTargets": [
        {
            "resourceType": "string",
            "targetName": "string",
            "targetInformation": {
                "string": "string"
            }
        }
    ],
    "nextToken": "string"
}
```
