# Builds

### 2.1 `start-build`

Starts running a build.

**Synopsis:**
```bash
aws codebuild start-build \
    --project-name <value> \
    [--secondary-sources-override <value>] \
    [--secondary-sources-version-override <value>] \
    [--source-version <value>] \
    [--artifacts-override <value>] \
    [--secondary-artifacts-override <value>] \
    [--environment-variables-override <value>] \
    [--source-type-override <value>] \
    [--source-location-override <value>] \
    [--source-auth-override <value>] \
    [--git-clone-depth-override <value>] \
    [--git-submodules-config-override <value>] \
    [--buildspec-override <value>] \
    [--insecure-ssl-override | --no-insecure-ssl-override] \
    [--report-build-status-override | --no-report-build-status-override] \
    [--environment-type-override <value>] \
    [--image-override <value>] \
    [--compute-type-override <value>] \
    [--certificate-override <value>] \
    [--cache-override <value>] \
    [--service-role-override <value>] \
    [--privileged-mode-override | --no-privileged-mode-override] \
    [--timeout-in-minutes-override <value>] \
    [--queued-timeout-in-minutes-override <value>] \
    [--encryption-key-override <value>] \
    [--idempotency-token <value>] \
    [--logs-config-override <value>] \
    [--registry-credential-override <value>] \
    [--image-pull-credentials-type-override <value>] \
    [--debug-session-enabled | --no-debug-session-enabled] \
    [--fleet-override <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project-name` | **Yes** | string | -- | Name of the build project |
| `--source-version` | No | string | None | Source version (branch, tag, commit ID) |
| `--artifacts-override` | No | structure | None | Override artifact settings |
| `--environment-variables-override` | No | list | None | Override environment variables. Shorthand: `name=string,value=string,type=PLAINTEXT\|PARAMETER_STORE\|SECRETS_MANAGER ...` |
| `--source-type-override` | No | string | None | Override source type |
| `--source-location-override` | No | string | None | Override source location |
| `--buildspec-override` | No | string | None | Override buildspec (inline YAML or file path) |
| `--environment-type-override` | No | string | None | Override environment type |
| `--image-override` | No | string | None | Override build image |
| `--compute-type-override` | No | string | None | Override compute type |
| `--service-role-override` | No | string | None | Override service role ARN |
| `--privileged-mode-override` | No | boolean | None | Override privileged mode |
| `--timeout-in-minutes-override` | No | integer | None | Override build timeout |
| `--queued-timeout-in-minutes-override` | No | integer | None | Override queue timeout |
| `--encryption-key-override` | No | string | None | Override encryption key |
| `--idempotency-token` | No | string | None | Idempotency token |
| `--logs-config-override` | No | structure | None | Override logs configuration |
| `--debug-session-enabled` | No | boolean | false | Enable AWS Systems Manager session for debugging |
| `--fleet-override` | No | structure | None | Override fleet configuration |
| `--cache-override` | No | structure | None | Override cache configuration |
| `--git-clone-depth-override` | No | integer | None | Override git clone depth |
| `--registry-credential-override` | No | structure | None | Override registry credential |
| `--image-pull-credentials-type-override` | No | string | None | Override image pull credentials type |

