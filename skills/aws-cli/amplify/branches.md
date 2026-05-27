# Branches

### 2.1 `create-branch`

Creates a new branch for an Amplify app.

**Synopsis:**
```bash
aws amplify create-branch \
    --app-id <value> \
    --branch-name <value> \
    [--description <value>] \
    [--stage <value>] \
    [--framework <value>] \
    [--enable-notification | --no-enable-notification] \
    [--enable-auto-build | --no-enable-auto-build] \
    [--environment-variables <value>] \
    [--basic-auth-credentials <value>] \
    [--enable-basic-auth | --no-enable-basic-auth] \
    [--enable-performance-mode | --no-enable-performance-mode] \
    [--tags <value>] \
    [--build-spec <value>] \
    [--ttl <value>] \
    [--display-name <value>] \
    [--enable-pull-request-preview | --no-enable-pull-request-preview] \
    [--pull-request-environment-name <value>] \
    [--backend-environment-arn <value>] \
    [--backend <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-id` | **Yes** | string | -- | Unique ID of the Amplify app |
| `--branch-name` | **Yes** | string | -- | Name for the branch |
| `--description` | No | string | None | Description for the branch |
| `--stage` | No | string | None | Stage: `PRODUCTION`, `BETA`, `DEVELOPMENT`, `EXPERIMENTAL`, `PULL_REQUEST` |
| `--framework` | No | string | None | Framework for the branch (e.g., `React`, `Angular`) |
| `--enable-notification` | No | boolean | false | Enable notifications for the branch |
| `--enable-auto-build` | No | boolean | true | Enable auto-build on push |
| `--environment-variables` | No | map | None | Environment variables. Shorthand: `KeyName1=string,KeyName2=string` |
| `--basic-auth-credentials` | No | string | None | Base64-encoded credentials for basic auth |
| `--enable-basic-auth` | No | boolean | false | Enable basic auth for the branch |
| `--enable-performance-mode` | No | boolean | false | Enable performance mode (longer cache TTL) |
| `--tags` | No | map | None | Tags. Shorthand: `KeyName1=string,KeyName2=string` |
| `--build-spec` | No | string | None | Build spec for the branch (overrides app-level) |
| `--ttl` | No | string | None | Content TTL for the branch |
| `--display-name` | No | string | None | Display name for the branch |
| `--enable-pull-request-preview` | No | boolean | false | Enable pull request previews |
| `--pull-request-environment-name` | No | string | None | Environment name for pull request previews |
| `--backend-environment-arn` | No | string | None | ARN of the backend environment |
| `--backend` | No | structure | None | Backend for the branch. Shorthand: `stackArn=string` |

**Output Schema:**
```json
{
    "branch": {
        "branchArn": "string",
        "branchName": "string",
        "description": "string",
        "tags": {"string": "string"},
        "stage": "PRODUCTION|BETA|DEVELOPMENT|EXPERIMENTAL|PULL_REQUEST",
        "displayName": "string",
        "enableNotification": "boolean",
        "createTime": "timestamp",
        "updateTime": "timestamp",
        "environmentVariables": {"string": "string"},
        "enableAutoBuild": "boolean",
        "customDomains": ["string"],
        "framework": "string",
        "activeJobId": "string",
        "totalNumberOfJobs": "string",
        "enableBasicAuth": "boolean",
        "enablePerformanceMode": "boolean",
        "thumbnailUrl": "string",
        "basicAuthCredentials": "string",
        "buildSpec": "string",
        "ttl": "string",
        "associatedResources": ["string"],
        "enablePullRequestPreview": "boolean",
        "pullRequestEnvironmentName": "string",
        "destinationBranch": "string",
        "sourceBranch": "string",
        "backendEnvironmentArn": "string",
        "backend": {
            "stackArn": "string"
        }
    }
}
```

---

### 2.2 `delete-branch`

Deletes a branch for an Amplify app.

**Synopsis:**
```bash
aws amplify delete-branch \
    --app-id <value> \
    --branch-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-id` | **Yes** | string | -- | Unique ID of the Amplify app |
| `--branch-name` | **Yes** | string | -- | Name of the branch to delete |

**Output Schema:**
```json
{
    "branch": {
        "branchArn": "string",
        "branchName": "string",
        "description": "string",
        "stage": "PRODUCTION|BETA|DEVELOPMENT|EXPERIMENTAL|PULL_REQUEST",
        "displayName": "string",
        "enableNotification": "boolean",
        "createTime": "timestamp",
        "updateTime": "timestamp",
        "environmentVariables": {"string": "string"},
        "enableAutoBuild": "boolean",
        "framework": "string",
        "enableBasicAuth": "boolean",
        "ttl": "string"
    }
}
```

---

### 2.3 `get-branch`

Returns a branch for an Amplify app.

**Synopsis:**
```bash
aws amplify get-branch \
    --app-id <value> \
    --branch-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-id` | **Yes** | string | -- | Unique ID of the Amplify app |
| `--branch-name` | **Yes** | string | -- | Name of the branch |

