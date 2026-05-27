# Projects

### 1.1 `create-project`

Creates a build project.

**Synopsis:**
```bash
aws codebuild create-project \
    --name <value> \
    --source <value> \
    --artifacts <value> \
    --environment <value> \
    --service-role <value> \
    [--description <value>] \
    [--secondary-sources <value>] \
    [--secondary-source-versions <value>] \
    [--secondary-artifacts <value>] \
    [--cache <value>] \
    [--timeout-in-minutes <value>] \
    [--queued-timeout-in-minutes <value>] \
    [--encryption-key <value>] \
    [--tags <value>] \
    [--vpc-config <value>] \
    [--badge-enabled | --no-badge-enabled] \
    [--logs-config <value>] \
    [--file-system-locations <value>] \
    [--build-batch-config <value>] \
    [--concurrent-build-limit <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Project name (2-255 chars) |
| `--source` | **Yes** | structure | -- | Source configuration (type, location, buildspec, etc.) |
| `--artifacts` | **Yes** | structure | -- | Build output artifact configuration |
| `--environment` | **Yes** | structure | -- | Build environment configuration |
| `--service-role` | **Yes** | string | -- | IAM role ARN for CodeBuild to use |
| `--description` | No | string | None | Project description (max 255 chars) |
| `--secondary-sources` | No | list | None | Additional source definitions (max 12) |
| `--secondary-source-versions` | No | list | None | Versions for secondary sources |
| `--secondary-artifacts` | No | list | None | Additional artifact definitions (max 12) |
| `--cache` | No | structure | None | Cache configuration |
| `--timeout-in-minutes` | No | integer | 60 | Build timeout (5-2160 minutes / 36 hours) |
| `--queued-timeout-in-minutes` | No | integer | 480 | Queue timeout (5-480 minutes / 8 hours) |
| `--encryption-key` | No | string | AWS-managed key | KMS key ARN for artifact encryption |
| `--tags` | No | list | None | Tags (max 50). Shorthand: `key=string,value=string ...` |
| `--vpc-config` | No | structure | None | VPC configuration |
| `--badge-enabled` | No | boolean | false | Enable build badge |
| `--logs-config` | No | structure | None | CloudWatch Logs and S3 log configuration |
| `--file-system-locations` | No | list | None | EFS file system mount points |
| `--build-batch-config` | No | structure | None | Batch build configuration |
| `--concurrent-build-limit` | No | integer | None | Maximum concurrent builds |

**Source Structure:**
```json
{
    "type": "CODECOMMIT|CODEPIPELINE|GITHUB|GITHUB_ENTERPRISE|BITBUCKET|S3|NO_SOURCE|GITLAB|GITLAB_SELF_MANAGED",
    "location": "string",
    "gitCloneDepth": "integer",
    "gitSubmodulesConfig": {
        "fetchSubmodules": true|false
    },
    "buildspec": "string",
    "auth": {
        "type": "OAUTH|CODECONNECTIONS",
        "resource": "string"
    },
    "reportBuildStatus": true|false,
    "buildStatusConfig": {
        "context": "string",
        "targetUrl": "string"
    },
    "insecureSsl": true|false,
    "sourceIdentifier": "string"
}
```

**Environment Structure:**
```json
{
    "type": "WINDOWS_CONTAINER|LINUX_CONTAINER|LINUX_GPU_CONTAINER|ARM_CONTAINER|WINDOWS_SERVER_2019_CONTAINER|LINUX_LAMBDA_CONTAINER|ARM_LAMBDA_CONTAINER",
    "image": "string",
    "computeType": "BUILD_GENERAL1_SMALL|BUILD_GENERAL1_MEDIUM|BUILD_GENERAL1_LARGE|BUILD_GENERAL1_XLARGE|BUILD_GENERAL1_2XLARGE|BUILD_LAMBDA_1GB|BUILD_LAMBDA_2GB|BUILD_LAMBDA_4GB|BUILD_LAMBDA_8GB|BUILD_LAMBDA_10GB",
    "environmentVariables": [
        {
            "name": "string",
            "value": "string",
            "type": "PLAINTEXT|PARAMETER_STORE|SECRETS_MANAGER"
        }
    ],
    "privilegedMode": true|false,
    "certificate": "string",
    "registryCredential": {
        "credential": "string",
        "credentialProvider": "SECRETS_MANAGER"
    },
    "imagePullCredentialsType": "CODEBUILD|SERVICE_ROLE",
    "fleet": {
        "fleetArn": "string"
    }
}
```

**Artifacts Structure:**
```json
{
    "type": "CODEPIPELINE|S3|NO_ARTIFACTS",
    "location": "string",
    "path": "string",
    "namespaceType": "NONE|BUILD_ID",
    "name": "string",
    "packaging": "NONE|ZIP",
    "overrideArtifactName": true|false,
    "encryptionDisabled": true|false,
    "artifactIdentifier": "string",
    "bucketOwnerAccess": "NONE|READ_ONLY|FULL"
}
```

**Output Schema:**
```json
{
    "project": {
        "name": "string",
        "arn": "string",
        "description": "string",
        "source": { },
        "secondarySources": [],
        "secondarySourceVersions": [],
        "artifacts": { },
        "secondaryArtifacts": [],
        "cache": {
            "type": "NO_CACHE|S3|LOCAL",
            "location": "string",
            "modes": ["LOCAL_DOCKER_LAYER_CACHE|LOCAL_SOURCE_CACHE|LOCAL_CUSTOM_CACHE"]
        },
        "environment": { },
        "serviceRole": "string",
        "timeoutInMinutes": "integer",
        "queuedTimeoutInMinutes": "integer",
        "encryptionKey": "string",
        "tags": [],
        "created": "timestamp",
        "lastModified": "timestamp",
        "webhook": { },
        "vpcConfig": {
            "vpcId": "string",
            "subnets": ["string"],
            "securityGroupIds": ["string"]
        },
        "badge": {
            "badgeEnabled": true|false,
            "badgeRequestUrl": "string"
        },
        "logsConfig": {
            "cloudWatchLogs": {
                "status": "ENABLED|DISABLED",
                "groupName": "string",
                "streamName": "string"
            },
            "s3Logs": {
                "status": "ENABLED|DISABLED",
                "location": "string",
                "encryptionDisabled": true|false,
                "bucketOwnerAccess": "NONE|READ_ONLY|FULL"
            }
        },
        "fileSystemLocations": [],
        "buildBatchConfig": {
            "serviceRole": "string",
            "combineArtifacts": true|false,
            "restrictions": {
                "maximumBuildsAllowed": "integer",
                "computeTypesAllowed": ["string"]
            },
            "timeoutInMins": "integer",
            "batchReportMode": "REPORT_INDIVIDUAL_BUILDS|REPORT_AGGREGATED_BATCH"
        },
        "concurrentBuildLimit": "integer",
        "projectVisibility": "PUBLIC_READ|PRIVATE",
        "publicProjectAlias": "string",
        "resourceAccessRole": "string"
    }
}
```

---

### 1.2 `delete-project`

Deletes a build project. Does not delete builds already completed.

**Synopsis:**
```bash
aws codebuild delete-project \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Project name or ARN |

