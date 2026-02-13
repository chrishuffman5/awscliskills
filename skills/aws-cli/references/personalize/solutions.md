# Solutions

### 4.1 `create-solution`

Creates a solution, which defines the recipe and configuration for training a model. A solution can have multiple trained versions (solution versions).

**Synopsis:**
```bash
aws personalize create-solution \
    --name <value> \
    --dataset-group-arn <value> \
    [--recipe-arn <value>] \
    [--event-type <value>] \
    [--perform-hpo | --no-perform-hpo] \
    [--perform-auto-ml | --no-perform-auto-ml] \
    [--perform-auto-training | --no-perform-auto-training] \
    [--solution-config <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Solution name (1-63 chars) |
| `--dataset-group-arn` | **Yes** | string | -- | ARN of the dataset group |
| `--recipe-arn` | No | string | None | ARN of the recipe. Required unless `--perform-auto-ml` is true |
| `--event-type` | No | string | None | Event type to use for training (e.g., `click`) |
| `--perform-hpo` | No | boolean | false | Enable hyperparameter optimization |
| `--perform-auto-ml` | No | boolean | false | Enable automated machine learning |
| `--perform-auto-training` | No | boolean | true | Enable automatic retraining every 7 days |
| `--solution-config` | No | structure | None | Advanced configuration (HPO, hyperparameters, optimization) |
| `--tags` | No | list | None | Tags (max 200) |

**Output Schema:**
```json
{
    "solutionArn": "string"
}
```

---

### 4.2 `describe-solution`

Describes a solution.

**Synopsis:**
```bash
aws personalize describe-solution \
    --solution-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--solution-arn` | **Yes** | string | -- | ARN of the solution |

**Output Schema:**
```json
{
    "solution": {
        "name": "string",
        "solutionArn": "string",
        "performHPO": true|false,
        "performAutoML": true|false,
        "performAutoTraining": true|false,
        "recipeArn": "string",
        "datasetGroupArn": "string",
        "eventType": "string",
        "solutionConfig": {},
        "status": "string",
        "creationDateTime": "timestamp",
        "lastUpdatedDateTime": "timestamp",
        "latestSolutionVersion": {
            "solutionVersionArn": "string",
            "status": "string",
            "trainingMode": "FULL|UPDATE|AUTOTRAIN",
            "trainingType": "AUTOMATIC|MANUAL",
            "creationDateTime": "timestamp",
            "lastUpdatedDateTime": "timestamp",
            "failureReason": "string"
        },
        "latestSolutionUpdate": {}
    }
}
```

---

### 4.3 `list-solutions`

Lists solutions in a dataset group. **Paginated operation.**

**Synopsis:**
```bash
aws personalize list-solutions \
    [--dataset-group-arn <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--dataset-group-arn` | No | string | None | Filter by dataset group ARN |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call (max 100) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "solutions": [
        {
            "name": "string",
            "solutionArn": "string",
            "status": "string",
            "creationDateTime": "timestamp",
            "lastUpdatedDateTime": "timestamp",
            "recipeArn": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 4.4 `update-solution`

Updates a solution to disable automatic training or change auto-training frequency.

**Synopsis:**
```bash
aws personalize update-solution \
    --solution-arn <value> \
    [--perform-auto-training | --no-perform-auto-training] \
    [--solution-update-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--solution-arn` | **Yes** | string | -- | ARN of the solution |
| `--perform-auto-training` | No | boolean | None | Enable or disable automatic training |
| `--solution-update-config` | No | structure | None | Update configuration (auto-training schedule) |

**Output Schema:**
```json
{
    "solutionArn": "string"
}
```

---

### 4.5 `delete-solution`

Deletes a solution and all solution versions. Must delete all campaigns first.

**Synopsis:**
```bash
aws personalize delete-solution \
    --solution-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--solution-arn` | **Yes** | string | -- | ARN of the solution to delete |

**Output:** None

---

### 4.6 `create-solution-version`

Trains a new model (solution version) from the solution configuration and latest dataset.

**Synopsis:**
```bash
aws personalize create-solution-version \
    --solution-arn <value> \
    [--training-mode <value>] \
    [--tags <value>] \
    [--name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--solution-arn` | **Yes** | string | -- | ARN of the solution |
| `--training-mode` | No | string | `FULL` | Training mode: `FULL` or `UPDATE` |
| `--tags` | No | list | None | Tags (max 200) |
| `--name` | No | string | None | Name for the solution version (1-63 chars) |

**Output Schema:**
```json
{
    "solutionVersionArn": "string"
}
```

---

### 4.7 `describe-solution-version`

Describes a solution version (trained model).

**Synopsis:**
```bash
aws personalize describe-solution-version \
    --solution-version-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--solution-version-arn` | **Yes** | string | -- | ARN of the solution version |

**Output Schema:**
```json
{
    "solutionVersion": {
        "name": "string",
        "solutionVersionArn": "string",
        "solutionArn": "string",
        "performHPO": true|false,
        "performAutoML": true|false,
        "recipeArn": "string",
        "eventType": "string",
        "datasetGroupArn": "string",
        "solutionConfig": {},
        "trainingHours": "double",
        "trainingMode": "FULL|UPDATE|AUTOTRAIN",
        "trainingType": "AUTOMATIC|MANUAL",
        "status": "string",
        "failureReason": "string",
        "creationDateTime": "timestamp",
        "lastUpdatedDateTime": "timestamp"
    }
}
```

---

### 4.8 `list-solution-versions`

Lists solution versions for a solution. **Paginated operation.**

**Synopsis:**
```bash
aws personalize list-solution-versions \
    [--solution-arn <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--solution-arn` | No | string | None | Filter by solution ARN |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call (max 100) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "solutionVersions": [
        {
            "solutionVersionArn": "string",
            "status": "string",
            "trainingMode": "FULL|UPDATE|AUTOTRAIN",
            "trainingType": "AUTOMATIC|MANUAL",
            "creationDateTime": "timestamp",
            "lastUpdatedDateTime": "timestamp",
            "failureReason": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 4.9 `get-solution-metrics`

Gets evaluation metrics for a trained solution version.

**Synopsis:**
```bash
aws personalize get-solution-metrics \
    --solution-version-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--solution-version-arn` | **Yes** | string | -- | ARN of the solution version |

**Output Schema:**
```json
{
    "solutionVersionArn": "string",
    "metrics": {
        "string": "double"
    }
}
```

---

### 4.10 `stop-solution-version-creation`

Stops training of a solution version that is in progress.

**Synopsis:**
```bash
aws personalize stop-solution-version-creation \
    --solution-version-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--solution-version-arn` | **Yes** | string | -- | ARN of the solution version |

**Output:** None
