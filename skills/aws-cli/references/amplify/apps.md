# Apps

### 1.1 `create-app`

Creates a new Amplify app.

**Synopsis:**
```bash
aws amplify create-app \
    --name <value> \
    [--description <value>] \
    [--repository <value>] \
    [--platform <value>] \
    [--iam-service-role-arn <value>] \
    [--oauth-token <value>] \
    [--access-token <value>] \
    [--environment-variables <value>] \
    [--enable-branch-auto-build | --no-enable-branch-auto-build] \
    [--enable-branch-auto-deletion | --no-enable-branch-auto-deletion] \
    [--enable-basic-auth | --no-enable-basic-auth] \
    [--basic-auth-credentials <value>] \
    [--custom-rules <value>] \
    [--tags <value>] \
    [--build-spec <value>] \
    [--custom-headers <value>] \
    [--enable-auto-branch-creation | --no-enable-auto-branch-creation] \
    [--auto-branch-creation-patterns <value>] \
    [--auto-branch-creation-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name for the Amplify app |
| `--description` | No | string | None | Description for the app |
| `--repository` | No | string | None | Repository URL (e.g., GitHub, Bitbucket, CodeCommit) |
| `--platform` | No | string | `WEB` | Platform: `WEB`, `WEB_DYNAMIC`, `WEB_COMPUTE` |
| `--iam-service-role-arn` | No | string | None | IAM service role ARN for the app |
| `--oauth-token` | No | string | None | OAuth token for third-party source control |
| `--access-token` | No | string | None | Personal access token for third-party source control |
| `--environment-variables` | No | map | None | Environment variables. Shorthand: `KeyName1=string,KeyName2=string` |
| `--enable-branch-auto-build` | No | boolean | false | Enable auto-build for branches |
| `--enable-branch-auto-deletion` | No | boolean | false | Automatically disconnect branches when deleted from repository |
| `--enable-basic-auth` | No | boolean | false | Enable basic auth for all branches |
| `--basic-auth-credentials` | No | string | None | Base64-encoded credentials for basic auth (`user:password`) |
| `--custom-rules` | No | list | None | Custom redirect/rewrite rules. Shorthand: `source=string,target=string,status=string,condition=string ...` |
| `--tags` | No | map | None | Tags. Shorthand: `KeyName1=string,KeyName2=string` |
| `--build-spec` | No | string | None | Build spec content (YAML string) |
| `--custom-headers` | No | string | None | Custom HTTP headers (YAML string) |
| `--enable-auto-branch-creation` | No | boolean | false | Enable auto branch creation |
| `--auto-branch-creation-patterns` | No | list(string) | None | Glob patterns for auto branch creation (e.g., `feature/*`) |
| `--auto-branch-creation-config` | No | structure | None | Auto branch creation config |

**Auto Branch Creation Config Structure:**
```json
{
    "stage": "PRODUCTION|BETA|DEVELOPMENT|EXPERIMENTAL|PULL_REQUEST",
    "framework": "string",
    "enableAutoBuild": true|false,
    "environmentVariables": {"string": "string"},
    "basicAuthCredentials": "string",
    "enableBasicAuth": true|false,
    "enablePerformanceMode": true|false,
    "buildSpec": "string",
    "enablePullRequestPreview": true|false,
    "pullRequestEnvironmentName": "string"
}
```

**Output Schema:**
```json
{
    "app": {
        "appId": "string",
        "appArn": "string",
        "name": "string",
        "tags": {"string": "string"},
        "description": "string",
        "repository": "string",
        "platform": "WEB|WEB_DYNAMIC|WEB_COMPUTE",
        "createTime": "timestamp",
        "updateTime": "timestamp",
        "iamServiceRoleArn": "string",
        "environmentVariables": {"string": "string"},
        "defaultDomain": "string",
        "enableBranchAutoBuild": "boolean",
        "enableBranchAutoDeletion": "boolean",
        "enableBasicAuth": "boolean",
        "basicAuthCredentials": "string",
        "customRules": [
            {
                "source": "string",
                "target": "string",
                "status": "string",
                "condition": "string"
            }
        ],
        "productionBranch": {
            "lastDeployTime": "timestamp",
            "status": "string",
            "thumbnailUrl": "string",
            "branchName": "string"
        },
        "buildSpec": "string",
        "customHeaders": "string",
        "enableAutoBranchCreation": "boolean",
        "autoBranchCreationPatterns": ["string"],
        "autoBranchCreationConfig": {
            "stage": "string",
            "framework": "string",
            "enableAutoBuild": "boolean",
            "environmentVariables": {"string": "string"},
            "basicAuthCredentials": "string",
            "enableBasicAuth": "boolean",
            "enablePerformanceMode": "boolean",
            "buildSpec": "string",
            "enablePullRequestPreview": "boolean",
            "pullRequestEnvironmentName": "string"
        },
        "repositoryCloneMethod": "SSH|TOKEN|SIGV4"
    }
}
```

---

### 1.2 `delete-app`

Deletes an existing Amplify app by appId.

**Synopsis:**
```bash
aws amplify delete-app \
    --app-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-id` | **Yes** | string | -- | Unique ID of the Amplify app to delete |

**Output Schema:**
```json
{
    "app": {
        "appId": "string",
        "appArn": "string",
        "name": "string",
        "tags": {"string": "string"},
        "description": "string",
        "repository": "string",
        "platform": "WEB|WEB_DYNAMIC|WEB_COMPUTE",
        "createTime": "timestamp",
        "updateTime": "timestamp",
        "environmentVariables": {"string": "string"},
        "defaultDomain": "string",
        "enableBranchAutoBuild": "boolean",
        "enableBranchAutoDeletion": "boolean",
        "enableBasicAuth": "boolean",
        "customRules": [],
        "buildSpec": "string"
    }
}
```

---

### 1.3 `get-app`

Returns an existing Amplify app by appId.

**Synopsis:**
```bash
aws amplify get-app \
    --app-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-id` | **Yes** | string | -- | Unique ID of the Amplify app |

**Output Schema:**
```json
{
    "app": {
        "appId": "string",
        "appArn": "string",
        "name": "string",
        "tags": {"string": "string"},
        "description": "string",
        "repository": "string",
        "platform": "WEB|WEB_DYNAMIC|WEB_COMPUTE",
        "createTime": "timestamp",
        "updateTime": "timestamp",
        "iamServiceRoleArn": "string",
        "environmentVariables": {"string": "string"},
        "defaultDomain": "string",
        "enableBranchAutoBuild": "boolean",
        "enableBranchAutoDeletion": "boolean",
        "enableBasicAuth": "boolean",
        "basicAuthCredentials": "string",
        "customRules": [
            {
                "source": "string",
                "target": "string",
                "status": "string",
                "condition": "string"
            }
        ],
        "productionBranch": {
            "lastDeployTime": "timestamp",
            "status": "string",
            "thumbnailUrl": "string",
            "branchName": "string"
        },
        "buildSpec": "string",
        "customHeaders": "string",
        "enableAutoBranchCreation": "boolean",
        "autoBranchCreationPatterns": ["string"],
        "autoBranchCreationConfig": {},
        "repositoryCloneMethod": "SSH|TOKEN|SIGV4"
    }
}
```

---

### 1.4 `list-apps`

Returns a list of existing Amplify apps. **Paginated operation.**

**Synopsis:**
```bash
aws amplify list-apps \
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
| `--page-size` | No | integer | None | Items per API call (max 100) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "apps": [
        {
            "appId": "string",
            "appArn": "string",
            "name": "string",
            "tags": {"string": "string"},
            "description": "string",
            "repository": "string",
            "platform": "WEB|WEB_DYNAMIC|WEB_COMPUTE",
            "createTime": "timestamp",
            "updateTime": "timestamp",
            "iamServiceRoleArn": "string",
            "environmentVariables": {"string": "string"},
            "defaultDomain": "string",
            "enableBranchAutoBuild": "boolean",
            "enableBranchAutoDeletion": "boolean",
            "enableBasicAuth": "boolean",
            "customRules": [],
            "buildSpec": "string",
            "productionBranch": {},
            "repositoryCloneMethod": "SSH|TOKEN|SIGV4"
        }
    ],
    "nextToken": "string"
}
```

---

### 1.5 `update-app`

Updates an existing Amplify app.

**Synopsis:**
```bash
aws amplify update-app \
    --app-id <value> \
    [--name <value>] \
    [--description <value>] \
    [--platform <value>] \
    [--iam-service-role-arn <value>] \
    [--environment-variables <value>] \
    [--enable-branch-auto-build | --no-enable-branch-auto-build] \
    [--enable-branch-auto-deletion | --no-enable-branch-auto-deletion] \
    [--enable-basic-auth | --no-enable-basic-auth] \
    [--basic-auth-credentials <value>] \
    [--custom-rules <value>] \
    [--build-spec <value>] \
    [--custom-headers <value>] \
    [--enable-auto-branch-creation | --no-enable-auto-branch-creation] \
    [--auto-branch-creation-patterns <value>] \
    [--auto-branch-creation-config <value>] \
    [--repository <value>] \
    [--oauth-token <value>] \
    [--access-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-id` | **Yes** | string | -- | Unique ID of the Amplify app |
| `--name` | No | string | None | New name for the app |
| `--description` | No | string | None | New description for the app |
| `--platform` | No | string | None | Platform: `WEB`, `WEB_DYNAMIC`, `WEB_COMPUTE` |
| `--iam-service-role-arn` | No | string | None | IAM service role ARN |
| `--environment-variables` | No | map | None | Environment variables |
| `--enable-branch-auto-build` | No | boolean | None | Enable auto-build for branches |
| `--enable-branch-auto-deletion` | No | boolean | None | Enable auto-deletion for branches |
| `--enable-basic-auth` | No | boolean | None | Enable basic auth |
| `--basic-auth-credentials` | No | string | None | Base64-encoded credentials |
| `--custom-rules` | No | list | None | Custom redirect/rewrite rules |
| `--build-spec` | No | string | None | Build spec content (YAML string) |
| `--custom-headers` | No | string | None | Custom HTTP headers (YAML string) |
| `--enable-auto-branch-creation` | No | boolean | None | Enable auto branch creation |
| `--auto-branch-creation-patterns` | No | list(string) | None | Glob patterns for auto branch creation |
| `--auto-branch-creation-config` | No | structure | None | Auto branch creation config |
| `--repository` | No | string | None | Updated repository URL |
| `--oauth-token` | No | string | None | OAuth token |
| `--access-token` | No | string | None | Personal access token |

**Output Schema:**
```json
{
    "app": {
        "appId": "string",
        "appArn": "string",
        "name": "string",
        "tags": {"string": "string"},
        "description": "string",
        "repository": "string",
        "platform": "WEB|WEB_DYNAMIC|WEB_COMPUTE",
        "createTime": "timestamp",
        "updateTime": "timestamp",
        "iamServiceRoleArn": "string",
        "environmentVariables": {"string": "string"},
        "defaultDomain": "string",
        "enableBranchAutoBuild": "boolean",
        "enableBranchAutoDeletion": "boolean",
        "enableBasicAuth": "boolean",
        "customRules": [],
        "buildSpec": "string",
        "customHeaders": "string",
        "enableAutoBranchCreation": "boolean",
        "autoBranchCreationPatterns": ["string"],
        "autoBranchCreationConfig": {},
        "repositoryCloneMethod": "SSH|TOKEN|SIGV4"
    }
}
```

---

### 1.6 `generate-access-logs`

Returns the access logs URL for a specified time range for an Amplify app.

**Synopsis:**
```bash
aws amplify generate-access-logs \
    --app-id <value> \
    --domain-name <value> \
    [--start-time <value>] \
    [--end-time <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-id` | **Yes** | string | -- | Unique ID of the Amplify app |
| `--domain-name` | **Yes** | string | -- | Domain name for access logs |
| `--start-time` | No | timestamp | None | Start time for the access log request (ISO 8601) |
| `--end-time` | No | timestamp | None | End time for the access log request (ISO 8601) |

**Output Schema:**
```json
{
    "logUrl": "string"
}
```
