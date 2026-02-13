# Components

### 4.1 `create-component`

Creates a new component that can be used to build, validate, and test images. Components are defined using a YAML document format.

**Synopsis:**
```bash
aws imagebuilder create-component \
    --name <value> \
    --semantic-version <value> \
    --platform <value> \
    [--description <value>] \
    [--change-description <value>] \
    [--supported-os-versions <value>] \
    [--data <value>] \
    [--uri <value>] \
    [--kms-key-id <value>] \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the component |
| `--semantic-version` | **Yes** | string | -- | Semantic version (e.g., `1.0.0`) |
| `--platform` | **Yes** | string | -- | Platform: `Windows` or `Linux` |
| `--description` | No | string | -- | Description |
| `--change-description` | No | string | -- | Description of changes in this version |
| `--supported-os-versions` | No | list(string) | None | Supported OS versions |
| `--data` | No | string | -- | Inline component YAML document |
| `--uri` | No | string | -- | S3 URI of the component YAML document |
| `--kms-key-id` | No | string | -- | KMS key ID for encryption |
| `--tags` | No | map | None | Tags |
| `--client-token` | No | string | auto-generated | Idempotency token |

**Output Schema:**
```json
{
    "requestId": "string",
    "clientToken": "string",
    "componentBuildVersionArn": "string"
}
```

---

### 4.2 `get-component`

Gets a component object.

**Synopsis:**
```bash
aws imagebuilder get-component \
    --component-build-version-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--component-build-version-arn` | **Yes** | string | -- | ARN of the component build version |

**Output Schema:**
```json
{
    "requestId": "string",
    "component": {
        "arn": "string",
        "name": "string",
        "version": "string",
        "description": "string",
        "changeDescription": "string",
        "type": "BUILD|TEST",
        "platform": "Windows|Linux",
        "supportedOsVersions": ["string"],
        "state": {
            "status": "DEPRECATED",
            "reason": "string"
        },
        "parameters": [
            {
                "name": "string",
                "type": "string",
                "defaultValue": ["string"],
                "description": "string"
            }
        ],
        "owner": "string",
        "data": "string",
        "kmsKeyId": "string",
        "encrypted": "boolean",
        "dateCreated": "string",
        "tags": {},
        "publisher": "string",
        "obfuscate": "boolean"
    }
}
```

---

### 4.3 `list-components`

Lists component build versions. **Paginated operation.**

**Synopsis:**
```bash
aws imagebuilder list-components \
    [--owner <value>] \
    [--filters <value>] \
    [--by-name | --no-by-name] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--owner` | No | string | `Self` | Owner filter: `Self`, `Shared`, `Amazon`, `ThirdParty` |
| `--filters` | No | list | None | Filters. Names: `name`, `platform`, `type` |
| `--by-name` | No | boolean | false | Return only latest version of each component |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "requestId": "string",
    "componentVersionList": [
        {
            "arn": "string",
            "name": "string",
            "version": "string",
            "description": "string",
            "platform": "Windows|Linux",
            "type": "BUILD|TEST",
            "owner": "string",
            "dateCreated": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 4.4 `import-component`

Imports a component and transforms its data into a component document.

**Synopsis:**
```bash
aws imagebuilder import-component \
    --name <value> \
    --semantic-version <value> \
    --type <value> \
    --format <value> \
    --platform <value> \
    [--description <value>] \
    [--change-description <value>] \
    [--data <value>] \
    [--uri <value>] \
    [--kms-key-id <value>] \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the component |
| `--semantic-version` | **Yes** | string | -- | Semantic version |
| `--type` | **Yes** | string | -- | Component type: `BUILD` or `TEST` |
| `--format` | **Yes** | string | -- | Format: `SHELL` |
| `--platform` | **Yes** | string | -- | Platform: `Windows` or `Linux` |
| `--description` | No | string | -- | Description |
| `--change-description` | No | string | -- | Change description |
| `--data` | No | string | -- | Inline component data |
| `--uri` | No | string | -- | S3 URI of the component data |
| `--kms-key-id` | No | string | -- | KMS key for encryption |
| `--tags` | No | map | None | Tags |
| `--client-token` | No | string | auto-generated | Idempotency token |

**Output Schema:**
```json
{
    "requestId": "string",
    "clientToken": "string",
    "componentBuildVersionArn": "string"
}
```

---

### 4.5 `get-component-policy`

Gets the policy for a component.

**Synopsis:**
```bash
aws imagebuilder get-component-policy \
    --component-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--component-arn` | **Yes** | string | -- | ARN of the component |

**Output Schema:**
```json
{
    "requestId": "string",
    "policy": "string"
}
```

---

### 4.6 `put-component-policy`

Applies a policy to a component for cross-account sharing.

**Synopsis:**
```bash
aws imagebuilder put-component-policy \
    --component-arn <value> \
    --policy <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--component-arn` | **Yes** | string | -- | ARN of the component |
| `--policy` | **Yes** | string | -- | Resource policy JSON document |

**Output Schema:**
```json
{
    "requestId": "string",
    "componentArn": "string"
}
```

---

### 4.7 `delete-component`

Deletes a component build version.

**Synopsis:**
```bash
aws imagebuilder delete-component \
    --component-build-version-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--component-build-version-arn` | **Yes** | string | -- | ARN of the component build version to delete |

**Output Schema:**
```json
{
    "requestId": "string",
    "componentBuildVersionArn": "string"
}
```

---

### 4.8 `list-component-build-versions`

Lists component build versions. **Paginated operation.**

**Synopsis:**
```bash
aws imagebuilder list-component-build-versions \
    --component-version-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--component-version-arn` | **Yes** | string | -- | ARN of the component version |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "requestId": "string",
    "componentSummaryList": [
        {
            "arn": "string",
            "name": "string",
            "version": "string",
            "platform": "Windows|Linux",
            "type": "BUILD|TEST",
            "owner": "string",
            "description": "string",
            "changeDescription": "string",
            "dateCreated": "string",
            "supportedOsVersions": ["string"],
            "state": {
                "status": "string",
                "reason": "string"
            },
            "publisher": "string",
            "obfuscate": "boolean"
        }
    ],
    "nextToken": "string"
}
```
