# Domains

### 8.1 `create-user-pool-domain`

Creates a domain for the hosted UI. Can be a Cognito-managed domain (prefix) or a custom domain with an ACM certificate.

**Synopsis:**
```bash
aws cognito-idp create-user-pool-domain \
    --domain <value> \
    --user-pool-id <value> \
    [--custom-domain-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Domain prefix (for Cognito domain: `my-app`) or full custom domain (e.g., `auth.example.com`) |
| `--user-pool-id` | **Yes** | string | -- | ID of the user pool |
| `--custom-domain-config` | Cond. | structure | None | Required for custom domains. Shorthand: `CertificateArn=arn:aws:acm:us-east-1:123456789012:certificate/abc123` |

**Output Schema:**
```json
{
    "CloudFrontDomain": "string"
}
```

Cognito domain URL format: `https://<domain-prefix>.auth.<region>.amazoncognito.com`

---

### 8.2 `delete-user-pool-domain`

Deletes a user pool domain.

**Synopsis:**
```bash
aws cognito-idp delete-user-pool-domain \
    --domain <value> \
    --user-pool-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Domain to delete |
| `--user-pool-id` | **Yes** | string | -- | ID of the user pool |

**Output:** None

---

### 8.3 `describe-user-pool-domain`

Gets information about a user pool domain.

**Synopsis:**
```bash
aws cognito-idp describe-user-pool-domain \
    --domain <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Domain name |

**Output Schema:**
```json
{
    "DomainDescription": {
        "UserPoolId": "string",
        "AWSAccountId": "string",
        "Domain": "string",
        "S3Bucket": "string",
        "CloudFrontDistribution": "string",
        "Version": "string",
        "Status": "CREATING|DELETING|UPDATING|ACTIVE|FAILED",
        "CustomDomainConfig": {
            "CertificateArn": "string"
        }
    }
}
```

---

### 8.4 `update-user-pool-domain`

Updates the certificate for a custom domain.

**Synopsis:**
```bash
aws cognito-idp update-user-pool-domain \
    --domain <value> \
    --user-pool-id <value> \
    --custom-domain-config <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Custom domain name |
| `--user-pool-id` | **Yes** | string | -- | ID of the user pool |
| `--custom-domain-config` | **Yes** | structure | -- | Updated certificate. Shorthand: `CertificateArn=arn:aws:acm:us-east-1:123456789012:certificate/abc123` |

**Output Schema:**
```json
{
    "CloudFrontDomain": "string"
}
```
