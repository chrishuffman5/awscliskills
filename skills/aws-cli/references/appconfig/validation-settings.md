# Validation & Settings

### 8.1 `validate-configuration`

Validates the configuration data against the schema defined for the configuration profile.

**Synopsis:**
```bash
aws appconfig validate-configuration \
    --application-id <value> \
    --configuration-profile-id <value> \
    --configuration-version <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application ID |
| `--configuration-profile-id` | **Yes** | string | -- | Configuration profile ID |
| `--configuration-version` | **Yes** | string | -- | Configuration version to validate (1-1024 chars) |

**Output:** None

---

### 8.2 `get-account-settings`

Retrieves account-level settings for AppConfig, including DeletionProtection settings.

**Synopsis:**
```bash
aws appconfig get-account-settings \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output Schema:**
```json
{
    "DeletionProtection": {
        "Enabled": "boolean",
        "ProtectionPeriodInMinutes": "integer"
    }
}
```

---

### 8.3 `update-account-settings`

Updates account-level settings for AppConfig.

**Synopsis:**
```bash
aws appconfig update-account-settings \
    [--deletion-protection <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--deletion-protection` | No | structure | None | Deletion protection settings |

**DeletionProtection structure:**
```json
{
    "Enabled": true,
    "ProtectionPeriodInMinutes": 60
}
```

**Output Schema:**
```json
{
    "DeletionProtection": {
        "Enabled": "boolean",
        "ProtectionPeriodInMinutes": "integer"
    }
}
```
