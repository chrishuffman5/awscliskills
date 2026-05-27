# Operations

### 8.1 `stop-resource`

Stops an in-progress resource creation job. Applicable to dataset import jobs, predictor creation, forecast creation, and other resource types.

**Synopsis:**
```bash
aws forecast stop-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN (max 256 chars) |

**Output:** None

**Notes:**
- Only stops resources with `CREATE_IN_PROGRESS` status
- After stopping, resource status becomes `CREATE_STOPPED`
- Cannot restart a stopped resource; must create a new one

---

### 8.2 `resume-resource`

Resumes a stopped resource.

**Synopsis:**
```bash
aws forecast resume-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN (max 256 chars) |

**Output:** None

---

### 8.3 `delete-resource-tree`

Deletes a resource and all its child resources. For example, deleting a dataset group also deletes all predictors, forecasts, and exports derived from it.

**Synopsis:**
```bash
aws forecast delete-resource-tree \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Root resource ARN (max 256 chars) |

**Output:** None

**Notes:**
- Cascade deletes all child resources
- Cannot be undone
- Use for cleanup when you want to remove an entire resource hierarchy
