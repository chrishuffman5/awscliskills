# Certificate Authorities

### 1.1 `create-certificate-authority`

Creates a private certificate authority (CA). After creation, the CA is in `PENDING_CERTIFICATE` status until you install a certificate.

**Synopsis:**
```bash
aws acm-pca create-certificate-authority \
    --certificate-authority-configuration <value> \
    --certificate-authority-type <value> \
    [--revocation-configuration <value>] \
    [--idempotency-token <value>] \
    [--key-storage-security-standard <value>] \
    [--tags <value>] \
    [--usage-mode <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-authority-configuration` | **Yes** | structure | -- | CA config: key algorithm, signing algorithm, and subject |
| `--certificate-authority-type` | **Yes** | string | -- | CA type: `ROOT` or `SUBORDINATE` |
| `--revocation-configuration` | No | structure | None | CRL and/or OCSP revocation configuration |
| `--idempotency-token` | No | string | None | Deduplication token (1-36 chars, 5-min window) |
| `--key-storage-security-standard` | No | string | `FIPS_140_2_LEVEL_3_OR_HIGHER` | Crypto key compliance: `FIPS_140_2_LEVEL_2_OR_HIGHER`, `FIPS_140_2_LEVEL_3_OR_HIGHER`, `CCPC_LEVEL_1_OR_HIGHER` |
| `--tags` | No | list | None | Tags (max 50). Shorthand: `Key=string,Value=string ...` |
| `--usage-mode` | No | string | `GENERAL_PURPOSE` | `GENERAL_PURPOSE` or `SHORT_LIVED_CERTIFICATE` |

**CA Configuration Structure:**
```json
{
    "KeyAlgorithm": "RSA_2048|RSA_3072|RSA_4096|EC_prime256v1|EC_secp384r1|EC_secp521r1",
    "SigningAlgorithm": "SHA256WITHRSA|SHA384WITHRSA|SHA512WITHRSA|SHA256WITHECDSA|SHA384WITHECDSA|SHA512WITHECDSA",
    "Subject": {
        "Country": "string",
        "Organization": "string",
        "OrganizationalUnit": "string",
        "State": "string",
        "CommonName": "string",
        "Locality": "string",
        "SerialNumber": "string",
        "Title": "string",
        "Surname": "string",
        "GivenName": "string",
        "Initials": "string",
        "Pseudonym": "string",
        "GenerationQualifier": "string",
        "DistinguishedNameQualifier": "string",
        "CustomAttributes": [
            {
                "ObjectIdentifier": "string",
                "Value": "string"
            }
        ]
    },
    "CsrExtensions": {
        "KeyUsage": {
            "DigitalSignature": true|false,
            "NonRepudiation": true|false,
            "KeyEncipherment": true|false,
            "DataEncipherment": true|false,
            "KeyAgreement": true|false,
            "KeyCertSign": true|false,
            "CRLSign": true|false,
            "EncipherOnly": true|false,
            "DecipherOnly": true|false
        },
        "SubjectInformationAccess": []
    }
}
```

**Revocation Configuration Structure:**
```json
{
    "CrlConfiguration": {
        "Enabled": true|false,
        "ExpirationInDays": "integer (1-5000)",
        "CustomCname": "string",
        "S3BucketName": "string",
        "S3ObjectAcl": "PUBLIC_READ|BUCKET_OWNER_FULL_CONTROL",
        "CrlDistributionPointExtensionConfiguration": {
            "OmitExtension": true|false
        },
        "CrlType": "COMPLETE|PARTITIONED",
        "CustomPath": "string"
    },
    "OcspConfiguration": {
        "Enabled": true|false,
        "OcspCustomCname": "string"
    }
}
```

**Output Schema:**
```json
{
    "CertificateAuthorityArn": "string"
}
```

---

### 1.2 `delete-certificate-authority`

Deletes the specified CA. The CA enters a restorable `DELETED` state for the specified retention period.

**Synopsis:**
```bash
aws acm-pca delete-certificate-authority \
    --certificate-authority-arn <value> \
    [--permanent-deletion-time-in-days <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-authority-arn` | **Yes** | string | -- | ARN of the CA to delete |
| `--permanent-deletion-time-in-days` | No | integer | 30 | Retention period (7-30 days) before permanent deletion |

**Output Schema:**

No output fields (empty response on success).

---

### 1.3 `describe-certificate-authority`

Returns detailed information about a CA.

**Synopsis:**
```bash
aws acm-pca describe-certificate-authority \
    --certificate-authority-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-authority-arn` | **Yes** | string | -- | ARN of the CA |

