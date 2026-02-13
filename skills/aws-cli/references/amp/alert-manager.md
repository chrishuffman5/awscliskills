# Alert Manager

### 2.1 `create-alert-manager-definition`

Creates an alert manager definition for a workspace.

**Synopsis:**
```bash
aws amp create-alert-manager-definition \
    --workspace-id <value> \
    --data <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | ID of the workspace |
| `--data` | **Yes** | blob | -- | Alert manager definition data (YAML, base64-encoded or `fileb://`) |
| `--client-token` | No | string | auto-generated | Idempotency token |

**Output Schema:**
```json
{
    "status": {
        "statusCode": "CREATING|ACTIVE|UPDATING|CREATION_FAILED|UPDATE_FAILED",
        "statusReason": "string"
    }
}
```

---

### 2.2 `delete-alert-manager-definition`

Deletes the alert manager definition from a workspace.

**Synopsis:**
```bash
aws amp delete-alert-manager-definition \
    --workspace-id <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | ID of the workspace |
| `--client-token` | No | string | auto-generated | Idempotency token |

**Output Schema:**
```json
{}
```

---

### 2.3 `describe-alert-manager-definition`

Describes the alert manager definition for a workspace.

**Synopsis:**
```bash
aws amp describe-alert-manager-definition \
    --workspace-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | ID of the workspace |

**Output Schema:**
```json
{
    "alertManagerDefinition": {
        "createdAt": "timestamp",
        "data": "blob",
        "modifiedAt": "timestamp",
        "status": {
            "statusCode": "CREATING|ACTIVE|UPDATING|CREATION_FAILED|UPDATE_FAILED",
            "statusReason": "string"
        }
    }
}
```

---

### 2.4 `put-alert-manager-definition`

Updates the alert manager definition for a workspace. Replaces the existing definition.

**Synopsis:**
```bash
aws amp put-alert-manager-definition \
    --workspace-id <value> \
    --data <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | ID of the workspace |
| `--data` | **Yes** | blob | -- | New alert manager definition data (YAML, base64-encoded or `fileb://`) |
| `--client-token` | No | string | auto-generated | Idempotency token |

**Output Schema:**
```json
{
    "status": {
        "statusCode": "CREATING|ACTIVE|UPDATING|CREATION_FAILED|UPDATE_FAILED",
        "statusReason": "string"
    }
}
```
