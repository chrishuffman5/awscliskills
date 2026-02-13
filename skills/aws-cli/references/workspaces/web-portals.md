# Web Portals

> Commands use `aws workspaces-web` CLI prefix.

### 8.1 `create-portal`

Creates a web portal for WorkSpaces Web.

**Synopsis:**
```bash
aws workspaces-web create-portal \
    [--display-name <value>] \
    [--authentication-type <value>] \
    [--additional-encryption-context <value>] \
    [--customer-managed-key <value>] \
    [--tags <value>] \
    [--instance-type <value>] \
    [--max-concurrent-sessions <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--display-name` | No | string | None | The name of the portal (1-64 chars) |
| `--authentication-type` | No | string | `Standard` | Authentication type: `Standard`, `IAM_Identity_Center` |
| `--additional-encryption-context` | No | map | None | Additional encryption context for the portal |
| `--customer-managed-key` | No | string | None | KMS key ARN for encryption |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |
| `--instance-type` | No | string | None | Instance type for the portal (e.g., `standard.regular`, `standard.large`, `standard.xlarge`) |
| `--max-concurrent-sessions` | No | integer | None | Maximum concurrent sessions |

**Output Schema:**
```json
{
    "portalArn": "string",
    "portalEndpoint": "string"
}
```

---

### 8.2 `delete-portal`

Deletes a web portal.

**Synopsis:**
```bash
aws workspaces-web delete-portal \
    --portal-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--portal-arn` | **Yes** | string | -- | The ARN of the portal to delete |

**Output Schema:**
```json
{}
```

---

### 8.3 `get-portal`

Gets a web portal.

**Synopsis:**
```bash
aws workspaces-web get-portal \
    --portal-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--portal-arn` | **Yes** | string | -- | The ARN of the portal |

**Output Schema:**
```json
{
    "portal": {
        "portalArn": "string",
        "rendererType": "AppStream",
        "browserType": "Chrome",
        "portalStatus": "Incomplete|Pending|Active",
        "portalEndpoint": "string",
        "displayName": "string",
        "creationDate": "timestamp",
        "browserSettingsArn": "string",
        "userSettingsArn": "string",
        "networkSettingsArn": "string",
        "trustStoreArn": "string",
        "userAccessLoggingSettingsArn": "string",
        "authenticationType": "Standard|IAM_Identity_Center",
        "ipAccessSettingsArn": "string",
        "customerManagedKey": "string",
        "additionalEncryptionContext": {
            "string": "string"
        },
        "instanceType": "string",
        "maxConcurrentSessions": "integer"
    }
}
```

---

### 8.4 `list-portals`

Lists web portals. **Paginated operation.**

**Synopsis:**
```bash
aws workspaces-web list-portals \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "portals": [
        {
            "portalArn": "string",
            "rendererType": "AppStream",
            "browserType": "Chrome",
            "portalStatus": "Incomplete|Pending|Active",
            "portalEndpoint": "string",
            "displayName": "string",
            "creationDate": "timestamp",
            "browserSettingsArn": "string",
            "userSettingsArn": "string",
            "networkSettingsArn": "string",
            "trustStoreArn": "string",
            "authenticationType": "string",
            "instanceType": "string",
            "maxConcurrentSessions": "integer"
        }
    ],
    "nextToken": "string"
}
```

---

### 8.5 `update-portal`

Updates a web portal.

**Synopsis:**
```bash
aws workspaces-web update-portal \
    --portal-arn <value> \
    [--display-name <value>] \
    [--authentication-type <value>] \
    [--instance-type <value>] \
    [--max-concurrent-sessions <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--portal-arn` | **Yes** | string | -- | The ARN of the portal to update |
| `--display-name` | No | string | None | New display name |
| `--authentication-type` | No | string | None | New authentication type: `Standard`, `IAM_Identity_Center` |
| `--instance-type` | No | string | None | New instance type |
| `--max-concurrent-sessions` | No | integer | None | New max concurrent sessions |

**Output Schema:**
```json
{
    "portal": {
        "portalArn": "string",
        "rendererType": "AppStream",
        "browserType": "Chrome",
        "portalStatus": "Incomplete|Pending|Active",
        "portalEndpoint": "string",
        "displayName": "string",
        "creationDate": "timestamp",
        "browserSettingsArn": "string",
        "userSettingsArn": "string",
        "networkSettingsArn": "string",
        "trustStoreArn": "string",
        "authenticationType": "string",
        "instanceType": "string",
        "maxConcurrentSessions": "integer"
    }
}
```
