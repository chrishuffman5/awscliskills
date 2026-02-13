# Frameworks

### 8.1 `create-framework`

Creates a compliance framework with controls to evaluate backup practices.

**Synopsis:**
```bash
aws backup create-framework \
    --framework-name <value> \
    --framework-controls <value> \
    [--framework-description <value>] \
    [--idempotency-token <value>] \
    [--framework-tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--framework-name` | **Yes** | string | -- | Framework name (1-256 chars, `[a-zA-Z][_a-zA-Z0-9]*`) |
| `--framework-controls` | **Yes** | list | -- | List of framework controls |
| `--framework-description` | No | string | None | Description (0-1024 chars) |
| `--idempotency-token` | No | string | None | Idempotency token |
| `--framework-tags` | No | map | None | Tags |

**Framework Controls Structure:**
```json
[
    {
        "ControlName": "string",
        "ControlInputParameters": [
            {
                "ParameterName": "string",
                "ParameterValue": "string"
            }
        ],
        "ControlScope": {
            "ComplianceResourceIds": ["string"],
            "ComplianceResourceTypes": ["string"],
            "Tags": {"string": "string"}
        }
    }
]
```

**Output Schema:**
```json
{
    "FrameworkName": "string",
    "FrameworkArn": "string"
}
```

---

### 8.2 `update-framework`

Updates an existing framework.

**Synopsis:**
```bash
aws backup update-framework \
    --framework-name <value> \
    [--framework-description <value>] \
    [--framework-controls <value>] \
    [--idempotency-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--framework-name` | **Yes** | string | -- | Framework name |
| `--framework-description` | No | string | None | Updated description |
| `--framework-controls` | No | list | None | Updated controls |

**Output Schema:**
```json
{
    "FrameworkName": "string",
    "FrameworkArn": "string",
    "CreationTime": "timestamp"
}
```

---

### 8.3 `describe-framework`

Returns details of a framework.

**Synopsis:**
```bash
aws backup describe-framework \
    --framework-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--framework-name` | **Yes** | string | -- | Framework name |

**Output Schema:**
```json
{
    "FrameworkName": "string",
    "FrameworkArn": "string",
    "FrameworkDescription": "string",
    "FrameworkControls": [],
    "CreationTime": "timestamp",
    "DeploymentStatus": "CREATE_IN_PROGRESS|UPDATE_IN_PROGRESS|DELETE_IN_PROGRESS|COMPLETED|FAILED",
    "FrameworkStatus": "ACTIVE|PARTIALLY_ACTIVE|INACTIVE|UNAVAILABLE",
    "IdempotencyToken": "string"
}
```

---

### 8.4 `list-frameworks`

Lists all frameworks. **Paginated operation.**

**Synopsis:**
```bash
aws backup list-frameworks \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Output Schema:**
```json
{
    "Frameworks": [
        {
            "FrameworkName": "string",
            "FrameworkArn": "string",
            "FrameworkDescription": "string",
            "NumberOfControls": "integer",
            "CreationTime": "timestamp",
            "DeploymentStatus": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 8.5 `delete-framework`

Deletes a framework.

**Synopsis:**
```bash
aws backup delete-framework \
    --framework-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--framework-name` | **Yes** | string | -- | Framework name |

**Output:** None
