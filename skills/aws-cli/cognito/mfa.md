# MFA (Multi-Factor Authentication)

### 7.1 `set-user-pool-mfa-config`

Sets the MFA configuration for a user pool, including SMS MFA and software token (TOTP) MFA.

**Synopsis:**
```bash
aws cognito-idp set-user-pool-mfa-config \
    --user-pool-id <value> \
    [--sms-mfa-configuration <value>] \
    [--software-token-mfa-configuration <value>] \
    [--mfa-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-pool-id` | **Yes** | string | -- | ID of the user pool |
| `--sms-mfa-configuration` | No | structure | None | SMS MFA config. Shorthand: `SmsAuthenticationMessage=string,SmsConfiguration={SnsCallerArn=string,ExternalId=string,SnsRegion=string}` |
| `--software-token-mfa-configuration` | No | structure | None | TOTP MFA config. Shorthand: `Enabled=true` |
| `--mfa-configuration` | No | string | None | MFA enforcement: `OFF`, `ON`, `OPTIONAL` |

**Output Schema:**
```json
{
    "SmsMfaConfiguration": {
        "SmsAuthenticationMessage": "string",
        "SmsConfiguration": {
            "SnsCallerArn": "string",
            "ExternalId": "string",
            "SnsRegion": "string"
        }
    },
    "SoftwareTokenMfaConfiguration": {
        "Enabled": "boolean"
    },
    "MfaConfiguration": "OFF|ON|OPTIONAL"
}
```

---

### 7.2 `get-user-pool-mfa-config`

Gets the MFA configuration for a user pool.

**Synopsis:**
```bash
aws cognito-idp get-user-pool-mfa-config \
    --user-pool-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-pool-id` | **Yes** | string | -- | ID of the user pool |

**Output Schema:** Same as `set-user-pool-mfa-config`.

---

### 7.3 `admin-set-user-mfa-preference`

Sets MFA preference for a specific user (admin operation).

**Synopsis:**
```bash
aws cognito-idp admin-set-user-mfa-preference \
    --user-pool-id <value> \
    --username <value> \
    [--sms-mfa-settings <value>] \
    [--software-token-mfa-settings <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-pool-id` | **Yes** | string | -- | ID of the user pool |
| `--username` | **Yes** | string | -- | Username |
| `--sms-mfa-settings` | No | structure | None | SMS MFA settings. Shorthand: `Enabled=boolean,PreferredMfa=boolean` |
| `--software-token-mfa-settings` | No | structure | None | TOTP MFA settings. Shorthand: `Enabled=boolean,PreferredMfa=boolean` |

**Output:** None

---

### 7.4 `set-user-mfa-preference`

Sets MFA preference for an authenticated user (client-side operation).

**Synopsis:**
```bash
aws cognito-idp set-user-mfa-preference \
    --access-token <value> \
    [--sms-mfa-settings <value>] \
    [--software-token-mfa-settings <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--access-token` | **Yes** | string | -- | Access token of the authenticated user |
| `--sms-mfa-settings` | No | structure | None | SMS MFA settings. Shorthand: `Enabled=boolean,PreferredMfa=boolean` |
| `--software-token-mfa-settings` | No | structure | None | TOTP MFA settings. Shorthand: `Enabled=boolean,PreferredMfa=boolean` |

**Output:** None

---

### 7.5 `associate-software-token`

Associates a TOTP software token with a user. Returns a secret code that the user enters into an authenticator app.

**Synopsis:**
```bash
aws cognito-idp associate-software-token \
    [--access-token <value>] \
    [--session <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--access-token` | Cond. | string | None | Access token (use for authenticated user flow) |
| `--session` | Cond. | string | None | Session from MFA_SETUP challenge response |

One of `--access-token` or `--session` is required.

**Output Schema:**
```json
{
    "SecretCode": "string",
    "Session": "string"
}
```

---

### 7.6 `verify-software-token`

Verifies a TOTP software token by checking a user-provided code from their authenticator app.

**Synopsis:**
```bash
aws cognito-idp verify-software-token \
    --user-code <value> \
    [--access-token <value>] \
    [--session <value>] \
    [--friendly-device-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-code` | **Yes** | string | -- | TOTP code from the authenticator app (6 digits) |
| `--access-token` | Cond. | string | None | Access token (use for authenticated user flow) |
| `--session` | Cond. | string | None | Session from `associate-software-token` |
| `--friendly-device-name` | No | string | None | Friendly name for the device |

**Output Schema:**
```json
{
    "Status": "SUCCESS|ERROR",
    "Session": "string"
}
```
