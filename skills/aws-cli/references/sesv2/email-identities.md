# Email Identities

### 1.1 `create-email-identity`

Creates an email identity (email address or domain). For domains, returns DKIM tokens for DNS configuration.

**Synopsis:**
```bash
aws sesv2 create-email-identity \
    --email-identity <value> \
    [--tags <value>] \
    [--dkim-signing-attributes <value>] \
    [--configuration-set-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--email-identity` | **Yes** | string | -- | Email address or domain to verify |
| `--tags` | No | list | None | Tags to apply. Shorthand: `Key=string,Value=string ...` |
| `--dkim-signing-attributes` | No | structure | None | DKIM signing configuration for BYODKIM |
| `--configuration-set-name` | No | string | None | Default configuration set for the identity |

**DKIM Signing Attributes Structure:**
```json
{
    "DomainSigningSelector": "string",
    "DomainSigningPrivateKey": "string",
    "NextSigningKeyLength": "RSA_1024_BIT|RSA_2048_BIT"
}
```

**Output Schema:**
```json
{
    "IdentityType": "EMAIL_ADDRESS|DOMAIN|MANAGED_DOMAIN",
    "VerifiedForSendingStatus": true|false,
    "DkimAttributes": {
        "SigningEnabled": true|false,
        "Status": "PENDING|SUCCESS|FAILED|TEMPORARY_FAILURE|NOT_STARTED",
        "Tokens": ["string"],
        "SigningAttributesOrigin": "AWS_SES|EXTERNAL|AWS_SES_AF_SOUTH_1|AWS_SES_EU_NORTH_1|AWS_SES_AP_SOUTH_2",
        "NextSigningKeyLength": "RSA_1024_BIT|RSA_2048_BIT",
        "CurrentSigningKeyLength": "RSA_1024_BIT|RSA_2048_BIT",
        "LastKeyGenerationTimestamp": "timestamp"
    }
}
```

---

### 1.2 `delete-email-identity`

Deletes an email identity. Also removes any authorization policies associated with the identity.

**Synopsis:**
```bash
aws sesv2 delete-email-identity \
    --email-identity <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--email-identity` | **Yes** | string | -- | Email identity to delete |

**Output Schema:**
```json
{}
```

---

### 1.3 `get-email-identity`

Provides information about a specific email identity, including verification status, DKIM configuration, and associated policies.

**Synopsis:**
```bash
aws sesv2 get-email-identity \
    --email-identity <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--email-identity` | **Yes** | string | -- | Email identity to retrieve |

**Output Schema:**
```json
{
    "IdentityType": "EMAIL_ADDRESS|DOMAIN|MANAGED_DOMAIN",
    "FeedbackForwardingStatus": true|false,
    "VerifiedForSendingStatus": true|false,
    "DkimAttributes": {
        "SigningEnabled": true|false,
        "Status": "PENDING|SUCCESS|FAILED|TEMPORARY_FAILURE|NOT_STARTED",
        "Tokens": ["string"],
        "SigningAttributesOrigin": "AWS_SES|EXTERNAL",
        "NextSigningKeyLength": "RSA_1024_BIT|RSA_2048_BIT",
        "CurrentSigningKeyLength": "RSA_1024_BIT|RSA_2048_BIT",
        "LastKeyGenerationTimestamp": "timestamp"
    },
    "MailFromAttributes": {
        "MailFromDomain": "string",
        "MailFromDomainStatus": "PENDING|SUCCESS|FAILED|TEMPORARY_FAILURE",
        "BehaviorOnMxFailure": "USE_DEFAULT_VALUE|REJECT_MESSAGE"
    },
    "Policies": {
        "PolicyName": "string"
    },
    "Tags": [
        {
            "Key": "string",
            "Value": "string"
        }
    ],
    "ConfigurationSetName": "string",
    "VerificationStatus": "PENDING|SUCCESS|FAILED|TEMPORARY_FAILURE|NOT_STARTED",
    "VerificationInfo": {
        "LastCheckedTimestamp": "timestamp",
        "LastSuccessTimestamp": "timestamp",
        "ErrorType": "SERVICE_ERROR|DNS_SERVER_ERROR|HOST_NOT_FOUND|TYPE_NOT_FOUND|INVALID_VALUE",
        "SOARecord": {
            "PrimaryNameServer": "string",
            "AdminEmail": "string",
            "SerialNumber": "long"
        }
    }
}
```

