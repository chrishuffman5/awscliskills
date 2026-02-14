# Policies

## Container Policies

### 2.1 `put-container-policy`

Creates or updates an access policy for a container.

**Synopsis:**
```bash
aws mediastore put-container-policy \
    --container-name <value> \
    --policy <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--container-name` | **Yes** | string | -- | Name of the container (1-255 chars) |
| `--policy` | **Yes** | string | -- | JSON policy document (1-8192 chars) |

**Output:** None

---

### 2.2 `get-container-policy`

Retrieves the access policy for a container.

**Synopsis:**
```bash
aws mediastore get-container-policy \
    --container-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--container-name` | **Yes** | string | -- | Name of the container |

**Output Schema:**
```json
{
    "Policy": "string"
}
```

---

### 2.3 `delete-container-policy`

Deletes the access policy from a container.

**Synopsis:**
```bash
aws mediastore delete-container-policy \
    --container-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--container-name` | **Yes** | string | -- | Name of the container |

**Output:** None

---

## CORS Policies

### 2.4 `put-cors-policy`

Creates or updates a CORS policy for browser-based access to a container.

**Synopsis:**
```bash
aws mediastore put-cors-policy \
    --container-name <value> \
    --cors-policy <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--container-name` | **Yes** | string | -- | Name of the container (1-255 chars) |
| `--cors-policy` | **Yes** | list | -- | CORS rules (1-100 rules) |

**CORS Rule Structure:**
```json
[
    {
        "AllowedOrigins": ["https://example.com", "https://*.example.com"],
        "AllowedMethods": ["GET", "HEAD", "PUT", "DELETE"],
        "AllowedHeaders": ["*"],
        "MaxAgeSeconds": 3000,
        "ExposeHeaders": ["x-amz-version-id"]
    }
]
```

| Field | Required | Type | Description |
|-------|----------|------|-------------|
| `AllowedOrigins` | **Yes** | list | Origins allowed (1-100, supports wildcard `*`) |
| `AllowedMethods` | No | list | HTTP methods: `GET`, `PUT`, `DELETE`, `HEAD` (1-4) |
| `AllowedHeaders` | **Yes** | list | Allowed headers in preflight (0-100, supports `*`) |
| `MaxAgeSeconds` | No | integer | Browser cache time for preflight (0-2147483647) |
| `ExposeHeaders` | No | list | Response headers exposed to client (0-100) |

**Output:** None

---

### 2.5 `get-cors-policy`

Retrieves the CORS policy for a container.

**Synopsis:**
```bash
aws mediastore get-cors-policy \
    --container-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--container-name` | **Yes** | string | -- | Name of the container |

**Output Schema:**
```json
{
    "CorsPolicy": [
        {
            "AllowedOrigins": ["string"],
            "AllowedMethods": ["GET|PUT|DELETE|HEAD"],
            "AllowedHeaders": ["string"],
            "MaxAgeSeconds": "integer",
            "ExposeHeaders": ["string"]
        }
    ]
}
```

---

### 2.6 `delete-cors-policy`

Deletes the CORS policy from a container.

**Synopsis:**
```bash
aws mediastore delete-cors-policy \
    --container-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--container-name` | **Yes** | string | -- | Name of the container |

**Output:** None

---

## Lifecycle Policies

### 2.7 `put-lifecycle-policy`

Creates or updates an object lifecycle policy for automatic deletion of objects.

**Synopsis:**
```bash
aws mediastore put-lifecycle-policy \
    --container-name <value> \
    --lifecycle-policy <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--container-name` | **Yes** | string | -- | Name of the container (1-255 chars) |
| `--lifecycle-policy` | **Yes** | string | -- | JSON lifecycle policy (0-8192 chars) |

**Example Lifecycle Policy:**
```json
{
    "rules": [
        {
            "definition": {
                "path": [{"prefix": "temp/"}],
                "days_since_create": [{"numeric": [">", 30]}]
            },
            "action": "EXPIRE"
        }
    ]
}
```

**Output:** None

---

### 2.8 `get-lifecycle-policy`

Retrieves the lifecycle policy for a container.

**Synopsis:**
```bash
aws mediastore get-lifecycle-policy \
    --container-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--container-name` | **Yes** | string | -- | Name of the container |

**Output Schema:**
```json
{
    "LifecyclePolicy": "string"
}
```

---

### 2.9 `delete-lifecycle-policy`

Deletes the lifecycle policy from a container.

**Synopsis:**
```bash
aws mediastore delete-lifecycle-policy \
    --container-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--container-name` | **Yes** | string | -- | Name of the container |

**Output:** None

---

## Metric Policies

### 2.10 `put-metric-policy`

Creates or updates a metric policy for CloudWatch metrics on a container.

**Synopsis:**
```bash
aws mediastore put-metric-policy \
    --container-name <value> \
    --metric-policy <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--container-name` | **Yes** | string | -- | Name of the container (1-255 chars) |
| `--metric-policy` | **Yes** | structure | -- | Metric policy configuration |

**MetricPolicy:**
```json
{
    "ContainerLevelMetrics": "ENABLED|DISABLED",
    "MetricPolicyRules": [
        {
            "ObjectGroup": "media/videos/*",
            "ObjectGroupName": "video_files"
        }
    ]
}
```

| Field | Required | Type | Description |
|-------|----------|------|-------------|
| `ContainerLevelMetrics` | **Yes** | string | `ENABLED` or `DISABLED` |
| `MetricPolicyRules` | No | list | Object group rules for path-level metrics (max 300) |
| `MetricPolicyRules[].ObjectGroup` | **Yes** | string | Path pattern with wildcards (max 900 chars) |
| `MetricPolicyRules[].ObjectGroupName` | **Yes** | string | Group reference name (max 30 chars, `[a-zA-Z0-9_]+`) |

**Output:** None

---

### 2.11 `get-metric-policy`

Retrieves the metric policy for a container.

**Synopsis:**
```bash
aws mediastore get-metric-policy \
    --container-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--container-name` | **Yes** | string | -- | Name of the container |

**Output Schema:**
```json
{
    "MetricPolicy": {
        "ContainerLevelMetrics": "ENABLED|DISABLED",
        "MetricPolicyRules": [
            {
                "ObjectGroup": "string",
                "ObjectGroupName": "string"
            }
        ]
    }
}
```

---

### 2.12 `delete-metric-policy`

Deletes the metric policy from a container.

**Synopsis:**
```bash
aws mediastore delete-metric-policy \
    --container-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--container-name` | **Yes** | string | -- | Name of the container |

**Output:** None
