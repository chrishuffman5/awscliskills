# API Keys & Licenses

### 5.1 `create-workspace-api-key`

Creates a Grafana API key for the workspace. API keys are used to authenticate HTTP API requests to the Grafana HTTP APIs. Deprecated in favor of service account tokens.

**Synopsis:**
```bash
aws grafana create-workspace-api-key \
    --workspace-id <value> \
    --key-name <value> \
    --key-role <value> \
    --seconds-to-live <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | The workspace ID |
| `--key-name` | **Yes** | string | -- | Name of the API key (1-100 chars) |
| `--key-role` | **Yes** | string | -- | Grafana role: `ADMIN`, `EDITOR`, `VIEWER` |
| `--seconds-to-live` | **Yes** | integer | -- | Key lifetime in seconds (1-2592000, max 30 days) |

**Output Schema:**
```json
{
    "key": "string",
    "keyName": "string",
    "workspaceId": "string"
}
```

---

### 5.2 `delete-workspace-api-key`

Deletes a Grafana API key for the workspace.

**Synopsis:**
```bash
aws grafana delete-workspace-api-key \
    --workspace-id <value> \
    --key-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | The workspace ID |
| `--key-name` | **Yes** | string | -- | The API key name to delete |

**Output Schema:**
```json
{
    "keyName": "string",
    "workspaceId": "string"
}
```

---

### 5.3 `associate-license`

Associates a Grafana Enterprise license with a workspace.

**Synopsis:**
```bash
aws grafana associate-license \
    --workspace-id <value> \
    --license-type <value> \
    [--grafana-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | The workspace ID |
| `--license-type` | **Yes** | string | -- | License type: `ENTERPRISE`, `ENTERPRISE_FREE_TRIAL` |
| `--grafana-token` | No | string | None | Grafana Enterprise license token |

**Output Schema:**
```json
{
    "workspace": {
        "accountAccessType": "string",
        "authentication": {},
        "created": "timestamp",
        "dataSources": [],
        "description": "string",
        "endpoint": "string",
        "freeTrialConsumed": true|false,
        "freeTrialExpiration": "timestamp",
        "grafanaToken": "string",
        "grafanaVersion": "string",
        "id": "string",
        "licenseExpiration": "timestamp",
        "licenseType": "ENTERPRISE|ENTERPRISE_FREE_TRIAL",
        "modified": "timestamp",
        "name": "string",
        "permissionType": "string",
        "status": "string",
        "tags": {}
    }
}
```

---

### 5.4 `disassociate-license`

Removes the Grafana Enterprise license from a workspace.

**Synopsis:**
```bash
aws grafana disassociate-license \
    --workspace-id <value> \
    --license-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | The workspace ID |
| `--license-type` | **Yes** | string | -- | License type: `ENTERPRISE`, `ENTERPRISE_FREE_TRIAL` |

**Output Schema:**
```json
{
    "workspace": {
        "accountAccessType": "string",
        "authentication": {},
        "created": "timestamp",
        "dataSources": [],
        "description": "string",
        "endpoint": "string",
        "freeTrialConsumed": true|false,
        "grafanaVersion": "string",
        "id": "string",
        "modified": "timestamp",
        "name": "string",
        "permissionType": "string",
        "status": "string",
        "tags": {}
    }
}
```