---

### 1.4 `list-email-identities`

Lists all email identities in the account. **Paginated operation.**

**Synopsis:**
```bash
aws sesv2 list-email-identities \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call (max 1000) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "EmailIdentities": [
        {
            "IdentityType": "EMAIL_ADDRESS|DOMAIN|MANAGED_DOMAIN",
            "IdentityName": "string",
            "SendingEnabled": true|false,
            "VerificationStatus": "PENDING|SUCCESS|FAILED|TEMPORARY_FAILURE|NOT_STARTED"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.5 `put-email-identity-dkim-signing-attributes`

Used to configure or change the DKIM authentication settings for an email identity. Supports Easy DKIM and BYODKIM.

**Synopsis:**
```bash
aws sesv2 put-email-identity-dkim-signing-attributes \
    --email-identity <value> \
    --signing-attributes-origin <value> \
    [--signing-attributes <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--email-identity` | **Yes** | string | -- | Email identity to configure |
| `--signing-attributes-origin` | **Yes** | string | -- | DKIM signing type: `AWS_SES` (Easy DKIM) or `EXTERNAL` (BYODKIM) |
| `--signing-attributes` | No | structure | None | DKIM signing key attributes |

**Signing Attributes Structure:**
```json
{
    "DomainSigningSelector": "string",
    "DomainSigningPrivateKey": "string",
    "NextSigningKeyLength": "RSA_1024_BIT|RSA_2048_BIT"
}
```

**Output Schema:**
```json
{
    "DkimStatus": "PENDING|SUCCESS|FAILED|TEMPORARY_FAILURE|NOT_STARTED",
    "DkimTokens": ["string"]
}
```

---

### 1.6 `put-email-identity-dkim-attributes`

Enable or disable DKIM signing for an email identity.

**Synopsis:**
```bash
aws sesv2 put-email-identity-dkim-attributes \
    --email-identity <value> \
    [--signing-enabled | --no-signing-enabled] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--email-identity` | **Yes** | string | -- | Email identity to configure |
| `--signing-enabled` | No | boolean | false | Enable DKIM signing |
| `--no-signing-enabled` | No | boolean | -- | Disable DKIM signing |

**Output Schema:**
```json
{}
```

---

### 1.7 `put-email-identity-feedback-attributes`

Enable or disable feedback forwarding for bounce and complaint notifications.

**Synopsis:**
```bash
aws sesv2 put-email-identity-feedback-attributes \
    --email-identity <value> \
    [--email-forwarding-enabled | --no-email-forwarding-enabled] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--email-identity` | **Yes** | string | -- | Email identity to configure |
| `--email-forwarding-enabled` | No | boolean | true | Enable email feedback forwarding |
| `--no-email-forwarding-enabled` | No | boolean | -- | Disable email feedback forwarding |

**Output Schema:**
```json
{}
```

---

### 1.8 `put-email-identity-mail-from-attributes`

Configure a custom MAIL FROM domain for an email identity.

**Synopsis:**
```bash
aws sesv2 put-email-identity-mail-from-attributes \
    --email-identity <value> \
    [--mail-from-domain <value>] \
    [--behavior-on-mx-failure <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--email-identity` | **Yes** | string | -- | Email identity to configure |
| `--mail-from-domain` | No | string | None | Custom MAIL FROM domain (must be subdomain of identity) |
| `--behavior-on-mx-failure` | No | string | `USE_DEFAULT_VALUE` | Action when MX record is missing: `USE_DEFAULT_VALUE` or `REJECT_MESSAGE` |

**Output Schema:**
```json
{}
```

---

### 1.9 `put-email-identity-configuration-set-attributes`

Associate a configuration set with an email identity. All emails sent using this identity will use the specified configuration set.

**Synopsis:**
```bash
aws sesv2 put-email-identity-configuration-set-attributes \
    --email-identity <value> \
    [--configuration-set-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--email-identity` | **Yes** | string | -- | Email identity to configure |
| `--configuration-set-name` | No | string | None | Configuration set name (omit to remove association) |

**Output Schema:**
```json
{}
```
