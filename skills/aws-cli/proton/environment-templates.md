# Environment Templates

### 2.1 `create-environment-template`

Creates an environment template.

**Synopsis:**
```bash
aws proton create-environment-template \
    --name <value> \
    [--display-name <value>] \
    [--description <value>] \
    [--encryption-key <value>] \
    [--provisioning <value>] \
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
| `--provisioning` | No | string | None | `CUSTOMER_MANAGED` for self-managed provisioning |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "environmentTemplate": {
        "arn": "string",
        "name": "string",
        "displayName": "string",
        "description": "string",
        "createdAt": "timestamp",
        "lastModifiedAt": "timestamp",
        "recommendedVersion": "string",
        "encryptionKey": "string",
        "provisioning": "CUSTOMER_MANAGED"
    }
}
```

---

### 2.2 `update-environment-template`

Updates an environment template.

**Synopsis:**
```bash
aws proton update-environment-template \
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

**Output Schema:** Same as `create-environment-template`.

---

### 2.3 `delete-environment-template`

Deletes an environment template.

**Synopsis:**
```bash
aws proton delete-environment-template \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Template name |

**Output Schema:** Same as `create-environment-template`.

---

### 2.4 `get-environment-template`

Gets an environment template.

**Synopsis:**
```bash
aws proton get-environment-template \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Template name |

**Output Schema:** Same as `create-environment-template`.

---

### 2.5 `list-environment-templates`

Lists environment templates. **Paginated operation.**

**Synopsis:**
```bash
aws proton list-environment-templates \
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
            "provisioning": "CUSTOMER_MANAGED"
        }
    ],
    "nextToken": "string"
}
```

---

### 2.6 `create-environment-template-version`

Creates a new version of an environment template.

**Synopsis:**
```bash
aws proton create-environment-template-version \
    --template-name <value> \
    --source <value> \
    [--major-version <value>] \
    [--description <value>] \
    [--client-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--template-name` | **Yes** | string | -- | Template name |
| `--source` | **Yes** | structure | -- | Source for the template. Shorthand: `s3={bucket=string,key=string}` |
| `--major-version` | No | string | None | Major version (auto-incremented if not specified) |
| `--description` | No | string | None | Description |
| `--client-token` | No | string | None | Idempotency token |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "environmentTemplateVersion": {
        "arn": "string",
        "templateName": "string",
        "majorVersion": "string",
        "minorVersion": "string",
        "description": "string",
        "status": "REGISTRATION_IN_PROGRESS|REGISTRATION_FAILED|DRAFT|PUBLISHED",
        "statusMessage": "string",
        "recommendedMinorVersion": "string",
        "schema": "string",
        "createdAt": "timestamp",
        "lastModifiedAt": "timestamp"
    }
}
```

---

### 2.7 `update-environment-template-version`

Updates a version of an environment template.

**Synopsis:**
```bash
aws proton update-environment-template-version \
    --template-name <value> \
    --major-version <value> \
    --minor-version <value> \
    [--description <value>] \
    [--status <value>] \
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

**Output Schema:** Same as `create-environment-template-version`.

---

### 2.8 `delete-environment-template-version`

Deletes a version of an environment template.

**Synopsis:**
```bash
aws proton delete-environment-template-version \
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

**Output Schema:** Same as `create-environment-template-version`.

---

### 2.9 `get-environment-template-version`

Gets a version of an environment template.

**Synopsis:**
```bash
aws proton get-environment-template-version \
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

**Output Schema:** Same as `create-environment-template-version`.

---

### 2.10 `list-environment-template-versions`

Lists versions of an environment template. **Paginated operation.**

**Synopsis:**
```bash
aws proton list-environment-template-versions \
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
