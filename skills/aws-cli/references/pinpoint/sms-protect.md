# SMS v2 Protect Configurations

All commands in this section use `aws pinpoint-sms-voice-v2`.

### 18.1 `create-protect-configuration`

Creates a new protect configuration for controlling message delivery by country.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 create-protect-configuration \
    [--deletion-protection-enabled | --no-deletion-protection-enabled] \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--deletion-protection-enabled` | No | boolean | false | Prevent deletion |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "ProtectConfigurationArn": "string",
    "ProtectConfigurationId": "string",
    "CreatedTimestamp": "timestamp",
    "AccountDefault": "boolean",
    "DeletionProtectionEnabled": "boolean",
    "Tags": [{"Key": "string", "Value": "string"}]
}
```

---

### 18.2 `describe-protect-configurations`

Describes protect configurations in your account.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 describe-protect-configurations \
    [--protect-configuration-ids <value>] \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--protect-configuration-ids` | No | list | None | IDs or ARNs (max 5) |
| `--filters` | No | list | None | Filters: `account-default`, `deletion-protection-enabled` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ProtectConfigurations": [
        {
            "ProtectConfigurationArn": "string",
            "ProtectConfigurationId": "string",
            "CreatedTimestamp": "timestamp",
            "AccountDefault": "boolean",
            "DeletionProtectionEnabled": "boolean"
        }
    ],
    "NextToken": "string"
}
```

---

### 18.3 `update-protect-configuration`

Updates protect configuration settings.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 update-protect-configuration \
    --protect-configuration-id <value> \
    [--deletion-protection-enabled | --no-deletion-protection-enabled] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--protect-configuration-id` | **Yes** | string | -- | Protect configuration ID or ARN |
| `--deletion-protection-enabled` | No | boolean | -- | Enable/disable deletion protection |

**Output Schema:**
```json
{
    "ProtectConfigurationArn": "string",
    "ProtectConfigurationId": "string",
    "CreatedTimestamp": "timestamp",
    "AccountDefault": "boolean",
    "DeletionProtectionEnabled": "boolean"
}
```

---

### 18.4 `delete-protect-configuration`

Deletes a protect configuration. Deletion protection must be disabled, must not be account default, and must not be associated with a configuration set.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 delete-protect-configuration \
    --protect-configuration-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--protect-configuration-id` | **Yes** | string | -- | Protect configuration ID or ARN |

**Output Schema:** Same as `update-protect-configuration`.

---

### 18.5 `get-protect-configuration-country-rule-set`

Gets country-level rules for a protect configuration.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 get-protect-configuration-country-rule-set \
    --protect-configuration-id <value> \
    --number-capability <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--protect-configuration-id` | **Yes** | string | -- | Protect configuration ID or ARN |
| `--number-capability` | **Yes** | string | -- | `SMS`, `VOICE`, or `MMS` |

**Output Schema:**
```json
{
    "ProtectConfigurationArn": "string",
    "ProtectConfigurationId": "string",
    "NumberCapability": "SMS|VOICE|MMS",
    "CountryRuleSet": {
        "US": {"ProtectStatus": "ALLOW|BLOCK|MONITOR|FILTER"},
        "CA": {"ProtectStatus": "ALLOW|BLOCK|MONITOR|FILTER"}
    }
}
```

---

### 18.6 `update-protect-configuration-country-rule-set`

Updates country-level rules for a protect configuration.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 update-protect-configuration-country-rule-set \
    --protect-configuration-id <value> \
    --number-capability <value> \
    --country-rule-set-updates <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--protect-configuration-id` | **Yes** | string | -- | Protect configuration ID or ARN |
| `--number-capability` | **Yes** | string | -- | `SMS`, `VOICE`, or `MMS` |
| `--country-rule-set-updates` | **Yes** | map | -- | Map of ISO country codes to rules. Shorthand: `US={ProtectStatus=ALLOW},CA={ProtectStatus=BLOCK}` |

**Output Schema:** Same as `get-protect-configuration-country-rule-set`.

---

### 18.7 `set-account-default-protect-configuration`

Sets a protect configuration as the account default.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 set-account-default-protect-configuration \
    --protect-configuration-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--protect-configuration-id` | **Yes** | string | -- | Protect configuration ID or ARN |

**Output Schema:**
```json
{
    "DefaultProtectConfigurationArn": "string",
    "DefaultProtectConfigurationId": "string"
}
```

---

### 18.8 `delete-account-default-protect-configuration`

Removes the account default protect configuration.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 delete-account-default-protect-configuration \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** No required parameters.

**Output Schema:**
```json
{
    "DefaultProtectConfigurationArn": "string",
    "DefaultProtectConfigurationId": "string"
}
```

---

### 18.9 `associate-protect-configuration`

Associates a protect configuration with a configuration set.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 associate-protect-configuration \
    --protect-configuration-id <value> \
    --configuration-set-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--protect-configuration-id` | **Yes** | string | -- | Protect configuration ID or ARN |
| `--configuration-set-name` | **Yes** | string | -- | Configuration set name or ARN |

**Output Schema:**
```json
{
    "ConfigurationSetArn": "string",
    "ConfigurationSetName": "string",
    "ProtectConfigurationArn": "string",
    "ProtectConfigurationId": "string"
}
```

---

### 18.10 `disassociate-protect-configuration`

Removes a protect configuration from a configuration set.

**Synopsis:**
```bash
aws pinpoint-sms-voice-v2 disassociate-protect-configuration \
    --protect-configuration-id <value> \
    --configuration-set-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--protect-configuration-id` | **Yes** | string | -- | Protect configuration ID or ARN |
| `--configuration-set-name` | **Yes** | string | -- | Configuration set name or ARN |

**Output Schema:** Same as `associate-protect-configuration`.
