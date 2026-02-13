# Origin Access Control

### 7.1 `create-origin-access-control`

Creates an origin access control (OAC) for restricting S3 origin access to CloudFront only. **Recommended over legacy OAI.**

**Synopsis:**
```bash
aws cloudfront create-origin-access-control \
    --origin-access-control-config <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--origin-access-control-config` | **Yes** | structure | OAC configuration |

**Config structure:**

| Field | Required | Type | Description |
|-------|----------|------|-------------|
| `Name` | **Yes** | string | Unique name (up to 64 chars) |
| `SigningProtocol` | **Yes** | string | `sigv4` |
| `SigningBehavior` | **Yes** | string | `always`, `never`, `no-override` |
| `OriginAccessControlOriginType` | **Yes** | string | `s3`, `mediastore`, `mediapackagev2`, `lambda` |
| `Description` | No | string | Description |

**Output Schema:**
```json
{
    "OriginAccessControl": {
        "Id": "string",
        "OriginAccessControlConfig": {
            "Name": "string",
            "Description": "string",
            "SigningProtocol": "sigv4",
            "SigningBehavior": "always|never|no-override",
            "OriginAccessControlOriginType": "s3|mediastore|mediapackagev2|lambda"
        }
    },
    "Location": "string",
    "ETag": "string"
}
```

---

### 7.2 `get-origin-access-control`

Gets an origin access control.

**Synopsis:**
```bash
aws cloudfront get-origin-access-control \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--id` | **Yes** | string | OAC ID |

**Output Schema:**
```json
{
    "OriginAccessControl": {
        "Id": "string",
        "OriginAccessControlConfig": { "..." }
    },
    "ETag": "string"
}
```

---

### 7.3 `get-origin-access-control-config`

Gets the configuration for an origin access control.

**Synopsis:**
```bash
aws cloudfront get-origin-access-control-config \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--id` | **Yes** | string | OAC ID |

**Output Schema:**
```json
{
    "OriginAccessControlConfig": { "..." },
    "ETag": "string"
}
```

---

### 7.4 `list-origin-access-controls`

Lists origin access controls.

**Synopsis:**
```bash
aws cloudfront list-origin-access-controls \
    [--marker <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--marker` | No | string | None | Pagination marker |
| `--max-items` | No | string | None | Maximum items to return |

**Output Schema:**
```json
{
    "OriginAccessControlList": {
        "Marker": "string",
        "MaxItems": "integer",
        "IsTruncated": "boolean",
        "NextMarker": "string",
        "Quantity": "integer",
        "Items": [
            {
                "Id": "string",
                "Description": "string",
                "Name": "string",
                "SigningProtocol": "sigv4",
                "SigningBehavior": "always|never|no-override",
                "OriginAccessControlOriginType": "s3|mediastore|mediapackagev2|lambda"
            }
        ]
    }
}
```

---

### 7.5 `update-origin-access-control`

Updates an origin access control.

**Synopsis:**
```bash
aws cloudfront update-origin-access-control \
    --id <value> \
    --origin-access-control-config <value> \
    --if-match <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--id` | **Yes** | string | OAC ID |
| `--origin-access-control-config` | **Yes** | structure | Updated OAC configuration |
| `--if-match` | **Yes** | string | ETag from `get-origin-access-control` |

**Output Schema:** Same as `get-origin-access-control`.

---

### 7.6 `delete-origin-access-control`

Deletes an origin access control. Must not be in use by any distribution.

**Synopsis:**
```bash
aws cloudfront delete-origin-access-control \
    --id <value> \
    --if-match <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--id` | **Yes** | string | OAC ID |
| `--if-match` | **Yes** | string | ETag from `get-origin-access-control` |

**Output:** None.

---
