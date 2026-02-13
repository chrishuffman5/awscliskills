# Lifecycle Policies

### 4.1 `get-lifecycle-policy`

Retrieves the lifecycle policy for a repository.

**Synopsis:**
```bash
aws ecr get-lifecycle-policy \
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
    "lifecyclePolicyText": "string",
    "lastEvaluatedAt": "timestamp"
}
```

> `lifecyclePolicyText` constraints: min 100, max 30720 chars.

---

### 4.2 `put-lifecycle-policy`

Creates or replaces a lifecycle policy for a repository.

**Synopsis:**
```bash
aws ecr put-lifecycle-policy \
    --repository-name <value> \
    --lifecycle-policy-text <value> \
    [--registry-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--repository-name` | **Yes** | string | -- | Repository name (2-256 chars) |
| `--lifecycle-policy-text` | **Yes** | string | -- | JSON lifecycle policy (100-30720 chars). Supports `file://` syntax |
| `--registry-id` | No | string | caller's account | AWS account ID (12 digits) |

**Lifecycle Policy JSON Structure:**
```json
{
    "rules": [
        {
            "rulePriority": 1,
            "description": "string",
            "selection": {
                "tagStatus": "untagged|tagged|any",
                "tagPrefixList": ["string"],
                "countType": "sinceImagePushed|imageCountMoreThan",
                "countUnit": "days",
                "countNumber": 14
            },
            "action": {
                "type": "expire"
            }
        }
    ]
}
```

**Output Schema:**
```json
{
    "registryId": "string",
    "repositoryName": "string",
    "lifecyclePolicyText": "string"
}
```

---

### 4.3 `delete-lifecycle-policy`

Deletes the lifecycle policy for a repository.

**Synopsis:**
```bash
aws ecr delete-lifecycle-policy \
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
    "lifecyclePolicyText": "string",
    "lastEvaluatedAt": "timestamp"
}
```

---

### 4.4 `start-lifecycle-policy-preview`

Starts a preview of a lifecycle policy to see which images would be affected.

**Synopsis:**
```bash
aws ecr start-lifecycle-policy-preview \
    --repository-name <value> \
    [--registry-id <value>] \
    [--lifecycle-policy-text <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--repository-name` | **Yes** | string | -- | Repository name (2-256 chars) |
| `--registry-id` | No | string | caller's account | AWS account ID (12 digits) |
| `--lifecycle-policy-text` | No | string | current policy | JSON lifecycle policy to preview (100-30720 chars). If omitted, uses existing policy |

**Output Schema:**
```json
{
    "registryId": "string",
    "repositoryName": "string",
    "lifecyclePolicyText": "string",
    "status": "IN_PROGRESS|COMPLETE|EXPIRED|FAILED"
}
```

---

### 4.5 `get-lifecycle-policy-preview`

Retrieves the results of a lifecycle policy preview. **Paginated operation.**

**Synopsis:**
```bash
aws ecr get-lifecycle-policy-preview \
    --repository-name <value> \
    [--registry-id <value>] \
    [--image-ids <value>] \
    [--filter <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--repository-name` | **Yes** | string | -- | Repository name (2-256 chars) |
| `--registry-id` | No | string | caller's account | AWS account ID (12 digits) |
| `--image-ids` | No | list | None | 1-100 image identifiers to filter results |
| `--filter` | No | structure | None | `tagStatus`: `TAGGED\|UNTAGGED\|ANY` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "registryId": "string",
    "repositoryName": "string",
    "lifecyclePolicyText": "string",
    "status": "IN_PROGRESS|COMPLETE|EXPIRED|FAILED",
    "previewResults": [
        {
            "imageTags": ["string"],
            "imageDigest": "string",
            "imagePushedAt": "timestamp",
            "action": {
                "type": "EXPIRE|TRANSITION",
                "targetStorageClass": "ARCHIVE"
            },
            "appliedRulePriority": "integer",
            "storageClass": "ARCHIVE|STANDARD"
        }
    ],
    "summary": {
        "expiringImageTotalCount": "integer",
        "transitioningImageTotalCounts": [
            {
                "targetStorageClass": "ARCHIVE",
                "imageTotalCount": "integer"
            }
        ]
    },
    "nextToken": "string"
}
```

---