**Output Schema:**
```json
{}
```

---

### 1.3 `batch-get-projects`

Gets information about one or more build projects.

**Synopsis:**
```bash
aws codebuild batch-get-projects \
    --names <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--names` | **Yes** | list(string) | -- | Project names or ARNs (max 100) |

**Output Schema:**
```json
{
    "projects": [
        {
            "name": "string",
            "arn": "string",
            "description": "string",
            "source": { },
            "artifacts": { },
            "environment": { },
            "serviceRole": "string",
            "timeoutInMinutes": "integer",
            "queuedTimeoutInMinutes": "integer",
            "encryptionKey": "string",
            "tags": [],
            "created": "timestamp",
            "lastModified": "timestamp",
            "webhook": { },
            "vpcConfig": { },
            "badge": { },
            "logsConfig": { },
            "concurrentBuildLimit": "integer"
        }
    ],
    "projectsNotFound": ["string"]
}
```

---

### 1.4 `list-projects`

Gets a list of build project names. **Paginated operation.**

**Synopsis:**
```bash
aws codebuild list-projects \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--sort-by` | No | string | `NAME` | Sort criterion: `NAME`, `CREATED_TIME`, `LAST_MODIFIED_TIME` |
| `--sort-order` | No | string | `ASCENDING` | Sort order: `ASCENDING`, `DESCENDING` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "projects": ["string"],
    "nextToken": "string"
}
```

---

### 1.5 `update-project`

Changes the settings of a build project. Takes the same parameters as `create-project` (except `--name` identifies the existing project).

**Synopsis:**
```bash
aws codebuild update-project \
    --name <value> \
    [--description <value>] \
    [--source <value>] \
    [--secondary-sources <value>] \
    [--secondary-source-versions <value>] \
    [--artifacts <value>] \
    [--secondary-artifacts <value>] \
    [--environment <value>] \
    [--service-role <value>] \
    [--cache <value>] \
    [--timeout-in-minutes <value>] \
    [--queued-timeout-in-minutes <value>] \
    [--encryption-key <value>] \
    [--tags <value>] \
    [--vpc-config <value>] \
    [--badge-enabled | --no-badge-enabled] \
    [--logs-config <value>] \
    [--file-system-locations <value>] \
    [--build-batch-config <value>] \
    [--concurrent-build-limit <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Project name to update |
| All other parameters | No | -- | -- | Same as `create-project`; only specified values are updated |

**Output Schema:**
Same as `create-project`.
