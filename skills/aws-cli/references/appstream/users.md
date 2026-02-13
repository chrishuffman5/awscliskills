# Users

### 9.1 `create-user`

Creates a new user in the user pool.

**Synopsis:**
```bash
aws appstream create-user \
    --user-name <value> \
    --authentication-type <value> \
    [--first-name <value>] \
    [--last-name <value>] \
    [--message-action <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-name` | **Yes** | string | -- | Email address of the user (used as username) |
| `--authentication-type` | **Yes** | string | -- | Authentication type: `API`, `SAML`, `USERPOOL`, `AWS_AD` |
| `--first-name` | No | string | -- | First name of the user |
| `--last-name` | No | string | -- | Last name of the user |
| `--message-action` | No | string | -- | Action for welcome email: `SUPPRESS`, `RESEND` |

**Output Schema:**
```json
{}
```

---

### 9.2 `delete-user`

Deletes a user from the user pool.

**Synopsis:**
```bash
aws appstream delete-user \
    --user-name <value> \
    --authentication-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-name` | **Yes** | string | -- | Email address of the user |
| `--authentication-type` | **Yes** | string | -- | Authentication type: `API`, `SAML`, `USERPOOL`, `AWS_AD` |

**Output Schema:**
```json
{}
```

---

### 9.3 `describe-users`

Describes users in the user pool.

**Synopsis:**
```bash
aws appstream describe-users \
    --authentication-type <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--authentication-type` | **Yes** | string | -- | Authentication type: `API`, `SAML`, `USERPOOL`, `AWS_AD` |
| `--max-results` | No | integer | -- | Maximum number of results |
| `--next-token` | No | string | -- | Pagination token |

**Output Schema:**
```json
{
    "Users": [
        {
            "Arn": "string",
            "UserName": "string",
            "Enabled": "boolean",
            "Status": "string",
            "FirstName": "string",
            "LastName": "string",
            "CreatedTime": "timestamp",
            "AuthenticationType": "API|SAML|USERPOOL|AWS_AD"
        }
    ],
    "NextToken": "string"
}
```

---

### 9.4 `disable-user`

Disables the specified user in the user pool. Disabled users cannot sign in.

**Synopsis:**
```bash
aws appstream disable-user \
    --user-name <value> \
    --authentication-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-name` | **Yes** | string | -- | Email address of the user |
| `--authentication-type` | **Yes** | string | -- | Authentication type: `API`, `SAML`, `USERPOOL`, `AWS_AD` |

**Output Schema:**
```json
{}
```

---

### 9.5 `enable-user`

Enables the specified user in the user pool.

**Synopsis:**
```bash
aws appstream enable-user \
    --user-name <value> \
    --authentication-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-name` | **Yes** | string | -- | Email address of the user |
| `--authentication-type` | **Yes** | string | -- | Authentication type: `API`, `SAML`, `USERPOOL`, `AWS_AD` |

**Output Schema:**
```json
{}
```

---

### 9.6 `batch-associate-user-stack`

Associates users with stacks in batch.

**Synopsis:**
```bash
aws appstream batch-associate-user-stack \
    --user-stack-associations <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-stack-associations` | **Yes** | list | -- | User-stack associations. Shorthand: `StackName=string,UserName=string,AuthenticationType=API\|SAML\|USERPOOL\|AWS_AD,SendEmailNotification=boolean ...` |

**Output Schema:**
```json
{
    "errors": [
        {
            "UserStackAssociation": {
                "StackName": "string",
                "UserName": "string",
                "AuthenticationType": "API|SAML|USERPOOL|AWS_AD",
                "SendEmailNotification": "boolean"
            },
            "ErrorCode": "STACK_NOT_FOUND|USER_NAME_NOT_FOUND|DIRECTORY_NOT_FOUND|INTERNAL_ERROR",
            "ErrorMessage": "string"
        }
    ]
}
```

---

### 9.7 `batch-disassociate-user-stack`

Disassociates users from stacks in batch.

**Synopsis:**
```bash
aws appstream batch-disassociate-user-stack \
    --user-stack-associations <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-stack-associations` | **Yes** | list | -- | User-stack associations. Shorthand: `StackName=string,UserName=string,AuthenticationType=API\|SAML\|USERPOOL\|AWS_AD ...` |

**Output Schema:**
```json
{
    "errors": [
        {
            "UserStackAssociation": {
                "StackName": "string",
                "UserName": "string",
                "AuthenticationType": "API|SAML|USERPOOL|AWS_AD"
            },
            "ErrorCode": "STACK_NOT_FOUND|USER_NAME_NOT_FOUND|DIRECTORY_NOT_FOUND|INTERNAL_ERROR",
            "ErrorMessage": "string"
        }
    ]
}
```

---

### 9.8 `describe-user-stack-associations`

Describes user-stack associations. At least one of `--stack-name`, `--user-name`, or both must be specified.

**Synopsis:**
```bash
aws appstream describe-user-stack-associations \
    [--stack-name <value>] \
    [--user-name <value>] \
    [--authentication-type <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stack-name` | No | string | -- | Name of the stack to filter by |
| `--user-name` | No | string | -- | Email address of the user to filter by |
| `--authentication-type` | No | string | -- | Authentication type: `API`, `SAML`, `USERPOOL`, `AWS_AD` |
| `--max-results` | No | integer | -- | Maximum number of results |
| `--next-token` | No | string | -- | Pagination token |

**Output Schema:**
```json
{
    "UserStackAssociations": [
        {
            "StackName": "string",
            "UserName": "string",
            "AuthenticationType": "API|SAML|USERPOOL|AWS_AD",
            "SendEmailNotification": "boolean"
        }
    ],
    "NextToken": "string"
}
```
