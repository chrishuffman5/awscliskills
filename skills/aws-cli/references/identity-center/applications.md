# Applications

### 5.1 `create-application`

Creates an OAuth 2.0 application in IAM Identity Center.

**Synopsis:**
```bash
aws sso-admin create-application \
    --instance-arn <value> \
    --application-provider-arn <value> \
    --name <value> \
    [--description <value>] \
    [--portal-options <value>] \
    [--tags <value>] \
    [--status <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-arn` | **Yes** | string | -- | ARN of the Identity Center instance |
| `--application-provider-arn` | **Yes** | string | -- | ARN of the application provider |
| `--name` | **Yes** | string | -- | Application name (1-100 chars) |
| `--description` | No | string | None | Description (1-128 chars) |
| `--portal-options` | No | structure | None | Portal visibility and sign-in options |
| `--tags` | No | list(structure) | None | Tags (max 75) |
| `--status` | No | string | None | `ENABLED` or `DISABLED` |
| `--client-token` | No | string | None | Idempotency token |

**Portal Options Structure:**
```json
{
    "SignInOptions": {
        "Origin": "IDENTITY_CENTER|APPLICATION",
        "ApplicationUrl": "string"
    },
    "Visibility": "ENABLED|DISABLED"
}
```

**Output Schema:**
```json
{
    "ApplicationArn": "string"
}
```

---

### 5.2 `delete-application`

Deletes an application from IAM Identity Center.

**Synopsis:**
```bash
aws sso-admin delete-application \
    --application-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-arn` | **Yes** | string | -- | ARN of the application to delete |

**Output Schema:**

No output on success (HTTP 200).

---

### 5.3 `describe-application`

Describes an application.

**Synopsis:**
```bash
aws sso-admin describe-application \
    --application-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-arn` | **Yes** | string | -- | ARN of the application |

**Output Schema:**
```json
{
    "ApplicationArn": "string",
    "ApplicationProviderArn": "string",
    "Name": "string",
    "Description": "string",
    "InstanceArn": "string",
    "Status": "ENABLED|DISABLED",
    "PortalOptions": {
        "SignInOptions": {
            "Origin": "IDENTITY_CENTER|APPLICATION",
            "ApplicationUrl": "string"
        },
        "Visibility": "ENABLED|DISABLED"
    },
    "CreatedDate": "timestamp"
}
```

---

### 5.4 `update-application`

Updates an application in IAM Identity Center.

**Synopsis:**
```bash
aws sso-admin update-application \
    --application-arn <value> \
    [--name <value>] \
    [--description <value>] \
    [--status <value>] \
    [--portal-options <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-arn` | **Yes** | string | -- | ARN of the application |
| `--name` | No | string | None | Updated name |
| `--description` | No | string | None | Updated description |
| `--status` | No | string | None | `ENABLED` or `DISABLED` |
| `--portal-options` | No | structure | None | Updated portal options |

**Output Schema:**

No output on success (HTTP 200).

---

### 5.5 `list-applications`

Lists all applications in an Identity Center instance. **Paginated operation.**

**Synopsis:**
```bash
aws sso-admin list-applications \
    --instance-arn <value> \
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
| `--instance-arn` | **Yes** | string | -- | ARN of the instance |
| `--filter` | No | structure | None | Filter by application account or provider ARN |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Applications": [
        {
            "ApplicationArn": "string",
            "ApplicationProviderArn": "string",
            "Name": "string",
            "Description": "string",
            "InstanceArn": "string",
            "Status": "ENABLED|DISABLED",
            "PortalOptions": {},
            "CreatedDate": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 5.6 `list-application-providers`

Lists all available application providers. **Paginated operation.**

**Synopsis:**
```bash
aws sso-admin list-application-providers \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ApplicationProviders": [
        {
            "ApplicationProviderArn": "string",
            "DisplayData": {
                "DisplayName": "string",
                "IconUrl": "string",
                "Description": "string"
            },
            "FederationProtocol": "SAML|OAUTH",
            "ResourceServerConfig": {
                "Scopes": {
                    "string": {
                        "LongDescription": "string",
                        "DetailedTitle": "string"
                    }
                }
            }
        }
    ],
    "NextToken": "string"
}
```

---

### 5.7 `create-application-assignment`

Assigns a user or group to an application.

**Synopsis:**
```bash
aws sso-admin create-application-assignment \
    --application-arn <value> \
    --principal-id <value> \
    --principal-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-arn` | **Yes** | string | -- | ARN of the application |
| `--principal-id` | **Yes** | string | -- | GUID of the user or group |
| `--principal-type` | **Yes** | string | -- | `USER` or `GROUP` |

**Output Schema:**

No output on success (HTTP 200).

---

### 5.8 `delete-application-assignment`

Deletes a user or group assignment from an application.

**Synopsis:**
```bash
aws sso-admin delete-application-assignment \
    --application-arn <value> \
    --principal-id <value> \
    --principal-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-arn` | **Yes** | string | -- | ARN of the application |
| `--principal-id` | **Yes** | string | -- | GUID of the user or group |
| `--principal-type` | **Yes** | string | -- | `USER` or `GROUP` |

**Output Schema:**

No output on success (HTTP 200).

---

### 5.9 `describe-application-assignment`

Describes an application assignment.

**Synopsis:**
```bash
aws sso-admin describe-application-assignment \
    --application-arn <value> \
    --principal-id <value> \
    --principal-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-arn` | **Yes** | string | -- | ARN of the application |
| `--principal-id` | **Yes** | string | -- | GUID of the user or group |
| `--principal-type` | **Yes** | string | -- | `USER` or `GROUP` |

**Output Schema:**
```json
{
    "ApplicationArn": "string",
    "PrincipalId": "string",
    "PrincipalType": "USER|GROUP"
}
```

---

### 5.10 `list-application-assignments`

Lists assignments for an application. **Paginated operation.**

**Synopsis:**
```bash
aws sso-admin list-application-assignments \
    --application-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-arn` | **Yes** | string | -- | ARN of the application |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ApplicationAssignments": [
        {
            "ApplicationArn": "string",
            "PrincipalId": "string",
            "PrincipalType": "USER|GROUP"
        }
    ],
    "NextToken": "string"
}
```

---

### 5.11 `list-application-assignments-for-principal`

Lists all application assignments for a specific user or group. **Paginated operation.**

**Synopsis:**
```bash
aws sso-admin list-application-assignments-for-principal \
    --instance-arn <value> \
    --principal-id <value> \
    --principal-type <value> \
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
| `--instance-arn` | **Yes** | string | -- | ARN of the instance |
| `--principal-id` | **Yes** | string | -- | GUID of the user or group |
| `--principal-type` | **Yes** | string | -- | `USER` or `GROUP` |
| `--filter` | No | structure | None | Filter by application ARN |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ApplicationAssignments": [
        {
            "ApplicationArn": "string",
            "PrincipalId": "string",
            "PrincipalType": "USER|GROUP"
        }
    ],
    "NextToken": "string"
}
```
