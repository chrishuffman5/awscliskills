# Wait Commands

The `aws acm-pca wait` subcommand blocks until a resource reaches a specific state.

### 6.1 `wait audit-report-created`

Waits until a CA audit report has been created. Polls `describe-certificate-authority-audit-report` every 3 seconds until the report status is `SUCCESS`.

**Synopsis:**
```bash
aws acm-pca wait audit-report-created \
    --certificate-authority-arn <value> \
    --audit-report-id <value> \
    [--cli-input-json | --cli-input-yaml]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-authority-arn` | **Yes** | string | -- | ARN of the CA |
| `--audit-report-id` | **Yes** | string | -- | ID of the audit report |

---

### 6.2 `wait certificate-authority-csr-created`

Waits until a CA CSR has been created. Polls `get-certificate-authority-csr` every 3 seconds until the CSR is available.

**Synopsis:**
```bash
aws acm-pca wait certificate-authority-csr-created \
    --certificate-authority-arn <value> \
    [--cli-input-json | --cli-input-yaml]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-authority-arn` | **Yes** | string | -- | ARN of the CA |

---

### 6.3 `wait certificate-issued`

Waits until a certificate has been issued. Polls `get-certificate` every 3 seconds until the certificate is available.

**Synopsis:**
```bash
aws acm-pca wait certificate-issued \
    --certificate-authority-arn <value> \
    --certificate-arn <value> \
    [--cli-input-json | --cli-input-yaml]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-authority-arn` | **Yes** | string | -- | ARN of the CA |
| `--certificate-arn` | **Yes** | string | -- | ARN of the certificate to wait for |

---

## Usage Examples

```bash
# Wait for audit report
aws acm-pca wait audit-report-created \
  --certificate-authority-arn "$CA_ARN" \
  --audit-report-id "$REPORT_ID"

# Wait for CSR generation after creating a CA
aws acm-pca wait certificate-authority-csr-created \
  --certificate-authority-arn "$CA_ARN"

# Wait for certificate issuance
aws acm-pca wait certificate-issued \
  --certificate-authority-arn "$CA_ARN" \
  --certificate-arn "$CERT_ARN"
```
