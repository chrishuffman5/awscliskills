# Repository Management

### 1.1 `create-repository`

Creates a repository in a registry.

**Synopsis:**
```bash
aws ecr create-repository \
    --repository-name <value> \
    [--registry-id <value>] \
    [--tags <value>] \
    [--image-tag-mutability <value>] \
    [--image-tag-mutability-exclusion-filters <value>] \
    [--image-scanning-configuration <value>] \
    [--encryption-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--repository-name` | **Yes** | string | -- | Repository name (2-256 chars). Pattern: `(?:[a-z0-9]+(?:[._-][a-z0-9]+)*/)*[a-z0-9]+(?:[._-][a-z0-9]+)*`. Supports namespaces: `project-a/nginx-web-app` |
| `--registry-id` | No | string | caller's account | AWS account ID (12 digits). Pattern: `[0-9]{12}` |
| `--tags` | No | list | None | Key-value metadata tags. Key max 128 chars, Value max 256 chars. Shorthand: `Key=string,Value=string ...` |
| `--image-tag-mutability` | No | string | `MUTABLE` | Values: `MUTABLE`, `IMMUTABLE`, `IMMUTABLE_WITH_EXCLUSION`, `MUTABLE_WITH_EXCLUSION` |
| `--image-tag-mutability-exclusion-filters` | No | list | None | 1-5 filters. Structure: `filterType=WILDCARD,filter=<pattern>`. Pattern max 128 chars: `^[0-9a-zA-Z._*-]{1,128}$` |
| `--image-scanning-configuration` | No | structure | None | Shorthand: `scanOnPush=true\|false`. **Deprecated at repo level; use registry-level scanning.** |
| `--encryption-configuration` | No | structure | AES256 | `encryptionType`: `AES256`, `KMS`, `KMS_DSSE`. Optional `kmsKey` (1-2048 chars) |

**Output Schema:**
```json
{
    "repository": {
        "repositoryArn": "string",
        "registryId": "string",
        "repositoryName": "string",
        "repositoryUri": "string",
        "createdAt": "timestamp",
        "imageTagMutability": "MUTABLE|IMMUTABLE|IMMUTABLE_WITH_EXCLUSION|MUTABLE_WITH_EXCLUSION",
        "imageTagMutabilityExclusionFilters": [
            {
                "filterType": "WILDCARD",
                "filter": "string"
            }
        ],
        "imageScanningConfiguration": {
            "scanOnPush": true|false
        },
        "encryptionConfiguration": {
            "encryptionType": "AES256|KMS|KMS_DSSE",
            "kmsKey": "string"
        }
    }
}
```

---

### 1.2 `delete-repository`

Deletes a repository. If the repository contains images, you must use `--force`.

**Synopsis:**
```bash
aws ecr delete-repository \
    --repository-name <value> \
    [--registry-id <value>] \
    [--force | --no-force] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--repository-name` | **Yes** | string | -- | Repository name (2-256 chars) |
| `--registry-id` | No | string | caller's account | AWS account ID (12 digits) |
| `--force` / `--no-force` | No | boolean | false | Force delete even if repository contains images |

**Output Schema:**
```json
{
    "repository": {
        "repositoryArn": "string",
        "registryId": "string",
        "repositoryName": "string",
        "repositoryUri": "string",
        "createdAt": "timestamp",
        "imageTagMutability": "MUTABLE|IMMUTABLE|IMMUTABLE_WITH_EXCLUSION|MUTABLE_WITH_EXCLUSION",
        "imageTagMutabilityExclusionFilters": [
            {
                "filterType": "WILDCARD",
                "filter": "string"
            }
        ],
        "imageScanningConfiguration": {
            "scanOnPush": true|false
        },
        "encryptionConfiguration": {
            "encryptionType": "AES256|KMS|KMS_DSSE",
            "kmsKey": "string"
        }
    }
}
```

---

### 1.3 `describe-repositories`

Describes image repositories in a registry. **Paginated operation.**