**Output Schema:**
```json
{
    "CertificateAuthority": {
        "Arn": "string",
        "OwnerAccount": "string",
        "CreatedAt": "timestamp",
        "LastStateChangeAt": "timestamp",
        "Type": "ROOT|SUBORDINATE",
        "Serial": "string",
        "Status": "CREATING|PENDING_CERTIFICATE|ACTIVE|DELETED|DISABLED|EXPIRED|FAILED",
        "NotBefore": "timestamp",
        "NotAfter": "timestamp",
        "FailureReason": "REQUEST_TIMED_OUT|UNSUPPORTED_ALGORITHM|OTHER",
        "CertificateAuthorityConfiguration": {
            "KeyAlgorithm": "string",
            "SigningAlgorithm": "string",
            "Subject": {}
        },
        "RevocationConfiguration": {
            "CrlConfiguration": {},
            "OcspConfiguration": {}
        },
        "RestorableUntil": "timestamp",
        "KeyStorageSecurityStandard": "string",
        "UsageMode": "GENERAL_PURPOSE|SHORT_LIVED_CERTIFICATE"
    }
}
```

---

### 1.4 `list-certificate-authorities`

Lists all private CAs in the account. **Paginated operation.**

**Synopsis:**
```bash
aws acm-pca list-certificate-authorities \
    [--resource-owner <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-owner` | No | string | `SELF` | Filter: `SELF` (own CAs) or `OTHER_ACCOUNTS` (shared CAs) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "CertificateAuthorities": [
        {
            "Arn": "string",
            "OwnerAccount": "string",
            "CreatedAt": "timestamp",
            "LastStateChangeAt": "timestamp",
            "Type": "ROOT|SUBORDINATE",
            "Serial": "string",
            "Status": "string",
            "NotBefore": "timestamp",
            "NotAfter": "timestamp",
            "CertificateAuthorityConfiguration": {},
            "RevocationConfiguration": {},
            "KeyStorageSecurityStandard": "string",
            "UsageMode": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.5 `update-certificate-authority`

Updates the status or revocation configuration of a CA.

**Synopsis:**
```bash
aws acm-pca update-certificate-authority \
    --certificate-authority-arn <value> \
    [--revocation-configuration <value>] \
    [--status <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-authority-arn` | **Yes** | string | -- | ARN of the CA to update |
| `--revocation-configuration` | No | structure | None | Updated CRL/OCSP configuration |
| `--status` | No | string | None | New status: `ACTIVE` or `DISABLED` |

**Output Schema:**

No output fields (empty response on success).

---

### 1.6 `restore-certificate-authority`

Restores a CA that is in `DELETED` status within the retention period.

**Synopsis:**
```bash
aws acm-pca restore-certificate-authority \
    --certificate-authority-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-authority-arn` | **Yes** | string | -- | ARN of the deleted CA to restore |

**Output Schema:**

No output fields (empty response on success).

---

### 1.7 `get-certificate-authority-certificate`

Retrieves the CA's own certificate and certificate chain.

**Synopsis:**
```bash
aws acm-pca get-certificate-authority-certificate \
    --certificate-authority-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-authority-arn` | **Yes** | string | -- | ARN of the CA |

**Output Schema:**
```json
{
    "Certificate": "string",
    "CertificateChain": "string"
}
```

---

### 1.8 `get-certificate-authority-csr`

Retrieves the certificate signing request (CSR) for the CA. Use this CSR to sign the CA certificate.

**Synopsis:**
```bash
aws acm-pca get-certificate-authority-csr \
    --certificate-authority-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-authority-arn` | **Yes** | string | -- | ARN of the CA |

**Output Schema:**
```json
{
    "Csr": "string"
}
```

---

### 1.9 `import-certificate-authority-certificate`

Imports a signed CA certificate into the CA. For root CAs, this is a self-signed certificate. For subordinate CAs, this is signed by the parent CA.

**Synopsis:**
```bash
aws acm-pca import-certificate-authority-certificate \
    --certificate-authority-arn <value> \
    --certificate <value> \
    [--certificate-chain <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-authority-arn` | **Yes** | string | -- | ARN of the CA |
| `--certificate` | **Yes** | blob | -- | PEM-encoded CA certificate (use `fileb://` for file) |
| `--certificate-chain` | No | blob | None | PEM-encoded certificate chain (use `fileb://` for file) |

**Output Schema:**

No output fields (empty response on success).
