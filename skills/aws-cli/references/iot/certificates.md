# Certificates

## 2.1 `create-keys-and-certificate`

Creates a new 2048-bit RSA key pair and issues an X.509 certificate.

**Synopsis:**
```bash
aws iot create-keys-and-certificate \
    [--set-as-active | --no-set-as-active] \
    [--certificate-pem-outfile <value>] \
    [--public-key-outfile <value>] \
    [--private-key-outfile <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--set-as-active` | No | boolean | false | Set certificate as ACTIVE |
| `--certificate-pem-outfile` | No | string | None | Save certificate PEM to file |
| `--public-key-outfile` | No | string | None | Save public key to file |
| `--private-key-outfile` | No | string | None | Save private key to file |

**Output Schema:**
```json
{
    "certificateArn": "string",
    "certificateId": "string",
    "certificatePem": "string",
    "keyPair": {
        "PublicKey": "string",
        "PrivateKey": "string"
    }
}
```

---

## 2.2 `create-certificate-from-csr`

Creates a certificate from a certificate signing request (CSR).

**Synopsis:**
```bash
aws iot create-certificate-from-csr \
    --certificate-signing-request <value> \
    [--set-as-active | --no-set-as-active] \
    [--certificate-pem-outfile <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-signing-request` | **Yes** | string | -- | CSR content (1-4096 chars) |
| `--set-as-active` | No | boolean | false | Set certificate as ACTIVE |
| `--certificate-pem-outfile` | No | string | None | Save certificate PEM to file |

**Output Schema:**
```json
{
    "certificateArn": "string",
    "certificateId": "string",
    "certificatePem": "string"
}
```

---

## 2.3 `describe-certificate`

Describes a certificate.

**Synopsis:**
```bash
aws iot describe-certificate \
    --certificate-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-id` | **Yes** | string | -- | Certificate ID (64-char hex) |

**Output Schema:**
```json
{
    "certificateDescription": {
        "certificateArn": "string",
        "certificateId": "string",
        "caCertificateId": "string",
        "status": "ACTIVE|INACTIVE|REVOKED|PENDING_TRANSFER|REGISTER_INACTIVE|PENDING_ACTIVATION",
        "certificatePem": "string",
        "ownedBy": "string",
        "previousOwnedBy": "string",
        "creationDate": "timestamp",
        "lastModifiedDate": "timestamp",
        "customerVersion": "integer",
        "transferData": {
            "transferMessage": "string",
            "rejectReason": "string",
            "transferDate": "timestamp",
            "acceptDate": "timestamp",
            "rejectDate": "timestamp"
        },
        "generationId": "string",
        "validity": {
            "notBefore": "timestamp",
            "notAfter": "timestamp"
        },
        "certificateMode": "DEFAULT|SNI_ONLY"
    }
}
```

---

## 2.4 `list-certificates`

Lists certificates. **Paginated operation.**

**Synopsis:**
```bash
aws iot list-certificates \
    [--page-size <value>] \
    [--marker <value>] \
    [--ascending-order | --no-ascending-order] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--page-size` | No | integer | None | Max results per page (1-250) |
| `--marker` | No | string | None | Pagination marker |
| `--ascending-order` | No | boolean | false | Sort ascending |

**Output Schema:**
```json
{
    "certificates": [
        {
            "certificateArn": "string",
            "certificateId": "string",
            "status": "ACTIVE|INACTIVE|REVOKED|PENDING_TRANSFER|REGISTER_INACTIVE|PENDING_ACTIVATION",
            "certificateMode": "DEFAULT|SNI_ONLY",
            "creationDate": "timestamp"
        }
    ],
    "nextMarker": "string"
}
```

---

## 2.5 `update-certificate`

Updates the status of a certificate.

**Synopsis:**
```bash
aws iot update-certificate \
    --certificate-id <value> \
    --new-status <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-id` | **Yes** | string | -- | Certificate ID |
| `--new-status` | **Yes** | string | -- | `ACTIVE`, `INACTIVE`, `REVOKED`, `PENDING_TRANSFER`, `REGISTER_INACTIVE`, `PENDING_ACTIVATION` |

**Output:** None

---

## 2.6 `delete-certificate`

Deletes a certificate.

**Synopsis:**
```bash
aws iot delete-certificate \
    --certificate-id <value> \
    [--force-delete | --no-force-delete] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-id` | **Yes** | string | -- | Certificate ID |
| `--force-delete` | No | boolean | false | Force delete even if active |

**Output:** None

---

## 2.7 `register-certificate`

Registers a certificate with a CA certificate.

**Synopsis:**
```bash
aws iot register-certificate \
    --certificate-pem <value> \
    [--ca-certificate-pem <value>] \
    [--set-as-active | --no-set-as-active] \
    [--status <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-pem` | **Yes** | string | -- | Certificate PEM content |
| `--ca-certificate-pem` | No | string | None | CA certificate PEM |
| `--set-as-active` | No | boolean | false | Set as active (deprecated, use --status) |
| `--status` | No | string | None | `ACTIVE` or `INACTIVE` |

