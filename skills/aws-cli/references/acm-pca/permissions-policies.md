# Permissions & Policies

### 4.1 `create-permission`

Grants an AWS service principal permission to perform actions on a CA. Used to allow services like ACM to automatically issue and renew certificates.

**Synopsis:**
```bash
aws acm-pca create-permission \
    --certificate-authority-arn <value> \
    --principal <value> \
    --actions <value> \
    [--source-account <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-authority-arn` | **Yes** | string | -- | ARN of the CA |
| `--principal` | **Yes** | string | -- | AWS service principal (e.g., `acm.amazonaws.com`) |
| `--actions` | **Yes** | list(string) | -- | Allowed actions: `IssueCertificate`, `GetCertificate`, `ListPermissions` |
| `--source-account` | No | string | None | AWS account ID of the calling account (for cross-account) |

**Output Schema:**

No output fields (empty response on success).

---

### 4.2 `delete-permission`

Revokes permissions previously granted to an AWS service on a CA.

**Synopsis:**
```bash
aws acm-pca delete-permission \
    --certificate-authority-arn <value> \
    --principal <value> \
    [--source-account <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-authority-arn` | **Yes** | string | -- | ARN of the CA |
| `--principal` | **Yes** | string | -- | AWS service principal to revoke |
| `--source-account` | No | string | None | AWS account ID of the principal |

**Output Schema:**

No output fields (empty response on success).

---

### 4.3 `list-permissions`

Lists permissions granted on a CA. **Paginated operation.**

**Synopsis:**
```bash
aws acm-pca list-permissions \
    --certificate-authority-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--certificate-authority-arn` | **Yes** | string | -- | ARN of the CA |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Permissions": [
        {
            "CertificateAuthorityArn": "string",
            "CreatedAt": "timestamp",
            "Principal": "string",
            "SourceAccount": "string",
            "Actions": ["IssueCertificate|GetCertificate|ListPermissions"],
            "Policy": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 4.4 `get-policy`

Retrieves the resource-based policy attached to a CA. Used for cross-account sharing.

**Synopsis:**
```bash
aws acm-pca get-policy \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the CA |

**Output Schema:**
```json
{
    "Policy": "string"
}
```

---

### 4.5 `put-policy`

Attaches a resource-based policy to a CA for cross-account access.

**Synopsis:**
```bash
aws acm-pca put-policy \
    --resource-arn <value> \
    --policy <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the CA |
| `--policy` | **Yes** | string | -- | JSON resource policy document |

**Output Schema:**

No output fields (empty response on success).

---

### 4.6 `delete-policy`

Removes the resource-based policy from a CA.

**Synopsis:**
```bash
aws acm-pca delete-policy \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the CA |

**Output Schema:**

No output fields (empty response on success).
