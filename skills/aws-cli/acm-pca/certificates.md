# Certificates

### 2.1 `issue-certificate`

Issues a new certificate from the specified CA. Returns the certificate ARN; use `get-certificate` to retrieve the PEM-encoded certificate.

**Synopsis:**
```bash
aws acm-pca issue-certificate \
    --certificate-authority-arn <value> \
    --csr <value> \
    --signing-algorithm <value> \
    --validity <value> \
    [--api-passthrough <value>] \
    [--template-arn <value>] \
    [--validity-not-before <value>] \
    [--idempotency-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-authority-arn` | **Yes** | string | -- | ARN of the issuing CA |
| `--csr` | **Yes** | blob | -- | CSR in PEM or DER format (use `fileb://` for file, max 32768 bytes) |
| `--signing-algorithm` | **Yes** | string | -- | Signing algorithm (see index.md for values) |
| `--validity` | **Yes** | structure | -- | Certificate validity period. Shorthand: `Value=integer,Type=DAYS\|MONTHS\|YEARS\|ABSOLUTE\|END_DATE` |
| `--api-passthrough` | No | structure | None | X.509 extensions and subject overrides (requires APIPassthrough template) |
| `--template-arn` | No | string | `EndEntityCertificate/V1` | Certificate template ARN |
| `--validity-not-before` | No | structure | None | "Not Before" date. Shorthand: `Value=integer,Type=ABSOLUTE` |
| `--idempotency-token` | No | string | None | Deduplication token (1-36 chars, 5-min window) |

**Validity Structure:**
```json
{
    "Value": "long",
    "Type": "END_DATE|ABSOLUTE|DAYS|MONTHS|YEARS"
}
```

**Output Schema:**
```json
{
    "CertificateArn": "string"
}
```

---

### 2.2 `get-certificate`

Retrieves the PEM-encoded certificate and certificate chain for an issued certificate.

**Synopsis:**
```bash
aws acm-pca get-certificate \
    --certificate-authority-arn <value> \
    --certificate-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-authority-arn` | **Yes** | string | -- | ARN of the issuing CA |
| `--certificate-arn` | **Yes** | string | -- | ARN of the certificate to retrieve |

**Output Schema:**
```json
{
    "Certificate": "string",
    "CertificateChain": "string"
}
```

---

### 2.3 `revoke-certificate`

Revokes an issued certificate. The certificate serial number is added to the CRL.

**Synopsis:**
```bash
aws acm-pca revoke-certificate \
    --certificate-authority-arn <value> \
    --certificate-serial <value> \
    --revocation-reason <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-authority-arn` | **Yes** | string | -- | ARN of the issuing CA |
| `--certificate-serial` | **Yes** | string | -- | Serial number of the certificate to revoke |
| `--revocation-reason` | **Yes** | string | -- | Reason: `UNSPECIFIED`, `KEY_COMPROMISE`, `CERTIFICATE_AUTHORITY_COMPROMISE`, `AFFILIATION_CHANGED`, `SUPERSEDED`, `CESSATION_OF_OPERATION`, `PRIVILEGE_WITHDRAWN`, `A_A_COMPROMISE` |

**Output Schema:**

No output fields (empty response on success).
