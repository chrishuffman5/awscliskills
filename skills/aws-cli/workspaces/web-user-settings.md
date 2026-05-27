# Web User Settings

> Commands use `aws workspaces-web` CLI prefix.

### 11.1 `create-user-settings`

Creates a user settings resource that defines user experience controls for a web portal.

**Synopsis:**
```bash
aws workspaces-web create-user-settings \
    --copy-allowed <value> \
    --paste-allowed <value> \
    --download-allowed <value> \
    --upload-allowed <value> \
    --print-allowed <value> \
    [--disconnect-timeout-in-minutes <value>] \
    [--idle-disconnect-timeout-in-minutes <value>] \
    [--deep-link-allowed <value>] \
    [--cookie-synchronization-configuration <value>] \
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
| `--copy-allowed` | **Yes** | string | -- | Allow clipboard copy: `Disabled`, `Enabled` |
| `--paste-allowed` | **Yes** | string | -- | Allow clipboard paste: `Disabled`, `Enabled` |
| `--download-allowed` | **Yes** | string | -- | Allow file download: `Disabled`, `Enabled` |
| `--upload-allowed` | **Yes** | string | -- | Allow file upload: `Disabled`, `Enabled` |
| `--print-allowed` | **Yes** | string | -- | Allow printing: `Disabled`, `Enabled` |
| `--disconnect-timeout-in-minutes` | No | integer | None | Disconnect timeout (1-600 minutes) |
| `--idle-disconnect-timeout-in-minutes` | No | integer | None | Idle disconnect timeout (0-60 minutes) |
| `--deep-link-allowed` | No | string | None | Allow deep links: `Disabled`, `Enabled` |
| `--cookie-synchronization-configuration` | No | structure | None | Cookie sync configuration |
| `--additional-encryption-context` | No | map | None | Additional encryption context |
| `--customer-managed-key` | No | string | None | KMS key ARN for encryption |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |
| `--client-token` | No | string | None | Idempotency token |

**Cookie Synchronization Configuration Structure:**
```json
{
    "allowlist": [
        {
            "domain": "string",
            "name": "string",
            "path": "string"
        }
    ],
    "blocklist": [
        {
            "domain": "string",
            "name": "string",
            "path": "string"
        }
    ]
}
```

**Output Schema:**
```json
{
    "userSettingsArn": "string"
}
```

---

### 11.2 `delete-user-settings`

Deletes user settings.

**Synopsis:**
```bash
aws workspaces-web delete-user-settings \
    --user-settings-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-settings-arn` | **Yes** | string | -- | The ARN of the user settings to delete |

**Output Schema:**
```json
{}
```

---

### 11.3 `get-user-settings`

Gets user settings.

**Synopsis:**
```bash
aws workspaces-web get-user-settings \
    --user-settings-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-settings-arn` | **Yes** | string | -- | The ARN of the user settings |

**Output Schema:**
```json
{
    "userSettings": {
        "userSettingsArn": "string",
        "associatedPortalArns": ["string"],
        "copyAllowed": "Disabled|Enabled",
        "pasteAllowed": "Disabled|Enabled",
        "downloadAllowed": "Disabled|Enabled",
        "uploadAllowed": "Disabled|Enabled",
        "printAllowed": "Disabled|Enabled",
        "disconnectTimeoutInMinutes": "integer",
        "idleDisconnectTimeoutInMinutes": "integer",
        "deepLinkAllowed": "Disabled|Enabled",
        "cookieSynchronizationConfiguration": {
            "allowlist": [
                {
                    "domain": "string",
                    "name": "string",
                    "path": "string"
                }
            ],
            "blocklist": []
        },
        "customerManagedKey": "string",
        "additionalEncryptionContext": {
            "string": "string"
        }
    }
}
```

---

### 11.4 `list-user-settings`

Lists user settings. **Paginated operation.**

**Synopsis:**
```bash
aws workspaces-web list-user-settings \
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
    "userSettings": [
        {
            "userSettingsArn": "string",
            "copyAllowed": "Disabled|Enabled",
            "pasteAllowed": "Disabled|Enabled",
            "downloadAllowed": "Disabled|Enabled",
            "uploadAllowed": "Disabled|Enabled",
            "printAllowed": "Disabled|Enabled",
            "disconnectTimeoutInMinutes": "integer",
            "idleDisconnectTimeoutInMinutes": "integer",
            "deepLinkAllowed": "Disabled|Enabled",
            "cookieSynchronizationConfiguration": {}
        }
    ],
    "nextToken": "string"
}
```

---

### 11.5 `update-user-settings`

Updates user settings.

**Synopsis:**
```bash
aws workspaces-web update-user-settings \
    --user-settings-arn <value> \
    [--copy-allowed <value>] \
    [--paste-allowed <value>] \
    [--download-allowed <value>] \
    [--upload-allowed <value>] \
    [--print-allowed <value>] \
    [--disconnect-timeout-in-minutes <value>] \
    [--idle-disconnect-timeout-in-minutes <value>] \
    [--deep-link-allowed <value>] \
    [--cookie-synchronization-configuration <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-settings-arn` | **Yes** | string | -- | The ARN of the user settings to update |
| `--copy-allowed` | No | string | None | Allow clipboard copy: `Disabled`, `Enabled` |
| `--paste-allowed` | No | string | None | Allow clipboard paste: `Disabled`, `Enabled` |
| `--download-allowed` | No | string | None | Allow file download: `Disabled`, `Enabled` |
| `--upload-allowed` | No | string | None | Allow file upload: `Disabled`, `Enabled` |
| `--print-allowed` | No | string | None | Allow printing: `Disabled`, `Enabled` |
| `--disconnect-timeout-in-minutes` | No | integer | None | Disconnect timeout |
| `--idle-disconnect-timeout-in-minutes` | No | integer | None | Idle disconnect timeout |
| `--deep-link-allowed` | No | string | None | Allow deep links: `Disabled`, `Enabled` |
| `--cookie-synchronization-configuration` | No | structure | None | Cookie sync configuration |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "userSettings": {
        "userSettingsArn": "string",
        "associatedPortalArns": ["string"],
        "copyAllowed": "Disabled|Enabled",
        "pasteAllowed": "Disabled|Enabled",
        "downloadAllowed": "Disabled|Enabled",
        "uploadAllowed": "Disabled|Enabled",
        "printAllowed": "Disabled|Enabled",
        "disconnectTimeoutInMinutes": "integer",
        "idleDisconnectTimeoutInMinutes": "integer",
        "deepLinkAllowed": "Disabled|Enabled",
        "cookieSynchronizationConfiguration": {},
        "customerManagedKey": "string",
        "additionalEncryptionContext": {}
    }
}
```

---

### 11.6 `associate-user-settings`

Associates user settings with a web portal.

**Synopsis:**
```bash
aws workspaces-web associate-user-settings \
    --portal-arn <value> \
    --user-settings-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--portal-arn` | **Yes** | string | -- | The ARN of the portal |
| `--user-settings-arn` | **Yes** | string | -- | The ARN of the user settings |

**Output Schema:**
```json
{
    "portalArn": "string",
    "userSettingsArn": "string"
}
```

---

### 11.7 `disassociate-user-settings`

Disassociates user settings from a web portal.

**Synopsis:**
```bash
aws workspaces-web disassociate-user-settings \
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
