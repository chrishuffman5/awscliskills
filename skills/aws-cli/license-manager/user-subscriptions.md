# User Subscriptions

> All commands in this file use the `aws license-manager-user-subscriptions` namespace.

### 9.1 `register-identity-provider`

Registers an identity provider (Active Directory) for user-based subscriptions.

**Synopsis:**
```bash
aws license-manager-user-subscriptions register-identity-provider \
    --identity-provider <value> \
    --product <value> \
    [--settings <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identity-provider` | **Yes** | tagged union | -- | Identity provider details (only `ActiveDirectoryIdentityProvider` supported) |
| `--product` | **Yes** | string | -- | Product: `VISUAL_STUDIO_ENTERPRISE`, `VISUAL_STUDIO_PROFESSIONAL`, `OFFICE_PROFESSIONAL_PLUS`, `REMOTE_DESKTOP_SERVICES` |
| `--settings` | No | structure | None | Settings with `Subnets` and `SecurityGroupId` for VPC endpoints |
| `--tags` | No | map | None | Tags (max 50) |

**Identity Provider Structure:**
```json
{
    "ActiveDirectoryIdentityProvider": {
        "DirectoryId": "string",
        "ActiveDirectorySettings": {
            "DomainName": "string",
            "DomainIpv4List": ["string"],
            "DomainCredentialsProvider": {
                "SecretsManagerCredentialsProvider": {
                    "SecretId": "string"
                }
            }
        },
        "ActiveDirectoryType": "SELF_MANAGED|AWS_MANAGED"
    }
}
```

**Output Schema:**
```json
{
    "IdentityProviderSummary": {
        "IdentityProvider": {},
        "Settings": {
            "Subnets": ["string"],
            "SecurityGroupId": "string"
        },
        "Product": "string",
        "Status": "string",
        "IdentityProviderArn": "string",
        "FailureMessage": "string"
    }
}
```

---

### 9.2 `deregister-identity-provider`

Deregisters an identity provider.

**Synopsis:**
```bash
aws license-manager-user-subscriptions deregister-identity-provider \
    [--identity-provider <value>] \
    [--product <value>] \
    [--identity-provider-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identity-provider` | No | tagged union | None | Identity provider to deregister |
| `--product` | No | string | None | Product name |
| `--identity-provider-arn` | No | string | None | ARN of the identity provider |

**Output Schema:**
```json
{
    "IdentityProviderSummary": {
        "IdentityProvider": {},
        "Product": "string",
        "Status": "string",
        "IdentityProviderArn": "string"
    }
}
```

---

### 9.3 `list-identity-providers`

Lists registered identity providers. **Paginated operation.**

