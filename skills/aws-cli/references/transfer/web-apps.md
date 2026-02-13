# Web Apps

Commands for managing Transfer Family web app portals.

### 10.1 `create-web-app`

Creates a web app portal for browser-based file transfers via IAM Identity Center.

**Synopsis:**
```bash
aws transfer create-web-app \
    --identity-provider-details <value> \
    [--access-endpoint <value>] \
    [--web-app-units <value>] \
    [--tags <value>] \
    [--web-app-endpoint-policy <value>] \
    [--endpoint-details <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identity-provider-details` | **Yes** | structure | -- | IAM Identity Center config with InstanceArn and Role |
| `--access-endpoint` | No | string | None | Custom URL for web app access |
| `--web-app-units` | No | structure | None | Provisioned capacity (each unit = 250 sessions) |
| `--tags` | No | list | None | Tags |
| `--web-app-endpoint-policy` | No | string | `STANDARD` | `STANDARD` or `FIPS` |
| `--endpoint-details` | No | structure | None | VPC configuration |

**Identity Provider Details (JSON):**
```json
{
    "IdentityCenterConfig": {
        "InstanceArn": "string",
        "Role": "string"
    }
}
```

**Output Schema:**
```json
{
    "WebAppId": "string"
}
```

---

### 10.2 `delete-web-app`

Deletes a web app.

**Synopsis:**
```bash
aws transfer delete-web-app \
    --web-app-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--web-app-id` | **Yes** | string | -- | Web app ID |

**Output:** None on success.

---

### 10.3 `describe-web-app`

Gets details about a web app.

**Synopsis:**
```bash
aws transfer describe-web-app \
    --web-app-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--web-app-id` | **Yes** | string | -- | Web app ID |

**Output Schema:**
```json
{
    "WebApp": {
        "Arn": "string",
        "WebAppId": "string",
        "DescribedIdentityProviderDetails": {
            "IdentityCenterConfig": {
                "ApplicationArn": "string",
                "InstanceArn": "string",
                "Role": "string"
            }
        },
        "AccessEndpoint": "string",
        "WebAppEndpoint": "string",
        "WebAppUnits": {"Provisioned": "integer"},
        "Tags": [{"Key": "string", "Value": "string"}],
        "WebAppEndpointPolicy": "STANDARD|FIPS"
    }
}
```

---

### 10.4 `list-web-apps`

Lists web apps. **Paginated operation.**

**Synopsis:**
```bash
aws transfer list-web-apps \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Output Schema:**
```json
{
    "WebApps": [
        {
            "Arn": "string",
            "WebAppId": "string",
            "AccessEndpoint": "string",
            "WebAppEndpoint": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 10.5 `update-web-app`

Updates web app settings.

**Synopsis:**
```bash
aws transfer update-web-app \
    --web-app-id <value> \
    [--identity-provider-details <value>] \
    [--access-endpoint <value>] \
    [--web-app-units <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--web-app-id` | **Yes** | string | -- | Web app ID |
| `--identity-provider-details` | No | structure | None | Updated identity config |
| `--access-endpoint` | No | string | None | Updated access URL |
| `--web-app-units` | No | structure | None | Updated capacity |

**Output Schema:**
```json
{
    "WebAppId": "string"
}
```

---

### 10.6 `describe-web-app-customization`

Gets web app branding customization (logo, favicon, title).

**Synopsis:**
```bash
aws transfer describe-web-app-customization \
    --web-app-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--web-app-id` | **Yes** | string | -- | Web app ID |

**Output Schema:**
```json
{
    "WebAppCustomization": {
        "Arn": "string",
        "WebAppId": "string",
        "Title": "string",
        "LogoFile": "blob",
        "FaviconFile": "blob"
    }
}
```

---

### 10.7 `update-web-app-customization`

Updates web app branding.

**Synopsis:**
```bash
aws transfer update-web-app-customization \
    --web-app-id <value> \
    [--title <value>] \
    [--logo-file <value>] \
    [--favicon-file <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--web-app-id` | **Yes** | string | -- | Web app ID |
| `--title` | No | string | None | Custom title |
| `--logo-file` | No | blob | None | Logo image file |
| `--favicon-file` | No | blob | None | Favicon image file |

**Output Schema:**
```json
{
    "WebAppId": "string"
}
```

---

### 10.8 `delete-web-app-customization`

Deletes web app branding customization.

**Synopsis:**
```bash
aws transfer delete-web-app-customization \
    --web-app-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--web-app-id` | **Yes** | string | -- | Web app ID |

**Output:** None on success.