**Output Schema:**
```json
{
    "certificateArn": "string",
    "certificateId": "string"
}
```

---

## 2.8 `register-certificate-without-ca`

Registers a certificate without an associated CA certificate.

**Synopsis:**
```bash
aws iot register-certificate-without-ca \
    --certificate-pem <value> \
    [--status <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-pem` | **Yes** | string | -- | Certificate PEM content |
| `--status` | No | string | None | `ACTIVE` or `INACTIVE` |

**Output Schema:**
```json
{
    "certificateArn": "string",
    "certificateId": "string"
}
```

---

## 2.9 `register-ca-certificate`

Registers a CA certificate with IoT.

**Synopsis:**
```bash
aws iot register-ca-certificate \
    --ca-certificate <value> \
    [--verification-certificate <value>] \
    [--set-as-active | --no-set-as-active] \
    [--allow-auto-registration | --no-allow-auto-registration] \
    [--registration-config <value>] \
    [--tags <value>] \
    [--certificate-mode <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--ca-certificate` | **Yes** | string | -- | CA certificate PEM |
| `--verification-certificate` | No | string | None | Verification certificate PEM |
| `--set-as-active` | No | boolean | false | Set as active |
| `--allow-auto-registration` | No | boolean | false | Enable auto-registration |
| `--registration-config` | No | structure | None | Registration configuration |
| `--tags` | No | list | None | Tags |
| `--certificate-mode` | No | string | None | `DEFAULT` or `SNI_ONLY` |

**RegistrationConfig:**
```json
{
    "templateBody": "string",
    "roleArn": "string",
    "templateName": "string"
}
```

**Output Schema:**
```json
{
    "certificateArn": "string",
    "certificateId": "string"
}
```

---

## 2.10 `describe-ca-certificate`

Describes a CA certificate.

**Synopsis:**
```bash
aws iot describe-ca-certificate \
    --certificate-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-id` | **Yes** | string | -- | CA certificate ID |

**Output Schema:**
```json
{
    "certificateDescription": {
        "certificateArn": "string",
        "certificateId": "string",
        "status": "ACTIVE|INACTIVE",
        "certificatePem": "string",
        "ownedBy": "string",
        "creationDate": "timestamp",
        "autoRegistrationStatus": "ENABLE|DISABLE",
        "lastModifiedDate": "timestamp",
        "customerVersion": "integer",
        "generationId": "string",
        "validity": {"notBefore": "timestamp", "notAfter": "timestamp"},
        "certificateMode": "DEFAULT|SNI_ONLY"
    },
    "registrationConfig": {
        "templateBody": "string",
        "roleArn": "string",
        "templateName": "string"
    }
}
```

---

## 2.11 `list-ca-certificates`

Lists CA certificates. **Paginated operation.**

**Synopsis:**
```bash
aws iot list-ca-certificates \
    [--page-size <value>] \
    [--marker <value>] \
    [--ascending-order | --no-ascending-order] \
    [--template-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--page-size` | No | integer | None | Max results per page |
| `--marker` | No | string | None | Pagination marker |
| `--ascending-order` | No | boolean | false | Sort ascending |
| `--template-name` | No | string | None | Filter by template name |

**Output Schema:**
```json
{
    "certificates": [
        {
            "certificateArn": "string",
            "certificateId": "string",
            "status": "ACTIVE|INACTIVE",
            "creationDate": "timestamp"
        }
    ],
    "nextMarker": "string"
}
```

---

## 2.12 `update-ca-certificate`

Updates a CA certificate status or registration config.

**Synopsis:**
```bash
aws iot update-ca-certificate \
    --certificate-id <value> \
    [--new-status <value>] \
    [--new-auto-registration-status <value>] \
    [--registration-config <value>] \
    [--remove-auto-registration | --no-remove-auto-registration] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-id` | **Yes** | string | -- | CA certificate ID |
| `--new-status` | No | string | None | `ACTIVE` or `INACTIVE` |
| `--new-auto-registration-status` | No | string | None | `ENABLE` or `DISABLE` |
| `--registration-config` | No | structure | None | Registration config |
| `--remove-auto-registration` | No | boolean | false | Remove auto-registration |

**Output:** None

---

## 2.13 `delete-ca-certificate`

Deletes a CA certificate.

**Synopsis:**
```bash
aws iot delete-ca-certificate \
    --certificate-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-id` | **Yes** | string | -- | CA certificate ID |

**Output:** None

---

## 2.14 `list-certificates-by-ca`

Lists certificates signed by a specific CA. **Paginated operation.**

**Synopsis:**
```bash
aws iot list-certificates-by-ca \
    --ca-certificate-id <value> \
    [--page-size <value>] \
    [--marker <value>] \
    [--ascending-order | --no-ascending-order] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--ca-certificate-id` | **Yes** | string | -- | CA certificate ID |
| `--page-size` | No | integer | None | Max results per page |
| `--marker` | No | string | None | Pagination marker |
| `--ascending-order` | No | boolean | false | Sort ascending |

**Output Schema:**
```json
{
    "certificates": [
        {
            "certificateArn": "string",
            "certificateId": "string",
            "status": "string",
            "certificateMode": "DEFAULT|SNI_ONLY",
            "creationDate": "timestamp"
        }
    ],
    "nextMarker": "string"
}
```

