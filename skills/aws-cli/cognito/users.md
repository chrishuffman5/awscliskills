# Users

### 3.1 `admin-create-user`

Creates a new user in a user pool (admin operation). Can send a welcome message with a temporary password.

**Synopsis:**
```bash
aws cognito-idp admin-create-user \
    --user-pool-id <value> \
    --username <value> \
    [--user-attributes <value>] \
    [--validation-data <value>] \
    [--temporary-password <value>] \
    [--force-alias-creation | --no-force-alias-creation] \
    [--message-action <value>] \
    [--desired-delivery-mediums <value>] \
    [--client-metadata <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-pool-id` | **Yes** | string | -- | ID of the user pool |
| `--username` | **Yes** | string | -- | Username (or email/phone if used as username) |
| `--user-attributes` | No | list | None | User attributes. Shorthand: `Name=email,Value=user@example.com Name=phone_number,Value=+1234567890` |
| `--temporary-password` | No | string | None | Temporary password. Auto-generated if not specified |
| `--force-alias-creation` | No | boolean | false | Force alias creation even if alias exists |
| `--message-action` | No | string | None | `SUPPRESS` to skip sending welcome message, `RESEND` to resend |
| `--desired-delivery-mediums` | No | list(string) | `["SMS"]` | Delivery medium: `SMS`, `EMAIL` |
| `--client-metadata` | No | map | None | Metadata to pass to Lambda triggers |

**Output Schema:**
```json
{
    "User": {
        "Username": "string",
        "Attributes": [
            {
                "Name": "string",
                "Value": "string"
            }
        ],
        "UserCreateDate": "timestamp",
        "UserLastModifiedDate": "timestamp",
        "Enabled": "boolean",
        "UserStatus": "UNCONFIRMED|CONFIRMED|ARCHIVED|COMPROMISED|UNKNOWN|RESET_REQUIRED|FORCE_CHANGE_PASSWORD",
        "MFAOptions": [
            {
                "DeliveryMedium": "SMS|EMAIL",
                "AttributeName": "string"
            }
        ]
    }
}
```

---

### 3.2 `admin-delete-user`

Deletes a user from the user pool.

**Synopsis:**
```bash
aws cognito-idp admin-delete-user \
    --user-pool-id <value> \
    --username <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-pool-id` | **Yes** | string | -- | ID of the user pool |
| `--username` | **Yes** | string | -- | Username |

**Output:** None

---

### 3.3 `admin-get-user`

Gets detailed information about a user.

**Synopsis:**
```bash
aws cognito-idp admin-get-user \
    --user-pool-id <value> \
    --username <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-pool-id` | **Yes** | string | -- | ID of the user pool |
| `--username` | **Yes** | string | -- | Username |

**Output Schema:**
```json
{
    "Username": "string",
    "UserAttributes": [
        {
            "Name": "string",
            "Value": "string"
        }
    ],
    "UserCreateDate": "timestamp",
    "UserLastModifiedDate": "timestamp",
    "Enabled": "boolean",
    "UserStatus": "UNCONFIRMED|CONFIRMED|ARCHIVED|COMPROMISED|UNKNOWN|RESET_REQUIRED|FORCE_CHANGE_PASSWORD",
    "MFAOptions": [],
    "PreferredMfaSetting": "string",
    "UserMFASettingList": ["string"]
}
```

---

### 3.4 `admin-set-user-password`

Sets a user's password. Can set a permanent or temporary password.

**Synopsis:**
```bash
aws cognito-idp admin-set-user-password \
    --user-pool-id <value> \
    --username <value> \
    --password <value> \
    [--permanent | --no-permanent] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-pool-id` | **Yes** | string | -- | ID of the user pool |
| `--username` | **Yes** | string | -- | Username |
| `--password` | **Yes** | string | -- | New password |
| `--permanent` | No | boolean | false | If true, sets a permanent password. If false, sets a temporary password |

**Output:** None

---

### 3.5 `admin-confirm-sign-up`

Confirms user registration without a confirmation code (admin operation).

**Synopsis:**
```bash
aws cognito-idp admin-confirm-sign-up \
    --user-pool-id <value> \
    --username <value> \
    [--client-metadata <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-pool-id` | **Yes** | string | -- | ID of the user pool |
| `--username` | **Yes** | string | -- | Username |
| `--client-metadata` | No | map | None | Metadata for Lambda triggers |

**Output:** None

---

### 3.6 `admin-disable-user`

Disables a user, preventing them from signing in.

**Synopsis:**
```bash
aws cognito-idp admin-disable-user \
    --user-pool-id <value> \
    --username <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-pool-id` | **Yes** | string | -- | ID of the user pool |
| `--username` | **Yes** | string | -- | Username |

**Output:** None

---

### 3.7 `admin-enable-user`

Enables a previously disabled user.

**Synopsis:**
```bash
aws cognito-idp admin-enable-user \
    --user-pool-id <value> \
    --username <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-pool-id` | **Yes** | string | -- | ID of the user pool |
| `--username` | **Yes** | string | -- | Username |

**Output:** None

---

### 3.8 `admin-update-user-attributes`

Updates user attributes for a user.

