# Origin Request Policies

### 5.1 `create-origin-request-policy`

Creates an origin request policy that controls what CloudFront includes in requests sent to the origin.

**Synopsis:**
```bash
aws cloudfront create-origin-request-policy \
    --origin-request-policy-config <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--origin-request-policy-config` | **Yes** | structure | Origin request policy configuration |

**Config structure:**

| Field | Required | Type | Description |
|-------|----------|------|-------------|
| `Name` | **Yes** | string | Unique name |
| `HeadersConfig` | **Yes** | structure | `HeaderBehavior`: `none`, `whitelist`, `allViewer`, `allViewerAndWhitelistCloudFront`, `allExcept` |
| `CookiesConfig` | **Yes** | structure | `CookieBehavior`: `none`, `whitelist`, `all`, `allExcept` |
| `QueryStringsConfig` | **Yes** | structure | `QueryStringBehavior`: `none`, `whitelist`, `all`, `allExcept` |
| `Comment` | No | string | Description (max 128 chars) |

**Output Schema:**
```json
{
    "OriginRequestPolicy": {
        "Id": "string",
        "LastModifiedTime": "timestamp",
        "OriginRequestPolicyConfig": {
            "Comment": "string",
            "Name": "string",
            "HeadersConfig": { "..." },
            "CookiesConfig": { "..." },
            "QueryStringsConfig": { "..." }
        }
    },
    "Location": "string",
    "ETag": "string"
}
```

---

### 5.2 `get-origin-request-policy`

Gets an origin request policy.

**Synopsis:**
```bash
aws cloudfront get-origin-request-policy \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--id` | **Yes** | string | Origin request policy ID |

**Output Schema:**
```json
{
    "OriginRequestPolicy": {
        "Id": "string",
        "LastModifiedTime": "timestamp",
        "OriginRequestPolicyConfig": { "..." }
    },
    "ETag": "string"
}
```

---

### 5.3 `get-origin-request-policy-config`

Gets the configuration for an origin request policy.

**Synopsis:**
```bash
aws cloudfront get-origin-request-policy-config \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--id` | **Yes** | string | Origin request policy ID |

**Output Schema:**
```json
{
    "OriginRequestPolicyConfig": { "..." },
    "ETag": "string"
}
```

---

### 5.4 `list-origin-request-policies`

Lists origin request policies.

**Synopsis:**
```bash
aws cloudfront list-origin-request-policies \
    [--type <value>] \
    [--marker <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--type` | No | string | None | `managed`, `custom`, or omit for all |
| `--marker` | No | string | None | Pagination marker |
| `--max-items` | No | string | None | Maximum items to return |

**Output Schema:**
```json
{
    "OriginRequestPolicyList": {
        "MaxItems": "integer",
        "Quantity": "integer",
        "NextMarker": "string",
        "Items": [
            {
                "Type": "managed|custom",
                "OriginRequestPolicy": {
                    "Id": "string",
                    "LastModifiedTime": "timestamp",
                    "OriginRequestPolicyConfig": { "..." }
                }
            }
        ]
    }
}
```

---

### 5.5 `update-origin-request-policy`

Updates an origin request policy.

**Synopsis:**
```bash
aws cloudfront update-origin-request-policy \
    --id <value> \
    --origin-request-policy-config <value> \
    --if-match <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--id` | **Yes** | string | Origin request policy ID |
| `--origin-request-policy-config` | **Yes** | structure | Updated configuration |
| `--if-match` | **Yes** | string | ETag from `get-origin-request-policy` |

**Output Schema:** Same as `get-origin-request-policy`.

---

### 5.6 `delete-origin-request-policy`

Deletes an origin request policy. Must not be attached to any distribution.

**Synopsis:**
```bash
aws cloudfront delete-origin-request-policy \
    --id <value> \
    --if-match <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--id` | **Yes** | string | Origin request policy ID |
| `--if-match` | **Yes** | string | ETag from `get-origin-request-policy` |

**Output:** None.

---
