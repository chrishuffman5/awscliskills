# Domains

### 1.1 `create-domain`

Creates a new CodeArtifact domain. Domains contain repositories and provide deduplication of package storage across repositories.

**Synopsis:**
```bash
aws codeartifact create-domain \
    --domain <value> \
    [--encryption-key <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Name of the domain to create (2-50 chars: lowercase letters, numbers, hyphens) |
| `--encryption-key` | No | string | AWS managed key | ARN of the KMS key to use for encryption |
| `--tags` | No | list | None | Tags to associate. Shorthand: `key=string,value=string ...` |

**Output Schema:**
```json
{
    "domain": {
        "name": "string",
        "owner": "string",
        "arn": "string",
        "status": "Active|Deleted",
        "createdTime": "timestamp",
        "encryptionKey": "string",
        "repositoryCount": "integer",
        "assetSizeBytes": "long",
        "s3BucketArn": "string"
    }
}
```

---

### 1.2 `delete-domain`

Deletes a domain. All repositories in the domain must be deleted before deleting the domain.

**Synopsis:**
```bash
aws codeartifact delete-domain \
    --domain <value> \
    [--domain-owner <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Name of the domain to delete |
| `--domain-owner` | No | string | Caller account | The 12-digit account ID of the domain owner |

**Output Schema:**
```json
{
    "domain": {
        "name": "string",
        "owner": "string",
        "arn": "string",
        "status": "Active|Deleted",
        "createdTime": "timestamp",
        "encryptionKey": "string",
        "repositoryCount": "integer",
        "assetSizeBytes": "long",
        "s3BucketArn": "string"
    }
}
```

---

### 1.3 `describe-domain`

Returns information about a domain.

**Synopsis:**
```bash
aws codeartifact describe-domain \
    --domain <value> \
    [--domain-owner <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Name of the domain to describe |
| `--domain-owner` | No | string | Caller account | The 12-digit account ID of the domain owner |

**Output Schema:**
```json
{
    "domain": {
        "name": "string",
        "owner": "string",
        "arn": "string",
        "status": "Active|Deleted",
        "createdTime": "timestamp",
        "encryptionKey": "string",
        "repositoryCount": "integer",
        "assetSizeBytes": "long",
        "s3BucketArn": "string"
    }
}
```

---

### 1.4 `list-domains`

Returns a list of domains in the account. **Paginated operation.**

**Synopsis:**
```bash
aws codeartifact list-domains \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "domains": [
        {
            "name": "string",
            "owner": "string",
            "arn": "string",
            "status": "Active|Deleted",
            "createdTime": "timestamp",
            "encryptionKey": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 1.5 `get-domain-permissions-policy`

Returns the resource policy attached to the specified domain.

**Synopsis:**
```bash
aws codeartifact get-domain-permissions-policy \
    --domain <value> \
    [--domain-owner <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Name of the domain |
| `--domain-owner` | No | string | Caller account | The 12-digit account ID of the domain owner |

**Output Schema:**
```json
{
    "policy": {
        "resourceArn": "string",
        "revision": "string",
        "document": "string"
    }
}
```

---

### 1.6 `put-domain-permissions-policy`

Sets a resource policy on a domain that specifies permissions to perform operations on it.

**Synopsis:**
```bash
aws codeartifact put-domain-permissions-policy \
    --domain <value> \
    --policy-document <value> \
    [--domain-owner <value>] \
    [--policy-revision <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Name of the domain |
| `--policy-document` | **Yes** | string | -- | JSON policy document or `file://` path |
| `--domain-owner` | No | string | Caller account | The 12-digit account ID of the domain owner |
| `--policy-revision` | No | string | None | Current revision of the policy for optimistic locking |

**Output Schema:**
```json
{
    "policy": {
        "resourceArn": "string",
        "revision": "string",
        "document": "string"
    }
}
```

---

### 1.7 `delete-domain-permissions-policy`

Deletes the resource policy set on a domain.

**Synopsis:**
```bash
aws codeartifact delete-domain-permissions-policy \
    --domain <value> \
    [--domain-owner <value>] \
    [--policy-revision <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain` | **Yes** | string | -- | Name of the domain |
| `--domain-owner` | No | string | Caller account | The 12-digit account ID of the domain owner |
| `--policy-revision` | No | string | None | Current revision of the policy for optimistic locking |

**Output Schema:**
```json
{
    "policy": {
        "resourceArn": "string",
        "revision": "string",
        "document": "string"
    }
}
```
