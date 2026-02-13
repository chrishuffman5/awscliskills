# Experiment Templates

### 1.1 `create-experiment-template`

Creates an experiment template that defines the actions, targets, and stop conditions for an experiment.

**Synopsis:**
```bash
aws fis create-experiment-template \
    --description <value> \
    --stop-conditions <value> \
    --actions <value> \
    --role-arn <value> \
    [--client-token <value>] \
    [--targets <value>] \
    [--tags <value>] \
    [--log-configuration <value>] \
    [--experiment-options <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--description` | **Yes** | string | -- | Description of the experiment template |
| `--stop-conditions` | **Yes** | list | -- | Stop conditions. JSON: `[{"source":"none"}]` or `[{"source":"aws:cloudwatch:alarm","value":"arn:aws:cloudwatch:..."}]` |
| `--actions` | **Yes** | map | -- | Map of action names to action definitions (see structure below) |
| `--role-arn` | **Yes** | string | -- | IAM role ARN for the experiment |
| `--client-token` | No | string | Auto-generated | Idempotency token |
| `--targets` | No | map | None | Map of target names to target definitions (see structure below) |
| `--tags` | No | map | None | Tags. JSON: `{"key":"value"}` |
| `--log-configuration` | No | structure | None | Logging configuration (see structure below) |
| `--experiment-options` | No | structure | None | Experiment options. Shorthand: `accountTargeting=single-account\|multi-account,emptyTargetResolutionMode=fail\|skip` |

**Action Structure:**
```json
{
    "actionName": {
        "actionId": "string",
        "description": "string",
        "parameters": {
            "string": "string"
        },
        "targets": {
            "string": "string"
        },
        "startAfter": ["string"]
    }
}
```

**Target Structure:**
```json
{
    "targetName": {
        "resourceType": "string",
        "selectionMode": "ALL|COUNT(n)|PERCENT(n)",
        "resourceArns": ["string"],
        "resourceTags": {
            "string": ["string"]
        },
        "filters": [
            {
                "path": "string",
                "values": ["string"]
            }
        ],
        "parameters": {
            "string": "string"
        }
    }
}
```

**Log Configuration Structure:**
```json
{
    "cloudWatchLogsConfiguration": {
        "logGroupArn": "string"
    },
    "s3Configuration": {
        "bucketName": "string",
        "prefix": "string"
    },
    "logSchemaVersion": 2
}
```

**Output Schema:**
```json
{
    "experimentTemplate": {
        "id": "string",
        "description": "string",
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
                "startAfter": ["string"]
            }
        },
        "stopConditions": [
            {
                "source": "string",
                "value": "string"
            }
        ],
        "creationTime": "timestamp",
        "lastUpdateTime": "timestamp",
        "roleArn": "string",
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
            "emptyTargetResolutionMode": "fail|skip"
        },
        "targetAccountConfigurationsCount": "long"
    }
}
```

---

### 1.2 `delete-experiment-template`

Deletes an experiment template.

**Synopsis:**
```bash
aws fis delete-experiment-template \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | ID of the experiment template to delete |

**Output Schema:**
```json
{
    "experimentTemplate": {
        "id": "string",
        "description": "string",
        "targets": {},
        "actions": {},
        "stopConditions": [],
        "creationTime": "timestamp",
        "lastUpdateTime": "timestamp",
        "roleArn": "string",
        "tags": {},
        "logConfiguration": {},
        "experimentOptions": {},
        "targetAccountConfigurationsCount": "long"
    }
}
```

---

### 1.3 `get-experiment-template`

Returns details of an experiment template.

**Synopsis:**
```bash
aws fis get-experiment-template \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | ID of the experiment template |

**Output Schema:**
```json
{
    "experimentTemplate": {
        "id": "string",
        "description": "string",
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
                "startAfter": ["string"]
            }
        },
        "stopConditions": [
            {
                "source": "string",
                "value": "string"
            }
        ],
        "creationTime": "timestamp",
        "lastUpdateTime": "timestamp",
        "roleArn": "string",
        "tags": {},
        "logConfiguration": {},
        "experimentOptions": {
            "accountTargeting": "single-account|multi-account",
            "emptyTargetResolutionMode": "fail|skip"
        },
        "targetAccountConfigurationsCount": "long"
    }
}
```

---

### 1.4 `list-experiment-templates`

Lists experiment templates. **Paginated operation.**

**Synopsis:**
```bash
aws fis list-experiment-templates \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "experimentTemplates": [
        {
            "id": "string",
            "description": "string",
            "creationTime": "timestamp",
            "lastUpdateTime": "timestamp",
            "tags": {}
        }
    ],
    "nextToken": "string"
}
```

---

### 1.5 `update-experiment-template`

Updates an experiment template.

**Synopsis:**
```bash
aws fis update-experiment-template \
    --id <value> \
    [--description <value>] \
    [--stop-conditions <value>] \
    [--targets <value>] \
    [--actions <value>] \
    [--role-arn <value>] \
    [--log-configuration <value>] \
    [--experiment-options <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | ID of the experiment template to update |
| `--description` | No | string | None | Updated description |
| `--stop-conditions` | No | list | None | Updated stop conditions |
| `--targets` | No | map | None | Updated targets (replaces all targets) |
| `--actions` | No | map | None | Updated actions (replaces all actions) |
| `--role-arn` | No | string | None | Updated IAM role ARN |
| `--log-configuration` | No | structure | None | Updated logging configuration |
| `--experiment-options` | No | structure | None | Updated experiment options |

**Output Schema:**
```json
{
    "experimentTemplate": {
        "id": "string",
        "description": "string",
        "targets": {},
        "actions": {},
        "stopConditions": [],
        "creationTime": "timestamp",
        "lastUpdateTime": "timestamp",
        "roleArn": "string",
        "tags": {},
        "logConfiguration": {},
        "experimentOptions": {},
        "targetAccountConfigurationsCount": "long"
    }
}
```
