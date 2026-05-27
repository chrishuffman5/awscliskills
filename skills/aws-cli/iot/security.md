# Security

## 8.1 `create-authorizer`

Creates a custom authorizer for authenticating MQTT connections.

**Synopsis:**
```bash
aws iot create-authorizer \
    --authorizer-name <value> \
    --authorizer-function-arn <value> \
    [--token-key-name <value>] \
    [--token-signing-public-keys <value>] \
    [--status <value>] \
    [--tags <value>] \
    [--signing-disabled | --no-signing-disabled] \
    [--enable-caching-for-http | --no-enable-caching-for-http] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--authorizer-name` | **Yes** | string | -- | Authorizer name (1-128 chars) |
| `--authorizer-function-arn` | **Yes** | string | -- | Lambda function ARN |
| `--token-key-name` | No | string | None | Token header key name |
| `--token-signing-public-keys` | No | map | None | Public keys for token verification |
| `--status` | No | string | None | `ACTIVE` or `INACTIVE` |
| `--tags` | No | list | None | Tags |
| `--signing-disabled` | No | boolean | false | Disable token signing |
| `--enable-caching-for-http` | No | boolean | false | Enable caching for HTTP authorizer |

**Output Schema:**
```json
{
    "authorizerName": "string",
    "authorizerArn": "string"
}
```

---

## 8.2 `describe-authorizer`

Describes a custom authorizer.

**Synopsis:**
```bash
aws iot describe-authorizer \
    --authorizer-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--authorizer-name` | **Yes** | string | -- | Authorizer name |

**Output Schema:**
```json
{
    "authorizerDescription": {
        "authorizerName": "string",
        "authorizerArn": "string",
        "authorizerFunctionArn": "string",
        "tokenKeyName": "string",
        "tokenSigningPublicKeys": {},
        "status": "ACTIVE|INACTIVE",
        "creationDate": "timestamp",
        "lastModifiedDate": "timestamp",
        "signingDisabled": "boolean",
        "enableCachingForHttp": "boolean"
    }
}
```

---

## 8.3 `list-authorizers`

Lists custom authorizers. **Paginated operation.**

**Synopsis:**
```bash
aws iot list-authorizers \
    [--page-size <value>] \
    [--marker <value>] \
    [--ascending-order | --no-ascending-order] \
    [--status <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--page-size` | No | integer | None | Max results per page |
| `--marker` | No | string | None | Pagination marker |
| `--ascending-order` | No | boolean | false | Sort ascending |
| `--status` | No | string | None | Filter: `ACTIVE` or `INACTIVE` |

**Output Schema:**
```json
{
    "authorizers": [
        {
            "authorizerName": "string",
            "authorizerArn": "string"
        }
    ],
    "nextMarker": "string"
}
```

---

## 8.4 `update-authorizer`

Updates a custom authorizer.

**Synopsis:**
```bash
aws iot update-authorizer \
    --authorizer-name <value> \
    [--authorizer-function-arn <value>] \
    [--token-key-name <value>] \
    [--token-signing-public-keys <value>] \
    [--status <value>] \
    [--enable-caching-for-http | --no-enable-caching-for-http] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--authorizer-name` | **Yes** | string | -- | Authorizer name |
| `--authorizer-function-arn` | No | string | None | Updated Lambda ARN |
| `--token-key-name` | No | string | None | Updated token key name |
| `--token-signing-public-keys` | No | map | None | Updated public keys |
| `--status` | No | string | None | `ACTIVE` or `INACTIVE` |
| `--enable-caching-for-http` | No | boolean | None | Enable/disable caching |

**Output Schema:**
```json
{
    "authorizerName": "string",
    "authorizerArn": "string"
}
```

---

## 8.5 `delete-authorizer`

Deletes a custom authorizer.

**Synopsis:**
```bash
aws iot delete-authorizer \
    --authorizer-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--authorizer-name` | **Yes** | string | -- | Authorizer name |

**Output:** None

---

## 8.6 `set-default-authorizer`

Sets the default custom authorizer.

**Synopsis:**
```bash
aws iot set-default-authorizer \
    --authorizer-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--authorizer-name` | **Yes** | string | -- | Authorizer name |

**Output Schema:**
```json
{
    "authorizerName": "string",
    "authorizerArn": "string"
}
```

---

## 8.7 `clear-default-authorizer`

Clears the default custom authorizer.

**Synopsis:**
```bash
aws iot clear-default-authorizer \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output:** None

---

## 8.8 `describe-default-authorizer`

Describes the default custom authorizer.

**Synopsis:**
```bash
aws iot describe-default-authorizer \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output Schema:**
```json
{
    "authorizerDescription": {
        "authorizerName": "string",
        "authorizerArn": "string",
        "authorizerFunctionArn": "string",
        "tokenKeyName": "string",
        "tokenSigningPublicKeys": {},
        "status": "ACTIVE|INACTIVE",
        "creationDate": "timestamp",
        "lastModifiedDate": "timestamp",
        "signingDisabled": "boolean",
        "enableCachingForHttp": "boolean"
    }
}
```

