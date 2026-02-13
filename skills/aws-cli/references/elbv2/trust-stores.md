# Trust Stores

### 7.1 `create-trust-store`

Creates a trust store for mutual TLS authentication on HTTPS listeners.

**Synopsis:**
```bash
aws elbv2 create-trust-store \
    --name <value> \
    --ca-certificates-bundle-s3-bucket <value> \
    --ca-certificates-bundle-s3-key <value> \
    [--ca-certificates-bundle-s3-object-version <value>] \
    [--tags <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Trust store name. Max 32 chars, alphanumeric and hyphens |
| `--ca-certificates-bundle-s3-bucket` | **Yes** | string | -- | S3 bucket for CA certificates bundle |
| `--ca-certificates-bundle-s3-key` | **Yes** | string | -- | S3 key for CA certificates bundle |
| `--ca-certificates-bundle-s3-object-version` | No | string | current version | S3 object version |
| `--tags` | No | list | None | Key-value tags |

**Output Schema:**
```json
{
    "TrustStores": [
        {
            "Name": "string",
            "TrustStoreArn": "string",
            "Status": "ACTIVE|CREATING",
            "NumberOfCaCertificates": integer,
            "TotalRevokedEntries": integer
        }
    ]
}
```

---

### 7.2 `delete-trust-store`

Deletes a trust store.

**Synopsis:**
```bash
aws elbv2 delete-trust-store \
    --trust-store-arn <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--trust-store-arn` | **Yes** | string | -- | ARN of the trust store |

**Output Schema:** None (no output on success).

---

### 7.3 `describe-trust-stores`

Describes the specified trust stores. **Paginated operation.**

**Synopsis:**
```bash
aws elbv2 describe-trust-stores \
    [--trust-store-arns <value>] \
    [--names <value>] \
    [--page-size <value>] \
    [--starting-token <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--trust-store-arns` | No | list | -- | ARNs of trust stores |
| `--names` | No | list | -- | Names of trust stores |
| `--page-size` | No | integer | -- | Number of items per API call |
| `--starting-token` | No | string | -- | Pagination token |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "TrustStores": [
        {
            "Name": "string",
            "TrustStoreArn": "string",
            "Status": "ACTIVE|CREATING",
            "NumberOfCaCertificates": integer,
            "TotalRevokedEntries": integer
        }
    ],
    "NextMarker": "string"
}
```

---

### 7.4 `modify-trust-store`

Updates the CA certificates bundle for a trust store.

**Synopsis:**
```bash
aws elbv2 modify-trust-store \
    --trust-store-arn <value> \
    --ca-certificates-bundle-s3-bucket <value> \
    --ca-certificates-bundle-s3-key <value> \
    [--ca-certificates-bundle-s3-object-version <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--trust-store-arn` | **Yes** | string | -- | ARN of the trust store |
| `--ca-certificates-bundle-s3-bucket` | **Yes** | string | -- | S3 bucket for CA certificates bundle |
| `--ca-certificates-bundle-s3-key` | **Yes** | string | -- | S3 key for CA certificates bundle |
| `--ca-certificates-bundle-s3-object-version` | No | string | current version | S3 object version |

**Output Schema:**
```json
{
    "TrustStores": [
        {
            "Name": "string",
            "TrustStoreArn": "string",
            "Status": "ACTIVE|CREATING",
            "NumberOfCaCertificates": integer,
            "TotalRevokedEntries": integer
        }
    ]
}
```

---

### 7.5 `get-trust-store-ca-certificates-bundle`

Retrieves the CA certificate bundle for the specified trust store.

**Synopsis:**
```bash
aws elbv2 get-trust-store-ca-certificates-bundle \
    --trust-store-arn <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--trust-store-arn` | **Yes** | string | -- | ARN of the trust store |

**Output Schema:**
```json
{
    "Location": "string"
}
```

---

### 7.6 `describe-trust-store-associations`

Describes all resources associated with the specified trust store. **Paginated operation.**

**Synopsis:**
```bash
aws elbv2 describe-trust-store-associations \
    --trust-store-arn <value> \
    [--page-size <value>] \
    [--starting-token <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--trust-store-arn` | **Yes** | string | -- | ARN of the trust store |
| `--page-size` | No | integer | -- | Number of items per API call |
| `--starting-token` | No | string | -- | Pagination token |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "TrustStoreAssociations": [
        {
            "ResourceArn": "string"
        }
    ],
    "NextMarker": "string"
}
```

---

### 7.7 `add-trust-store-revocations`

Adds the specified revocation content to the specified trust store.

**Synopsis:**
```bash
aws elbv2 add-trust-store-revocations \
    --trust-store-arn <value> \
    [--revocation-contents <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--trust-store-arn` | **Yes** | string | -- | ARN of the trust store |
| `--revocation-contents` | No | list | -- | Revocation content. Shorthand: `S3Bucket=string,S3Key=string,S3ObjectVersion=string,RevocationType=CRL ...` |

**Output Schema:**
```json
{
    "TrustStoreRevocations": [
        {
            "TrustStoreArn": "string",
            "RevocationId": long,
            "RevocationType": "CRL",
            "NumberOfRevokedEntries": long
        }
    ]
}
```

---

### 7.8 `remove-trust-store-revocations`

Removes the specified revocation from the specified trust store.

**Synopsis:**
```bash
aws elbv2 remove-trust-store-revocations \
    --trust-store-arn <value> \
    --revocation-ids <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--trust-store-arn` | **Yes** | string | -- | ARN of the trust store |
| `--revocation-ids` | **Yes** | list | -- | Revocation IDs to remove |

**Output Schema:** None (no output on success).

---

### 7.9 `describe-trust-store-revocations`

Describes the revocations for the specified trust store. **Paginated operation.**

**Synopsis:**
```bash
aws elbv2 describe-trust-store-revocations \
    --trust-store-arn <value> \
    [--revocation-ids <value>] \
    [--page-size <value>] \
    [--starting-token <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--trust-store-arn` | **Yes** | string | -- | ARN of the trust store |
| `--revocation-ids` | No | list | -- | Specific revocation IDs to describe |
| `--page-size` | No | integer | -- | Number of items per API call |
| `--starting-token` | No | string | -- | Pagination token |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "TrustStoreRevocations": [
        {
            "TrustStoreArn": "string",
            "RevocationId": long,
            "RevocationType": "CRL",
            "NumberOfRevokedEntries": long
        }
    ],
    "NextMarker": "string"
}
```

---

### 7.10 `get-trust-store-revocation-content`

Retrieves the specified revocation content from the specified trust store.

**Synopsis:**
```bash
aws elbv2 get-trust-store-revocation-content \
    --trust-store-arn <value> \
    --revocation-id <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--trust-store-arn` | **Yes** | string | -- | ARN of the trust store |
| `--revocation-id` | **Yes** | long | -- | ID of the revocation |

**Output Schema:**
```json
{
    "Location": "string"
}
```

---

### 7.11 `delete-shared-trust-store-association`

Deletes a shared trust store association.

**Synopsis:**
```bash
aws elbv2 delete-shared-trust-store-association \
    --trust-store-arn <value> \
    --resource-arn <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--trust-store-arn` | **Yes** | string | -- | ARN of the trust store |
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |

**Output Schema:** None (no output on success).

---
