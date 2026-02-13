# Blueprints

### 10.1 `create-blueprint`

Creates a blueprint.

**Synopsis:**
```bash
aws glue create-blueprint \
    --name <value> \
    --blueprint-location <value> \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Blueprint name |
| `--blueprint-location` | **Yes** | string | -- | S3 path to the blueprint ZIP |
| `--description` | No | string | -- | Description |
| `--tags` | No | map | -- | Tags as JSON |

**Output Schema:**
```json
{
    "Name": "string"
}
```

---

### 10.2 `delete-blueprint`

Deletes a blueprint.

**Synopsis:**
```bash
aws glue delete-blueprint \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Blueprint name |

**Output Schema:**
```json
{
    "Name": "string"
}
```

---

### 10.3 `get-blueprint`

Retrieves a blueprint definition.

**Synopsis:**
```bash
aws glue get-blueprint \
    --name <value> \
    [--include-blueprint | --no-include-blueprint] \
    [--include-parameter-spec | --no-include-parameter-spec] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Blueprint name |
| `--include-blueprint` | No | boolean | false | Include blueprint body |
| `--include-parameter-spec` | No | boolean | false | Include parameter spec |

**Output Schema:**
```json
{
    "Blueprint": {
        "Name": "string",
        "Description": "string",
        "CreatedOn": "timestamp",
        "LastModifiedOn": "timestamp",
        "ParameterSpec": "string",
        "BlueprintLocation": "string",
        "BlueprintServiceLocation": "string",
        "Status": "CREATING|ACTIVE|UPDATING|FAILED",
        "ErrorMessage": "string",
        "LastActiveDefinition": {
            "Description": "string",
            "LastModifiedOn": "timestamp",
            "ParameterSpec": "string",
            "BlueprintLocation": "string",
            "BlueprintServiceLocation": "string"
        }
    }
}
```

---

### 10.4 `get-blueprint-run`

Retrieves a specific blueprint run.

**Synopsis:**
```bash
aws glue get-blueprint-run \
    --blueprint-name <value> \
    --run-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--blueprint-name` | **Yes** | string | -- | Blueprint name |
| `--run-id` | **Yes** | string | -- | Blueprint run ID |

**Output Schema:**
```json
{
    "BlueprintRun": {
        "BlueprintName": "string",
        "RunId": "string",
        "WorkflowName": "string",
        "State": "RUNNING|SUCCEEDED|FAILED|ROLLING_BACK",
        "StartedOn": "timestamp",
        "CompletedOn": "timestamp",
        "ErrorMessage": "string",
        "RollbackErrorMessage": "string",
        "Parameters": "string",
        "RoleArn": "string"
    }
}
```

---

### 10.5 `get-blueprint-runs`

Lists blueprint runs. **Paginated operation.**

**Synopsis:**
```bash
aws glue get-blueprint-runs \
    --blueprint-name <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--blueprint-name` | **Yes** | string | -- | Blueprint name |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "BlueprintRuns": ["<BlueprintRun structure>"],
    "NextToken": "string"
}
```

---

### 10.6 `list-blueprints`

Lists blueprint names. **Paginated operation.**

**Synopsis:**
```bash
aws glue list-blueprints \
    [--tags <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--tags` | No | map | -- | Filter by tags |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "Blueprints": ["string"],
    "NextToken": "string"
}
```

---

### 10.7 `start-blueprint-run`

Starts a blueprint run (creates a workflow from the blueprint).

**Synopsis:**
```bash
aws glue start-blueprint-run \
    --blueprint-name <value> \
    --role-arn <value> \
    [--parameters <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--blueprint-name` | **Yes** | string | -- | Blueprint name |
| `--role-arn` | **Yes** | string | -- | IAM role ARN |
| `--parameters` | No | string | -- | Blueprint parameters (JSON string) |

**Output Schema:**
```json
{
    "RunId": "string"
}
```

---

### 10.8 `update-blueprint`

Updates a blueprint.

**Synopsis:**
```bash
aws glue update-blueprint \
    --name <value> \
    --blueprint-location <value> \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Blueprint name |
| `--blueprint-location` | **Yes** | string | -- | Updated S3 path |
| `--description` | No | string | -- | Updated description |

**Output Schema:**
```json
{
    "Name": "string"
}
```

---

### 10.9 `batch-get-blueprints`

Returns detailed information for a list of blueprints.

**Synopsis:**
```bash
aws glue batch-get-blueprints \
    --names <value> \
    [--include-blueprint | --no-include-blueprint] \
    [--include-parameter-spec | --no-include-parameter-spec] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--names` | **Yes** | list(string) | -- | Blueprint names |
| `--include-blueprint` | No | boolean | false | Include blueprint body |
| `--include-parameter-spec` | No | boolean | false | Include parameter spec |

**Output Schema:**
```json
{
    "Blueprints": ["<Blueprint structure>"],
    "MissingBlueprints": ["string"]
}
```