---

## 8.9 `test-invoke-authorizer`

Tests invoking a custom authorizer.

**Synopsis:**
```bash
aws iot test-invoke-authorizer \
    --authorizer-name <value> \
    [--token <value>] \
    [--token-signature <value>] \
    [--http-context <value>] \
    [--mqtt-context <value>] \
    [--tls-context <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--authorizer-name` | **Yes** | string | -- | Authorizer name |
| `--token` | No | string | None | Token value |
| `--token-signature` | No | string | None | Token signature |
| `--http-context` | No | structure | None | HTTP request context (headers, queryString) |
| `--mqtt-context` | No | structure | None | MQTT context (username, password, clientId) |
| `--tls-context` | No | structure | None | TLS context (serverName) |

**Output Schema:**
```json
{
    "isAuthenticated": "boolean",
    "principalId": "string",
    "policyDocuments": ["string"],
    "refreshAfterInSeconds": "integer",
    "disconnectAfterInSeconds": "integer"
}
```

---

## 8.10 `create-domain-configuration`

Creates a custom domain configuration for IoT endpoints.

**Synopsis:**
```bash
aws iot create-domain-configuration \
    --domain-configuration-name <value> \
    [--domain-name <value>] \
    [--server-certificate-arns <value>] \
    [--authorizer-config <value>] \
    [--service-type <value>] \
    [--tags <value>] \
    [--tls-config <value>] \
    [--server-certificate-config <value>] \
    [--authentication-type <value>] \
    [--application-protocol <value>] \
    [--client-certificate-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-configuration-name` | **Yes** | string | -- | Domain config name (1-128 chars) |
| `--domain-name` | No | string | None | Custom domain name |
| `--server-certificate-arns` | No | list | None | ACM certificate ARNs |
| `--authorizer-config` | No | structure | None | Custom authorizer config |
| `--service-type` | No | string | None | `DATA`, `CREDENTIAL_PROVIDER`, `JOBS` |
| `--tags` | No | list | None | Tags |
| `--tls-config` | No | structure | None | TLS configuration |
| `--server-certificate-config` | No | structure | None | Server certificate config |
| `--authentication-type` | No | string | None | Authentication type |
| `--application-protocol` | No | string | None | Application protocol |
| `--client-certificate-config` | No | structure | None | Client certificate config |

**Output Schema:**
```json
{
    "domainConfigurationName": "string",
    "domainConfigurationArn": "string"
}
```

---

## 8.11 `describe-domain-configuration`

Describes a domain configuration.

**Synopsis:**
```bash
aws iot describe-domain-configuration \
    --domain-configuration-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-configuration-name` | **Yes** | string | -- | Domain config name |

**Output Schema:**
```json
{
    "domainConfigurationName": "string",
    "domainConfigurationArn": "string",
    "domainName": "string",
    "serverCertificates": [{"serverCertificateArn": "string", "serverCertificateStatus": "string", "serverCertificateStatusDetail": "string"}],
    "authorizerConfig": {"defaultAuthorizerName": "string", "allowAuthorizerOverride": "boolean"},
    "domainConfigurationStatus": "ENABLED|DISABLED",
    "serviceType": "DATA|CREDENTIAL_PROVIDER|JOBS",
    "domainType": "ENDPOINT|AWS_MANAGED|CUSTOMER_MANAGED",
    "lastStatusChangeDate": "timestamp",
    "tlsConfig": {},
    "serverCertificateConfig": {},
    "authenticationType": "string",
    "applicationProtocol": "string",
    "clientCertificateConfig": {}
}
```

---

## 8.12 `list-domain-configurations`

Lists domain configurations. **Paginated operation.**

**Synopsis:**
```bash
aws iot list-domain-configurations \
    [--marker <value>] \
    [--page-size <value>] \
    [--service-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--marker` | No | string | None | Pagination marker |
| `--page-size` | No | integer | None | Max results |
| `--service-type` | No | string | None | Filter: `DATA`, `CREDENTIAL_PROVIDER`, `JOBS` |

**Output Schema:**
```json
{
    "domainConfigurations": [
        {
            "domainConfigurationName": "string",
            "domainConfigurationArn": "string",
            "serviceType": "string"
        }
    ],
    "nextMarker": "string"
}
```

---

## 8.13 `update-domain-configuration`

Updates a domain configuration.

**Synopsis:**
```bash
aws iot update-domain-configuration \
    --domain-configuration-name <value> \
    [--authorizer-config <value>] \
    [--domain-configuration-status <value>] \
    [--remove-authorizer-config | --no-remove-authorizer-config] \
    [--tls-config <value>] \
    [--server-certificate-config <value>] \
    [--authentication-type <value>] \
    [--application-protocol <value>] \
    [--client-certificate-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-configuration-name` | **Yes** | string | -- | Domain config name |
