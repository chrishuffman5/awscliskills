# Account

### 1.1 `create-account-customization`

Creates account-level customization settings (default theme, email template).

**Synopsis:**
```bash
aws quicksight create-account-customization \
    --aws-account-id <value> \
    --account-customization <value> \
    [--namespace <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-account-id` | **Yes** | string | -- | AWS account ID |
| `--account-customization` | **Yes** | structure | -- | Customization settings. `{"DefaultTheme":"arn:...","DefaultEmailCustomizationTemplate":"arn:..."}` |
| `--namespace` | No | string | `default` | QuickSight namespace |
| `--tags` | No | list | None | Resource tags |

**Output Schema:**
```json
{
    "Arn": "string",
    "AwsAccountId": "string",
    "Namespace": "string",
    "AccountCustomization": {
        "DefaultTheme": "string",
        "DefaultEmailCustomizationTemplate": "string"
    },
    "RequestId": "string",
    "Status": "integer"
}
```

---

### 1.2 `describe-account-customization`

Describes account customization settings.

**Synopsis:**
```bash
aws quicksight describe-account-customization \
    --aws-account-id <value> \
    [--namespace <value>] \
    [--resolved | --no-resolved] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-account-id` | **Yes** | string | -- | AWS account ID |
| `--namespace` | No | string | `default` | QuickSight namespace |
| `--resolved` | No | boolean | false | Return resolved customization values |

**Output Schema:** Same as `create-account-customization`.

---

### 1.3 `update-account-customization`

Updates account customization settings.

**Synopsis:**
```bash
aws quicksight update-account-customization \
    --aws-account-id <value> \
    --account-customization <value> \
    [--namespace <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** Same as `create-account-customization` (without `--tags`).

**Output Schema:** Same as `create-account-customization`.

---

### 1.4 `delete-account-customization`

Deletes account customization settings.

**Synopsis:**
```bash
aws quicksight delete-account-customization \
    --aws-account-id <value> \
    [--namespace <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-account-id` | **Yes** | string | -- | AWS account ID |
| `--namespace` | No | string | `default` | Namespace |

**Output Schema:**
```json
{
    "RequestId": "string",
    "Status": "integer"
}
```

---

### 1.5 `describe-account-settings`

Describes account-level settings (edition, termination protection, default namespace, notification email).

**Synopsis:**
```bash
aws quicksight describe-account-settings \
    --aws-account-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-account-id` | **Yes** | string | -- | AWS account ID |

**Output Schema:**
```json
{
    "AccountSettings": {
        "AccountName": "string",
        "Edition": "STANDARD|ENTERPRISE|ENTERPRISE_AND_Q",
        "DefaultNamespace": "string",
        "NotificationEmail": "string",
        "PublicSharingEnabled": "boolean",
        "TerminationProtectionEnabled": "boolean"
    },
    "RequestId": "string",
    "Status": "integer"
}
```

---

### 1.6 `update-account-settings`

Updates account settings.

**Synopsis:**
```bash
aws quicksight update-account-settings \
    --aws-account-id <value> \
    --default-namespace <value> \
    [--notification-email <value>] \
    [--termination-protection-enabled | --no-termination-protection-enabled] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-account-id` | **Yes** | string | -- | AWS account ID |
| `--default-namespace` | **Yes** | string | -- | Default namespace |
| `--notification-email` | No | string | unchanged | Notification email address |
| `--termination-protection-enabled` | No | boolean | unchanged | Enable termination protection |

**Output Schema:**
```json
{
    "RequestId": "string",
    "Status": "integer"
}
```

---

### 1.7 `describe-account-subscription`

Describes the QuickSight account subscription details.

**Synopsis:**
```bash
aws quicksight describe-account-subscription \
    --aws-account-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-account-id` | **Yes** | string | -- | AWS account ID |

**Output Schema:**
```json
{
    "AccountInfo": {
        "AccountName": "string",
        "Edition": "STANDARD|ENTERPRISE|ENTERPRISE_AND_Q",
        "NotificationEmail": "string",
        "AuthenticationType": "string",
        "AccountSubscriptionStatus": "string",
        "IAMIdentityCenterInstanceArn": "string"
    },
    "Status": "integer",
    "RequestId": "string"
}
```

---

### 1.8 `create-account-subscription`

Creates a new QuickSight account subscription.

**Synopsis:**
```bash
aws quicksight create-account-subscription \
    --aws-account-id <value> \
    --edition <value> \
    --authentication-method <value> \
    --account-name <value> \
    --notification-email <value> \
    [--admin-group <value>] \
    [--author-group <value>] \
    [--reader-group <value>] \
    [--admin-pro-group <value>] \
    [--author-pro-group <value>] \
    [--reader-pro-group <value>] \
    [--first-name <value>] \
    [--last-name <value>] \
    [--email-address <value>] \
    [--contact-number <value>] \
    [--iam-identity-center-instance-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-account-id` | **Yes** | string | -- | AWS account ID |
| `--edition` | **Yes** | string | -- | `STANDARD`, `ENTERPRISE`, or `ENTERPRISE_AND_Q` |
| `--authentication-method` | **Yes** | string | -- | `IAM_AND_QUICKSIGHT`, `IAM_ONLY`, `ACTIVE_DIRECTORY`, `IAM_IDENTITY_CENTER` |
| `--account-name` | **Yes** | string | -- | Account name for the subscription |
| `--notification-email` | **Yes** | string | -- | Notification email address |
| `--admin-group` | No | list(string) | None | Active Directory admin groups |
| `--author-group` | No | list(string) | None | Active Directory author groups |
| `--reader-group` | No | list(string) | None | Active Directory reader groups |

**Output Schema:**
```json
{
    "SignupResponse": {
        "IAMUser": "boolean",
        "UserLoginName": "string",
        "AccountName": "string",
        "DirectoryType": "string"
    },
    "Status": "integer",
    "RequestId": "string"
}
```

---

### 1.9 `delete-account-subscription`

Deletes a QuickSight account subscription.

**Synopsis:**
```bash
aws quicksight delete-account-subscription \
    --aws-account-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--aws-account-id` | **Yes** | string | -- | AWS account ID |

**Output Schema:**
```json
{
    "RequestId": "string",
    "Status": "integer"
}
```
