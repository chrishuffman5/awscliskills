# Distributions

### 1.1 `create-distribution`

Creates a new CloudFront distribution.

**Synopsis:**
```bash
aws cloudfront create-distribution \
    --distribution-config <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--distribution-config` | **Yes** | structure (JSON) | Distribution configuration. Typically provided via `file://dist-config.json` |

**Key fields within `--distribution-config`:**

| Field | Required | Type | Description |
|-------|----------|------|-------------|
| `CallerReference` | **Yes** | string | Unique value to prevent request replay (e.g., timestamp) |
| `Comment` | **Yes** | string | Distribution description (max 128 chars) |
| `Origins` | **Yes** | structure | Origin servers configuration |
| `DefaultCacheBehavior` | **Yes** | structure | Default cache behavior for requests |
| `Enabled` | **Yes** | boolean | Whether the distribution is enabled |
| `Aliases` | No | structure | CNAME alternate domain names |
| `DefaultRootObject` | No | string | Default object for root URL (e.g., `index.html`) |
| `OriginGroups` | No | structure | Origin failover configuration |
| `CacheBehaviors` | No | structure | Path-pattern-based cache behaviors |
| `CustomErrorResponses` | No | structure | Custom error pages |
| `Logging` | No | structure | S3 access log configuration |
| `PriceClass` | No | string | `PriceClass_100`, `PriceClass_200`, `PriceClass_All` |
| `ViewerCertificate` | No | structure | SSL/TLS certificate config (ACM or IAM) |
| `Restrictions` | No | structure | Geo-restriction configuration |
| `WebACLId` | No | string | WAF web ACL ID |
| `HttpVersion` | No | string | `http1.1`, `http2`, `http3`, `http2and3` |
| `IsIPV6Enabled` | No | boolean | Whether IPv6 is enabled |

**Output Schema:**
```json
{
    "Distribution": {
        "Id": "string",
        "ARN": "string",
        "Status": "InProgress|Deployed",
        "LastModifiedTime": "timestamp",
        "InProgressInvalidationBatches": "integer",
        "DomainName": "string",
        "ActiveTrustedSigners": {
            "Enabled": "boolean",
            "Quantity": "integer",
            "Items": [{"AwsAccountNumber": "string", "KeyPairIds": {}}]
        },
        "ActiveTrustedKeyGroups": {
            "Enabled": "boolean",
            "Quantity": "integer",
            "Items": [{"KeyGroupId": "string", "KeyPairIds": {}}]
        },
        "DistributionConfig": { "..." }
    },
    "Location": "string",
    "ETag": "string"
}
```

---

### 1.2 `create-distribution-with-tags`

Creates a distribution with tags in a single call.

**Synopsis:**
```bash
aws cloudfront create-distribution-with-tags \
    --distribution-config-with-tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--distribution-config-with-tags` | **Yes** | structure | Contains `DistributionConfig` (same as create-distribution) and `Tags` |

**Tags structure:**
```json
{
    "DistributionConfig": { "..." },
    "Tags": {
        "Items": [
            {"Key": "string", "Value": "string"}
        ]
    }
}
```

**Output Schema:** Same as `create-distribution`.

---

### 1.3 `get-distribution`

Gets information about a distribution including its configuration.

**Synopsis:**
```bash
aws cloudfront get-distribution \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--id` | **Yes** | string | Distribution ID |

**Output Schema:**
```json
{
    "Distribution": {
        "Id": "string",
        "ARN": "string",
        "Status": "InProgress|Deployed",
        "LastModifiedTime": "timestamp",
        "InProgressInvalidationBatches": "integer",
        "DomainName": "string",
        "ActiveTrustedSigners": {},
        "ActiveTrustedKeyGroups": {},
        "DistributionConfig": { "..." }
    },
    "ETag": "string"
}
```

---

### 1.4 `get-distribution-config`

Gets the configuration for a distribution. Use the returned `ETag` for updates.

**Synopsis:**
```bash
aws cloudfront get-distribution-config \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--id` | **Yes** | string | Distribution ID |

**Output Schema:**
```json
{
    "DistributionConfig": {
        "CallerReference": "string",
        "Aliases": {"Quantity": "integer", "Items": ["string"]},
        "DefaultRootObject": "string",
        "Origins": { "..." },
        "OriginGroups": { "..." },
        "DefaultCacheBehavior": { "..." },
        "CacheBehaviors": { "..." },
        "CustomErrorResponses": { "..." },
        "Comment": "string",
        "Logging": { "..." },
        "PriceClass": "string",
        "Enabled": "boolean",
        "ViewerCertificate": { "..." },
        "Restrictions": { "..." },
        "WebACLId": "string",
        "HttpVersion": "string",
        "IsIPV6Enabled": "boolean"
    },
    "ETag": "string"
}
```

---

### 1.5 `list-distributions`

Lists all distributions. **Paginated operation.**

**Synopsis:**
```bash
aws cloudfront list-distributions \
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
    "DistributionList": {
        "Marker": "string",
        "MaxItems": "integer",
        "IsTruncated": "boolean",
        "NextMarker": "string",
        "Quantity": "integer",
        "Items": [
            {
                "Id": "string",
                "ARN": "string",
                "Status": "string",
                "LastModifiedTime": "timestamp",
                "DomainName": "string",
                "Aliases": {"Quantity": "integer", "Items": ["string"]},
                "Origins": { "..." },
                "DefaultCacheBehavior": { "..." },
                "CacheBehaviors": { "..." },
                "CustomErrorResponses": { "..." },
                "Comment": "string",
                "PriceClass": "string",
                "Enabled": "boolean",
                "ViewerCertificate": { "..." },
                "Restrictions": { "..." },
                "WebACLId": "string",
                "HttpVersion": "string",
                "IsIPV6Enabled": "boolean"
            }
        ]
    }
}
```

