# Actions

### 11.1 `execute-action`

Executes an action on a target resource (e.g., alarm acknowledgment).

**Synopsis:**
```bash
aws iotsitewise execute-action \
    --target-resource <value> \
    --action-definition-id <value> \
    --action-payload <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--target-resource` | **Yes** | structure | -- | Target resource for the action |
| `--action-definition-id` | **Yes** | string | -- | Action definition ID (UUID) |
| `--action-payload` | **Yes** | structure | -- | Action payload |
| `--client-token` | No | string | Auto | Idempotency token |

**Target Resource Structure:**
```json
{
    "assetId": "string"
}
```

**Action Payload Structure:**
```json
{
    "stringValue": "string"
}
```

**Output Schema:**
```json
{
    "actionId": "string"
}
```

---

### 11.2 `describe-action`

Describes an action that was executed.

**Synopsis:**
```bash
aws iotsitewise describe-action \
    --action-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--action-id` | **Yes** | string | -- | Action ID (UUID) |

**Output Schema:**
```json
{
    "actionId": "string",
    "targetResource": {"assetId": "string"},
    "actionDefinitionId": "string",
    "actionPayload": {"stringValue": "string"},
    "executionTime": "timestamp"
}
```

---

### 11.3 `list-actions`

Lists actions for a target resource. **Paginated operation.**

**Synopsis:**
```bash
aws iotsitewise list-actions \
    --target-resource-type <value> \
    --target-resource-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--target-resource-type` | **Yes** | string | -- | `ASSET` |
| `--target-resource-id` | **Yes** | string | -- | Target resource ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "actionSummaries": [
        {
            "actionId": "string",
            "actionDefinitionId": "string",
            "targetResource": {"assetId": "string"},
            "actionPayload": {"stringValue": "string"}
        }
    ],
    "nextToken": "string"
}
```
