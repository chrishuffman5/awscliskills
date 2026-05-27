# Deployment Strategies

### 4.1 `create-deployment-strategy`

Creates a deployment strategy that defines important criteria for rolling out a configuration to the designated targets, including the overall duration, growth factor, and the type of growth.

**Synopsis:**
```bash
aws appconfig create-deployment-strategy \
    --name <value> \
    --deployment-duration-in-minutes <value> \
    --growth-factor <value> \
    [--description <value>] \
    [--final-bake-time-in-minutes <value>] \
    [--growth-type <value>] \
    [--replicate-to <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Strategy name (1-64 chars) |
| `--deployment-duration-in-minutes` | **Yes** | integer | -- | Total deployment duration (0-1440 minutes) |
| `--growth-factor` | **Yes** | float | -- | Percentage of targets per interval (1.0-100.0) |
| `--description` | No | string | None | Description (0-1024 chars) |
| `--final-bake-time-in-minutes` | No | integer | 0 | Monitoring time after 100% deployment (0-1440 minutes) |
| `--growth-type` | No | string | LINEAR | `LINEAR` or `EXPONENTIAL` |
| `--replicate-to` | No | string | None | `NONE` or `SSM_DOCUMENT` |
| `--tags` | No | map | None | Tags (max 50) |

**Output Schema:**
```json
{
    "Id": "string",
    "Name": "string",
    "Description": "string",
    "DeploymentDurationInMinutes": "integer",
    "GrowthType": "LINEAR|EXPONENTIAL",
    "GrowthFactor": "float",
    "FinalBakeTimeInMinutes": "integer",
    "ReplicateTo": "NONE|SSM_DOCUMENT"
}
```

---

### 4.2 `get-deployment-strategy`

Retrieves a deployment strategy.

**Synopsis:**
```bash
aws appconfig get-deployment-strategy \
    --deployment-strategy-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--deployment-strategy-id` | **Yes** | string | -- | Deployment strategy ID or predefined strategy ID |

**Output Schema:**
```json
{
    "Id": "string",
    "Name": "string",
    "Description": "string",
    "DeploymentDurationInMinutes": "integer",
    "GrowthType": "LINEAR|EXPONENTIAL",
    "GrowthFactor": "float",
    "FinalBakeTimeInMinutes": "integer",
    "ReplicateTo": "NONE|SSM_DOCUMENT"
}
```

---

### 4.3 `list-deployment-strategies`

Lists deployment strategies. **Paginated operation.**

**Synopsis:**
```bash
aws appconfig list-deployment-strategies \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--max-results` | No | integer | None | Max results per page (1-50) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "Items": [
        {
            "Id": "string",
            "Name": "string",
            "Description": "string",
            "DeploymentDurationInMinutes": "integer",
            "GrowthType": "LINEAR|EXPONENTIAL",
            "GrowthFactor": "float",
            "FinalBakeTimeInMinutes": "integer",
            "ReplicateTo": "NONE|SSM_DOCUMENT"
        }
    ],
    "NextToken": "string"
}
```

---

### 4.4 `update-deployment-strategy`

Updates a deployment strategy.

**Synopsis:**
```bash
aws appconfig update-deployment-strategy \
    --deployment-strategy-id <value> \
    [--description <value>] \
    [--deployment-duration-in-minutes <value>] \
    [--final-bake-time-in-minutes <value>] \
    [--growth-factor <value>] \
    [--growth-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--deployment-strategy-id` | **Yes** | string | -- | Deployment strategy ID |
| `--description` | No | string | None | Updated description (0-1024 chars) |
| `--deployment-duration-in-minutes` | No | integer | None | Updated deployment duration (0-1440 minutes) |
| `--final-bake-time-in-minutes` | No | integer | None | Updated bake time (0-1440 minutes) |
| `--growth-factor` | No | float | None | Updated growth factor (1.0-100.0) |
| `--growth-type` | No | string | None | `LINEAR` or `EXPONENTIAL` |

**Output Schema:**
```json
{
    "Id": "string",
    "Name": "string",
    "Description": "string",
    "DeploymentDurationInMinutes": "integer",
    "GrowthType": "LINEAR|EXPONENTIAL",
    "GrowthFactor": "float",
    "FinalBakeTimeInMinutes": "integer",
    "ReplicateTo": "NONE|SSM_DOCUMENT"
}
```

---

### 4.5 `delete-deployment-strategy`

Deletes a deployment strategy.

**Synopsis:**
```bash
aws appconfig delete-deployment-strategy \
    --deployment-strategy-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--deployment-strategy-id` | **Yes** | string | -- | Deployment strategy ID |

**Output:** None
