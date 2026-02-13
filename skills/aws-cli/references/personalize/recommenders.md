# Recommenders

### 6.1 `create-recommender`

Creates a recommender for a Domain dataset group. Recommenders use pre-configured recipes for specific use cases.

**Synopsis:**
```bash
aws personalize create-recommender \
    --name <value> \
    --dataset-group-arn <value> \
    --recipe-arn <value> \
    [--recommender-config <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Recommender name (1-63 chars) |
| `--dataset-group-arn` | **Yes** | string | -- | ARN of the Domain dataset group |
| `--recipe-arn` | **Yes** | string | -- | ARN of the recipe for the use case |
| `--recommender-config` | No | structure | None | Configuration (throughput, exploration, metadata) |
| `--tags` | No | list | None | Tags (max 200) |

**RecommenderConfig Structure:**
```json
{
    "itemExplorationConfig": {"string": "string"},
    "minRecommendationRequestsPerSecond": "integer",
    "trainingDataConfig": {
        "excludedDatasetColumns": {"string": ["string"]},
        "includedDatasetColumns": {"string": ["string"]}
    },
    "enableMetadataWithRecommendations": true|false
}
```

**Output Schema:**
```json
{
    "recommenderArn": "string"
}
```

---

### 6.2 `describe-recommender`

Describes a recommender.

**Synopsis:**
```bash
aws personalize describe-recommender \
    --recommender-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--recommender-arn` | **Yes** | string | -- | ARN of the recommender |

**Output Schema:**
```json
{
    "recommender": {
        "recommenderArn": "string",
        "datasetGroupArn": "string",
        "name": "string",
        "recipeArn": "string",
        "recommenderConfig": {},
        "creationDateTime": "timestamp",
        "lastUpdatedDateTime": "timestamp",
        "status": "string",
        "failureReason": "string",
        "latestRecommenderUpdate": {
            "recommenderConfig": {},
            "status": "string",
            "failureReason": "string",
            "creationDateTime": "timestamp",
            "lastUpdatedDateTime": "timestamp"
        },
        "modelMetrics": {"string": "double"}
    }
}
```

---

### 6.3 `list-recommenders`

Lists recommenders. **Paginated operation.**

**Synopsis:**
```bash
aws personalize list-recommenders \
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
    "recommenders": [
        {
            "name": "string",
            "recommenderArn": "string",
            "datasetGroupArn": "string",
            "recipeArn": "string",
            "recommenderConfig": {},
            "status": "string",
            "creationDateTime": "timestamp",
            "lastUpdatedDateTime": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 6.4 `update-recommender`

Updates a recommender configuration.

**Synopsis:**
```bash
aws personalize update-recommender \
    --recommender-arn <value> \
    --recommender-config <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--recommender-arn` | **Yes** | string | -- | ARN of the recommender |
| `--recommender-config` | **Yes** | structure | -- | Updated configuration |

**Output Schema:**
```json
{
    "recommenderArn": "string"
}
```

---

### 6.5 `delete-recommender`

Deletes a recommender.

**Synopsis:**
```bash
aws personalize delete-recommender \
    --recommender-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--recommender-arn` | **Yes** | string | -- | ARN of the recommender to delete |

**Output:** None

---

### 6.6 `start-recommender`

Starts a stopped recommender, resuming billing.

**Synopsis:**
```bash
aws personalize start-recommender \
    --recommender-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--recommender-arn` | **Yes** | string | -- | ARN of the recommender to start |

**Output Schema:**
```json
{
    "recommenderArn": "string"
}
```

---

### 6.7 `stop-recommender`

Stops a running recommender to reduce costs. Can be restarted later.

**Synopsis:**
```bash
aws personalize stop-recommender \
    --recommender-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--recommender-arn` | **Yes** | string | -- | ARN of the recommender to stop |

**Output Schema:**
```json
{
    "recommenderArn": "string"
}
```