**Synopsis:**
```bash
aws license-manager-user-subscriptions list-identity-providers \
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
| `--filters` | No | list | None | Filters to scope results |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "IdentityProviderSummaries": [
        {
            "IdentityProvider": {},
            "Product": "string",
            "Status": "string",
            "IdentityProviderArn": "string",
            "FailureMessage": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 9.4 `update-identity-provider-settings`

Updates identity provider settings.

**Synopsis:**
```bash
aws license-manager-user-subscriptions update-identity-provider-settings \
    --identity-provider <value> \
    --product <value> \
    [--update-settings <value>] \
    [--identity-provider-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identity-provider` | **Yes** | tagged union | -- | Identity provider to update |
| `--product` | **Yes** | string | -- | Product name |
| `--update-settings` | No | structure | None | Updated settings (subnets, security group) |
| `--identity-provider-arn` | No | string | None | ARN of the identity provider |

**Output Schema:**
```json
{
    "IdentityProviderSummary": {
        "IdentityProvider": {},
        "Product": "string",
        "Status": "string",
        "IdentityProviderArn": "string"
    }
}
```

---

### 9.5 `associate-user`

Associates a user with an EC2 instance for user-based subscriptions.

**Synopsis:**
```bash
aws license-manager-user-subscriptions associate-user \
    --username <value> \
    --instance-id <value> \
    --identity-provider <value> \
    [--domain <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--username` | **Yes** | string | -- | User name from the identity provider |
| `--instance-id` | **Yes** | string | -- | EC2 instance ID providing the subscription |
| `--identity-provider` | **Yes** | tagged union | -- | Identity provider details |
| `--domain` | No | string | None | Active Directory domain name |
| `--tags` | No | map | None | Tags (max 50) |

**Output Schema:**
```json
{
    "InstanceUserSummary": {
        "Username": "string",
        "InstanceId": "string",
        "IdentityProvider": {},
        "Status": "string",
        "InstanceUserArn": "string",
        "StatusMessage": "string",
        "Domain": "string",
        "AssociationDate": "string",
        "DisassociationDate": "string"
    }
}
```

---

### 9.6 `disassociate-user`

Disassociates a user from an EC2 instance.

**Synopsis:**
```bash
aws license-manager-user-subscriptions disassociate-user \
    [--username <value>] \
    [--instance-id <value>] \
    [--identity-provider <value>] \
    [--domain <value>] \
    [--instance-user-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--username` | No | string | None | User name |
| `--instance-id` | No | string | None | EC2 instance ID |
| `--identity-provider` | No | tagged union | None | Identity provider |
| `--domain` | No | string | None | Active Directory domain name |
| `--instance-user-arn` | No | string | None | ARN of the user-instance association |

**Output Schema:**
```json
{
    "InstanceUserSummary": {
        "Username": "string",
        "InstanceId": "string",
        "IdentityProvider": {},
        "Status": "string",
        "InstanceUserArn": "string"
    }
}
```

---

### 9.7 `list-user-associations`

Lists user associations. **Paginated operation.**

**Synopsis:**
```bash
aws license-manager-user-subscriptions list-user-associations \
    --instance-id <value> \
    [--identity-provider <value>] \
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
| `--instance-id` | **Yes** | string | -- | EC2 instance ID |
| `--identity-provider` | No | tagged union | None | Identity provider |
| `--filters` | No | list | None | Filters to scope results |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "InstanceUserSummaries": [],
    "NextToken": "string"
}
```

---

### 9.8 `list-instances`

Lists EC2 instances with user-based subscriptions. **Paginated operation.**

**Synopsis:**
```bash
aws license-manager-user-subscriptions list-instances \
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
| `--filters` | No | list | None | Filters to scope results |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "InstanceSummaries": [
        {
            "InstanceId": "string",
            "Status": "string",
            "StatusMessage": "string",
            "Products": ["string"],
            "LastStatusCheckDate": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 9.9 `list-product-subscriptions`

Lists product subscriptions. **Paginated operation.**

**Synopsis:**
```bash
aws license-manager-user-subscriptions list-product-subscriptions \
    --identity-provider <value> \
    --product <value> \
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
| `--identity-provider` | **Yes** | tagged union | -- | Identity provider |
| `--product` | **Yes** | string | -- | Product name |
| `--filters` | No | list | None | Filters to scope results |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ProductUserSummaries": [
        {
            "Username": "string",
            "Product": "string",
            "IdentityProvider": {},
            "Status": "string",
            "ProductUserArn": "string",
            "Domain": "string",
            "SubscriptionStartDate": "string",
            "SubscriptionEndDate": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 9.10 `start-product-subscription`

Starts a product subscription for a user.

**Synopsis:**
```bash
aws license-manager-user-subscriptions start-product-subscription \
    --username <value> \
    --identity-provider <value> \
    --product <value> \
    [--domain <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--username` | **Yes** | string | -- | User name from the identity provider |
| `--identity-provider` | **Yes** | tagged union | -- | Identity provider details |
| `--product` | **Yes** | string | -- | Product: `VISUAL_STUDIO_ENTERPRISE`, `VISUAL_STUDIO_PROFESSIONAL`, `OFFICE_PROFESSIONAL_PLUS`, `REMOTE_DESKTOP_SERVICES` |
| `--domain` | No | string | None | Active Directory domain name |
| `--tags` | No | map | None | Tags (max 50) |

**Output Schema:**
```json
{
    "ProductUserSummary": {
        "Username": "string",
        "Product": "string",
        "IdentityProvider": {},
        "Status": "string",
        "ProductUserArn": "string",
        "Domain": "string",
        "SubscriptionStartDate": "string",
        "SubscriptionEndDate": "string"
    }
}
```

---

### 9.11 `stop-product-subscription`

Stops a product subscription.

**Synopsis:**
```bash
aws license-manager-user-subscriptions stop-product-subscription \
    [--username <value>] \
    [--identity-provider <value>] \
    [--product <value>] \
    [--domain <value>] \
    [--product-user-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--username` | No | string | None | User name |
| `--identity-provider` | No | tagged union | None | Identity provider |
| `--product` | No | string | None | Product name |
| `--domain` | No | string | None | Active Directory domain name |
| `--product-user-arn` | No | string | None | ARN of the product user subscription |

**Output Schema:**
```json
{
    "ProductUserSummary": {
        "Username": "string",
        "Product": "string",
        "IdentityProvider": {},
        "Status": "string",
        "ProductUserArn": "string"
    }
}
```

---

### 9.12 `create-license-server-endpoint`

Creates a license server endpoint for Remote Desktop Services.

**Synopsis:**
```bash
aws license-manager-user-subscriptions create-license-server-endpoint \
    --identity-provider-arn <value> \
    --license-server-settings <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--identity-provider-arn` | **Yes** | string | -- | ARN of the identity provider |
| `--license-server-settings` | **Yes** | structure | -- | License server settings with `ServerType` and `ServerSettings` |
| `--tags` | No | map | None | Tags (max 50) |

**License Server Settings Structure:**
```json
{
    "ServerType": "RDS_SAL",
    "ServerSettings": {
        "RdsSalSettings": {
            "RdsSalCredentialsProvider": {
                "SecretsManagerCredentialsProvider": {
                    "SecretId": "string"
                }
            }
        }
    }
}
```

**Output Schema:**
```json
{
    "IdentityProviderArn": "string",
    "LicenseServerEndpointArn": "string"
}
```

---

### 9.13 `delete-license-server-endpoint`

Deletes a license server endpoint.

**Synopsis:**
```bash
aws license-manager-user-subscriptions delete-license-server-endpoint \
    --license-server-endpoint-arn <value> \
    --server-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--license-server-endpoint-arn` | **Yes** | string | -- | ARN of the license server endpoint |
| `--server-type` | **Yes** | string | -- | Server type: `RDS_SAL` |

**Output Schema:**
```json
{
    "LicenseServerEndpoint": {
        "LicenseServerEndpointArn": "string",
        "IdentityProviderArn": "string",
        "LicenseServerEndpointId": "string",
        "Status": "string",
        "StatusMessage": "string",
        "ServerType": "RDS_SAL",
        "LicenseServers": [],
        "CreationTime": "string"
    }
}
```

---

### 9.14 `list-license-server-endpoints`

Lists license server endpoints. **Paginated operation.**

**Synopsis:**
```bash
aws license-manager-user-subscriptions list-license-server-endpoints \
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
| `--filters` | No | list | None | Filters: `IdentityProviderArn` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "LicenseServerEndpoints": [
        {
            "LicenseServerEndpointArn": "string",
            "IdentityProviderArn": "string",
            "LicenseServerEndpointId": "string",
            "Status": "string",
            "ServerType": "RDS_SAL",
            "LicenseServers": [],
            "CreationTime": "string"
        }
    ],
    "NextToken": "string"
}
```
