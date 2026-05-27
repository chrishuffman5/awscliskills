# Build Batches

### 3.1 `start-build-batch`

Starts a batch build for a project.

**Synopsis:**
```bash
aws codebuild start-build-batch \
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
    [--report-build-batch-status-override | --no-report-build-batch-status-override] \
    [--environment-type-override <value>] \
    [--image-override <value>] \
    [--compute-type-override <value>] \
    [--certificate-override <value>] \
    [--cache-override <value>] \
    [--service-role-override <value>] \
    [--privileged-mode-override | --no-privileged-mode-override] \
    [--build-timeout-in-minutes-override <value>] \
    [--queued-timeout-in-minutes-override <value>] \
    [--encryption-key-override <value>] \
    [--idempotency-token <value>] \
    [--logs-config-override <value>] \
    [--registry-credential-override <value>] \
    [--image-pull-credentials-type-override <value>] \
    [--build-batch-config-override <value>] \
    [--debug-session-enabled | --no-debug-session-enabled] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project-name` | **Yes** | string | -- | Name of the build project |
| `--source-version` | No | string | None | Source version (branch, tag, commit ID) |
| `--artifacts-override` | No | structure | None | Override artifact settings |
| `--environment-variables-override` | No | list | None | Override environment variables |
| `--buildspec-override` | No | string | None | Override buildspec |
| `--environment-type-override` | No | string | None | Override environment type |
| `--image-override` | No | string | None | Override build image |
| `--compute-type-override` | No | string | None | Override compute type |
| `--service-role-override` | No | string | None | Override service role ARN |
| `--build-timeout-in-minutes-override` | No | integer | None | Override build timeout |
| `--queued-timeout-in-minutes-override` | No | integer | None | Override queue timeout |
| `--encryption-key-override` | No | string | None | Override encryption key |
| `--idempotency-token` | No | string | None | Idempotency token |
| `--logs-config-override` | No | structure | None | Override logs configuration |
| `--build-batch-config-override` | No | structure | None | Override batch config |
| `--debug-session-enabled` | No | boolean | false | Enable debug session |

**Output Schema:**
```json
{
    "buildBatch": {
        "id": "string",
        "arn": "string",
        "startTime": "timestamp",
        "endTime": "timestamp",
        "currentPhase": "string",
        "buildBatchStatus": "SUCCEEDED|FAILED|FAULT|TIMED_OUT|IN_PROGRESS|STOPPED",
        "sourceVersion": "string",
        "resolvedSourceVersion": "string",
        "projectName": "string",
        "phases": [
            {
                "phaseType": "SUBMITTED|DOWNLOAD_BATCHSPEC|IN_PROGRESS|COMBINE_ARTIFACTS|SUCCEEDED|FAILED|STOPPED",
                "phaseStatus": "SUCCEEDED|FAILED|FAULT|TIMED_OUT|IN_PROGRESS|STOPPED",
                "startTime": "timestamp",
                "endTime": "timestamp",
                "durationInSeconds": "long",
                "contexts": []
            }
        ],
        "source": { },
        "secondarySources": [],
        "secondarySourceVersions": [],
        "artifacts": { },
        "secondaryArtifacts": [],
        "cache": { },
        "environment": { },
        "serviceRole": "string",
        "logConfig": { },
        "buildTimeoutInMinutes": "integer",
        "queuedTimeoutInMinutes": "integer",
        "complete": true|false,
        "initiator": "string",
        "vpcConfig": { },
        "encryptionKey": "string",
        "buildBatchNumber": "long",
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
        "buildGroups": [
            {
                "identifier": "string",
                "dependsOn": ["string"],
                "ignoreFailure": true|false,
                "currentBuildSummary": {
                    "arn": "string",
                    "requestedOn": "timestamp",
                    "buildStatus": "string",
                    "primaryArtifact": {
                        "type": "string",
                        "location": "string",
                        "identifier": "string"
                    },
                    "secondaryArtifacts": []
                },
                "priorBuildSummaryList": []
            }
        ],
        "debugSessionEnabled": true|false
    }
}
```

---

### 3.2 `stop-build-batch`

Stops a running batch build.

**Synopsis:**
```bash
aws codebuild stop-build-batch \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Build batch ID |

**Output Schema:**
```json
{
    "buildBatch": {
        "id": "string",
        "arn": "string",
        "buildBatchStatus": "STOPPED",
        "projectName": "string",
        "phases": [],
        "source": { },
        "artifacts": { },
        "environment": { },
        "buildBatchConfig": { },
        "buildGroups": []
    }
}
```

---

### 3.3 `retry-build-batch`

Retries a batch build.

**Synopsis:**
```bash
aws codebuild retry-build-batch \
    [--id <value>] \
    [--idempotency-token <value>] \
    [--retry-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | No | string | None | Build batch ID to retry |
| `--idempotency-token` | No | string | None | Idempotency token |
| `--retry-type` | No | string | None | Retry type: `RETRY_ALL_BUILDS`, `RETRY_FAILED_BUILDS` |

**Output Schema:**
Same as `start-build-batch`.

---

### 3.4 `delete-build-batch`

Deletes a batch build.

**Synopsis:**
```bash
aws codebuild delete-build-batch \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Build batch ID to delete |

**Output Schema:**
```json
{
    "statusCode": "string",
    "buildsDeleted": ["string"],
    "buildsNotDeleted": [
        {
            "id": "string",
            "statusCode": "string"
        }
    ]
}
```

---

### 3.5 `batch-get-build-batches`

Gets information about one or more batch builds.

**Synopsis:**
```bash
aws codebuild batch-get-build-batches \
    --ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--ids` | **Yes** | list(string) | -- | Build batch IDs (max 100) |

**Output Schema:**
```json
{
    "buildBatches": [
        {
            "id": "string",
            "arn": "string",
            "startTime": "timestamp",
            "endTime": "timestamp",
            "currentPhase": "string",
            "buildBatchStatus": "SUCCEEDED|FAILED|FAULT|TIMED_OUT|IN_PROGRESS|STOPPED",
            "projectName": "string",
            "phases": [],
            "source": { },
            "artifacts": { },
            "environment": { },
            "buildBatchConfig": { },
            "buildGroups": []
        }
    ],
    "buildBatchesNotFound": ["string"]
}
```

---

### 3.6 `list-build-batches`

Retrieves the IDs of your build batches. **Paginated operation.**

**Synopsis:**
```bash
aws codebuild list-build-batches \
    [--filter <value>] \
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
| `--filter` | No | structure | None | Filter by status. Shorthand: `status=SUCCEEDED\|FAILED\|FAULT\|TIMED_OUT\|IN_PROGRESS\|STOPPED` |
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

### 3.7 `list-build-batches-for-project`

Retrieves the IDs of build batches for a specific project. **Paginated operation.**

**Synopsis:**
```bash
aws codebuild list-build-batches-for-project \
    [--project-name <value>] \
    [--filter <value>] \
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
| `--project-name` | No | string | None | Build project name |
| `--filter` | No | structure | None | Filter by status |
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
