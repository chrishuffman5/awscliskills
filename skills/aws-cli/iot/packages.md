# Packages

## 14.1 `create-package`

Creates a software package for IoT device management.

**Synopsis:**
```bash
aws iot create-package \
    --package-name <value> \
    [--description <value>] \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--package-name` | **Yes** | string | -- | Package name (1-128 chars, pattern `[a-zA-Z0-9-_.]+`) |
| `--description` | No | string | None | Description (max 1024 chars) |
| `--tags` | No | map | None | Tags (max 50) |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "packageName": "string",
    "packageArn": "string",
    "description": "string"
}
```

---

## 14.2 `get-package`

Gets a software package.

**Synopsis:**
```bash
aws iot get-package \
    --package-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--package-name` | **Yes** | string | -- | Package name |

**Output Schema:**
```json
{
    "packageName": "string",
    "packageArn": "string",
    "description": "string",
    "defaultVersionName": "string",
    "creationDate": "timestamp",
    "lastModifiedDate": "timestamp"
}
```

---

## 14.3 `list-packages`

Lists software packages. **Paginated operation.**

**Synopsis:**
```bash
aws iot list-packages \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--max-results` | No | integer | None | Max results |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "packageSummaries": [
        {
            "packageName": "string",
            "defaultVersionName": "string",
            "creationDate": "timestamp",
            "lastModifiedDate": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

## 14.4 `update-package`

Updates a software package.

**Synopsis:**
```bash
aws iot update-package \
    --package-name <value> \
    [--description <value>] \
    [--default-version-name <value>] \
    [--unset-default-version | --no-unset-default-version] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--package-name` | **Yes** | string | -- | Package name |
| `--description` | No | string | None | Updated description |
| `--default-version-name` | No | string | None | Set default version |
| `--unset-default-version` | No | boolean | false | Unset default version |
| `--client-token` | No | string | Auto | Idempotency token |

**Output:** None

---

## 14.5 `delete-package`

Deletes a software package. All versions must be deleted first.

**Synopsis:**
```bash
aws iot delete-package \
    --package-name <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--package-name` | **Yes** | string | -- | Package name |
| `--client-token` | No | string | Auto | Idempotency token |

**Output:** None

---

## 14.6 `get-package-configuration`

Gets the package configuration (S3 destination for version attributes).

**Synopsis:**
```bash
aws iot get-package-configuration \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output Schema:**
```json
{
    "versionUpdateByJobsConfig": {
        "enabled": "boolean",
        "roleArn": "string"
    }
}
```

---

## 14.7 `update-package-configuration`

Updates the package configuration.

**Synopsis:**
```bash
aws iot update-package-configuration \
    [--version-update-by-jobs-config <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--version-update-by-jobs-config` | No | structure | None | `{enabled: boolean, roleArn: "string"}` |
| `--client-token` | No | string | Auto | Idempotency token |

**Output:** None

---

## 14.8 `create-package-version`

Creates a software package version.

**Synopsis:**
```bash
aws iot create-package-version \
    --package-name <value> \
    --version-name <value> \
    [--description <value>] \
    [--attributes <value>] \
    [--artifact <value>] \
    [--recipe <value>] \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--package-name` | **Yes** | string | -- | Package name |
