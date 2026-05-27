# Search & Tags

## 1. `search`

Searches SageMaker resources matching specified criteria.

**Synopsis:**
```bash
aws sagemaker search \
    --resource <value> \
    [--search-expression <value>] \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--cross-account-filter-option <value>] \
    [--visibility-conditions <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource` | **Yes** | string | -- | Resource type to search |
| `--search-expression` | No | structure | -- | Search filters and boolean logic |
| `--sort-by` | No | string | -- | Property name to sort by |
| `--sort-order` | No | string | `Descending` | `Ascending`, `Descending` |
| `--cross-account-filter-option` | No | string | -- | `SameAccount`, `CrossAccount` |
| `--visibility-conditions` | No | list | -- | Visibility filter conditions |

**Searchable Resource Types:**
`TrainingJob`, `Experiment`, `ExperimentTrial`, `ExperimentTrialComponent`, `Endpoint`, `EndpointConfig`, `Model`, `ModelPackage`, `ModelPackageGroup`, `Pipeline`, `PipelineExecution`, `FeatureGroup`, `FeatureMetadata`, `Image`, `ImageVersion`, `Project`, `HyperParameterTuningJob`, `ModelCard`

**Search Expression:**
```json
{
    "Filters": [
        {
            "Name": "string",
            "Operator": "Equals|NotEquals|GreaterThan|GreaterThanOrEqualTo|LessThan|LessThanOrEqualTo|Contains|Exists|NotExists|In",
            "Value": "string"
        }
    ],
    "NestedFilters": [
        {
            "NestedPropertyName": "string",
            "Filters": [...]
        }
    ],
    "SubExpressions": [...],
    "Operator": "And|Or"
}
```

**Output Schema:**
```json
{
    "Results": [
        {
            "TrainingJob": {...},
            "Experiment": {...},
            "Trial": {...},
            "TrialComponent": {...},
            "Endpoint": {...},
            "ModelPackage": {...},
            "ModelPackageGroup": {...},
            "Pipeline": {...},
            "PipelineExecution": {...},
            "FeatureGroup": {...},
            "FeatureMetadata": {...},
            "Project": {...},
            "HyperParameterTuningJob": {...},
            "ModelCard": {...},
            "Model": {...}
        }
    ],
    "NextToken": "string"
}
```

**Example: Find completed training jobs:**
```bash
aws sagemaker search \
    --resource TrainingJob \
    --search-expression '{
        "Filters": [
            {"Name": "TrainingJobStatus", "Operator": "Equals", "Value": "Completed"}
        ]
    }' \
    --sort-by CreationTime \
    --sort-order Descending \
    --max-items 10
```

**Example: Find models by name pattern:**
```bash
aws sagemaker search \
    --resource Model \
    --search-expression '{
        "Filters": [
            {"Name": "ModelName", "Operator": "Contains", "Value": "xgboost"}
        ]
    }'
```

---

## 2. `get-search-suggestions`

Gets search suggestions for a resource type.

```bash
aws sagemaker get-search-suggestions \
    --resource <value> \
    [--suggestion-query <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource` | **Yes** | string | -- | Resource type |
| `--suggestion-query` | No | structure | -- | `PropertyNameQuery`: `PropertyNameHint` |

**Output Schema:**
```json
{
    "PropertyNameSuggestions": [
        {
            "PropertyName": "string"
        }
    ]
}
```

---

## Tags

### 3. `add-tags`

Adds tags to a SageMaker resource.

```bash
aws sagemaker add-tags \
    --resource-arn <value> \
    --tags <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |
| `--tags` | **Yes** | list | -- | `[{Key, Value}]` tags to add (max 50) |

**Output Schema:**
```json
{
    "Tags": [{"Key": "string", "Value": "string"}]
}
```

---

### 4. `delete-tags`

Removes tags from a SageMaker resource.

```bash
aws sagemaker delete-tags \
    --resource-arn <value> \
    --tag-keys <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |
| `--tag-keys` | **Yes** | list | -- | Tag keys to remove |

**Output:** None

---

### 5. `list-tags`

Lists tags for a SageMaker resource. **Paginated operation.**

```bash
aws sagemaker list-tags \
    --resource-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |

**Output Schema:**
```json
{
    "Tags": [{"Key": "string", "Value": "string"}],
    "NextToken": "string"
}
```

---

### 6. `list-aliases`

Lists aliases for a SageMaker image version.

```bash
aws sagemaker list-aliases \
    --image-name <value> \
    [--alias <value>] \
    [--version <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Output Schema:**
```json
{
    "SageMakerImageVersionAliases": ["string"],
    "NextToken": "string"
}
```
