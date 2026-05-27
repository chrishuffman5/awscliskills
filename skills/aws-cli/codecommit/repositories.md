# Repositories

### 1.1 `create-repository`

Creates a new, empty repository.

**Synopsis:**
```bash
aws codecommit create-repository \
    --repository-name <value> \
    [--repository-description <value>] \
    [--tags <value>] \
    [--kms-key-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--repository-name` | **Yes** | string | -- | Name of the repository (1-100 chars) |
| `--repository-description` | No | string | -- | Description of the repository |
| `--tags` | No | map | -- | Tags as key-value pairs |
| `--kms-key-id` | No | string | -- | KMS key ID or ARN for encryption |

**Output Schema:**
```json
{
    "repositoryMetadata": {
        "accountId": "string",
        "repositoryId": "string",
        "repositoryName": "string",
        "repositoryDescription": "string",
        "defaultBranch": "string",
        "lastModifiedDate": "timestamp",
        "creationDate": "timestamp",
        "cloneUrlHttp": "string",
        "cloneUrlSsh": "string",
        "Arn": "string",
        "kmsKeyId": "string"
    }
}
```

---

### 1.2 `delete-repository`

Deletes a repository. This action cannot be undone.

**Synopsis:**
```bash
aws codecommit delete-repository \
    --repository-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--repository-name` | **Yes** | string | -- | Name of the repository to delete |

**Output Schema:**
```json
{
    "repositoryId": "string"
}
```

---

### 1.3 `get-repository`

Returns information about a repository.

**Synopsis:**
```bash
aws codecommit get-repository \
    --repository-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--repository-name` | **Yes** | string | -- | Name of the repository |

**Output Schema:**
```json
{
    "repositoryMetadata": {
        "accountId": "string",
        "repositoryId": "string",
        "repositoryName": "string",
        "repositoryDescription": "string",
        "defaultBranch": "string",
        "lastModifiedDate": "timestamp",
        "creationDate": "timestamp",
        "cloneUrlHttp": "string",
        "cloneUrlSsh": "string",
        "Arn": "string",
        "kmsKeyId": "string"
    }
}
```

---

### 1.4 `list-repositories`

Lists all repositories in the account. **Paginated operation.**

**Synopsis:**
```bash
aws codecommit list-repositories \
    [--sort-by <value>] \
    [--order <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--sort-by` | No | string | `repositoryName` | Sort field: `repositoryName`, `lastModifiedDate` |
| `--order` | No | string | `ascending` | Sort order: `ascending`, `descending` |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "repositories": [
        {
            "repositoryName": "string",
            "repositoryId": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 1.5 `batch-get-repositories`

Returns information about one or more repositories.

**Synopsis:**
```bash
aws codecommit batch-get-repositories \
    --repository-names <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--repository-names` | **Yes** | list(string) | -- | Names of the repositories (max 25) |

**Output Schema:**
```json
{
    "repositories": [
        {
            "accountId": "string",
            "repositoryId": "string",
            "repositoryName": "string",
            "repositoryDescription": "string",
            "defaultBranch": "string",
            "lastModifiedDate": "timestamp",
            "creationDate": "timestamp",
            "cloneUrlHttp": "string",
            "cloneUrlSsh": "string",
            "Arn": "string",
            "kmsKeyId": "string"
        }
    ],
    "repositoriesNotFound": ["string"],
    "errors": [
        {
            "repositoryId": "string",
            "repositoryName": "string",
            "errorCode": "string",
            "errorMessage": "string"
        }
    ]
}
```

---

### 1.6 `update-repository-description`

Updates the description for a repository.

**Synopsis:**
```bash
aws codecommit update-repository-description \
    --repository-name <value> \
    [--repository-description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--repository-name` | **Yes** | string | -- | Name of the repository |
| `--repository-description` | No | string | -- | New description (empty string to clear) |

**Output Schema:**
```json
{}
```

---

### 1.7 `update-repository-name`

Renames a repository. The repository ID stays the same; only the name changes.

**Synopsis:**
```bash
aws codecommit update-repository-name \
    --old-name <value> \
    --new-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--old-name` | **Yes** | string | -- | Current name of the repository |
| `--new-name` | **Yes** | string | -- | New name for the repository |

**Output Schema:**
```json
{}
```
