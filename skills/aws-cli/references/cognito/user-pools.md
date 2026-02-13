# User Pools

### 1.1 `create-user-pool`

Creates a new Amazon Cognito user pool.

**Synopsis:**
```bash
aws cognito-idp create-user-pool \
    --pool-name <value> \
    [--policies <value>] \
    [--deletion-protection <value>] \
    [--lambda-config <value>] \
    [--auto-verified-attributes <value>] \
    [--alias-attributes <value>] \
    [--username-attributes <value>] \
    [--sms-verification-message <value>] \
    [--email-verification-message <value>] \
    [--email-verification-subject <value>] \
    [--verification-message-template <value>] \
    [--sms-authentication-message <value>] \
    [--mfa-configuration <value>] \
    [--device-configuration <value>] \
    [--email-configuration <value>] \
    [--sms-configuration <value>] \
    [--user-pool-tags <value>] \
    [--admin-create-user-config <value>] \
    [--schema <value>] \
    [--user-pool-add-ons <value>] \
    [--username-configuration <value>] \
    [--account-recovery-setting <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--pool-name` | **Yes** | string | -- | Name of the user pool (1-128 chars) |
| `--policies` | No | structure | None | Password policies. Shorthand: `PasswordPolicy={MinimumLength=integer,RequireUppercase=boolean,RequireLowercase=boolean,RequireNumbers=boolean,RequireSymbols=boolean,TemporaryPasswordValidityDays=integer}` |
| `--deletion-protection` | No | string | `INACTIVE` | Deletion protection: `ACTIVE` or `INACTIVE` |
| `--lambda-config` | No | structure | None | Lambda trigger configuration |
| `--auto-verified-attributes` | No | list(string) | None | Attributes to auto-verify: `email`, `phone_number` |
| `--alias-attributes` | No | list(string) | None | Alias attributes: `phone_number`, `email`, `preferred_username` |
| `--username-attributes` | No | list(string) | None | Username attributes: `phone_number`, `email` |
| `--mfa-configuration` | No | string | `OFF` | MFA configuration: `OFF`, `ON`, `OPTIONAL` |
| `--email-configuration` | No | structure | None | Email config. Shorthand: `SourceArn=string,ReplyToEmailAddress=string,EmailSendingAccount=COGNITO_DEFAULT|DEVELOPER,From=string,ConfigurationSet=string` |
| `--sms-configuration` | No | structure | None | SMS config. Shorthand: `SnsCallerArn=string,ExternalId=string,SnsRegion=string` |
| `--schema` | No | list | None | Schema attributes. Shorthand: `Name=string,AttributeDataType=String|Number|DateTime|Boolean,Mutable=boolean,Required=boolean ...` |
| `--admin-create-user-config` | No | structure | None | Admin user creation config. Shorthand: `AllowAdminCreateUserOnly=boolean,UnusedAccountValidityDays=integer` |
| `--username-configuration` | No | structure | None | Username config. Shorthand: `CaseSensitive=boolean` |
| `--account-recovery-setting` | No | structure | None | Account recovery settings |
| `--user-pool-tags` | No | map | None | Key-value tags |
| `--user-pool-add-ons` | No | structure | None | Advanced security. Shorthand: `AdvancedSecurityMode=OFF|AUDIT|ENFORCED` |
| `--device-configuration` | No | structure | None | Device tracking. Shorthand: `ChallengeRequiredOnNewDevice=boolean,DeviceOnlyRememberedOnUserPrompt=boolean` |

**Output Schema:**
```json
{
    "UserPool": {
        "Id": "string",
        "Name": "string",
        "Policies": {
            "PasswordPolicy": {
                "MinimumLength": "integer",
                "RequireUppercase": "boolean",
                "RequireLowercase": "boolean",
                "RequireNumbers": "boolean",
                "RequireSymbols": "boolean",
                "TemporaryPasswordValidityDays": "integer"
            }
        },
        "DeletionProtection": "ACTIVE|INACTIVE",
        "LambdaConfig": {},
        "Status": "Enabled|Disabled",
        "LastModifiedDate": "timestamp",
        "CreationDate": "timestamp",
        "SchemaAttributes": [
            {
                "Name": "string",
                "AttributeDataType": "String|Number|DateTime|Boolean",
                "DeveloperOnlyAttribute": "boolean",
                "Mutable": "boolean",
                "Required": "boolean",
                "NumberAttributeConstraints": {},
                "StringAttributeConstraints": {}
            }
        ],
        "AutoVerifiedAttributes": ["email|phone_number"],
        "AliasAttributes": ["phone_number|email|preferred_username"],
        "UsernameAttributes": ["phone_number|email"],
        "MfaConfiguration": "OFF|ON|OPTIONAL",
        "EstimatedNumberOfUsers": "integer",
        "EmailConfiguration": {},
        "SmsConfiguration": {},
        "UserPoolTags": {},
        "AdminCreateUserConfig": {},
        "UsernameConfiguration": {"CaseSensitive": "boolean"},
        "Arn": "string",
        "AccountRecoverySetting": {}
    }
}
```

---

### 1.2 `delete-user-pool`

Deletes a user pool. Users in the pool are not deleted.

**Synopsis:**
```bash
aws cognito-idp delete-user-pool \
    --user-pool-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-pool-id` | **Yes** | string | -- | ID of the user pool to delete |

**Output:** None

---

### 1.3 `describe-user-pool`

Gets detailed information about a user pool.

**Synopsis:**
```bash
aws cognito-idp describe-user-pool \
    --user-pool-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-pool-id` | **Yes** | string | -- | ID of the user pool |

**Output Schema:** Same structure as `create-user-pool` output.

---

### 1.4 `list-user-pools`

Lists user pools. **Paginated operation.**

**Synopsis:**
```bash
aws cognito-idp list-user-pools \
    --max-results <value> \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--max-results` | **Yes** | integer | -- | Maximum items (1-60) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "UserPools": [
        {
            "Id": "string",
            "Name": "string",
            "LambdaConfig": {},
            "Status": "string",
            "LastModifiedDate": "timestamp",
            "CreationDate": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.5 `update-user-pool`

Updates user pool configuration. Accepts all the same optional parameters as `create-user-pool`.

**Synopsis:**
```bash
aws cognito-idp update-user-pool \
    --user-pool-id <value> \
    [--policies <value>] \
    [--deletion-protection <value>] \
    [--lambda-config <value>] \
    [--auto-verified-attributes <value>] \
    [--mfa-configuration <value>] \
    [--device-configuration <value>] \
    [--email-configuration <value>] \
    [--sms-configuration <value>] \
    [--user-pool-tags <value>] \
    [--admin-create-user-config <value>] \
    [--user-pool-add-ons <value>] \
    [--account-recovery-setting <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-pool-id` | **Yes** | string | -- | ID of the user pool |
| All other parameters are the same optional parameters as `create-user-pool`. Only specified parameters are updated. |

**Output:** None
