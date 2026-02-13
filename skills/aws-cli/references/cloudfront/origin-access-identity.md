# Origin Access Identity (Legacy)

> **Note:** Origin Access Identity (OAI) is the legacy method for restricting S3 access. Use Origin Access Control (OAC) for new distributions.

### 8.1 `create-cloud-front-origin-access-identity`

Creates a legacy origin access identity.

**Synopsis:**
```bash
aws cloudfront create-cloud-front-origin-access-identity \
    --cloud-front-origin-access-identity-config <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--cloud-front-origin-access-identity-config` | **Yes** | structure | OAI configuration |

**Config structure:**

| Field | Required | Type | Description |
|-------|----------|------|-------------|
| `CallerReference` | **Yes** | string | Unique value to prevent replay |
| `Comment` | **Yes** | string | Description |

**Output Schema:**
```json
{
    "CloudFrontOriginAccessIdentity": {
        "Id": "string",
        "S3CanonicalUserId": "string",
        "CloudFrontOriginAccessIdentityConfig": {
            "CallerReference": "string",
            "Comment": "string"
        }
    },
    "Location": "string",
    "ETag": "string"
}
```

---

### 8.2 `get-cloud-front-origin-access-identity`

Gets an origin access identity.

**Synopsis:**
```bash
aws cloudfront get-cloud-front-origin-access-identity \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--id` | **Yes** | string | OAI ID |

**Output Schema:**
```json
{
    "CloudFrontOriginAccessIdentity": {
        "Id": "string",
        "S3CanonicalUserId": "string",
        "CloudFrontOriginAccessIdentityConfig": { "..." }
    },
    "ETag": "string"
}
```

---

### 8.3 `get-cloud-front-origin-access-identity-config`

Gets the configuration for an origin access identity.

**Synopsis:**
```bash
aws cloudfront get-cloud-front-origin-access-identity-config \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--id` | **Yes** | string | OAI ID |

**Output Schema:**
```json
{
    "CloudFrontOriginAccessIdentityConfig": {
        "CallerReference": "string",
        "Comment": "string"
    },
    "ETag": "string"
}
```

---

### 8.4 `list-cloud-front-origin-access-identities`

Lists origin access identities. **Paginated operation.**

**Synopsis:**
```bash
aws cloudfront list-cloud-front-origin-access-identities \
    [--max-items <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--max-items` | No | integer | None | Total items to return |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |

**Output Schema:**
```json
{
    "CloudFrontOriginAccessIdentityList": {
        "Marker": "string",
        "MaxItems": "integer",
        "IsTruncated": "boolean",
        "NextMarker": "string",
        "Quantity": "integer",
        "Items": [
            {
                "Id": "string",
                "S3CanonicalUserId": "string",
                "Comment": "string"
            }
        ]
    }
}
```

---

### 8.5 `update-cloud-front-origin-access-identity`

Updates an origin access identity.

**Synopsis:**
```bash
aws cloudfront update-cloud-front-origin-access-identity \
    --id <value> \
    --cloud-front-origin-access-identity-config <value> \
    --if-match <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--id` | **Yes** | string | OAI ID |
| `--cloud-front-origin-access-identity-config` | **Yes** | structure | Updated configuration |
| `--if-match` | **Yes** | string | ETag from `get-cloud-front-origin-access-identity` |

**Output Schema:** Same as `get-cloud-front-origin-access-identity`.

---

### 8.6 `delete-cloud-front-origin-access-identity`

Deletes an origin access identity. Must not be in use by any distribution.

**Synopsis:**
```bash
aws cloudfront delete-cloud-front-origin-access-identity \
    --id <value> \
    --if-match <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--id` | **Yes** | string | OAI ID |
| `--if-match` | **Yes** | string | ETag from `get-cloud-front-origin-access-identity` |

**Output:** None.

---
