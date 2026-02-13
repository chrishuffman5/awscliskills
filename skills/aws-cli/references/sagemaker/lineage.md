# Lineage

## Actions

### 1. `create-action`

Creates a lineage action (a step in an ML workflow).

```bash
aws sagemaker create-action \
    --action-name <value> \
    --source <value> \
    --action-type <value> \
    [--description <value>] \
    [--status <value>] \
    [--properties <value>] \
    [--metadata-properties <value>] \
    [--tags <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--action-name` | **Yes** | string | -- | Action name (1-120 chars) |
| `--source` | **Yes** | structure | -- | `SourceUri`, `SourceType`, `SourceId` |
| `--action-type` | **Yes** | string | -- | Action type (max 256 chars) |
| `--description` | No | string | -- | Description |
| `--status` | No | string | -- | `Unknown`, `InProgress`, `Completed`, `Failed`, `Stopping`, `Stopped` |
| `--properties` | No | map | -- | Key-value properties (max 30) |
| `--tags` | No | list | -- | Key-value tags |

**Output Schema:**
```json
{
    "ActionArn": "string"
}
```

---

### 2. `describe-action` / `list-actions` / `update-action` / `delete-action`

```bash
aws sagemaker describe-action --action-name <value>
aws sagemaker list-actions [--source-uri <value>] [--action-type <value>] [--created-after <value>] [--created-before <value>] [--sort-by <value>] [--sort-order <value>]
aws sagemaker update-action --action-name <value> [--description <value>] [--status <value>] [--properties <value>] [--properties-to-remove <value>]
aws sagemaker delete-action --action-name <value>
```

---

## Artifacts

### 3. `create-artifact`

Creates a lineage artifact (a data object, model, or dataset).

```bash
aws sagemaker create-artifact \
    --source <value> \
    --artifact-type <value> \
    [--artifact-name <value>] \
    [--properties <value>] \
    [--metadata-properties <value>] \
    [--tags <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source` | **Yes** | structure | -- | `SourceUri`, `SourceTypes` (list of `SourceIdType`/`Value`) |
| `--artifact-type` | **Yes** | string | -- | Artifact type (max 256 chars) |
| `--artifact-name` | No | string | -- | Optional name |
| `--properties` | No | map | -- | Key-value properties |
| `--tags` | No | list | -- | Key-value tags |

**Output Schema:**
```json
{
    "ArtifactArn": "string"
}
```

---

### 4. `describe-artifact` / `list-artifacts` / `update-artifact` / `delete-artifact`

```bash
aws sagemaker describe-artifact --artifact-arn <value>
aws sagemaker list-artifacts [--source-uri <value>] [--artifact-type <value>] [--created-after <value>] [--created-before <value>] [--sort-by <value>] [--sort-order <value>]
aws sagemaker update-artifact --artifact-arn <value> [--artifact-name <value>] [--properties <value>] [--properties-to-remove <value>]
aws sagemaker delete-artifact [--artifact-arn <value>] [--source <value>]
```

---

## Contexts

### 5. `create-context`

Creates a lineage context (a logical grouping, like an experiment or pipeline).

```bash
aws sagemaker create-context \
    --context-name <value> \
    --source <value> \
    --context-type <value> \
    [--description <value>] \
    [--properties <value>] \
    [--tags <value>]
```

**Output Schema:**
```json
{
    "ContextArn": "string"
}
```

---

### 6. `describe-context` / `list-contexts` / `update-context` / `delete-context`

```bash
aws sagemaker describe-context --context-name <value>
aws sagemaker list-contexts [--source-uri <value>] [--context-type <value>] [--created-after <value>] [--created-before <value>] [--sort-by <value>] [--sort-order <value>]
aws sagemaker update-context --context-name <value> [--description <value>] [--properties <value>] [--properties-to-remove <value>]
aws sagemaker delete-context --context-name <value>
```

---

## Associations

### 7. `add-association`

Creates an association between lineage entities.

```bash
aws sagemaker add-association \
    --source-arn <value> \
    --destination-arn <value> \
    [--association-type <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-arn` | **Yes** | string | -- | Source entity ARN |
| `--destination-arn` | **Yes** | string | -- | Destination entity ARN |
| `--association-type` | No | string | -- | `ContributedTo`, `AssociatedWith`, `DerivedFrom`, `Produced`, `SameAs` |

**Output Schema:**
```json
{
    "SourceArn": "string",
    "DestinationArn": "string"
}
```

---

### 8. `list-associations` / `delete-association`

```bash
aws sagemaker list-associations [--source-arn <value>] [--destination-arn <value>] [--source-type <value>] [--destination-type <value>] [--association-type <value>] [--created-after <value>] [--created-before <value>] [--sort-by <value>] [--sort-order <value>]
aws sagemaker delete-association --source-arn <value> --destination-arn <value>
```

---

## Lineage Groups & Query

### 9. `describe-lineage-group` / `list-lineage-groups`

```bash
aws sagemaker describe-lineage-group --lineage-group-name <value>
aws sagemaker list-lineage-groups [--created-after <value>] [--created-before <value>] [--sort-by <value>] [--sort-order <value>]
```

---

### 10. `query-lineage`

Queries the lineage graph for related entities.

```bash
aws sagemaker query-lineage \
    [--start-arns <value>] \
    [--direction <value>] \
    [--include-edges | --no-include-edges] \
    [--filters <value>] \
    [--max-depth <value>] \
    [--max-results <value>] \
    [--next-token <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--start-arns` | No | list | -- | Starting entity ARNs (max 1) |
| `--direction` | No | string | `Both` | `Both`, `Ascendants`, `Descendants` |
| `--include-edges` | No | boolean | false | Include edge details |
| `--filters` | No | structure | -- | Filter by `Types`, `LineageTypes`, `CreatedBefore`, `CreatedAfter`, `ModifiedBefore`, `ModifiedAfter`, `Properties` |
| `--max-depth` | No | integer | 10 | Maximum traversal depth |

**Output Schema:**
```json
{
    "Vertices": [
        {
            "Arn": "string",
            "Type": "string",
            "LineageType": "TrialComponent|Artifact|Context|Action"
        }
    ],
    "Edges": [
        {
            "SourceArn": "string",
            "DestinationArn": "string",
            "AssociationType": "ContributedTo|AssociatedWith|DerivedFrom|Produced|SameAs"
        }
    ],
    "NextToken": "string"
}
```
