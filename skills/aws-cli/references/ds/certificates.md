# Certificates

### 8.1 `register-certificate`

Registers a certificate for use with LDAPS or client authentication.

**Synopsis:**
```bash
aws ds register-certificate \
    --directory-id <value> \
    --certificate-data <value> \
    [--type <value>] \
    [--client-cert-auth-settings <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |
| `--certificate-data` | **Yes** | string | -- | Certificate data in PEM format (use `file://` to read from file) |
| `--type` | No | string | None | `ClientCertAuth` or `ClientLDAPS` |
| `--client-cert-auth-settings` | No | structure | None | Settings for client certificate auth. Structure: `OCSPUrl=string` |

**Output Schema:**
```json
{
    "CertificateId": "string"
}
```

---

### 8.2 `deregister-certificate`

Removes a certificate from a directory.

**Synopsis:**
```bash
aws ds deregister-certificate \
    --directory-id <value> \
    --certificate-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |
| `--certificate-id` | **Yes** | string | -- | Certificate ID to deregister |

**Output Schema:**

No output on success (HTTP 200).

---

### 8.3 `describe-certificate`

Describes a certificate registered with a directory.

**Synopsis:**
```bash
aws ds describe-certificate \
    --directory-id <value> \
    --certificate-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |
| `--certificate-id` | **Yes** | string | -- | Certificate ID |

**Output Schema:**
```json
{
    "Certificate": {
        "CertificateId": "string",
        "State": "Registering|Registered|RegisterFailed|Deregistering|Deregistered|DeregisterFailed",
        "StateReason": "string",
        "CommonName": "string",
        "RegisteredDateTime": "timestamp",
        "ExpiryDateTime": "timestamp",
        "Type": "ClientCertAuth|ClientLDAPS",
        "ClientCertAuthSettings": {
            "OCSPUrl": "string"
        }
    }
}
```

---

### 8.4 `list-certificates`

Lists all certificates registered with a directory. **Paginated operation.**

**Synopsis:**
```bash
aws ds list-certificates \
    --directory-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "CertificatesInfo": [
        {
            "CertificateId": "string",
            "CommonName": "string",
            "State": "Registering|Registered|RegisterFailed|Deregistering|Deregistered|DeregisterFailed",
            "ExpiryDateTime": "timestamp",
            "Type": "ClientCertAuth|ClientLDAPS"
        }
    ],
    "NextToken": "string"
}
```

---

### 8.5 `enable-ca-enrollment-policy`

Enables auto-enrollment of certificates for computers in the directory.

**Synopsis:**
```bash
aws ds enable-ca-enrollment-policy \
    --directory-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |

**Output Schema:**

No output on success (HTTP 200).

---

### 8.6 `disable-ca-enrollment-policy`

Disables auto-enrollment of certificates.

**Synopsis:**
```bash
aws ds disable-ca-enrollment-policy \
    --directory-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |

**Output Schema:**

No output on success (HTTP 200).

---

### 8.7 `describe-ca-enrollment-policy`

Describes the CA enrollment policy for a directory.

**Synopsis:**
```bash
aws ds describe-ca-enrollment-policy \
    --directory-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | Directory ID |

**Output Schema:**
```json
{
    "DirectoryId": "string",
    "CaEnrollmentPolicyStatus": "Enabled|Disabled|Enabling|Disabling|EnableFailed|DisableFailed"
}
```
