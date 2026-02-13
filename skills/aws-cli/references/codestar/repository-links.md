# Repository Links

### 3.1 `create-repository-link`

Creates a link to a specified external code repository.

**Synopsis:**
```bash
aws codestar-connections create-repository-link \
    --connection-arn <value> \
    --owner-id <value> \
    --repository-name <value> \
    [--encryption-key-arn <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--connection-arn` | **Yes** | string | -- | ARN of the connection to use |
| `--owner-id` | **Yes** | string | -- | Owner or organization of the repository (e.g., GitHub org or user) |
| `--repository-name` | **Yes** | string | -- | Name of the repository |
| `--encryption-key-arn` | No | string | None | KMS key ARN for encryption |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "RepositoryLinkInfo": {
        "ConnectionArn": "string",
        "EncryptionKeyArn": "string",
        "OwnerId": "string",
        "ProviderType": "Bitbucket|GitHub|GitHubEnterpriseServer|GitLab|GitLabSelfManaged",
        "RepositoryLinkArn": "string",
        "RepositoryLinkId": "string",
        "RepositoryName": "string"
    }
}
```

---

### 3.2 `delete-repository-link`

Deletes a repository link.

**Synopsis:**
```bash
aws codestar-connections delete-repository-link \
    --repository-link-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--repository-link-id` | **Yes** | string | -- | ID of the repository link to delete |

**Output Schema:**
```json
{}
```

---

### 3.3 `get-repository-link`

Returns details of a repository link.

**Synopsis:**
```bash
aws codestar-connections get-repository-link \
    --repository-link-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--repository-link-id` | **Yes** | string | -- | ID of the repository link |

**Output Schema:**
```json
{
    "RepositoryLinkInfo": {
        "ConnectionArn": "string",
        "EncryptionKeyArn": "string",
        "OwnerId": "string",
        "ProviderType": "Bitbucket|GitHub|GitHubEnterpriseServer|GitLab|GitLabSelfManaged",
        "RepositoryLinkArn": "string",
        "RepositoryLinkId": "string",
        "RepositoryName": "string"
    }
}
```

---

### 3.4 `list-repository-links`

Lists repository links in the account. **Paginated operation.**

**Synopsis:**
```bash
aws codestar-connections list-repository-links \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "RepositoryLinks": [
        {
            "ConnectionArn": "string",
            "EncryptionKeyArn": "string",
            "OwnerId": "string",
            "ProviderType": "string",
            "RepositoryLinkArn": "string",
            "RepositoryLinkId": "string",
            "RepositoryName": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.5 `update-repository-link`

Updates a repository link's connection or encryption key.

**Synopsis:**
```bash
aws codestar-connections update-repository-link \
    --repository-link-id <value> \
    [--connection-arn <value>] \
    [--encryption-key-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--repository-link-id` | **Yes** | string | -- | ID of the repository link to update |
| `--connection-arn` | No | string | None | New connection ARN |
| `--encryption-key-arn` | No | string | None | New KMS key ARN |

**Output Schema:**
```json
{
    "RepositoryLinkInfo": {
        "ConnectionArn": "string",
        "EncryptionKeyArn": "string",
        "OwnerId": "string",
        "ProviderType": "string",
        "RepositoryLinkArn": "string",
        "RepositoryLinkId": "string",
        "RepositoryName": "string"
    }
}
```

---

### 3.6 `get-repository-sync-status`

Returns the sync status of a repository link for a specific sync type.

**Synopsis:**
```bash
aws codestar-connections get-repository-sync-status \
    --branch <value> \
    --repository-link-id <value> \
    --sync-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--branch` | **Yes** | string | -- | Branch name |
| `--repository-link-id` | **Yes** | string | -- | ID of the repository link |
| `--sync-type` | **Yes** | string | -- | Sync type: `CFN_STACK_SYNC` |

**Output Schema:**
```json
{
    "LatestSync": {
        "StartedAt": "timestamp",
        "Status": "FAILED|INITIATED|IN_PROGRESS|SUCCEEDED|QUEUED",
        "Events": [
            {
                "Event": "string",
                "ExternalId": "string",
                "Time": "timestamp",
                "Type": "string"
            }
        ]
    }
}
```

---

### 3.7 `list-repository-sync-definitions`

Lists repository sync definitions for a repository link. **Paginated operation.**

**Synopsis:**
```bash
aws codestar-connections list-repository-sync-definitions \
    --repository-link-id <value> \
    --sync-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--repository-link-id` | **Yes** | string | -- | ID of the repository link |
| `--sync-type` | **Yes** | string | -- | Sync type: `CFN_STACK_SYNC` |

**Output Schema:**
```json
{
    "RepositorySyncDefinitions": [
        {
            "Branch": "string",
            "Directory": "string",
            "Parent": "string",
            "Target": "string"
        }
    ],
    "NextToken": "string"
}
```
