# Service Templates

### 5.1 `create-service-template`

Creates a service template.

**Synopsis:**
```bash
aws proton create-service-template \
    --name <value> \
    [--display-name <value>] \
    [--description <value>] \
    [--encryption-key <value>] \
    [--pipeline-provisioning <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Template name |
| `--display-name` | No | string | None | Display name |
| `--description` | No | string | None | Description |
| `--encryption-key` | No | string | None | KMS key ARN for encryption |
| `--pipeline-provisioning` | No | string | None | `CUSTOMER_MANAGED` to disable Proton-managed pipeline |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "serviceTemplate": {
        "arn": "string",
        "name": "string",
        "displayName": "string",
        "description": "string",
        "createdAt": "timestamp",
        "lastModifiedAt": "timestamp",
        "recommendedVersion": "string",
        "encryptionKey": "string",
        "pipelineProvisioning": "CUSTOMER_MANAGED"
    }
}
```

---

### 5.2 `update-service-template`

Updates a service template.

**Synopsis:**
```bash
aws proton update-service-template \
    --name <value> \
    [--display-name <value>] \
    [--description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Template name |
| `--display-name` | No | string | None | Updated display name |
| `--description` | No | string | None | Updated description |

**Output Schema:** Same as `create-service-template`.

---

### 5.3 `delete-service-template`

Deletes a service template.

**Synopsis:**
```bash
aws proton delete-service-template \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Template name |

**Output Schema:** Same as `create-service-template`.

---

### 5.4 `get-service-template`

Gets a service template.

**Synopsis:**
```bash
aws proton get-service-template \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Template name |

**Output Schema:** Same as `create-service-template`.

---

### 5.5 `list-service-templates`

Lists service templates. **Paginated operation.**

**Synopsis:**
```bash
aws proton list-service-templates \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "templates": [
        {
            "arn": "string",
            "name": "string",
            "displayName": "string",
            "description": "string",
            "createdAt": "timestamp",
            "lastModifiedAt": "timestamp",
            "recommendedVersion": "string",
            "pipelineProvisioning": "CUSTOMER_MANAGED"
        }
    ],
    "nextToken": "string"
}
```

---

### 5.6 `create-service-template-version`

Creates a new version of a service template.

**Synopsis:**
```bash
aws proton create-service-template-version \
    --template-name <value> \
    --source <value> \
    --compatible-environment-templates <value> \
    [--major-version <value>] \
    [--description <value>] \
    [--supported-component-sources <value>] \
    [--client-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--template-name` | **Yes** | string | -- | Template name |
| `--source` | **Yes** | structure | -- | Template source. Shorthand: `s3={bucket=string,key=string}` |
| `--compatible-environment-templates` | **Yes** | list | -- | Compatible env templates. Shorthand: `templateName=string,majorVersion=string ...` |
| `--major-version` | No | string | None | Major version |
| `--description` | No | string | None | Description |
| `--supported-component-sources` | No | list | None | Component sources: `DIRECTLY_DEFINED` |
| `--client-token` | No | string | None | Idempotency token |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "serviceTemplateVersion": {
        "arn": "string",
        "templateName": "string",
        "majorVersion": "string",
        "minorVersion": "string",
        "description": "string",
        "status": "REGISTRATION_IN_PROGRESS|REGISTRATION_FAILED|DRAFT|PUBLISHED",
        "statusMessage": "string",
        "recommendedMinorVersion": "string",
        "schema": "string",
        "compatibleEnvironmentTemplates": [
            {
                "templateName": "string",
                "majorVersion": "string"
            }
        ],
        "supportedComponentSources": ["DIRECTLY_DEFINED"],
        "createdAt": "timestamp",
        "lastModifiedAt": "timestamp"
    }
}
```

---

### 5.7 `update-service-template-version`

Updates a version of a service template.

**Synopsis:**
```bash
aws proton update-service-template-version \
    --template-name <value> \
    --major-version <value> \
    --minor-version <value> \
    [--description <value>] \
    [--status <value>] \
    [--compatible-environment-templates <value>] \
    [--supported-component-sources <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--template-name` | **Yes** | string | -- | Template name |
| `--major-version` | **Yes** | string | -- | Major version |
| `--minor-version` | **Yes** | string | -- | Minor version |
| `--description` | No | string | None | Updated description |
| `--status` | No | string | None | `DRAFT` or `PUBLISHED` |
| `--compatible-environment-templates` | No | list | None | Updated compatible env templates |
| `--supported-component-sources` | No | list | None | Updated component sources |

**Output Schema:** Same as `create-service-template-version`.

---

### 5.8 `delete-service-template-version`

Deletes a version of a service template.

**Synopsis:**
```bash
aws proton delete-service-template-version \
    --template-name <value> \
    --major-version <value> \
    --minor-version <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--template-name` | **Yes** | string | -- | Template name |
| `--major-version` | **Yes** | string | -- | Major version |
| `--minor-version` | **Yes** | string | -- | Minor version |

**Output Schema:** Same as `create-service-template-version`.

---

### 5.9 `get-service-template-version`

Gets a version of a service template.

**Synopsis:**
```bash
aws proton get-service-template-version \
    --template-name <value> \
    --major-version <value> \
    --minor-version <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--template-name` | **Yes** | string | -- | Template name |
| `--major-version` | **Yes** | string | -- | Major version |
| `--minor-version` | **Yes** | string | -- | Minor version |

**Output Schema:** Same as `create-service-template-version`.

---

### 5.10 `list-service-template-versions`

Lists versions of a service template. **Paginated operation.**

**Synopsis:**
```bash
aws proton list-service-template-versions \
    --template-name <value> \
    [--major-version <value>] \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--template-name` | **Yes** | string | -- | Template name |
| `--major-version` | No | string | None | Filter by major version |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "templateVersions": [
        {
            "arn": "string",
            "templateName": "string",
            "majorVersion": "string",
            "minorVersion": "string",
            "description": "string",
            "status": "string",
            "statusMessage": "string",
            "recommendedMinorVersion": "string",
            "createdAt": "timestamp",
            "lastModifiedAt": "timestamp"
        }
    ],
    "nextToken": "string"
}
```