| `--version-name` | **Yes** | string | -- | Version name (1-64 chars) |
| `--description` | No | string | None | Description |
| `--attributes` | No | map | None | Version attributes |
| `--artifact` | No | structure | None | S3 artifact location |
| `--recipe` | No | string | None | Recipe content |
| `--tags` | No | map | None | Tags |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "packageVersionArn": "string",
    "packageName": "string",
    "versionName": "string",
    "description": "string",
    "attributes": {},
    "status": "DRAFT|PUBLISHED|DEPRECATED",
    "errorReason": "string"
}
```

---

## 14.9 `get-package-version`

Gets a software package version.

**Synopsis:**
```bash
aws iot get-package-version \
    --package-name <value> \
    --version-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--package-name` | **Yes** | string | -- | Package name |
| `--version-name` | **Yes** | string | -- | Version name |

**Output Schema:**
```json
{
    "packageVersionArn": "string",
    "packageName": "string",
    "versionName": "string",
    "description": "string",
    "attributes": {},
    "artifact": {"s3Location": {"bucket": "string", "key": "string", "version": "string"}},
    "status": "DRAFT|PUBLISHED|DEPRECATED",
    "errorReason": "string",
    "creationDate": "timestamp",
    "lastModifiedDate": "timestamp",
    "sbom": {},
    "sbomValidationStatus": "IN_PROGRESS|SUCCEEDED|FAILED",
    "recipe": "string"
}
```

---

## 14.10 `list-package-versions`

Lists package versions. **Paginated operation.**

**Synopsis:**
```bash
aws iot list-package-versions \
    --package-name <value> \
    [--status <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--package-name` | **Yes** | string | -- | Package name |
| `--status` | No | string | None | Filter: `DRAFT`, `PUBLISHED`, `DEPRECATED` |
| `--max-results` | No | integer | None | Max results |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "packageVersionSummaries": [
        {
            "packageName": "string",
            "versionName": "string",
            "status": "DRAFT|PUBLISHED|DEPRECATED",
            "creationDate": "timestamp",
            "lastModifiedDate": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

## 14.11 `update-package-version`

Updates a package version status or attributes.

**Synopsis:**
```bash
aws iot update-package-version \
    --package-name <value> \
    --version-name <value> \
    [--description <value>] \
    [--attributes <value>] \
    [--artifact <value>] \
    [--recipe <value>] \
    [--action <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--package-name` | **Yes** | string | -- | Package name |
| `--version-name` | **Yes** | string | -- | Version name |
| `--description` | No | string | None | Updated description |
| `--attributes` | No | map | None | Updated attributes |
| `--artifact` | No | structure | None | Updated artifact |
| `--recipe` | No | string | None | Updated recipe |
| `--action` | No | string | None | `PUBLISH` or `DEPRECATE` |
| `--client-token` | No | string | Auto | Idempotency token |

**Output:** None

---

## 14.12 `delete-package-version`

Deletes a package version.

**Synopsis:**
```bash
aws iot delete-package-version \
    --package-name <value> \
    --version-name <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--package-name` | **Yes** | string | -- | Package name |
| `--version-name` | **Yes** | string | -- | Version name |
| `--client-token` | No | string | Auto | Idempotency token |

**Output:** None

---

## 14.13 `associate-sbom-with-package-version`

Associates an SBOM (Software Bill of Materials) with a package version.

**Synopsis:**
```bash
aws iot associate-sbom-with-package-version \
    --package-name <value> \
    --version-name <value> \
    --sbom <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--package-name` | **Yes** | string | -- | Package name |
| `--version-name` | **Yes** | string | -- | Version name |
| `--sbom` | **Yes** | structure | -- | SBOM S3 location: `{s3Location: {bucket, key, version}}` |
| `--client-token` | No | string | Auto | Idempotency token |

**Output:** None

---

## 14.14 `disassociate-sbom-from-package-version`

Removes an SBOM from a package version.

**Synopsis:**
```bash
aws iot disassociate-sbom-from-package-version \
    --package-name <value> \
    --version-name <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--package-name` | **Yes** | string | -- | Package name |
| `--version-name` | **Yes** | string | -- | Version name |
| `--client-token` | No | string | Auto | Idempotency token |

**Output:** None

---

## 14.15 `list-sbom-validation-results`

Lists SBOM validation results. **Paginated operation.**

**Synopsis:**
```bash
aws iot list-sbom-validation-results \
    --package-name <value> \
    --version-name <value> \
    --validation-result <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--package-name` | **Yes** | string | -- | Package name |
| `--version-name` | **Yes** | string | -- | Version name |
| `--validation-result` | **Yes** | string | -- | `FAILED` or `SUCCEEDED` |
| `--max-results` | No | integer | None | Max results |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "validationResultSummaries": [
        {
            "fileName": "string",
            "validationResult": "FAILED|SUCCEEDED",
            "errorCode": "string",
            "errorMessage": "string"
        }
    ],
    "nextToken": "string"
}
```
