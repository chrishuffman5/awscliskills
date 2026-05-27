# Service Accounts

### 4.1 `create-workspace-service-account`

Creates a service account for the workspace. Service accounts are used for automated access to Grafana HTTP APIs.

**Synopsis:**
```bash
aws grafana create-workspace-service-account \
    --workspace-id <value> \
    --name <value> \
    --grafana-role <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | The workspace ID |
| `--name` | **Yes** | string | -- | Name of the service account (1-128 chars) |
| `--grafana-role` | **Yes** | string | -- | Grafana role: `ADMIN`, `EDITOR`, `VIEWER` |

**Output Schema:**
```json
{
    "id": "string",
    "name": "string",
    "grafanaRole": "ADMIN|EDITOR|VIEWER",
    "workspaceId": "string"
}
```

---

### 4.2 `delete-workspace-service-account`

Deletes a workspace service account. This also deletes all tokens associated with the service account.

**Synopsis:**
```bash
aws grafana delete-workspace-service-account \
    --workspace-id <value> \
    --service-account-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | The workspace ID |
| `--service-account-id` | **Yes** | string | -- | The service account ID to delete |

**Output Schema:**
```json
{
    "serviceAccountId": "string",
    "workspaceId": "string"
}
```

---

### 4.3 `list-workspace-service-accounts`

Returns a list of service accounts for a workspace. **Paginated operation.**

**Synopsis:**
```bash
aws grafana list-workspace-service-accounts \
    --workspace-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | The workspace ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "serviceAccounts": [
        {
            "id": "string",
            "name": "string",
            "grafanaRole": "ADMIN|EDITOR|VIEWER",
            "isDisabled": "string"
        }
    ],
    "nextToken": "string",
    "workspaceId": "string"
}
```

---

### 4.4 `create-workspace-service-account-token`

Creates a token for a workspace service account. The token is used to authenticate API requests.

**Synopsis:**
```bash
aws grafana create-workspace-service-account-token \
    --workspace-id <value> \
    --service-account-id <value> \
    --name <value> \
    --seconds-to-live <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | The workspace ID |
| `--service-account-id` | **Yes** | string | -- | The service account ID |
| `--name` | **Yes** | string | -- | Name of the token (1-128 chars) |
| `--seconds-to-live` | **Yes** | integer | -- | Token lifetime in seconds (1-2592000, max 30 days) |

**Output Schema:**
```json
{
    "serviceAccountToken": {
        "id": "string",
        "name": "string",
        "key": "string"
    },
    "serviceAccountId": "string",
    "workspaceId": "string"
}
```

---

### 4.5 `delete-workspace-service-account-token`

Deletes a service account token.

**Synopsis:**
```bash
aws grafana delete-workspace-service-account-token \
    --workspace-id <value> \
    --service-account-id <value> \
    --token-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | The workspace ID |
| `--service-account-id` | **Yes** | string | -- | The service account ID |
| `--token-id` | **Yes** | string | -- | The token ID to delete |

**Output Schema:**
```json
{
    "serviceAccountId": "string",
    "tokenId": "string",
    "workspaceId": "string"
}
```

---

### 4.6 `list-workspace-service-account-tokens`

Returns a list of tokens for a workspace service account. **Paginated operation.**

**Synopsis:**
```bash
aws grafana list-workspace-service-account-tokens \
    --workspace-id <value> \
    --service-account-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | The workspace ID |
| `--service-account-id` | **Yes** | string | -- | The service account ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "serviceAccountTokens": [
        {
            "id": "string",
            "name": "string",
            "createdAt": "timestamp",
            "expiresAt": "timestamp",
            "lastUsedAt": "timestamp"
        }
    ],
    "nextToken": "string",
    "serviceAccountId": "string",
    "workspaceId": "string"
}
```
