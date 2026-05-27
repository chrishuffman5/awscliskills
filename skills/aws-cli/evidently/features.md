# Features

### 2.1 `create-feature`

Creates a feature. A feature is a configuration variable that can have different variations served to users.

**Synopsis:**
```bash
aws evidently create-feature \
    --project <value> \
    --name <value> \
    --variations <value> \
    [--default-variation <value>] \
    [--description <value>] \
    [--entity-overrides <value>] \
    [--evaluation-strategy <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project` | **Yes** | string | -- | Project name or ARN (0-2048 chars) |
| `--name` | **Yes** | string | -- | Feature name (1-127 chars, pattern: `^[-a-zA-Z0-9._]*$`) |
| `--variations` | **Yes** | list | -- | Feature variations (1-5) |
| `--default-variation` | No | string | None | Default variation name |
| `--description` | No | string | None | Description (0-160 chars) |
| `--entity-overrides` | No | map | None | User-to-variation overrides (max 2500 or 40KB) |
| `--evaluation-strategy` | No | string | None | `ALL_RULES` or `DEFAULT_VARIATION` |
| `--tags` | No | map | None | Tags (max 50) |

**Variations structure:**
```json
[
    {
        "name": "string",
        "value": {
            "boolValue": true,
            "doubleValue": 1.5,
            "longValue": 100,
            "stringValue": "string"
        }
    }
]
```

Only one value type per variation (boolValue, doubleValue, longValue, or stringValue).

**Output Schema:**
```json
{
    "feature": {
        "arn": "string",
        "name": "string",
        "project": "string",
        "description": "string",
        "createdTime": "timestamp",
        "lastUpdatedTime": "timestamp",
        "status": "AVAILABLE|UPDATING",
        "evaluationStrategy": "ALL_RULES|DEFAULT_VARIATION",
        "defaultVariation": "string",
        "valueType": "STRING|LONG|DOUBLE|BOOLEAN",
        "variations": [
            {
                "name": "string",
                "value": {}
            }
        ],
        "entityOverrides": {},
        "evaluationRules": [],
        "tags": {}
    }
}
```

---

### 2.2 `get-feature`

Retrieves feature details.

**Synopsis:**
```bash
aws evidently get-feature \
    --project <value> \
    --feature <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project` | **Yes** | string | -- | Project name or ARN |
| `--feature` | **Yes** | string | -- | Feature name (1-127 chars) |

**Output Schema:**
```json
{
    "feature": {
        "arn": "string",
        "name": "string",
        "project": "string",
        "description": "string",
        "createdTime": "timestamp",
        "lastUpdatedTime": "timestamp",
        "status": "AVAILABLE|UPDATING",
        "evaluationStrategy": "ALL_RULES|DEFAULT_VARIATION",
        "defaultVariation": "string",
        "valueType": "STRING|LONG|DOUBLE|BOOLEAN",
        "variations": [],
        "entityOverrides": {},
        "evaluationRules": [],
        "tags": {}
    }
}
```

---

### 2.3 `list-features`

Lists features in a project. **Paginated operation.**

**Synopsis:**
```bash
aws evidently list-features \
    --project <value> \
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
| `--max-items` | No | integer | None | Total number of items to return |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Size of each page |

**Output Schema:**
```json
{
    "nextToken": "string",
    "features": [
        {
            "arn": "string",
            "name": "string",
            "project": "string",
            "status": "AVAILABLE|UPDATING",
            "evaluationStrategy": "ALL_RULES|DEFAULT_VARIATION",
            "createdTime": "timestamp",
            "lastUpdatedTime": "timestamp",
            "defaultVariation": "string",
            "evaluationRules": [],
            "tags": {}
        }
    ]
}
```

---

### 2.4 `update-feature`

Updates a feature.

**Synopsis:**
```bash
aws evidently update-feature \
    --project <value> \
    --feature <value> \
    [--description <value>] \
    [--add-or-update-variations <value>] \
    [--remove-variations <value>] \
    [--default-variation <value>] \
    [--entity-overrides <value>] \
    [--evaluation-strategy <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project` | **Yes** | string | -- | Project name or ARN |
| `--feature` | **Yes** | string | -- | Feature name (1-127 chars) |
| `--description` | No | string | None | Updated description |
| `--add-or-update-variations` | No | list | None | Variations to add or update (1-5) |
| `--remove-variations` | No | list | None | Variation names to remove |
| `--default-variation` | No | string | None | Updated default variation |
| `--entity-overrides` | No | map | None | Updated entity overrides |
| `--evaluation-strategy` | No | string | None | `ALL_RULES` or `DEFAULT_VARIATION` |

**Output Schema:**
```json
{
    "feature": {
        "arn": "string",
        "name": "string",
        "project": "string",
        "status": "AVAILABLE|UPDATING",
        "evaluationStrategy": "ALL_RULES|DEFAULT_VARIATION",
        "defaultVariation": "string",
        "valueType": "STRING|LONG|DOUBLE|BOOLEAN",
        "variations": [],
        "entityOverrides": {},
        "evaluationRules": [],
        "tags": {}
    }
}
```

---

### 2.5 `delete-feature`

Deletes a feature.

**Synopsis:**
```bash
aws evidently delete-feature \
    --project <value> \
    --feature <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project` | **Yes** | string | -- | Project name or ARN |
| `--feature` | **Yes** | string | -- | Feature name |

**Output:** None

---

### 2.6 `evaluate-feature`

Evaluates a feature for a specific entity, returning the variation to serve.

**Synopsis:**
```bash
aws evidently evaluate-feature \
    --project <value> \
    --feature <value> \
    --entity-id <value> \
    [--evaluation-context <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project` | **Yes** | string | -- | Project name or ARN |
| `--feature` | **Yes** | string | -- | Feature name (1-127 chars) |
| `--entity-id` | **Yes** | string | -- | Unique entity/user ID (1-512 chars) |
| `--evaluation-context` | No | string | None | JSON attributes for segment matching |

**Output Schema:**
```json
{
    "details": "string",
    "reason": "DEFAULT|LAUNCH_RULE_MATCH|EXPERIMENT_RULE_MATCH|ENTITY_OVERRIDES_MATCH",
    "value": {
        "boolValue": "boolean",
        "doubleValue": "double",
        "longValue": "long",
        "stringValue": "string"
    },
    "variation": "string"
}
```

---

### 2.7 `batch-evaluate-feature`

Evaluates features for multiple entities in a single call.

**Synopsis:**
```bash
aws evidently batch-evaluate-feature \
    --project <value> \
    --requests <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project` | **Yes** | string | -- | Project name or ARN |
| `--requests` | **Yes** | list | -- | Evaluation requests (1-20) |

**Requests structure:**
```json
[
    {
        "entityId": "string",
        "feature": "string",
        "evaluationContext": "string"
    }
]
```

**Output Schema:**
```json
{
    "results": [
        {
            "entityId": "string",
            "feature": "string",
            "project": "string",
            "details": "string",
            "reason": "DEFAULT|LAUNCH_RULE_MATCH|EXPERIMENT_RULE_MATCH|ENTITY_OVERRIDES_MATCH",
            "value": {},
            "variation": "string"
        }
    ]
}
```
