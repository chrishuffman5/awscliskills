# Inference Profiles

### `create-inference-profile`

Creates an application inference profile to track metrics and costs separately for a model. The inference profile copies the configuration from a foundation model or system-defined inference profile.

**Synopsis:**
```bash
aws bedrock create-inference-profile \
    --inference-profile-name <value> \
    --model-source <value> \
    [--description <value>] \
    [--client-request-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--inference-profile-name` | **Yes** | string | -- | Name for the profile (1-64 chars). Pattern: `([0-9a-zA-Z][ _-]?)+` |
| `--model-source` | **Yes** | structure | -- | Source model or profile. Structure: `copyFrom=<ARN>` |
| `--description` | No | string | None | Description (1-200 chars) |
| `--client-request-token` | No | string | None | Idempotency token (1-256 chars) |
| `--tags` | No | list | None | Tags (max 200) |

**Model Source Structure:**
```json
{
    "copyFrom": "arn:aws:bedrock:us-east-1::foundation-model/anthropic.claude-3-sonnet-20240229-v1:0"
}
```

**Output Schema:**
```json
{
    "inferenceProfileArn": "string",
    "status": "ACTIVE"
}
```

---

### `get-inference-profile`

Gets details of an inference profile.

**Synopsis:**
```bash
aws bedrock get-inference-profile \
    --inference-profile-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--inference-profile-identifier` | **Yes** | string | -- | Profile ID or ARN |

**Output Schema:**
```json
{
    "inferenceProfileName": "string",
    "inferenceProfileArn": "string",
    "inferenceProfileId": "string",
    "description": "string",
    "type": "SYSTEM_DEFINED|APPLICATION",
    "status": "ACTIVE",
    "models": [
        {
            "modelArn": "string"
        }
    ],
    "createdAt": "timestamp",
    "updatedAt": "timestamp"
}
```

---

### `list-inference-profiles`

Lists inference profiles in the account. **Paginated operation.**

**Synopsis:**
```bash
aws bedrock list-inference-profiles \
    [--type-equals <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--type-equals` | No | string | None | Filter by type: `SYSTEM_DEFINED`, `APPLICATION` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "inferenceProfileSummaries": [
        {
            "inferenceProfileName": "string",
            "inferenceProfileArn": "string",
            "inferenceProfileId": "string",
            "description": "string",
            "type": "SYSTEM_DEFINED|APPLICATION",
            "status": "ACTIVE",
            "models": [{"modelArn": "string"}],
            "createdAt": "timestamp",
            "updatedAt": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### `delete-inference-profile`

Deletes an application inference profile.

**Synopsis:**
```bash
aws bedrock delete-inference-profile \
    --inference-profile-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--inference-profile-identifier` | **Yes** | string | -- | Profile ID or ARN |

**Output:** None (HTTP 200 on success)

---

### `create-prompt-router`

Creates a prompt router to route requests to different models based on prompt characteristics.

**Synopsis:**
```bash
aws bedrock create-prompt-router \
    --prompt-router-name <value> \
    --routing-criteria <value> \
    --models <value> \
    --fallback-model <value> \
    [--description <value>] \
    [--tags <value>] \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--prompt-router-name` | **Yes** | string | -- | Name for the prompt router |
| `--routing-criteria` | **Yes** | structure | -- | Criteria for routing decisions |
| `--models` | **Yes** | list | -- | List of models to route between |
| `--fallback-model` | **Yes** | structure | -- | Default model when no criteria match |
| `--description` | No | string | None | Description |
| `--tags` | No | list | None | Tags (max 200) |
| `--client-request-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "promptRouterArn": "string"
}
```

---

### `get-prompt-router`

Gets details of a prompt router.

**Synopsis:**
```bash
aws bedrock get-prompt-router \
    --prompt-router-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--prompt-router-arn` | **Yes** | string | -- | Prompt router ARN |

**Output Schema:**
```json
{
    "promptRouterName": "string",
    "promptRouterArn": "string",
    "description": "string",
    "routingCriteria": {
        "responseQualityDifference": "double"
    },
    "models": [
        {
            "modelArn": "string"
        }
    ],
    "fallbackModel": {
        "modelArn": "string"
    },
    "status": "AVAILABLE",
    "type": "custom|default",
    "createdAt": "timestamp",
    "updatedAt": "timestamp"
}
```

---

### `list-prompt-routers`

Lists prompt routers. **Paginated operation.**

**Synopsis:**
```bash
aws bedrock list-prompt-routers \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Output Schema:**
```json
{
    "promptRouterSummaries": [
        {
            "promptRouterName": "string",
            "promptRouterArn": "string",
            "description": "string",
            "status": "AVAILABLE",
            "type": "custom|default",
            "models": [{"modelArn": "string"}],
            "fallbackModel": {"modelArn": "string"},
            "createdAt": "timestamp",
            "updatedAt": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### `delete-prompt-router`

Deletes a prompt router.

**Synopsis:**
```bash
aws bedrock delete-prompt-router \
    --prompt-router-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--prompt-router-arn` | **Yes** | string | -- | Prompt router ARN |

**Output:** None (HTTP 200 on success)