**Synopsis:**
```bash
aws cognito-idp admin-update-user-attributes \
    --user-pool-id <value> \
    --username <value> \
    --user-attributes <value> \
    [--client-metadata <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-pool-id` | **Yes** | string | -- | ID of the user pool |
| `--username` | **Yes** | string | -- | Username |
| `--user-attributes` | **Yes** | list | -- | Attributes to update. Shorthand: `Name=email,Value=new@example.com` |
| `--client-metadata` | No | map | None | Metadata for Lambda triggers |

**Output:** None

---

### 3.9 `list-users`

Lists users in a user pool. **Paginated operation.**

**Synopsis:**
```bash
aws cognito-idp list-users \
    --user-pool-id <value> \
    [--attributes-to-get <value>] \
    [--filter <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-pool-id` | **Yes** | string | -- | ID of the user pool |
| `--attributes-to-get` | No | list(string) | None | Specific attributes to return |
| `--filter` | No | string | None | Filter expression (e.g., `email = "user@example.com"`, `username ^= "john"`, `status = "Enabled"`) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call (max 60) |
| `--max-items` | No | integer | None | Total items to return |

**Filter Syntax:**
- Attribute filter: `"<attribute> <operator> \"<value>\""` where operator is `=`, `^=` (prefix match)
- Filterable attributes: `username`, `email`, `phone_number`, `name`, `given_name`, `family_name`, `preferred_username`, `cognito:user_status`, `status`, `sub`

**Output Schema:**
```json
{
    "Users": [
        {
            "Username": "string",
            "Attributes": [
                {
                    "Name": "string",
                    "Value": "string"
                }
            ],
            "UserCreateDate": "timestamp",
            "UserLastModifiedDate": "timestamp",
            "Enabled": "boolean",
            "UserStatus": "string"
        }
    ],
    "PaginationToken": "string"
}
```

---

### 3.10 `sign-up`

Registers a new user (client-side operation, no admin credentials needed).

**Synopsis:**
```bash
aws cognito-idp sign-up \
    --client-id <value> \
    --username <value> \
    --password <value> \
    [--user-attributes <value>] \
    [--secret-hash <value>] \
    [--client-metadata <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--client-id` | **Yes** | string | -- | App client ID |
| `--username` | **Yes** | string | -- | Username |
| `--password` | **Yes** | string | -- | Password |
| `--user-attributes` | No | list | None | User attributes |
| `--secret-hash` | No | string | None | HMAC of username + client ID (required if client has a secret) |
| `--client-metadata` | No | map | None | Metadata for Lambda triggers |

**Output Schema:**
```json
{
    "UserConfirmed": "boolean",
    "CodeDeliveryDetails": {
        "Destination": "string",
        "DeliveryMedium": "SMS|EMAIL",
        "AttributeName": "string"
    },
    "UserSub": "string"
}
```

---

### 3.11 `confirm-sign-up`

Confirms user registration with a verification code.

**Synopsis:**
```bash
aws cognito-idp confirm-sign-up \
    --client-id <value> \
    --username <value> \
    --confirmation-code <value> \
    [--secret-hash <value>] \
    [--force-alias-creation | --no-force-alias-creation] \
    [--client-metadata <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--client-id` | **Yes** | string | -- | App client ID |
| `--username` | **Yes** | string | -- | Username |
| `--confirmation-code` | **Yes** | string | -- | Confirmation code from email/SMS |
| `--secret-hash` | No | string | None | HMAC (required if client has a secret) |
| `--force-alias-creation` | No | boolean | false | Force alias creation |
| `--client-metadata` | No | map | None | Metadata for Lambda triggers |

**Output:** None

---

### 3.12 `forgot-password`

Initiates a forgot password flow, sending a reset code to the user.

**Synopsis:**
```bash
aws cognito-idp forgot-password \
    --client-id <value> \
    --username <value> \
    [--secret-hash <value>] \
    [--client-metadata <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--client-id` | **Yes** | string | -- | App client ID |
| `--username` | **Yes** | string | -- | Username |
| `--secret-hash` | No | string | None | HMAC (required if client has a secret) |
| `--client-metadata` | No | map | None | Metadata for Lambda triggers |

**Output Schema:**
```json
{
    "CodeDeliveryDetails": {
        "Destination": "string",
        "DeliveryMedium": "SMS|EMAIL",
        "AttributeName": "string"
    }
}
```

---

### 3.13 `confirm-forgot-password`

Confirms a new password using a verification code from `forgot-password`.

**Synopsis:**
```bash
aws cognito-idp confirm-forgot-password \
    --client-id <value> \
    --username <value> \
    --confirmation-code <value> \
    --password <value> \
    [--secret-hash <value>] \
    [--client-metadata <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--client-id` | **Yes** | string | -- | App client ID |
| `--username` | **Yes** | string | -- | Username |
| `--confirmation-code` | **Yes** | string | -- | Confirmation code from email/SMS |
| `--password` | **Yes** | string | -- | New password |
| `--secret-hash` | No | string | None | HMAC (required if client has a secret) |
| `--client-metadata` | No | map | None | Metadata for Lambda triggers |

**Output:** None