| `--authorizer-config` | No | structure | None | Updated authorizer config |
| `--domain-configuration-status` | No | string | None | `ENABLED` or `DISABLED` |
| `--remove-authorizer-config` | No | boolean | false | Remove authorizer config |
| `--tls-config` | No | structure | None | Updated TLS config |
| `--server-certificate-config` | No | structure | None | Updated server cert config |
| `--authentication-type` | No | string | None | Updated auth type |
| `--application-protocol` | No | string | None | Updated app protocol |
| `--client-certificate-config` | No | structure | None | Updated client cert config |

**Output Schema:**
```json
{
    "domainConfigurationName": "string",
    "domainConfigurationArn": "string"
}
```

---

## 8.14 `delete-domain-configuration`

Deletes a domain configuration.

**Synopsis:**
```bash
aws iot delete-domain-configuration \
    --domain-configuration-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-configuration-name` | **Yes** | string | -- | Domain config name |

**Output:** None

---

## 8.15 `create-role-alias`

Creates a role alias for credentials provider.

**Synopsis:**
```bash
aws iot create-role-alias \
    --role-alias <value> \
    --role-arn <value> \
    [--credential-duration-seconds <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--role-alias` | **Yes** | string | -- | Role alias name (1-128 chars) |
| `--role-arn` | **Yes** | string | -- | IAM role ARN |
| `--credential-duration-seconds` | No | integer | 3600 | Duration (900-43200 seconds) |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "roleAlias": "string",
    "roleAliasArn": "string"
}
```

---

## 8.16 `describe-role-alias`

Describes a role alias.

**Synopsis:**
```bash
aws iot describe-role-alias \
    --role-alias <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--role-alias` | **Yes** | string | -- | Role alias name |

**Output Schema:**
```json
{
    "roleAliasDescription": {
        "roleAlias": "string",
        "roleAliasArn": "string",
        "roleArn": "string",
        "owner": "string",
        "credentialDurationSeconds": "integer",
        "creationDate": "timestamp",
        "lastModifiedDate": "timestamp"
    }
}
```

---

## 8.17 `list-role-aliases`

Lists role aliases. **Paginated operation.**

**Synopsis:**
```bash
aws iot list-role-aliases \
    [--page-size <value>] \
    [--marker <value>] \
    [--ascending-order | --no-ascending-order] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--page-size` | No | integer | None | Max results per page |
| `--marker` | No | string | None | Pagination marker |
| `--ascending-order` | No | boolean | false | Sort ascending |

**Output Schema:**
```json
{
    "roleAliases": ["string"],
    "nextMarker": "string"
}
```

---

## 8.18 `update-role-alias`

Updates a role alias.

**Synopsis:**
```bash
aws iot update-role-alias \
    --role-alias <value> \
    [--role-arn <value>] \
    [--credential-duration-seconds <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--role-alias` | **Yes** | string | -- | Role alias name |
| `--role-arn` | No | string | None | Updated IAM role ARN |
| `--credential-duration-seconds` | No | integer | None | Updated duration (900-43200) |

**Output Schema:**
```json
{
    "roleAlias": "string",
    "roleAliasArn": "string"
}
```

---

## 8.19 `delete-role-alias`

Deletes a role alias.

**Synopsis:**
```bash
aws iot delete-role-alias \
    --role-alias <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--role-alias` | **Yes** | string | -- | Role alias name |

**Output:** None

---

## 8.20 `describe-endpoint`

Describes the IoT endpoint for a specific endpoint type.

**Synopsis:**
```bash
aws iot describe-endpoint \
    [--endpoint-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--endpoint-type` | No | string | None | `iot:Data-ATS`, `iot:Data`, `iot:CredentialProvider`, `iot:Jobs` |

**Output Schema:**
```json
{
    "endpointAddress": "string"
}
```

---

## 8.21 `describe-event-configurations`

Describes event configurations.

**Synopsis:**
```bash
aws iot describe-event-configurations \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output Schema:**
```json
{
    "eventConfigurations": {
        "THING|THING_GROUP|THING_TYPE|THING_GROUP_MEMBERSHIP|THING_GROUP_HIERARCHY|THING_TYPE_ASSOCIATION|JOB|JOB_EXECUTION|POLICY|CERTIFICATE|CA_CERTIFICATE": {
            "Enabled": "boolean"
        }
    },
    "creationDate": "timestamp",
    "lastModifiedDate": "timestamp"
}
```

---

## 8.22 `update-event-configurations`

Updates event configurations.

**Synopsis:**
```bash
aws iot update-event-configurations \
    [--event-configurations <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--event-configurations` | No | map | None | Map of event type to {Enabled: boolean} |

**Output:** None

---

## 8.23 `describe-encryption-configuration`

Describes the IoT encryption configuration (customer-managed KMS key).

**Synopsis:**
```bash
aws iot describe-encryption-configuration \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output Schema:**
```json
{
    "kmsKeyId": "string"
}
```

---

## 8.24 `update-encryption-configuration`

Updates the IoT encryption configuration.

**Synopsis:**
```bash
aws iot update-encryption-configuration \
    --kms-key-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--kms-key-id` | **Yes** | string | -- | KMS key ARN or alias |

**Output Schema:**
```json
{
    "kmsKeyId": "string"
}
```
