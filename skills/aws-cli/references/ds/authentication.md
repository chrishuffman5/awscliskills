# Authentication

### 7.1 `enable-sso`

Enables single sign-on for a directory. Users can then use their directory credentials to sign in to Amazon WorkSpaces, Amazon WorkDocs, etc.

**Synopsis:**
```bash
aws ds enable-sso \
    --directory-id <value> \
    [--user-name <value>] \
    [--password <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |
| `--user-name` | No | string | None | Username for SSO service account (for AD Connector) |
| `--password` | No | string | None | Password for SSO service account |

**Output Schema:**

No output on success (HTTP 200).

---

### 7.2 `disable-sso`

Disables single sign-on for a directory.

**Synopsis:**
```bash
aws ds disable-sso \
    --directory-id <value> \
    [--user-name <value>] \
    [--password <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |
| `--user-name` | No | string | None | Username for SSO service account |
| `--password` | No | string | None | Password for SSO service account |

**Output Schema:**

No output on success (HTTP 200).

---

### 7.3 `enable-radius`

Enables multi-factor authentication (MFA) with RADIUS for a directory.

**Synopsis:**
```bash
aws ds enable-radius \
    --directory-id <value> \
    --radius-settings <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |
| `--radius-settings` | **Yes** | structure | -- | RADIUS server configuration |

**RADIUS Settings Structure:**
```json
{
    "RadiusServers": ["string"],
    "RadiusPort": "integer",
    "RadiusTimeout": "integer",
    "RadiusRetries": "integer",
    "SharedSecret": "string",
    "AuthenticationProtocol": "PAP|CHAP|MS-CHAPv1|MS-CHAPv2",
    "DisplayLabel": "string",
    "UseSameUsername": "boolean"
}
```

**Output Schema:**

No output on success (HTTP 200).

---

### 7.4 `disable-radius`

Disables RADIUS MFA for a directory.

**Synopsis:**
```bash
aws ds disable-radius \
    --directory-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |

**Output Schema:**

No output on success (HTTP 200).

---

### 7.5 `update-radius`

Updates the RADIUS server configuration for a directory.

**Synopsis:**
```bash
aws ds update-radius \
    --directory-id <value> \
    --radius-settings <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |
| `--radius-settings` | **Yes** | structure | -- | Updated RADIUS settings |

**Output Schema:**

No output on success (HTTP 200).

---

### 7.6 `enable-ldaps`

Activates LDAPS (Lightweight Directory Access Protocol over TLS/SSL) for a directory.

**Synopsis:**
```bash
aws ds enable-ldaps \
    --directory-id <value> \
    --type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |
| `--type` | **Yes** | string | -- | `Client` |

**Output Schema:**

No output on success (HTTP 200).

---

### 7.7 `disable-ldaps`

Disables LDAPS for a directory.

**Synopsis:**
```bash
aws ds disable-ldaps \
    --directory-id <value> \
    --type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |
| `--type` | **Yes** | string | -- | `Client` |

**Output Schema:**

No output on success (HTTP 200).

---

### 7.8 `describe-ldaps-settings`

Describes the status of LDAPS for a directory. **Paginated operation.**

**Synopsis:**
```bash
aws ds describe-ldaps-settings \
    --directory-id <value> \
    [--type <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |
| `--type` | No | string | None | `Client` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "LDAPSSettingsInfo": [
        {
            "LDAPSStatus": "Enabling|Enabled|EnableFailed|Disabled",
            "LDAPSStatusReason": "string",
            "LastUpdatedDateTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 7.9 `enable-client-authentication`

Enables alternative client authentication methods for a directory.

**Synopsis:**
```bash
aws ds enable-client-authentication \
    --directory-id <value> \
    --type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |
| `--type` | **Yes** | string | -- | `SmartCard` or `SmartCardOrPassword` |

**Output Schema:**

No output on success (HTTP 200).

---

### 7.10 `disable-client-authentication`

Disables alternative client authentication for a directory.

**Synopsis:**
```bash
aws ds disable-client-authentication \
    --directory-id <value> \
    --type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |
| `--type` | **Yes** | string | -- | `SmartCard` or `SmartCardOrPassword` |

**Output Schema:**

No output on success (HTTP 200).

---

### 7.11 `describe-client-authentication-settings`

Describes the client authentication settings for a directory. **Paginated operation.**

**Synopsis:**
```bash
aws ds describe-client-authentication-settings \
    --directory-id <value> \
    [--type <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |
| `--type` | No | string | None | `SmartCard` or `SmartCardOrPassword` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ClientAuthenticationSettingsInfo": [
        {
            "Type": "SmartCard|SmartCardOrPassword",
            "Status": "Enabled|Disabled",
            "LastUpdatedDateTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 7.12 `reset-user-password`

Resets the password for a user in the directory.

**Synopsis:**
```bash
aws ds reset-user-password \
    --directory-id <value> \
    --user-name <value> \
    --new-password <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |
| `--user-name` | **Yes** | string | -- | Username of the user (1-64 chars) |
| `--new-password` | **Yes** | string | -- | New password (1-127 chars) |

**Output Schema:**

No output on success (HTTP 200).