---

### 1.6 `update-distribution`

Updates a distribution's configuration. **Requires `--if-match` with the ETag from `get-distribution-config`.**

**Synopsis:**
```bash
aws cloudfront update-distribution \
    --id <value> \
    --distribution-config <value> \
    --if-match <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--id` | **Yes** | string | Distribution ID |
| `--distribution-config` | **Yes** | structure | Updated distribution configuration |
| `--if-match` | **Yes** | string | ETag from `get-distribution-config` (optimistic locking) |

**Output Schema:** Same as `get-distribution`.

---

### 1.7 `delete-distribution`

Deletes a distribution. **Distribution must be disabled first** (`Enabled: false`) and fully deployed.

**Synopsis:**
```bash
aws cloudfront delete-distribution \
    --id <value> \
    --if-match <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--id` | **Yes** | string | Distribution ID |
| `--if-match` | **Yes** | string | ETag from `get-distribution` (optimistic locking) |

**Output:** None.

---

### 1.8 `list-distributions-by-web-acl-id`

Lists distributions associated with a specified WAF web ACL.

**Synopsis:**
```bash
aws cloudfront list-distributions-by-web-acl-id \
    --web-acl-id <value> \
    [--marker <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--web-acl-id` | **Yes** | string | WAF web ACL ID |
| `--marker` | No | string | Pagination marker |
| `--max-items` | No | string | Maximum number of items |

**Output Schema:** Same structure as `list-distributions`.

---

### 1.9 `list-distributions-by-cache-policy-id`

Lists distributions that use a specified cache policy.

**Synopsis:**
```bash
aws cloudfront list-distributions-by-cache-policy-id \
    --cache-policy-id <value> \
    [--marker <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--cache-policy-id` | **Yes** | string | Cache policy ID |
| `--marker` | No | string | Pagination marker |
| `--max-items` | No | string | Maximum number of items |

**Output Schema:**
```json
{
    "DistributionIdList": {
        "Marker": "string",
        "MaxItems": "integer",
        "IsTruncated": "boolean",
        "NextMarker": "string",
        "Quantity": "integer",
        "Items": ["string"]
    }
}
```

---

### 1.10 `list-distributions-by-origin-request-policy-id`

Lists distributions that use a specified origin request policy.

**Synopsis:**
```bash
aws cloudfront list-distributions-by-origin-request-policy-id \
    --origin-request-policy-id <value> \
    [--marker <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--origin-request-policy-id` | **Yes** | string | Origin request policy ID |
| `--marker` | No | string | Pagination marker |
| `--max-items` | No | string | Maximum number of items |

**Output Schema:** Same as `list-distributions-by-cache-policy-id`.

---

### 1.11 `list-distributions-by-response-headers-policy-id`

Lists distributions that use a specified response headers policy.

**Synopsis:**
```bash
aws cloudfront list-distributions-by-response-headers-policy-id \
    --response-headers-policy-id <value> \
    [--marker <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--response-headers-policy-id` | **Yes** | string | Response headers policy ID |
| `--marker` | No | string | Pagination marker |
| `--max-items` | No | string | Maximum number of items |

**Output Schema:** Same as `list-distributions-by-cache-policy-id`.

---

### 1.12 `list-distributions-by-key-group`

Lists distributions associated with a specified key group.

**Synopsis:**
```bash
aws cloudfront list-distributions-by-key-group \
    --key-group-id <value> \
    [--marker <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--key-group-id` | **Yes** | string | Key group ID |
| `--marker` | No | string | Pagination marker |
| `--max-items` | No | string | Maximum number of items |

**Output Schema:** Same as `list-distributions-by-cache-policy-id`.

---

### 1.13 `list-distributions-by-realtime-log-config`

Lists distributions associated with a specified real-time log configuration.

**Synopsis:**
```bash
aws cloudfront list-distributions-by-realtime-log-config \
    [--marker <value>] \
    [--max-items <value>] \
    [--realtime-log-config-name <value>] \
    [--realtime-log-config-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--realtime-log-config-name` | No* | string | Name of the real-time log config (*one of name or ARN required) |
| `--realtime-log-config-arn` | No* | string | ARN of the real-time log config |
| `--marker` | No | string | Pagination marker |
| `--max-items` | No | string | Maximum number of items |

**Output Schema:** Same structure as `list-distributions`.

---

### 1.14 `list-conflicting-aliases`

Lists conflicting CNAME aliases. Useful for finding which distribution owns a specific alias.

**Synopsis:**
```bash
aws cloudfront list-conflicting-aliases \
    --distribution-id <value> \
    --alias <value> \
    [--marker <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--distribution-id` | **Yes** | string | Distribution ID |
| `--alias` | **Yes** | string | The alias (CNAME) to check for conflicts |
| `--marker` | No | string | Pagination marker |
| `--max-items` | No | integer | Maximum number of items |

**Output Schema:**
```json
{
    "ConflictingAliasesList": {
        "MaxItems": "integer",
        "Quantity": "integer",
        "NextMarker": "string",
        "Items": [
            {
                "Alias": "string",
                "DistributionId": "string",
                "AccountId": "string"
            }
        ]
    }
}
```

---
