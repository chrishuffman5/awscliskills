# Actions

Actions are post-launch automation steps (SSM documents) that run on migrated instances.

### 7.1 `put-source-server-action`

Adds or updates an action for a specific source server.

**Synopsis:**
```bash
aws mgn put-source-server-action \
    --source-server-id <value> \
    --action-name <value> \
    --action-id <value> \
    --document-identifier <value> \
    --order <value> \
    [--account-id <value>] \
    [--document-version <value>] \
    [--active | --no-active] \
    [--must-succeed-for-cutover | --no-must-succeed-for-cutover] \
    [--timeout-seconds <value>] \
    [--category <value>] \
    [--description <value>] \
    [--parameters <value>] \
    [--external-parameters <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-server-id` | **Yes** | string | -- | Source server ID |
| `--action-name` | **Yes** | string | -- | Action name (1-256 chars) |
| `--action-id` | **Yes** | string | -- | Action ID (1-64 chars) |
| `--document-identifier` | **Yes** | string | -- | SSM document name or ARN |
| `--order` | **Yes** | integer | -- | Execution order (1001-10000) |
| `--account-id` | No | string | None | Account ID |
| `--document-version` | No | string | None | SSM document version |
| `--active` | No | boolean | None | Whether action is active |
| `--must-succeed-for-cutover` | No | boolean | None | Must succeed for cutover |
| `--timeout-seconds` | No | integer | None | Timeout (1-86400 seconds) |
| `--category` | No | string | None | `DISASTER_RECOVERY`, `OPERATING_SYSTEM`, `LICENSE_AND_SUBSCRIPTION`, `VALIDATION`, `OBSERVABILITY`, `REFACTORING`, `SECURITY`, `NETWORKING`, `CONFIGURATION`, `BACKUP`, `OTHER` |
| `--description` | No | string | None | Description (max 256 chars) |
| `--parameters` | No | map | None | SSM document parameters |
| `--external-parameters` | No | map | None | External parameters |

**Output Schema:**
```json
{
    "actionID": "string",
    "actionName": "string",
    "documentIdentifier": "string",
    "documentVersion": "string",
    "order": "integer",
    "active": true|false,
    "mustSucceedForCutover": true|false,
    "timeoutSeconds": "integer",
    "category": "string",
    "description": "string",
    "parameters": {},
    "externalParameters": {}
}
```

---

### 7.2 `remove-source-server-action`

Removes an action from a source server.

**Synopsis:**
```bash
aws mgn remove-source-server-action \
    --source-server-id <value> \
    --action-id <value> \
    [--account-id <value>]
```

**Output:** None

---

### 7.3 `list-source-server-actions`

Lists actions for a source server. **Paginated.**

**Synopsis:**
```bash
aws mgn list-source-server-actions \
    --source-server-id <value> \
    [--account-id <value>] \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Output Schema:**
```json
{
    "items": [{"actionID": "string", "...": "..."}],
    "nextToken": "string"
}
```

---

### 7.4 `put-template-action`

Adds or updates an action on a launch configuration template.

**Synopsis:**
```bash
aws mgn put-template-action \
    --launch-configuration-template-id <value> \
    --action-name <value> \
    --action-id <value> \
    --document-identifier <value> \
    --order <value> \
    [--document-version <value>] \
    [--active | --no-active] \
    [--must-succeed-for-cutover | --no-must-succeed-for-cutover] \
    [--timeout-seconds <value>] \
    [--category <value>] \
    [--description <value>] \
    [--operating-system <value>] \
    [--parameters <value>] \
    [--external-parameters <value>]
```

**Parameters:** Same as put-source-server-action but uses `--launch-configuration-template-id` instead of `--source-server-id`, plus optional `--operating-system` filter.

**Output Schema:** Same as put-source-server-action.

---

### 7.5 `remove-template-action`

Removes an action from a template.

```bash
aws mgn remove-template-action --launch-configuration-template-id <value> --action-id <value>
```

**Output:** None

---

### 7.6 `list-template-actions`

Lists actions for a template. **Paginated.**

```bash
aws mgn list-template-actions --launch-configuration-template-id <value> [--filters <value>]
```

**Output Schema:**
```json
{
    "items": [{"actionID": "string", "...": "..."}],
    "nextToken": "string"
}
```
