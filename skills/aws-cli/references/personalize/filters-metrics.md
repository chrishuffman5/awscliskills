# Filters & Metrics

### 9.1 `create-filter`

Creates a recommendation filter using a filter expression to include or exclude items from recommendations.

**Synopsis:**
```bash
aws personalize create-filter \
    --name <value> \
    --dataset-group-arn <value> \
    --filter-expression <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Filter name (1-63 chars) |
| `--dataset-group-arn` | **Yes** | string | -- | ARN of the dataset group |
| `--filter-expression` | **Yes** | string | -- | Filter expression (1-2500 chars) |
| `--tags` | No | list | None | Tags (max 200) |

**Output Schema:**
```json
{
    "filterArn": "string"
}
```

---

### 9.2 `describe-filter`

Describes a filter.

**Synopsis:**
```bash
aws personalize describe-filter \
    --filter-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filter-arn` | **Yes** | string | -- | ARN of the filter |

**Output Schema:**
```json
{
    "filter": {
        "name": "string",
        "filterArn": "string",
        "creationDateTime": "timestamp",
        "lastUpdatedDateTime": "timestamp",
        "datasetGroupArn": "string",
        "failureReason": "string",
        "filterExpression": "string",
        "status": "string"
    }
}
```

---

### 9.3 `list-filters`

Lists filters for a dataset group. **Paginated operation.**

**Synopsis:**
```bash
aws personalize list-filters \
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
    "Filters": [
        {
            "name": "string",
            "filterArn": "string",
            "creationDateTime": "timestamp",
            "lastUpdatedDateTime": "timestamp",
            "datasetGroupArn": "string",
            "failureReason": "string",
            "status": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 9.4 `delete-filter`

Deletes a filter.

**Synopsis:**
```bash
aws personalize delete-filter \
    --filter-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filter-arn` | **Yes** | string | -- | ARN of the filter to delete |

**Output:** None

---

### 9.5 `create-metric-attribution`

Creates a metric attribution for measuring the impact of recommendations on business metrics.

**Synopsis:**
```bash
aws personalize create-metric-attribution \
    --name <value> \
    --dataset-group-arn <value> \
    --metrics <value> \
    --metrics-output-config <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Metric attribution name (1-63 chars) |
| `--dataset-group-arn` | **Yes** | string | -- | ARN of the dataset group |
| `--metrics` | **Yes** | list | -- | Metric definitions |
| `--metrics-output-config` | **Yes** | structure | -- | Output configuration for metric data |

**Output Schema:**
```json
{
    "metricAttributionArn": "string"
}
```

---

### 9.6 `describe-metric-attribution`

Describes a metric attribution.

**Synopsis:**
```bash
aws personalize describe-metric-attribution \
    --metric-attribution-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--metric-attribution-arn` | **Yes** | string | -- | ARN of the metric attribution |

**Output Schema:**
```json
{
    "metricAttribution": {
        "name": "string",
        "metricAttributionArn": "string",
        "datasetGroupArn": "string",
        "metricsOutputConfig": {},
        "status": "string",
        "creationDateTime": "timestamp",
        "lastUpdatedDateTime": "timestamp",
        "failureReason": "string"
    }
}
```

---

### 9.7 `list-metric-attributions`

Lists metric attributions. **Paginated operation.**

**Synopsis:**
```bash
aws personalize list-metric-attributions \
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
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "metricAttributions": [
        {
            "name": "string",
            "metricAttributionArn": "string",
            "status": "string",
            "creationDateTime": "timestamp",
            "lastUpdatedDateTime": "timestamp",
            "failureReason": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 9.8 `list-metric-attribution-metrics`

Lists metric definitions for a metric attribution.

**Synopsis:**
```bash
aws personalize list-metric-attribution-metrics \
    [--metric-attribution-arn <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--metric-attribution-arn` | No | string | None | ARN of the metric attribution |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "metrics": [
        {
            "eventType": "string",
            "metricName": "string",
            "expression": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 9.9 `update-metric-attribution`

Updates a metric attribution.

**Synopsis:**
```bash
aws personalize update-metric-attribution \
    --metric-attribution-arn <value> \
    [--add-metrics <value>] \
    [--remove-metrics <value>] \
    [--metrics-output-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--metric-attribution-arn` | **Yes** | string | -- | ARN of the metric attribution |
| `--add-metrics` | No | list | None | Metrics to add |
| `--remove-metrics` | No | list(string) | None | Metric names to remove |
| `--metrics-output-config` | No | structure | None | Updated output configuration |

**Output Schema:**
```json
{
    "metricAttributionArn": "string"
}
```

---

### 9.10 `delete-metric-attribution`

Deletes a metric attribution.

**Synopsis:**
```bash
aws personalize delete-metric-attribution \
    --metric-attribution-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--metric-attribution-arn` | **Yes** | string | -- | ARN of the metric attribution to delete |

**Output:** None

---

### 9.11 `describe-recipe`

Describes a recipe (pre-built ML algorithm).

**Synopsis:**
```bash
aws personalize describe-recipe \
    --recipe-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--recipe-arn` | **Yes** | string | -- | ARN of the recipe |

**Output Schema:**
```json
{
    "recipe": {
        "name": "string",
        "recipeArn": "string",
        "algorithmArn": "string",
        "featureTransformationArn": "string",
        "status": "string",
        "description": "string",
        "creationDateTime": "timestamp",
        "recipeType": "string",
        "lastUpdatedDateTime": "timestamp"
    }
}
```

---

### 9.12 `list-recipes`

Lists available recipes. **Paginated operation.**

**Synopsis:**
```bash
aws personalize list-recipes \
    [--recipe-provider <value>] \
    [--domain <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--recipe-provider` | No | string | None | Provider filter: `SERVICE` |
| `--domain` | No | string | None | Domain filter: `ECOMMERCE` or `VIDEO_ON_DEMAND` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call (max 100) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "recipes": [
        {
            "name": "string",
            "recipeArn": "string",
            "status": "string",
            "creationDateTime": "timestamp",
            "lastUpdatedDateTime": "timestamp",
            "domain": "ECOMMERCE|VIDEO_ON_DEMAND"
        }
    ],
    "nextToken": "string"
}
```

---

### 9.13 `describe-algorithm`

Describes an algorithm.

**Synopsis:**
```bash
aws personalize describe-algorithm \
    --algorithm-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--algorithm-arn` | **Yes** | string | -- | ARN of the algorithm |

**Output Schema:**
```json
{
    "algorithm": {
        "name": "string",
        "algorithmArn": "string",
        "algorithmImage": {},
        "defaultHyperParameters": {"string": "string"},
        "defaultHyperParameterRanges": {},
        "defaultResourceConfig": {"string": "string"},
        "trainingInputMode": "string",
        "roleArn": "string",
        "creationDateTime": "timestamp",
        "lastUpdatedDateTime": "timestamp"
    }
}
```

---

### 9.14 `describe-feature-transformation`

Describes a feature transformation.

**Synopsis:**
```bash
aws personalize describe-feature-transformation \
    --feature-transformation-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--feature-transformation-arn` | **Yes** | string | -- | ARN of the feature transformation |

**Output Schema:**
```json
{
    "featureTransformation": {
        "name": "string",
        "featureTransformationArn": "string",
        "defaultParameters": {"string": "string"},
        "creationDateTime": "timestamp",
        "lastUpdatedDateTime": "timestamp",
        "status": "string"
    }
}
```
