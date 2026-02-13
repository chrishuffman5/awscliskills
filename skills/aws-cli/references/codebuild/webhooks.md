# Webhooks

### 7.1 `create-webhook`

For an existing CodeBuild build project that has its source code stored in a GitHub or Bitbucket repository, enables CodeBuild to start rebuilding the source code every time a code change is pushed to the repository.

**Synopsis:**
```bash
aws codebuild create-webhook \
    --project-name <value> \
    [--branch-filter <value>] \
    [--filter-groups <value>] \
    [--build-type <value>] \
    [--manual-creation | --no-manual-creation] \
    [--scope-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project-name` | **Yes** | string | -- | Build project name |
| `--branch-filter` | No | string | None | Regex to filter branches (deprecated, use `--filter-groups`) |
| `--filter-groups` | No | list(list) | None | Webhook event filter groups. Each group is a list of filters (AND logic); groups use OR logic |
| `--build-type` | No | string | None | Build type: `BUILD`, `BUILD_BATCH` |
| `--manual-creation` | No | boolean | false | Manually create the webhook (for GitHub Enterprise) |
| `--scope-configuration` | No | structure | None | Scope configuration for global or organization webhooks |

**Filter Group Structure:**
```json
[
    [
        {
            "type": "EVENT|BASE_REF|HEAD_REF|ACTOR_ACCOUNT_ID|FILE_PATH|COMMIT_MESSAGE|WORKFLOW_NAME|TAG_NAME|RELEASE_NAME",
            "pattern": "string",
            "excludeMatchedPattern": true|false
        }
    ]
]
```

**Event Patterns:**
| Pattern | Description |
|---------|-------------|
| `PUSH` | Push event |
| `PULL_REQUEST_CREATED` | Pull request created |
| `PULL_REQUEST_UPDATED` | Pull request updated |
| `PULL_REQUEST_CLOSED` | Pull request closed |
| `PULL_REQUEST_REOPENED` | Pull request reopened |
| `PULL_REQUEST_MERGED` | Pull request merged |
| `RELEASED` | Release created |
| `PRERELEASED` | Pre-release created |
| `WORKFLOW_JOB_QUEUED` | GitHub Actions workflow job queued |

**Scope Configuration Structure:**
```json
{
    "name": "string",
    "domain": "string",
    "scope": "GITHUB_ORGANIZATION|GITHUB_GLOBAL"
}
```

**Output Schema:**
```json
{
    "webhook": {
        "url": "string",
        "payloadUrl": "string",
        "secret": "string",
        "branchFilter": "string",
        "filterGroups": [
            [
                {
                    "type": "string",
                    "pattern": "string",
                    "excludeMatchedPattern": true|false
                }
            ]
        ],
        "buildType": "BUILD|BUILD_BATCH",
        "manualCreation": true|false,
        "lastModifiedSecret": "timestamp",
        "scopeConfiguration": {
            "name": "string",
            "domain": "string",
            "scope": "GITHUB_ORGANIZATION|GITHUB_GLOBAL"
        }
    }
}
```

---

### 7.2 `delete-webhook`

Deletes a webhook from a project.

**Synopsis:**
```bash
aws codebuild delete-webhook \
    --project-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project-name` | **Yes** | string | -- | Build project name |

**Output Schema:**
```json
{}
```

---

### 7.3 `update-webhook`

Updates the webhook associated with an AWS CodeBuild build project.

**Synopsis:**
```bash
aws codebuild update-webhook \
    --project-name <value> \
    [--branch-filter <value>] \
    [--filter-groups <value>] \
    [--build-type <value>] \
    [--rotate-secret | --no-rotate-secret] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project-name` | **Yes** | string | -- | Build project name |
| `--branch-filter` | No | string | None | Regex to filter branches |
| `--filter-groups` | No | list(list) | None | Updated webhook event filter groups |
| `--build-type` | No | string | None | Build type: `BUILD`, `BUILD_BATCH` |
| `--rotate-secret` | No | boolean | false | Rotate the webhook secret |

**Output Schema:**
Same as `create-webhook`.
