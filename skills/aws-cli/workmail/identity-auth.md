# Identity & Auth

### 13.1 `create-identity-center-application`

Creates an IAM Identity Center application for WorkMail.

**Synopsis:**
```bash
aws workmail create-identity-center-application \
    --name <value> \
    --instance-arn <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Application name |
| `--instance-arn` | **Yes** | string | -- | IAM Identity Center instance ARN |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "ApplicationArn": "string"
}
```

---

### 13.2 `delete-identity-center-application`

Deletes an IAM Identity Center application for WorkMail.

**Synopsis:**
```bash
aws workmail delete-identity-center-application \
    --application-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-arn` | **Yes** | string | -- | Identity Center application ARN |

**Output:** None

---

### 13.3 `put-identity-provider-configuration`

Configures an identity provider (IdP) for WorkMail authentication.

**Synopsis:**
```bash
aws workmail put-identity-provider-configuration \
    --organization-id <value> \
    --authentication-mode <value> \
    --identity-center-configuration <value> \
    --personal-access-token-configuration <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--authentication-mode` | **Yes** | string | -- | Authentication mode: `IDENTITY_PROVIDER_ONLY`, `IDENTITY_PROVIDER_AND_DIRECTORY` |
| `--identity-center-configuration` | **Yes** | structure | -- | Identity Center configuration |
| `--personal-access-token-configuration` | **Yes** | structure | -- | Personal access token configuration |

**Identity Center configuration:**
```json
{
    "InstanceArn": "string",
    "ApplicationArn": "string"
}
```

**Personal access token configuration:**
```json
{
    "Status": "ACTIVE|INACTIVE",
    "LifetimeInDays": 90
}
```

**Output:** None

---

### 13.4 `describe-identity-provider-configuration`

Describes identity provider configuration for an organization.

**Synopsis:**
```bash
aws workmail describe-identity-provider-configuration \
    --organization-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |

**Output Schema:**
```json
{
    "AuthenticationMode": "IDENTITY_PROVIDER_ONLY|IDENTITY_PROVIDER_AND_DIRECTORY",
    "IdentityCenterConfiguration": {
        "InstanceArn": "string",
        "ApplicationArn": "string"
    },
    "PersonalAccessTokenConfiguration": {
        "Status": "ACTIVE|INACTIVE",
        "LifetimeInDays": "integer"
    }
}
```

---

### 13.5 `delete-identity-provider-configuration`

Deletes identity provider configuration for an organization.

**Synopsis:**
```bash
aws workmail delete-identity-provider-configuration \
    --organization-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |

**Output:** None

---

### 13.6 `get-personal-access-token-metadata`

Gets metadata for a personal access token.

**Synopsis:**
```bash
aws workmail get-personal-access-token-metadata \
    --organization-id <value> \
    --personal-access-token-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--personal-access-token-id` | **Yes** | string | -- | Personal access token ID |

**Output Schema:**
```json
{
    "PersonalAccessTokenId": "string",
    "UserId": "string",
    "Name": "string",
    "DateCreated": "timestamp",
    "DateLastUsed": "timestamp",
    "ExpiresTime": "timestamp",
    "Scopes": ["string"]
}
```

---

### 13.7 `list-personal-access-tokens`

Lists personal access tokens for an organization. **Paginated operation.**

**Synopsis:**
```bash
aws workmail list-personal-access-tokens \
    --organization-id <value> \
    [--user-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--user-id` | No | string | None | Filter by user ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Size of each page |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "PersonalAccessTokenSummaries": [
        {
            "PersonalAccessTokenId": "string",
            "UserId": "string",
            "Name": "string",
            "DateCreated": "timestamp",
            "DateLastUsed": "timestamp",
            "ExpiresTime": "timestamp",
            "Scopes": ["string"]
        }
    ],
    "NextToken": "string"
}
```

---

### 13.8 `delete-personal-access-token`

Deletes a personal access token.

**Synopsis:**
```bash
aws workmail delete-personal-access-token \
    --organization-id <value> \
    --personal-access-token-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--personal-access-token-id` | **Yes** | string | -- | Token ID to delete |

**Output:** None
