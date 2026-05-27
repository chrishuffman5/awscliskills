# Repositories & Sync

### 8.1 `create-repository`

Links a repository to Proton for template sync or service sync.

**Synopsis:**
```bash
aws proton create-repository \
    --provider <value> \
    --name <value> \
    --connection-arn <value> \
    [--encryption-key <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--provider` | **Yes** | string | -- | `GITHUB`, `GITHUB_ENTERPRISE`, or `BITBUCKET` |
| `--name` | **Yes** | string | -- | Repository name (e.g., `owner/repo`) |
| `--connection-arn` | **Yes** | string | -- | CodeStar Connections ARN |
| `--encryption-key` | No | string | None | KMS key ARN for encryption |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "repository": {
        "arn": "string",
        "provider": "GITHUB|GITHUB_ENTERPRISE|BITBUCKET",
        "name": "string",
        "connectionArn": "string",
        "encryptionKey": "string"
    }
}
```

---

### 8.2 `delete-repository`

Unlinks a repository from Proton.

**Synopsis:**
```bash
aws proton delete-repository \
    --provider <value> \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--provider` | **Yes** | string | -- | Repository provider |
| `--name` | **Yes** | string | -- | Repository name |

**Output Schema:** Same as `create-repository`.

---

### 8.3 `get-repository`

Gets a linked repository.

**Synopsis:**
```bash
aws proton get-repository \
    --provider <value> \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--provider` | **Yes** | string | -- | Repository provider |
| `--name` | **Yes** | string | -- | Repository name |

**Output Schema:** Same as `create-repository`.

---

### 8.4 `list-repositories`

Lists linked repositories. **Paginated operation.**

**Synopsis:**
```bash
aws proton list-repositories \
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
    "repositories": [
        {
            "arn": "string",
            "provider": "GITHUB|GITHUB_ENTERPRISE|BITBUCKET",
            "name": "string",
            "connectionArn": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 8.5 `get-repository-sync-status`

Gets the repository sync status.

**Synopsis:**
```bash
aws proton get-repository-sync-status \
    --repository-name <value> \
    --repository-provider <value> \
    --branch <value> \
    --sync-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--repository-name` | **Yes** | string | -- | Repository name |
| `--repository-provider` | **Yes** | string | -- | Repository provider |
| `--branch` | **Yes** | string | -- | Branch name |
| `--sync-type` | **Yes** | string | -- | `TEMPLATE_SYNC` or `SERVICE_SYNC` |

**Output Schema:**
```json
{
    "latestSync": {
        "startedAt": "timestamp",
        "status": "INITIATED|IN_PROGRESS|SUCCEEDED|FAILED|QUEUED",
        "events": [
            {
                "type": "string",
                "externalId": "string",
                "time": "timestamp",
                "event": "string"
            }
        ]
    }
}
```

---

### 8.6 `create-template-sync-config`

Creates a template sync configuration to sync template bundles from a repository.

**Synopsis:**
```bash
aws proton create-template-sync-config \
    --template-name <value> \
    --template-type <value> \
    --repository-provider <value> \
    --repository-name <value> \
    --branch <value> \
    [--subdirectory <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--template-name` | **Yes** | string | -- | Template name |
| `--template-type` | **Yes** | string | -- | `ENVIRONMENT` or `SERVICE` |
| `--repository-provider` | **Yes** | string | -- | Repository provider |
| `--repository-name` | **Yes** | string | -- | Repository name |
| `--branch` | **Yes** | string | -- | Branch name |
| `--subdirectory` | No | string | None | Subdirectory path for template bundle |

**Output Schema:**
```json
{
    "templateSyncConfig": {
        "templateName": "string",
        "templateType": "ENVIRONMENT|SERVICE",
        "repositoryProvider": "string",
        "repositoryName": "string",
        "branch": "string",
        "subdirectory": "string"
    }
}
```

---

### 8.7 `update-template-sync-config`

Updates a template sync configuration.

**Synopsis:**
```bash
aws proton update-template-sync-config \
    --template-name <value> \
    --template-type <value> \
    --repository-provider <value> \
    --repository-name <value> \
    --branch <value> \
    [--subdirectory <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** Same as `create-template-sync-config`.

**Output Schema:** Same as `create-template-sync-config`.

---

### 8.8 `delete-template-sync-config`

Deletes a template sync configuration.

**Synopsis:**
```bash
aws proton delete-template-sync-config \
    --template-name <value> \
    --template-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--template-name` | **Yes** | string | -- | Template name |
| `--template-type` | **Yes** | string | -- | `ENVIRONMENT` or `SERVICE` |

**Output Schema:** Same as `create-template-sync-config`.

---

### 8.9 `get-template-sync-config`

Gets a template sync configuration.

**Synopsis:**
```bash
aws proton get-template-sync-config \
    --template-name <value> \
    --template-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--template-name` | **Yes** | string | -- | Template name |
| `--template-type` | **Yes** | string | -- | `ENVIRONMENT` or `SERVICE` |

**Output Schema:** Same as `create-template-sync-config`.

---

### 8.10 `get-template-sync-status`

Gets the template sync status for a template version.

**Synopsis:**
```bash
aws proton get-template-sync-status \
    --template-name <value> \
    --template-type <value> \
    --template-version <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--template-name` | **Yes** | string | -- | Template name |
| `--template-type` | **Yes** | string | -- | `ENVIRONMENT` or `SERVICE` |
| `--template-version` | **Yes** | string | -- | Template version |

**Output Schema:**
```json
{
    "latestSync": {
        "startedAt": "timestamp",
        "status": "INITIATED|IN_PROGRESS|SUCCEEDED|FAILED|QUEUED",
        "events": [
            {
                "type": "string",
                "externalId": "string",
                "time": "timestamp",
                "event": "string"
            }
        ]
    },
    "latestSuccessfulSync": {
        "startedAt": "timestamp",
        "status": "SUCCEEDED",
        "events": []
    },
    "desiredState": {
        "branch": "string",
        "repositoryName": "string",
        "repositoryProvider": "string",
        "sha": "string",
        "directory": "string"
    }
}
```

---

### 8.11 `create-service-sync-config`

Creates a service sync configuration to sync service specs from a repository.

**Synopsis:**
```bash
aws proton create-service-sync-config \
    --service-name <value> \
    --repository-provider <value> \
    --repository-name <value> \
    --branch <value> \
    --file-path <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-name` | **Yes** | string | -- | Service name |
| `--repository-provider` | **Yes** | string | -- | Repository provider |
| `--repository-name` | **Yes** | string | -- | Repository name |
| `--branch` | **Yes** | string | -- | Branch name |
| `--file-path` | **Yes** | string | -- | Path to service spec file in repository |

**Output Schema:**
```json
{
    "serviceSyncConfig": {
        "serviceName": "string",
        "repositoryProvider": "string",
        "repositoryName": "string",
        "branch": "string",
        "filePath": "string"
    }
}
```

---

### 8.12 `update-service-sync-config`

Updates a service sync configuration.

**Synopsis:**
```bash
aws proton update-service-sync-config \
    --service-name <value> \
    --repository-provider <value> \
    --repository-name <value> \
    --branch <value> \
    --file-path <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** Same as `create-service-sync-config`.

**Output Schema:** Same as `create-service-sync-config`.

---

### 8.13 `delete-service-sync-config`

Deletes a service sync configuration.

**Synopsis:**
```bash
aws proton delete-service-sync-config \
    --service-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-name` | **Yes** | string | -- | Service name |

**Output Schema:** Same as `create-service-sync-config`.

---

### 8.14 `get-service-sync-config`

Gets a service sync configuration.

**Synopsis:**
```bash
aws proton get-service-sync-config \
    --service-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-name` | **Yes** | string | -- | Service name |

**Output Schema:** Same as `create-service-sync-config`.

---

### 8.15 `get-service-sync-blocker-summary`

Gets a summary of sync blockers for a service.

**Synopsis:**
```bash
aws proton get-service-sync-blocker-summary \
    --service-name <value> \
    [--service-instance-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-name` | **Yes** | string | -- | Service name |
| `--service-instance-name` | No | string | None | Service instance name |

**Output Schema:**
```json
{
    "serviceSyncBlockerSummary": {
        "serviceName": "string",
        "serviceInstanceName": "string",
        "latestBlockers": [
            {
                "id": "string",
                "type": "AUTOMATED",
                "status": "ACTIVE|RESOLVED",
                "reason": "string",
                "createdAt": "timestamp",
                "createdReason": "string",
                "resolvedAt": "timestamp",
                "resolvedReason": "string",
                "contexts": [
                    {
                        "key": "string",
                        "value": "string"
                    }
                ]
            }
        ]
    }
}
```

---

### 8.16 `notify-resource-deployment-status-change`

Notifies Proton of a resource deployment status change (for self-managed provisioning).

**Synopsis:**
```bash
aws proton notify-resource-deployment-status-change \
    --resource-arn <value> \
    [--status <value>] \
    [--deployment-id <value>] \
    [--outputs <value>] \
    [--status-message <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the Proton resource |
| `--status` | No | string | None | `IN_PROGRESS`, `FAILED`, or `SUCCEEDED` |
| `--deployment-id` | No | string | None | Deployment ID |
| `--outputs` | No | list | None | Resource outputs. Shorthand: `key=string,valueString=string ...` |
| `--status-message` | No | string | None | Status message |

**Output Schema:**
```json
{}
```
