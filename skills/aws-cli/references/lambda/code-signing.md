# Code Signing

### 10.1 `create-code-signing-config`

Creates a code signing configuration that defines which signing profiles are trusted for deployment.

**Synopsis:**
```bash
aws lambda create-code-signing-config \
    --allowed-publishers <value> \
    [--description <value>] \
    [--code-signing-policies <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--allowed-publishers` | **Yes** | structure | -- | Signing profiles. JSON: `{"SigningProfileVersionArns":["arn:..."]}` (1-20 ARNs) |
| `--description` | No | string | -- | Description (0-256 chars) |
| `--code-signing-policies` | No | structure | `Warn` | Deployment validation policy. Shorthand: `UntrustedArtifactOnDeployment=Warn\|Enforce` |
| `--tags` | No | map | -- | Tags |

**Output Schema:**
```json
{
    "CodeSigningConfig": {
        "CodeSigningConfigId": "string",
        "CodeSigningConfigArn": "string",
        "Description": "string",
        "AllowedPublishers": {
            "SigningProfileVersionArns": ["string"]
        },
        "CodeSigningPolicies": {
            "UntrustedArtifactOnDeployment": "Warn|Enforce"
        },
        "LastModified": "string"
    }
}
```

---

### 10.2 `get-code-signing-config`

Returns a code signing configuration.

**Synopsis:**
```bash
aws lambda get-code-signing-config \
    --code-signing-config-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--code-signing-config-arn` | **Yes** | string | -- | Code signing config ARN |

**Output Schema:** Same as `create-code-signing-config`.

---

### 10.3 `update-code-signing-config`

Updates a code signing configuration.

**Synopsis:**
```bash
aws lambda update-code-signing-config \
    --code-signing-config-arn <value> \
    [--description <value>] \
    [--allowed-publishers <value>] \
    [--code-signing-policies <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--code-signing-config-arn` | **Yes** | string | -- | Code signing config ARN |
| `--description` | No | string | -- | Description (0-256 chars) |
| `--allowed-publishers` | No | structure | -- | Signing profiles |
| `--code-signing-policies` | No | structure | -- | Deployment validation policy |

**Output Schema:** Same as `create-code-signing-config`.

---

### 10.4 `list-code-signing-configs`

Lists code signing configurations. **Paginated operation.**

**Synopsis:**
```bash
aws lambda list-code-signing-configs \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "CodeSigningConfigs": [
        {
            "CodeSigningConfigId": "string",
            "CodeSigningConfigArn": "string",
            "Description": "string",
            "AllowedPublishers": {
                "SigningProfileVersionArns": ["string"]
            },
            "CodeSigningPolicies": {
                "UntrustedArtifactOnDeployment": "Warn|Enforce"
            },
            "LastModified": "string"
        }
    ],
    "NextMarker": "string"
}
```

---

### 10.5 `delete-code-signing-config`

Deletes a code signing configuration. Can only be deleted if not in use by any function.

**Synopsis:**
```bash
aws lambda delete-code-signing-config \
    --code-signing-config-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--code-signing-config-arn` | **Yes** | string | -- | Code signing config ARN |

**Output:** None on success.

---

### 10.6 `put-function-code-signing-config`

Associates a code signing configuration with a function.

**Synopsis:**
```bash
aws lambda put-function-code-signing-config \
    --code-signing-config-arn <value> \
    --function-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--code-signing-config-arn` | **Yes** | string | -- | Code signing config ARN |
| `--function-name` | **Yes** | string | -- | Function name or ARN (1-140 chars) |

**Output Schema:**
```json
{
    "CodeSigningConfigArn": "string",
    "FunctionName": "string"
}
```

---

### 10.7 `get-function-code-signing-config`

Returns the code signing configuration associated with a function.

**Synopsis:**
```bash
aws lambda get-function-code-signing-config \
    --function-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--function-name` | **Yes** | string | -- | Function name or ARN (1-140 chars) |

**Output Schema:**
```json
{
    "CodeSigningConfigArn": "string",
    "FunctionName": "string"
}
```

---

### 10.8 `delete-function-code-signing-config`

Removes the code signing configuration from a function.

**Synopsis:**
```bash
aws lambda delete-function-code-signing-config \
    --function-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--function-name` | **Yes** | string | -- | Function name or ARN (1-140 chars) |

**Output:** None on success.

---

### 10.9 `list-functions-by-code-signing-config`

Lists functions that use a code signing configuration. **Paginated operation.**

**Synopsis:**
```bash
aws lambda list-functions-by-code-signing-config \
    --code-signing-config-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--code-signing-config-arn` | **Yes** | string | -- | Code signing config ARN |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "FunctionArns": ["string"],
    "NextMarker": "string"
}
```

---
