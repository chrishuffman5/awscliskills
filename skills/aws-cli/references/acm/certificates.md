# Certificates

### 1.1 `request-certificate`

Requests an ACM certificate for use with AWS services. Public certificates require domain validation (DNS or email). Private certificates require an ACM Private CA.

**Synopsis:**
```bash
aws acm request-certificate \
    --domain-name <value> \
    [--validation-method <value>] \
    [--subject-alternative-names <value>] \
    [--idempotency-token <value>] \
    [--domain-validation-options <value>] \
    [--options <value>] \
    [--certificate-authority-arn <value>] \
    [--tags <value>] \
    [--key-algorithm <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Fully qualified domain name (FQDN), max 253 chars. Use `*` for wildcard |
| `--validation-method` | No | string | `DNS` | Domain validation method: `DNS` or `EMAIL` |
| `--subject-alternative-names` | No | list(string) | None | Additional FQDNs for the certificate (max 100 total including domain-name) |
| `--idempotency-token` | No | string | None | Token for idempotent requests (max 32 chars) |
| `--domain-validation-options` | No | list | None | Override validation domain for EMAIL method. Shorthand: `DomainName=string,ValidationDomain=string` |
| `--options` | No | structure | None | Certificate options. Shorthand: `CertificateTransparencyLoggingPreference=ENABLED\|DISABLED` |
| `--certificate-authority-arn` | No | string | None | ARN of the ACM Private CA to issue a private certificate |
| `--tags` | No | list | None | Tags for the certificate. Shorthand: `Key=string,Value=string ...` |
| `--key-algorithm` | No | string | `RSA_2048` | Key algorithm: `RSA_1024`, `RSA_2048`, `RSA_3072`, `RSA_4096`, `EC_prime256v1`, `EC_secp384r1`, `EC_secp521r1` |

**Output Schema:**
```json
{
    "CertificateArn": "string"
}
```

---

### 1.2 `describe-certificate`

Returns detailed information about the specified certificate, including domain validation status, renewal information, and key details.

**Synopsis:**
```bash
aws acm describe-certificate \
    --certificate-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-arn` | **Yes** | string | -- | ARN of the certificate |

**Output Schema:**
```json
{
    "Certificate": {
        "CertificateArn": "string",
        "DomainName": "string",
        "SubjectAlternativeNames": ["string"],
        "DomainValidationOptions": [
            {
                "DomainName": "string",
                "ValidationEmails": ["string"],
                "ValidationDomain": "string",
                "ValidationStatus": "PENDING_VALIDATION|SUCCESS|FAILED",
                "ResourceRecord": {
                    "Name": "string",
                    "Type": "CNAME",
                    "Value": "string"
                },
                "ValidationMethod": "EMAIL|DNS"
            }
        ],
        "Serial": "string",
        "Subject": "string",
        "Issuer": "string",
        "CreatedAt": "timestamp",
        "IssuedAt": "timestamp",
        "ImportedAt": "timestamp",
        "Status": "PENDING_VALIDATION|ISSUED|INACTIVE|REVOKED|EXPIRED|VALIDATION_TIMED_OUT|FAILED",
        "RevokedAt": "timestamp",
        "RevocationReason": "UNSPECIFIED|KEY_COMPROMISE|CA_COMPROMISE|AFFILIATION_CHANGED|SUPERCEDED|CESSATION_OF_OPERATION|CERTIFICATE_HOLD|REMOVE_FROM_CRL|PRIVILEGE_WITHDRAWN|A_A_COMPROMISE",
        "NotBefore": "timestamp",
        "NotAfter": "timestamp",
        "KeyAlgorithm": "RSA_1024|RSA_2048|RSA_3072|RSA_4096|EC_prime256v1|EC_secp384r1|EC_secp521r1",
        "SignatureAlgorithm": "string",
        "InUseBy": ["string"],
        "FailureReason": "NO_AVAILABLE_CONTACTS|ADDITIONAL_VERIFICATION_REQUIRED|DOMAIN_NOT_ALLOWED|INVALID_PUBLIC_DOMAIN|DOMAIN_VALIDATION_DENIED|CAA_ERROR|PCA_LIMIT_EXCEEDED|PCA_INVALID_ARN|PCA_INVALID_STATE|PCA_REQUEST_FAILED|PCA_NAME_CONSTRAINTS_VALIDATION|PCA_RESOURCE_NOT_FOUND|PCA_INVALID_ARGS|PCA_INVALID_DURATION|PCA_ACCESS_DENIED|SLR_NOT_FOUND|OTHER",
        "Type": "IMPORTED|AMAZON_ISSUED|PRIVATE",
        "RenewalSummary": {
            "RenewalStatus": "PENDING_AUTO_RENEWAL|PENDING_VALIDATION|SUCCESS|FAILED",
            "DomainValidationOptions": [],
            "RenewalStatusReason": "string",
            "UpdatedAt": "timestamp"
        },
        "KeyUsages": [
            {
                "Name": "DIGITAL_SIGNATURE|NON_REPUDIATION|KEY_ENCIPHERMENT|DATA_ENCIPHERMENT|KEY_AGREEMENT|CERTIFICATE_SIGNING|CRL_SIGNING|ENCIPHER_ONLY|DECIPHER_ONLY|ANY|CUSTOM"
            }
        ],
        "ExtendedKeyUsages": [
            {
                "Name": "TLS_WEB_SERVER_AUTHENTICATION|TLS_WEB_CLIENT_AUTHENTICATION|CODE_SIGNING|EMAIL_PROTECTION|TIME_STAMPING|OCSP_SIGNING|IPSEC_END_SYSTEM|IPSEC_TUNNEL|IPSEC_USER|ANY|NONE|CUSTOM",
                "OID": "string"
            }
        ],
        "CertificateAuthorityArn": "string",
        "RenewalEligibility": "ELIGIBLE|INELIGIBLE",
        "Options": {
            "CertificateTransparencyLoggingPreference": "ENABLED|DISABLED"
        }
    }
}
```

---

### 1.3 `delete-certificate`

Deletes a certificate and its associated private key. A certificate cannot be deleted if it is being used by another AWS service. Use `describe-certificate` to check the `InUseBy` field.

**Synopsis:**
```bash
aws acm delete-certificate \
    --certificate-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-arn` | **Yes** | string | -- | ARN of the certificate to delete |

**Output:** None (HTTP 200 on success)

---

### 1.4 `list-certificates`

Lists certificates in the account, optionally filtered by status. **Paginated operation.**

**Synopsis:**
```bash
aws acm list-certificates \
    [--certificate-statuses <value>] \
    [--includes <value>] \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-statuses` | No | list(string) | None | Filter by status: `PENDING_VALIDATION`, `ISSUED`, `INACTIVE`, `REVOKED`, `EXPIRED`, `VALIDATION_TIMED_OUT`, `FAILED` |
| `--includes` | No | structure | None | Filter criteria. Shorthand: `extendedKeyUsage=string,keyUsage=string,keyTypes=string` |
| `--sort-by` | No | string | None | Sort field: `CREATED_AT` |
| `--sort-order` | No | string | None | Sort order: `ASCENDING` or `DESCENDING` |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call (max 1000) |
| `--max-items` | No | integer | None | Total items to return |

**Includes Structure:**
```json
{
    "extendedKeyUsage": ["TLS_WEB_SERVER_AUTHENTICATION", "TLS_WEB_CLIENT_AUTHENTICATION", "CODE_SIGNING", "EMAIL_PROTECTION", "TIME_STAMPING", "OCSP_SIGNING", "IPSEC_END_SYSTEM", "IPSEC_TUNNEL", "IPSEC_USER", "ANY", "NONE", "CUSTOM"],
    "keyUsage": ["DIGITAL_SIGNATURE", "NON_REPUDIATION", "KEY_ENCIPHERMENT", "DATA_ENCIPHERMENT", "KEY_AGREEMENT", "CERTIFICATE_SIGNING", "CRL_SIGNING", "ENCIPHER_ONLY", "DECIPHER_ONLY", "ANY", "CUSTOM"],
    "keyTypes": ["RSA_1024", "RSA_2048", "RSA_3072", "RSA_4096", "EC_prime256v1", "EC_secp384r1", "EC_secp521r1"]
}
```

**Output Schema:**
```json
{
    "CertificateSummaryList": [
        {
            "CertificateArn": "string",
            "DomainName": "string",
            "SubjectAlternativeNameSummaries": ["string"],
            "HasAdditionalSubjectAlternativeNames": true|false,
            "Status": "PENDING_VALIDATION|ISSUED|INACTIVE|REVOKED|EXPIRED|VALIDATION_TIMED_OUT|FAILED",
            "Type": "IMPORTED|AMAZON_ISSUED|PRIVATE",
            "KeyAlgorithm": "string",
            "KeyUsages": ["string"],
            "ExtendedKeyUsages": ["string"],
            "InUse": true|false,
            "Exported": true|false,
            "RenewalEligibility": "ELIGIBLE|INELIGIBLE",
            "NotBefore": "timestamp",
            "NotAfter": "timestamp",
            "CreatedAt": "timestamp",
            "IssuedAt": "timestamp",
            "ImportedAt": "timestamp",
            "RevokedAt": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.5 `renew-certificate`

Renews an eligible ACM Private CA certificate. ACM-issued public certificates are automatically renewed. For imported certificates, use `import-certificate` to re-import.

**Synopsis:**
```bash
aws acm renew-certificate \
    --certificate-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-arn` | **Yes** | string | -- | ARN of the certificate to renew |

**Output:** None (HTTP 200 on success)

---

### 1.6 `resend-validation-email`

Resends the email used for domain ownership validation. Only works for certificates using EMAIL validation that are in `PENDING_VALIDATION` status.

**Synopsis:**
```bash
aws acm resend-validation-email \
    --certificate-arn <value> \
    --domain <value> \
    --validation-domain <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-arn` | **Yes** | string | -- | ARN of the certificate |
| `--domain` | **Yes** | string | -- | The FQDN in the certificate to validate |
| `--validation-domain` | **Yes** | string | -- | Base domain to which validation email is sent (must be a superdomain of `--domain`) |

**Output:** None (HTTP 200 on success)
