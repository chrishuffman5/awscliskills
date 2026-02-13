# Layers

### 3.1 `publish-layer-version`

Creates a new layer version from a zip archive.

**Synopsis:**
```bash
aws lambda publish-layer-version \
    --layer-name <value> \
    [--description <value>] \
    [--content <value>] \
    [--zip-file <value>] \
    [--compatible-runtimes <value>] \
    [--license-info <value>] \
    [--compatible-architectures <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--layer-name` | **Yes** | string | -- | Layer name or ARN (1-140 chars) |
| `--description` | No | string | -- | Description (0-256 chars) |
| `--content` | No | structure | -- | S3 location. Shorthand: `S3Bucket=string,S3Key=string,S3ObjectVersion=string` |
| `--zip-file` | No | blob | -- | Zip file path (e.g., `fileb://layer.zip`) |
| `--compatible-runtimes` | No | list | -- | Compatible runtimes (0-15 items) |
| `--license-info` | No | string | -- | License identifier (0-512 chars, SPDX ID or URL) |
| `--compatible-architectures` | No | list | -- | Values: `x86_64`, `arm64` (0-2 items) |

**Output Schema:**
```json
{
    "Content": {
        "Location": "string",
        "CodeSha256": "string",
        "CodeSize": "long",
        "SigningProfileVersionArn": "string",
        "SigningJobArn": "string"
    },
    "LayerArn": "string",
    "LayerVersionArn": "string",
    "Description": "string",
    "CreatedDate": "string",
    "Version": "long",
    "CompatibleRuntimes": ["string"],
    "LicenseInfo": "string",
    "CompatibleArchitectures": ["string"]
}
```

---

### 3.2 `get-layer-version`

Returns information about a layer version.

**Synopsis:**
```bash
aws lambda get-layer-version \
    --layer-name <value> \
    --version-number <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--layer-name` | **Yes** | string | -- | Layer name or ARN (1-140 chars) |
| `--version-number` | **Yes** | long | -- | Version number |

**Output Schema:** Same as `publish-layer-version`.

---

### 3.3 `get-layer-version-by-arn`

Returns information about a layer version using the full ARN.

**Synopsis:**
```bash
aws lambda get-layer-version-by-arn \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | Full layer version ARN |

**Output Schema:** Same as `publish-layer-version`.

---

### 3.4 `list-layers`

Lists Lambda layers and their latest versions. **Paginated operation.**

**Synopsis:**
```bash
aws lambda list-layers \
    [--compatible-runtime <value>] \
    [--compatible-architecture <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--compatible-runtime` | No | string | -- | Filter by compatible runtime |
| `--compatible-architecture` | No | string | -- | Filter by architecture (`x86_64` or `arm64`) |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "Layers": [
        {
            "LayerName": "string",
            "LayerArn": "string",
            "LatestMatchingVersion": {
                "LayerVersionArn": "string",
                "Version": "long",
                "Description": "string",
                "CreatedDate": "string",
                "CompatibleRuntimes": ["string"],
                "LicenseInfo": "string",
                "CompatibleArchitectures": ["string"]
            }
        }
    ],
    "NextMarker": "string"
}
```

---

### 3.5 `list-layer-versions`

Lists versions of a layer. **Paginated operation.**

**Synopsis:**
```bash
aws lambda list-layer-versions \
    --layer-name <value> \
    [--compatible-runtime <value>] \
    [--compatible-architecture <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--layer-name` | **Yes** | string | -- | Layer name or ARN (1-140 chars) |
| `--compatible-runtime` | No | string | -- | Filter by runtime |
| `--compatible-architecture` | No | string | -- | Filter by architecture |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "LayerVersions": [
        {
            "LayerVersionArn": "string",
            "Version": "long",
            "Description": "string",
            "CreatedDate": "string",
            "CompatibleRuntimes": ["string"],
            "LicenseInfo": "string",
            "CompatibleArchitectures": ["string"]
        }
    ],
    "NextMarker": "string"
}
```

---

### 3.6 `delete-layer-version`

Deletes a layer version.

**Synopsis:**
```bash
aws lambda delete-layer-version \
    --layer-name <value> \
    --version-number <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--layer-name` | **Yes** | string | -- | Layer name or ARN (1-140 chars) |
| `--version-number` | **Yes** | long | -- | Version number |

**Output:** None on success.

---

### 3.7 `get-layer-version-policy`

Returns the permission policy for a layer version.

**Synopsis:**
```bash
aws lambda get-layer-version-policy \
    --layer-name <value> \
    --version-number <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--layer-name` | **Yes** | string | -- | Layer name or ARN (1-140 chars) |
| `--version-number` | **Yes** | long | -- | Version number |

**Output Schema:**
```json
{
    "Policy": "string",
    "RevisionId": "string"
}
```

---

### 3.8 `add-layer-version-permission`

Adds permission to a layer version's resource-based policy.

**Synopsis:**
```bash
aws lambda add-layer-version-permission \
    --layer-name <value> \
    --version-number <value> \
    --statement-id <value> \
    --action <value> \
    --principal <value> \
    [--organization-id <value>] \
    [--revision-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--layer-name` | **Yes** | string | -- | Layer name or ARN (1-140 chars) |
| `--version-number` | **Yes** | long | -- | Version number |
| `--statement-id` | **Yes** | string | -- | Statement identifier (1-100 chars) |
| `--action` | **Yes** | string | -- | API action (e.g., `lambda:GetLayerVersion`) |
| `--principal` | **Yes** | string | -- | Account ID, `*`, or organization ID |
| `--organization-id` | No | string | -- | AWS Organizations ID (e.g., `o-a1b2c3d4e5`) |
| `--revision-id` | No | string | -- | Only update if revision ID matches |

**Output Schema:**
```json
{
    "Statement": "string",
    "RevisionId": "string"
}
```

---

### 3.9 `remove-layer-version-permission`

Removes a statement from a layer version's resource-based policy.

**Synopsis:**
```bash
aws lambda remove-layer-version-permission \
    --layer-name <value> \
    --version-number <value> \
    --statement-id <value> \
    [--revision-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--layer-name` | **Yes** | string | -- | Layer name or ARN (1-140 chars) |
| `--version-number` | **Yes** | long | -- | Version number |
| `--statement-id` | **Yes** | string | -- | Statement identifier (1-100 chars) |
| `--revision-id` | No | string | -- | Only update if revision ID matches |

**Output:** None on success.

---
