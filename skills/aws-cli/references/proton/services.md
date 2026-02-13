# Services

### 3.1 `create-service`

Creates a Proton service.

**Synopsis:**
```bash
aws proton create-service \
    --name <value> \
    --template-name <value> \
    --template-major-version <value> \
    --spec <value> \
    [--template-minor-version <value>] \
    [--description <value>] \
    [--repository-connection-arn <value>] \
    [--repository-id <value>] \
    [--branch-name <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Service name |
| `--template-name` | **Yes** | string | -- | Service template name |
| `--template-major-version` | **Yes** | string | -- | Template major version |
| `--spec` | **Yes** | string | -- | Service spec (YAML) |
| `--template-minor-version` | No | string | None | Template minor version |
| `--description` | No | string | None | Description |
| `--repository-connection-arn` | No | string | None | CodeStar connection ARN for pipeline |
| `--repository-id` | No | string | None | Repository ID for pipeline |
| `--branch-name` | No | string | None | Branch name for pipeline |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "service": {
        "arn": "string",
        "name": "string",
        "description": "string",
        "createdAt": "timestamp",
        "lastModifiedAt": "timestamp",
        "templateName": "string",
        "status": "CREATE_IN_PROGRESS|CREATE_FAILED_CLEANUP_IN_PROGRESS|CREATE_FAILED_CLEANUP_COMPLETE|CREATE_FAILED_CLEANUP_FAILED|CREATE_FAILED|ACTIVE|DELETE_IN_PROGRESS|DELETE_FAILED|UPDATE_IN_PROGRESS|UPDATE_FAILED_CLEANUP_IN_PROGRESS|UPDATE_FAILED_CLEANUP_COMPLETE|UPDATE_FAILED_CLEANUP_FAILED|UPDATE_FAILED|UPDATE_COMPLETE_CLEANUP_FAILED",
        "statusMessage": "string",
        "spec": "string",
        "pipeline": {
            "arn": "string",
            "createdAt": "timestamp",
            "lastDeploymentAttemptedAt": "timestamp",
            "lastDeploymentSucceededAt": "timestamp",
            "templateName": "string",
            "templateMajorVersion": "string",
            "templateMinorVersion": "string",
            "deploymentStatus": "string",
            "deploymentStatusMessage": "string",
            "spec": "string"
        },
        "repositoryConnectionArn": "string",
        "repositoryId": "string",
        "branchName": "string"
    }
}
```

---

### 3.2 `update-service`

Updates a service description or pipeline connection.

**Synopsis:**
```bash
aws proton update-service \
    --name <value> \
    [--description <value>] \
    [--spec <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Service name |
| `--description` | No | string | None | Updated description |
| `--spec` | No | string | None | Updated spec |

**Output Schema:** Same as `create-service`.

---

### 3.3 `delete-service`

Deletes a service with all its instances and pipeline.

**Synopsis:**
```bash
aws proton delete-service \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Service name |

**Output Schema:** Same as `create-service`.

---

### 3.4 `get-service`

Gets a service.

**Synopsis:**
```bash
aws proton get-service \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Service name |

**Output Schema:** Same as `create-service`.

---

### 3.5 `list-services`

Lists services. **Paginated operation.**

**Synopsis:**
```bash
aws proton list-services \
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
    "services": [
        {
            "arn": "string",
            "name": "string",
            "description": "string",
            "createdAt": "timestamp",
            "lastModifiedAt": "timestamp",
            "templateName": "string",
            "status": "string",
            "statusMessage": "string"
        }
    ],
    "nextToken": "string"
}
```