**Synopsis:**
```bash
aws ecr describe-repositories \
    [--registry-id <value>] \
    [--repository-names <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--registry-id` | No | string | caller's account | AWS account ID (12 digits) |
| `--repository-names` | No | list(string) | all repos | Specific repositories to describe (1-100 items) |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "repositories": [
        {
            "repositoryArn": "string",
            "registryId": "string",
            "repositoryName": "string",
            "repositoryUri": "string",
            "createdAt": "timestamp",
            "imageTagMutability": "MUTABLE|IMMUTABLE|IMMUTABLE_WITH_EXCLUSION|MUTABLE_WITH_EXCLUSION",
            "imageTagMutabilityExclusionFilters": [
                {
                    "filterType": "WILDCARD",
                    "filter": "string"
                }
            ],
            "imageScanningConfiguration": {
                "scanOnPush": true|false
            },
            "encryptionConfiguration": {
                "encryptionType": "AES256|KMS|KMS_DSSE",
                "kmsKey": "string"
            }
        }
    ],
    "nextToken": "string"
}
```

---

### 1.4 `put-image-tag-mutability`

Updates image tag mutability settings for a repository.

**Synopsis:**
```bash
aws ecr put-image-tag-mutability \
    --repository-name <value> \
    --image-tag-mutability <value> \
    [--registry-id <value>] \
    [--image-tag-mutability-exclusion-filters <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--repository-name` | **Yes** | string | -- | Repository name (2-256 chars) |
| `--image-tag-mutability` | **Yes** | string | -- | `MUTABLE`, `IMMUTABLE`, `IMMUTABLE_WITH_EXCLUSION`, `MUTABLE_WITH_EXCLUSION` |
| `--registry-id` | No | string | caller's account | AWS account ID (12 digits) |
| `--image-tag-mutability-exclusion-filters` | No | list | None | 1-5 exclusion filters. Structure: `filterType=WILDCARD,filter=<pattern>` |

**Output Schema:**
```json
{
    "registryId": "string",
    "repositoryName": "string",
    "imageTagMutability": "MUTABLE|IMMUTABLE|IMMUTABLE_WITH_EXCLUSION|MUTABLE_WITH_EXCLUSION",
    "imageTagMutabilityExclusionFilters": [
        {
            "filterType": "WILDCARD",
            "filter": "string"
        }
    ]
}
```

---

### 1.5 `set-repository-policy`

Applies an IAM-style repository policy to control access.

**Synopsis:**
```bash
aws ecr set-repository-policy \
    --repository-name <value> \
    --policy-text <value> \
    [--registry-id <value>] \
    [--force | --no-force] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--repository-name` | **Yes** | string | -- | Repository name (2-256 chars) |
| `--policy-text` | **Yes** | string | -- | JSON policy text (0-10240 chars). Supports `file://` syntax |
| `--registry-id` | No | string | caller's account | AWS account ID (12 digits) |
| `--force` / `--no-force` | No | boolean | false | Force apply even if policy would prevent future modifications |

**Output Schema:**
```json
{
    "registryId": "string",
    "repositoryName": "string",
    "policyText": "string"
}
```

---

### 1.6 `get-repository-policy`

Retrieves the repository policy for a specified repository.

**Synopsis:**
```bash
aws ecr get-repository-policy \
    --repository-name <value> \
    [--registry-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--repository-name` | **Yes** | string | -- | Repository name (2-256 chars) |
| `--registry-id` | No | string | caller's account | AWS account ID (12 digits) |

**Output Schema:**
```json
{
    "registryId": "string",
    "repositoryName": "string",
    "policyText": "string"
}
```

---

### 1.7 `delete-repository-policy`

Deletes the repository policy associated with a repository.

**Synopsis:**
```bash
aws ecr delete-repository-policy \
    --repository-name <value> \
    [--registry-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--repository-name` | **Yes** | string | -- | Repository name (2-256 chars) |
| `--registry-id` | No | string | caller's account | AWS account ID (12 digits) |

**Output Schema:**
```json
{
    "registryId": "string",
    "repositoryName": "string",
    "policyText": "string"
}
```

---

