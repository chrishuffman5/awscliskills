# Registry Management

### 6.1 `describe-registry`

Describes the settings for a registry, including replication configuration.

**Synopsis:**
```bash
aws ecr describe-registry \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None (only global options and skeleton/input options).

**Output Schema:**
```json
{
    "registryId": "string",
    "replicationConfiguration": {
        "rules": [
            {
                "destinations": [
                    {
                        "region": "string",
                        "registryId": "string"
                    }
                ],
                "repositoryFilters": [
                    {
                        "filter": "string",
                        "filterType": "PREFIX_MATCH"
                    }
                ]
            }
        ]
    }
}
```

| Field | Constraints |
|-------|-------------|
| `rules` | 0-10 rules |
| `destinations` | 0-100 per rule |
| `region` | 2-25 chars, pattern: `[0-9a-z-]{2,25}` |
| `repositoryFilters` | 1-100 per rule |
| `filter` | 2-256 chars, repository name prefix |
| `filterType` | Only `PREFIX_MATCH` |

---

### 6.2 `put-registry-policy`

Creates or updates the permissions policy for your registry (used for cross-account replication).

**Synopsis:**
```bash
aws ecr put-registry-policy \
    --policy-text <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--policy-text` | **Yes** | string | -- | JSON IAM-style policy text (0-10240 chars) |

**Output Schema:**
```json
{
    "registryId": "string",
    "policyText": "string"
}
```

---

### 6.3 `get-registry-policy`

Retrieves the permissions policy for a registry.

**Synopsis:**
```bash
aws ecr get-registry-policy \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None (only global options).

**Output Schema:**
```json
{
    "registryId": "string",
    "policyText": "string"
}
```

---

### 6.4 `delete-registry-policy`

Deletes the registry permissions policy.

