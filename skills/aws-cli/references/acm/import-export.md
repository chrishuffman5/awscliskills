# Import & Export

### 2.1 `import-certificate`

Imports a certificate into ACM. Use this to import third-party certificates (not issued by ACM). Can also be used to reimport a certificate for renewal. When reimporting, provide the `--certificate-arn` of the existing certificate.

**Synopsis:**
```bash
aws acm import-certificate \
    --certificate <value> \
    --private-key <value> \
    [--certificate-arn <value>] \
    [--certificate-chain <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate` | **Yes** | blob | -- | PEM-encoded certificate body. Use `fileb://` for file input |
| `--private-key` | **Yes** | blob | -- | PEM-encoded unencrypted private key. Use `fileb://` for file input |
| `--certificate-arn` | No | string | None | ARN of existing certificate to reimport (for renewal) |
| `--certificate-chain` | No | string | None | PEM-encoded certificate chain (intermediate + root CAs). Use `fileb://` for file input |
| `--tags` | No | list | None | Tags for the certificate. Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "CertificateArn": "string"
}
```

---

### 2.2 `export-certificate`

Exports a private certificate issued by ACM Private CA, along with its certificate chain and encrypted private key. The private key is encrypted with the provided passphrase.

**Synopsis:**
```bash
aws acm export-certificate \
    --certificate-arn <value> \
    --passphrase <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-arn` | **Yes** | string | -- | ARN of the private certificate to export |
| `--passphrase` | **Yes** | blob | -- | Passphrase to encrypt the private key. Use `fileb://` for file input |

**Output Schema:**
```json
{
    "Certificate": "string",
    "CertificateChain": "string",
    "PrivateKey": "string"
}
```

---

### 2.3 `get-certificate`

Retrieves the PEM-encoded certificate body and certificate chain for an ACM certificate. The private key is NOT included (use `export-certificate` for private certificates).

**Synopsis:**
```bash
aws acm get-certificate \
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
    "Certificate": "string",
    "CertificateChain": "string"
}
```
