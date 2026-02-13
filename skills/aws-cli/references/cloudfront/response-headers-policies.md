# Response Headers Policies

### 6.1 `create-response-headers-policy`

Creates a response headers policy for controlling HTTP headers in CloudFront responses (CORS, security headers, custom headers).

**Synopsis:**
```bash
aws cloudfront create-response-headers-policy \
    --response-headers-policy-config <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--response-headers-policy-config` | **Yes** | structure | Response headers policy configuration |

**Config structure:**

| Field | Required | Type | Description |
|-------|----------|------|-------------|
| `Name` | **Yes** | string | Unique name |
| `Comment` | No | string | Description (max 128 chars) |
| `CorsConfig` | No | structure | CORS header configuration |
| `SecurityHeadersConfig` | No | structure | Security headers (XSS, frame options, HSTS, CSP, etc.) |
| `ServerTimingHeadersConfig` | No | structure | Server-Timing header with sampling rate |
| `CustomHeadersConfig` | No | structure | Custom header name/value pairs |
| `RemoveHeadersConfig` | No | structure | Headers to remove from responses |

**CorsConfig fields:**

| Field | Required | Type | Description |
|-------|----------|------|-------------|
| `AccessControlAllowOrigins` | **Yes** | structure | Allowed origins list |
| `AccessControlAllowHeaders` | **Yes** | structure | Allowed headers list |
| `AccessControlAllowMethods` | **Yes** | structure | Allowed methods: `GET`, `POST`, `OPTIONS`, `PUT`, `DELETE`, `PATCH`, `HEAD`, `ALL` |
| `AccessControlAllowCredentials` | **Yes** | boolean | Whether credentials are supported |
| `OriginOverride` | **Yes** | boolean | Whether to override origin CORS headers |
| `AccessControlExposeHeaders` | No | structure | Headers to expose to client |
| `AccessControlMaxAgeSec` | No | integer | Max age in seconds |

**SecurityHeadersConfig fields:**

| Field | Required | Type | Description |
|-------|----------|------|-------------|
| `XSSProtection` | No | structure | `Protection` (boolean), `ModeBlock` (boolean), `ReportUri`, `Override` |
| `FrameOptions` | No | structure | `FrameOption` (`DENY` or `SAMEORIGIN`), `Override` |
| `ReferrerPolicy` | No | structure | `ReferrerPolicy` value, `Override` |
| `ContentSecurityPolicy` | No | structure | `ContentSecurityPolicy` string, `Override` |
| `ContentTypeOptions` | No | structure | `Override` (X-Content-Type-Options: nosniff) |
| `StrictTransportSecurity` | No | structure | `AccessControlMaxAgeSec`, `IncludeSubdomains`, `Preload`, `Override` |

**Output Schema:**
```json
{
    "ResponseHeadersPolicy": {
        "Id": "string",
        "LastModifiedTime": "timestamp",
        "ResponseHeadersPolicyConfig": { "..." }
    },
    "Location": "string",
    "ETag": "string"
}
```

---

### 6.2 `get-response-headers-policy`

Gets a response headers policy.

**Synopsis:**
```bash
aws cloudfront get-response-headers-policy \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--id` | **Yes** | string | Response headers policy ID |

**Output Schema:**
```json
{
    "ResponseHeadersPolicy": {
        "Id": "string",
        "LastModifiedTime": "timestamp",
        "ResponseHeadersPolicyConfig": { "..." }
    },
    "ETag": "string"
}
```

---

### 6.3 `get-response-headers-policy-config`

Gets the configuration for a response headers policy.

**Synopsis:**
```bash
aws cloudfront get-response-headers-policy-config \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--id` | **Yes** | string | Response headers policy ID |

**Output Schema:**
```json
{
    "ResponseHeadersPolicyConfig": { "..." },
    "ETag": "string"
}
```

---

### 6.4 `list-response-headers-policies`

Lists response headers policies.

**Synopsis:**
```bash
aws cloudfront list-response-headers-policies \
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
    "ResponseHeadersPolicyList": {
        "MaxItems": "integer",
        "Quantity": "integer",
        "NextMarker": "string",
        "Items": [
            {
                "Type": "managed|custom",
                "ResponseHeadersPolicy": {
                    "Id": "string",
                    "LastModifiedTime": "timestamp",
                    "ResponseHeadersPolicyConfig": { "..." }
                }
            }
        ]
    }
}
```

---

### 6.5 `update-response-headers-policy`

Updates a response headers policy.

**Synopsis:**
```bash
aws cloudfront update-response-headers-policy \
    --id <value> \
    --response-headers-policy-config <value> \
    --if-match <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--id` | **Yes** | string | Response headers policy ID |
| `--response-headers-policy-config` | **Yes** | structure | Updated configuration |
| `--if-match` | **Yes** | string | ETag from `get-response-headers-policy` |

**Output Schema:** Same as `get-response-headers-policy`.

---

### 6.6 `delete-response-headers-policy`

Deletes a response headers policy. Must not be attached to any distribution.

**Synopsis:**
```bash
aws cloudfront delete-response-headers-policy \
    --id <value> \
    --if-match <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--id` | **Yes** | string | Response headers policy ID |
| `--if-match` | **Yes** | string | ETag from `get-response-headers-policy` |

**Output:** None.

---