**Synopsis:**
```bash
aws ecr delete-registry-policy \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None (only global options).

**Output Schema:**
```json
{
    "registryId": "string",
    "policyText": "string"
}
```

---

### 6.5 `put-registry-scanning-configuration`

Creates or updates the scanning configuration for a private registry.

**Synopsis:**
```bash
aws ecr put-registry-scanning-configuration \
    [--scan-type <value>] \
    [--rules <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--scan-type` | No | string | `BASIC` | `BASIC` or `ENHANCED` (Amazon Inspector) |
| `--rules` | No | list | None | 0-2 scanning rules |

**Rule Structure:**
```json
[
    {
        "scanFrequency": "SCAN_ON_PUSH|CONTINUOUS_SCAN|MANUAL",
        "repositoryFilters": [
            {
                "filter": "string",
                "filterType": "WILDCARD"
            }
        ]
    }
]
```

| Field | Constraints |
|-------|-------------|
| `scanFrequency` | BASIC supports `SCAN_ON_PUSH` only; ENHANCED supports `SCAN_ON_PUSH` and `CONTINUOUS_SCAN` |
| `repositoryFilters` | 0-100 filters per rule |
| `filter` | 1-255 chars, pattern: `^[a-z0-9*](?:[._\-/a-z0-9*]?[a-z0-9*]+)*$` |
| `filterType` | Only `WILDCARD` |

**Output Schema:**
```json
{
    "registryScanningConfiguration": {
        "scanType": "BASIC|ENHANCED",
        "rules": [
            {
                "scanFrequency": "SCAN_ON_PUSH|CONTINUOUS_SCAN|MANUAL",
                "repositoryFilters": [
                    {
                        "filter": "string",
                        "filterType": "WILDCARD"
                    }
                ]
            }
        ]
    }
}
```

---

### 6.6 `get-registry-scanning-configuration`

Retrieves the scanning configuration for a registry.

**Synopsis:**
```bash
aws ecr get-registry-scanning-configuration \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None (only global options).

**Output Schema:**
```json
{
    "registryId": "string",
    "scanningConfiguration": {
        "scanType": "BASIC|ENHANCED",
        "rules": [
            {
                "scanFrequency": "SCAN_ON_PUSH|CONTINUOUS_SCAN|MANUAL",
                "repositoryFilters": [
                    {
                        "filter": "string",
                        "filterType": "WILDCARD"
                    }
                ]
            }
        ]
    }
}
```

---

### 6.7 `put-replication-configuration`

Creates or updates the replication configuration for a registry.

**Synopsis:**
```bash
aws ecr put-replication-configuration \
    --replication-configuration <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replication-configuration` | **Yes** | structure | -- | Replication configuration object |

**Replication Configuration Structure:**
```json
{
    "rules": [
        {
            "destinations": [
                {
                    "region": "string",
                    "registryId": "string"
                }
            ],
            "repositoryFilters": [
                {
                    "filter": "string",
                    "filterType": "PREFIX_MATCH"
                }
            ]
        }
    ]
}
```

| Field | Constraints |
|-------|-------------|
| `rules` | 0-10 |
| `destinations` | 0-100 per rule |
| `region` | 2-25 chars, pattern: `[0-9a-z-]{2,25}` |
| `registryId` | pattern: `[0-9]{12}` |
| `repositoryFilters` | 1-100 per rule (optional) |
| `filter` | 2-256 chars, repository name prefix |
| `filterType` | Only `PREFIX_MATCH` |

**Output Schema:**
```json
{
    "replicationConfiguration": {
        "rules": [
            {
                "destinations": [
                    {
                        "region": "string",
                        "registryId": "string"
                    }
                ],
                "repositoryFilters": [
                    {
                        "filter": "string",
                        "filterType": "PREFIX_MATCH"
                    }
                ]
            }
        ]
    }
}
```

> A service-linked IAM role is automatically created on first call. For cross-account replication, the destination account must grant permission via `put-registry-policy`.

---

### 6.8 `describe-pull-through-cache-rules`

Returns the pull through cache rules for a registry. **Paginated operation.**

**Synopsis:**
```bash
aws ecr describe-pull-through-cache-rules \
    [--registry-id <value>] \
    [--ecr-repository-prefixes <value>] \
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
| `--ecr-repository-prefixes` | No | list(string) | all rules | 1-100 prefixes to filter (each 2-30 chars) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "pullThroughCacheRules": [
        {
            "ecrRepositoryPrefix": "string",
            "upstreamRegistryUrl": "string",
            "createdAt": "timestamp",
            "registryId": "string",
            "credentialArn": "string",
            "customRoleArn": "string",
            "upstreamRepositoryPrefix": "string",
            "upstreamRegistry": "ecr|ecr-public|quay|k8s|docker-hub|github-container-registry|azure-container-registry|gitlab-container-registry",
            "updatedAt": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 6.9 `create-pull-through-cache-rule`

Creates a pull through cache rule that caches images from an upstream registry.

**Synopsis:**
```bash
aws ecr create-pull-through-cache-rule \
    --ecr-repository-prefix <value> \
    --upstream-registry-url <value> \
    [--registry-id <value>] \
    [--upstream-registry <value>] \
    [--credential-arn <value>] \
    [--custom-role-arn <value>] \
    [--upstream-repository-prefix <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--ecr-repository-prefix` | **Yes** | string | -- | Local repository prefix (2-30 chars). Pattern: `^((?:[a-z0-9]+(?:[._-][a-z0-9]+)*/)*[a-z0-9]+(?:[._-][a-z0-9]+)*/?\|ROOT)$` |
| `--upstream-registry-url` | **Yes** | string | -- | URL of the upstream registry |
| `--registry-id` | No | string | caller's account | AWS account ID (12 digits) |
| `--upstream-registry` | No | string | None | `ecr`, `ecr-public`, `quay`, `k8s`, `docker-hub`, `github-container-registry`, `azure-container-registry`, `gitlab-container-registry` |
| `--credential-arn` | No | string | None | Secrets Manager ARN for upstream credentials (50-612 chars) |
| `--custom-role-arn` | No | string | None | IAM role ARN for ECR authentication (max 2048 chars) |
| `--upstream-repository-prefix` | No | string | `ROOT` | Upstream repository prefix (2-30 chars) |

**Supported Upstream Registries:**

| Registry | URL |
|----------|-----|
| Amazon ECR | `<accountId>.dkr.ecr.<region>.amazonaws.com` |
| Amazon ECR Public | `public.ecr.aws` |
| Docker Hub | `registry-1.docker.io` |
| GitHub Container Registry | `ghcr.io` |
| GitLab Container Registry | `registry.gitlab.com` |
| Kubernetes | `registry.k8s.io` |
| Azure Container Registry | `<custom>.azurecr.io` |
| Quay | `quay.io` |

**Output Schema:**
```json
{
    "ecrRepositoryPrefix": "string",
    "upstreamRegistryUrl": "string",
    "createdAt": "timestamp",
    "registryId": "string",
    "upstreamRegistry": "string",
    "credentialArn": "string",
    "customRoleArn": "string",
    "upstreamRepositoryPrefix": "string"
}
```

---

### 6.10 `delete-pull-through-cache-rule`

Deletes a pull through cache rule.

**Synopsis:**
```bash
aws ecr delete-pull-through-cache-rule \
    --ecr-repository-prefix <value> \
    [--registry-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--ecr-repository-prefix` | **Yes** | string | -- | ECR repository prefix (2-30 chars) |
| `--registry-id` | No | string | caller's account | AWS account ID (12 digits) |

**Output Schema:**
```json
{
    "ecrRepositoryPrefix": "string",
    "upstreamRegistryUrl": "string",
    "createdAt": "timestamp",
    "registryId": "string",
    "credentialArn": "string",
    "customRoleArn": "string",
    "upstreamRepositoryPrefix": "string"
}
```

---