---

## 2.15 `list-outgoing-certificates`

Lists outgoing certificate transfers. **Paginated operation.**

**Synopsis:**
```bash
aws iot list-outgoing-certificates \
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
    "outgoingCertificates": [
        {
            "certificateArn": "string",
            "certificateId": "string",
            "transferredTo": "string",
            "transferDate": "timestamp",
            "transferMessage": "string",
            "creationDate": "timestamp"
        }
    ],
    "nextMarker": "string"
}
```

---

## 2.16 `transfer-certificate`

Transfers a certificate to another AWS account.

**Synopsis:**
```bash
aws iot transfer-certificate \
    --certificate-id <value> \
    --target-aws-account <value> \
    [--transfer-message <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-id` | **Yes** | string | -- | Certificate ID |
| `--target-aws-account` | **Yes** | string | -- | Target AWS account ID (12 digits) |
| `--transfer-message` | No | string | None | Transfer message |

**Output Schema:**
```json
{
    "transferredCertificateArn": "string"
}
```

---

## 2.17 `accept-certificate-transfer`

Accepts a certificate transfer.

**Synopsis:**
```bash
aws iot accept-certificate-transfer \
    --certificate-id <value> \
    [--set-as-active | --no-set-as-active] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-id` | **Yes** | string | -- | Certificate ID |
| `--set-as-active` | No | boolean | false | Set as active after accepting |

**Output:** None

---

## 2.18 `reject-certificate-transfer`

Rejects a certificate transfer.

**Synopsis:**
```bash
aws iot reject-certificate-transfer \
    --certificate-id <value> \
    [--reject-reason <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-id` | **Yes** | string | -- | Certificate ID |
| `--reject-reason` | No | string | None | Rejection reason |

**Output:** None

---

## 2.19 `cancel-certificate-transfer`

Cancels a pending certificate transfer.

**Synopsis:**
```bash
aws iot cancel-certificate-transfer \
    --certificate-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-id` | **Yes** | string | -- | Certificate ID |

**Output:** None

---

## 2.20 `get-registration-code`

Gets a registration code for registering CA certificates.

**Synopsis:**
```bash
aws iot get-registration-code \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output Schema:**
```json
{
    "registrationCode": "string"
}
```

---

## 2.21 `delete-registration-code`

Deletes the CA certificate registration code.

**Synopsis:**
```bash
aws iot delete-registration-code \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output:** None

---

## 2.22 `create-certificate-provider`

Creates a certificate provider for custom certificate creation.

**Synopsis:**
```bash
aws iot create-certificate-provider \
    --certificate-provider-name <value> \
    --lambda-function-arn <value> \
    --account-default-for-operations <value> \
    [--client-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-provider-name` | **Yes** | string | -- | Provider name (1-128 chars) |
| `--lambda-function-arn` | **Yes** | string | -- | Lambda function ARN |
| `--account-default-for-operations` | **Yes** | list | -- | Operations: `CreateCertificateFromCsr` |
| `--client-token` | No | string | Auto | Idempotency token |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "certificateProviderName": "string",
    "certificateProviderArn": "string"
}
```

---

## 2.23 `describe-certificate-provider`

Describes a certificate provider.

**Synopsis:**
```bash
aws iot describe-certificate-provider \
    --certificate-provider-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-provider-name` | **Yes** | string | -- | Provider name |

**Output Schema:**
```json
{
    "certificateProviderName": "string",
    "certificateProviderArn": "string",
    "lambdaFunctionArn": "string",
    "accountDefaultForOperations": ["string"],
    "creationDate": "timestamp",
    "lastModifiedDate": "timestamp"
}
```

---

## 2.24 `list-certificate-providers`

Lists certificate providers.

**Synopsis:**
```bash
aws iot list-certificate-providers \
    [--next-token <value>] \
    [--ascending-order | --no-ascending-order] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--next-token` | No | string | None | Pagination token |
| `--ascending-order` | No | boolean | false | Sort ascending |

**Output Schema:**
```json
{
    "certificateProviders": [
        {
            "certificateProviderName": "string",
            "certificateProviderArn": "string"
        }
    ],
    "nextToken": "string"
}
```

---

## 2.25 `update-certificate-provider`

Updates a certificate provider.

**Synopsis:**
```bash
aws iot update-certificate-provider \
    --certificate-provider-name <value> \
    [--lambda-function-arn <value>] \
    [--account-default-for-operations <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-provider-name` | **Yes** | string | -- | Provider name |
| `--lambda-function-arn` | No | string | None | Updated Lambda ARN |
| `--account-default-for-operations` | No | list | None | Updated operations |

**Output Schema:**
```json
{
    "certificateProviderName": "string",
    "certificateProviderArn": "string"
}
```

---

## 2.26 `delete-certificate-provider`

Deletes a certificate provider.

**Synopsis:**
```bash
aws iot delete-certificate-provider \
    --certificate-provider-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-provider-name` | **Yes** | string | -- | Provider name |

**Output:** None
