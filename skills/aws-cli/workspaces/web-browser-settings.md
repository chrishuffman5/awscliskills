# Web Browser Settings

> Commands use `aws workspaces-web` CLI prefix.

### 9.1 `create-browser-settings`

Creates a browser settings resource that defines browser policy for a web portal.

**Synopsis:**
```bash
aws workspaces-web create-browser-settings \
    --browser-policy <value> \
    [--additional-encryption-context <value>] \
    [--customer-managed-key <value>] \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--browser-policy` | **Yes** | string | -- | Browser policy JSON document (Chrome Enterprise policy format) |
| `--additional-encryption-context` | No | map | None | Additional encryption context |
| `--customer-managed-key` | No | string | None | KMS key ARN for encryption |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "browserSettingsArn": "string"
}
```

---

### 9.2 `delete-browser-settings`

Deletes browser settings.

**Synopsis:**
```bash
aws workspaces-web delete-browser-settings \
    --browser-settings-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--browser-settings-arn` | **Yes** | string | -- | The ARN of the browser settings to delete |

**Output Schema:**
```json
{}
```

---

### 9.3 `get-browser-settings`

Gets browser settings.

**Synopsis:**
```bash
aws workspaces-web get-browser-settings \
    --browser-settings-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--browser-settings-arn` | **Yes** | string | -- | The ARN of the browser settings |

**Output Schema:**
```json
{
    "browserSettings": {
        "browserSettingsArn": "string",
        "browserPolicy": "string",
        "associatedPortalArns": ["string"],
        "customerManagedKey": "string",
        "additionalEncryptionContext": {
            "string": "string"
        }
    }
}
```

---

### 9.4 `list-browser-settings`

Lists browser settings. **Paginated operation.**

**Synopsis:**
```bash
aws workspaces-web list-browser-settings \
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
    "browserSettings": [
        {
            "browserSettingsArn": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 9.5 `update-browser-settings`

Updates browser settings.

**Synopsis:**
```bash
aws workspaces-web update-browser-settings \
    --browser-settings-arn <value> \
    [--browser-policy <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--browser-settings-arn` | **Yes** | string | -- | The ARN of the browser settings to update |
| `--browser-policy` | No | string | None | Updated browser policy JSON document |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "browserSettings": {
        "browserSettingsArn": "string",
        "browserPolicy": "string",
        "associatedPortalArns": ["string"],
        "customerManagedKey": "string",
        "additionalEncryptionContext": {
            "string": "string"
        }
    }
}
```

---

### 9.6 `associate-browser-settings`

Associates browser settings with a web portal.

**Synopsis:**
```bash
aws workspaces-web associate-browser-settings \
    --portal-arn <value> \
    --browser-settings-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--portal-arn` | **Yes** | string | -- | The ARN of the portal |
| `--browser-settings-arn` | **Yes** | string | -- | The ARN of the browser settings |

**Output Schema:**
```json
{
    "portalArn": "string",
    "browserSettingsArn": "string"
}
```

---

### 9.7 `disassociate-browser-settings`

Disassociates browser settings from a web portal.

**Synopsis:**
```bash
aws workspaces-web disassociate-browser-settings \
    --portal-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--portal-arn` | **Yes** | string | -- | The ARN of the portal to disassociate from |

**Output Schema:**
```json
{}
```