**Output Schema:**
```json
{
    "build": {
        "id": "string",
        "arn": "string",
        "buildNumber": "long",
        "startTime": "timestamp",
        "endTime": "timestamp",
        "currentPhase": "string",
        "buildStatus": "SUCCEEDED|FAILED|FAULT|TIMED_OUT|IN_PROGRESS|STOPPED",
        "sourceVersion": "string",
        "resolvedSourceVersion": "string",
        "projectName": "string",
        "phases": [
            {
                "phaseType": "SUBMITTED|QUEUED|PROVISIONING|DOWNLOAD_SOURCE|INSTALL|PRE_BUILD|BUILD|POST_BUILD|UPLOAD_ARTIFACTS|FINALIZING|COMPLETED",
                "phaseStatus": "SUCCEEDED|FAILED|FAULT|TIMED_OUT|IN_PROGRESS|STOPPED",
                "startTime": "timestamp",
                "endTime": "timestamp",
                "durationInSeconds": "long",
                "contexts": [
                    {
                        "statusCode": "string",
                        "message": "string"
                    }
                ]
            }
        ],
        "source": { },
        "secondarySources": [],
        "secondarySourceVersions": [],
        "artifacts": {
            "location": "string",
            "sha256sum": "string",
            "md5sum": "string",
            "overrideArtifactName": true|false,
            "encryptionDisabled": true|false,
            "artifactIdentifier": "string",
            "bucketOwnerAccess": "NONE|READ_ONLY|FULL"
        },
        "secondaryArtifacts": [],
        "cache": { },
        "environment": { },
        "serviceRole": "string",
        "logs": {
            "groupName": "string",
            "streamName": "string",
            "deepLink": "string",
            "s3DeepLink": "string",
            "cloudWatchLogsArn": "string",
            "s3LogsArn": "string",
            "cloudWatchLogs": { },
            "s3Logs": { }
        },
        "timeoutInMinutes": "integer",
        "queuedTimeoutInMinutes": "integer",
        "buildComplete": true|false,
        "initiator": "string",
        "vpcConfig": { },
        "networkInterface": {
            "subnetId": "string",
            "networkInterfaceId": "string"
        },
        "encryptionKey": "string",
        "exportedEnvironmentVariables": [
            {
                "name": "string",
                "value": "string"
            }
        ],
        "reportArns": ["string"],
        "fileSystemLocations": [],
        "debugSession": {
            "sessionEnabled": true|false,
            "sessionTarget": "string"
        },
        "buildBatchArn": "string"
    }
}
```

---

### 2.2 `stop-build`

Attempts to stop a running build.

**Synopsis:**
```bash
aws codebuild stop-build \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Build ID (e.g., `project-name:build-id`) |

**Output Schema:**
```json
{
    "build": {
        "id": "string",
        "arn": "string",
        "buildStatus": "STOPPED",
        "projectName": "string",
        "phases": [],
        "source": { },
        "artifacts": { },
        "environment": { },
        "serviceRole": "string",
        "logs": { },
        "timeoutInMinutes": "integer",
        "buildComplete": true|false
    }
}
```

---

### 2.3 `retry-build`

Restarts a build.

**Synopsis:**
```bash
aws codebuild retry-build \
    [--id <value>] \
    [--idempotency-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | No | string | None | Build ID to retry |
| `--idempotency-token` | No | string | None | Idempotency token |

**Output Schema:**
Same as `start-build`.

---

### 2.4 `batch-get-builds`

Gets information about one or more builds.

**Synopsis:**
```bash
aws codebuild batch-get-builds \
    --ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--ids` | **Yes** | list(string) | -- | Build IDs (max 100) |

**Output Schema:**
```json
{
    "builds": [
        {
            "id": "string",
            "arn": "string",
            "buildNumber": "long",
            "startTime": "timestamp",
            "endTime": "timestamp",
            "currentPhase": "string",
            "buildStatus": "SUCCEEDED|FAILED|FAULT|TIMED_OUT|IN_PROGRESS|STOPPED",
            "sourceVersion": "string",
            "resolvedSourceVersion": "string",
            "projectName": "string",
            "phases": [],
            "source": { },
            "artifacts": { },
            "environment": { },
            "serviceRole": "string",
            "logs": { },
            "timeoutInMinutes": "integer",
            "buildComplete": true|false,
            "initiator": "string",
            "exportedEnvironmentVariables": [],
            "reportArns": []
        }
    ],
    "buildsNotFound": ["string"]
}
```

---

### 2.5 `list-builds`

Gets a list of build IDs. **Paginated operation.**

**Synopsis:**
```bash
aws codebuild list-builds \
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
| `--sort-order` | No | string | `ASCENDING` | Sort order: `ASCENDING`, `DESCENDING` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ids": ["string"],
    "nextToken": "string"
}
```

---

### 2.6 `list-builds-for-project`

Gets a list of build IDs for the specified build project. **Paginated operation.**

**Synopsis:**
```bash
aws codebuild list-builds-for-project \
    --project-name <value> \
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
| `--project-name` | **Yes** | string | -- | Build project name |
| `--sort-order` | No | string | `ASCENDING` | Sort order: `ASCENDING`, `DESCENDING` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ids": ["string"],
    "nextToken": "string"
}
```