**Output Schema:**
```json
{
    "branch": {
        "branchArn": "string",
        "branchName": "string",
        "description": "string",
        "tags": {"string": "string"},
        "stage": "PRODUCTION|BETA|DEVELOPMENT|EXPERIMENTAL|PULL_REQUEST",
        "displayName": "string",
        "enableNotification": "boolean",
        "createTime": "timestamp",
        "updateTime": "timestamp",
        "environmentVariables": {"string": "string"},
        "enableAutoBuild": "boolean",
        "customDomains": ["string"],
        "framework": "string",
        "activeJobId": "string",
        "totalNumberOfJobs": "string",
        "enableBasicAuth": "boolean",
        "enablePerformanceMode": "boolean",
        "thumbnailUrl": "string",
        "buildSpec": "string",
        "ttl": "string",
        "enablePullRequestPreview": "boolean",
        "pullRequestEnvironmentName": "string",
        "backendEnvironmentArn": "string",
        "backend": {
            "stackArn": "string"
        }
    }
}
```

---

### 2.4 `list-branches`

Lists the branches for an Amplify app. **Paginated operation.**

**Synopsis:**
```bash
aws amplify list-branches \
    --app-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-id` | **Yes** | string | -- | Unique ID of the Amplify app |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call (max 100) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "branches": [
        {
            "branchArn": "string",
            "branchName": "string",
            "description": "string",
            "stage": "PRODUCTION|BETA|DEVELOPMENT|EXPERIMENTAL|PULL_REQUEST",
            "displayName": "string",
            "enableNotification": "boolean",
            "createTime": "timestamp",
            "updateTime": "timestamp",
            "environmentVariables": {"string": "string"},
            "enableAutoBuild": "boolean",
            "framework": "string",
            "activeJobId": "string",
            "totalNumberOfJobs": "string",
            "enableBasicAuth": "boolean",
            "ttl": "string",
            "enablePullRequestPreview": "boolean"
        }
    ],
    "nextToken": "string"
}
```

---

### 2.5 `update-branch`

Updates a branch for an Amplify app.

**Synopsis:**
```bash
aws amplify update-branch \
    --app-id <value> \
    --branch-name <value> \
    [--description <value>] \
    [--framework <value>] \
    [--stage <value>] \
    [--enable-notification | --no-enable-notification] \
    [--enable-auto-build | --no-enable-auto-build] \
    [--environment-variables <value>] \
    [--basic-auth-credentials <value>] \
    [--enable-basic-auth | --no-enable-basic-auth] \
    [--enable-performance-mode | --no-enable-performance-mode] \
    [--build-spec <value>] \
    [--ttl <value>] \
    [--display-name <value>] \
    [--enable-pull-request-preview | --no-enable-pull-request-preview] \
    [--pull-request-environment-name <value>] \
    [--backend-environment-arn <value>] \
    [--backend <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-id` | **Yes** | string | -- | Unique ID of the Amplify app |
| `--branch-name` | **Yes** | string | -- | Name of the branch to update |
| `--description` | No | string | None | Updated description |
| `--framework` | No | string | None | Updated framework |
| `--stage` | No | string | None | Updated stage |
| `--enable-notification` | No | boolean | None | Enable/disable notifications |
| `--enable-auto-build` | No | boolean | None | Enable/disable auto-build |
| `--environment-variables` | No | map | None | Updated environment variables |
| `--basic-auth-credentials` | No | string | None | Updated basic auth credentials |
| `--enable-basic-auth` | No | boolean | None | Enable/disable basic auth |
| `--enable-performance-mode` | No | boolean | None | Enable/disable performance mode |
| `--build-spec` | No | string | None | Updated build spec |
| `--ttl` | No | string | None | Updated TTL |
| `--display-name` | No | string | None | Updated display name |
| `--enable-pull-request-preview` | No | boolean | None | Enable/disable PR previews |
| `--pull-request-environment-name` | No | string | None | Updated PR environment name |
| `--backend-environment-arn` | No | string | None | Updated backend environment ARN |
| `--backend` | No | structure | None | Updated backend. Shorthand: `stackArn=string` |

**Output Schema:**
```json
{
    "branch": {
        "branchArn": "string",
        "branchName": "string",
        "description": "string",
        "tags": {"string": "string"},
        "stage": "PRODUCTION|BETA|DEVELOPMENT|EXPERIMENTAL|PULL_REQUEST",
        "displayName": "string",
        "enableNotification": "boolean",
        "createTime": "timestamp",
        "updateTime": "timestamp",
        "environmentVariables": {"string": "string"},
        "enableAutoBuild": "boolean",
        "framework": "string",
        "enableBasicAuth": "boolean",
        "enablePerformanceMode": "boolean",
        "buildSpec": "string",
        "ttl": "string",
        "enablePullRequestPreview": "boolean",
        "pullRequestEnvironmentName": "string",
        "backendEnvironmentArn": "string",
        "backend": {
            "stackArn": "string"
        }
    }
}
```
