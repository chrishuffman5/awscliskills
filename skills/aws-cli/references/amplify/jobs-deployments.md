# Jobs & Deployments

### 4.1 `start-job`

Starts a new job for a branch of an Amplify app.

**Synopsis:**
```bash
aws amplify start-job \
    --app-id <value> \
    --branch-name <value> \
    --job-type <value> \
    [--job-id <value>] \
    [--job-reason <value>] \
    [--commit-id <value>] \
    [--commit-message <value>] \
    [--commit-time <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-id` | **Yes** | string | -- | Unique ID of the Amplify app |
| `--branch-name` | **Yes** | string | -- | Branch name for the job |
| `--job-type` | **Yes** | string | -- | Job type: `RELEASE`, `RETRY`, `MANUAL`, `WEB_HOOK` |
| `--job-id` | No | string | None | Job ID to retry (required for `RETRY` type) |
| `--job-reason` | No | string | None | Reason for the job |
| `--commit-id` | No | string | None | Commit ID for the job |
| `--commit-message` | No | string | None | Commit message for the job |
| `--commit-time` | No | timestamp | None | Commit time for the job |

**Output Schema:**
```json
{
    "jobSummary": {
        "jobArn": "string",
        "jobId": "string",
        "commitId": "string",
        "commitMessage": "string",
        "commitTime": "timestamp",
        "startTime": "timestamp",
        "status": "PENDING|PROVISIONING|RUNNING|FAILED|SUCCEED|CANCELLING|CANCELLED",
        "endTime": "timestamp",
        "jobType": "RELEASE|RETRY|MANUAL|WEB_HOOK"
    }
}
```

---

### 4.2 `stop-job`

Stops a running job for a branch of an Amplify app.

**Synopsis:**
```bash
aws amplify stop-job \
    --app-id <value> \
    --branch-name <value> \
    --job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-id` | **Yes** | string | -- | Unique ID of the Amplify app |
| `--branch-name` | **Yes** | string | -- | Branch name for the job |
| `--job-id` | **Yes** | string | -- | ID of the job to stop |

**Output Schema:**
```json
{
    "jobSummary": {
        "jobArn": "string",
        "jobId": "string",
        "commitId": "string",
        "commitMessage": "string",
        "commitTime": "timestamp",
        "startTime": "timestamp",
        "status": "CANCELLING|CANCELLED",
        "endTime": "timestamp",
        "jobType": "RELEASE|RETRY|MANUAL|WEB_HOOK"
    }
}
```

---

### 4.3 `get-job`

Returns a job for a branch of an Amplify app.

**Synopsis:**
```bash
aws amplify get-job \
    --app-id <value> \
    --branch-name <value> \
    --job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-id` | **Yes** | string | -- | Unique ID of the Amplify app |
| `--branch-name` | **Yes** | string | -- | Branch name for the job |
| `--job-id` | **Yes** | string | -- | ID of the job |

**Output Schema:**
```json
{
    "job": {
        "summary": {
            "jobArn": "string",
            "jobId": "string",
            "commitId": "string",
            "commitMessage": "string",
            "commitTime": "timestamp",
            "startTime": "timestamp",
            "status": "PENDING|PROVISIONING|RUNNING|FAILED|SUCCEED|CANCELLING|CANCELLED",
            "endTime": "timestamp",
            "jobType": "RELEASE|RETRY|MANUAL|WEB_HOOK"
        },
        "steps": [
            {
                "stepName": "string",
                "startTime": "timestamp",
                "status": "PENDING|PROVISIONING|RUNNING|FAILED|SUCCEED|CANCELLING|CANCELLED",
                "endTime": "timestamp",
                "logUrl": "string",
                "artifactsUrl": "string",
                "testArtifactsUrl": "string",
                "testConfigUrl": "string",
                "screenshots": {"string": "string"},
                "statusReason": "string",
                "context": "string"
            }
        ]
    }
}
```

---

### 4.4 `list-jobs`

Lists jobs for a branch of an Amplify app. **Paginated operation.**

**Synopsis:**
```bash
aws amplify list-jobs \
    --app-id <value> \
    --branch-name <value> \
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
| `--branch-name` | **Yes** | string | -- | Branch name for jobs |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call (max 100) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "jobSummaries": [
        {
            "jobArn": "string",
            "jobId": "string",
            "commitId": "string",
            "commitMessage": "string",
            "commitTime": "timestamp",
            "startTime": "timestamp",
            "status": "PENDING|PROVISIONING|RUNNING|FAILED|SUCCEED|CANCELLING|CANCELLED",
            "endTime": "timestamp",
            "jobType": "RELEASE|RETRY|MANUAL|WEB_HOOK"
        }
    ],
    "nextToken": "string"
}
```

---

### 4.5 `delete-job`

Deletes a job for a branch of an Amplify app.

**Synopsis:**
```bash
aws amplify delete-job \
    --app-id <value> \
    --branch-name <value> \
    --job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-id` | **Yes** | string | -- | Unique ID of the Amplify app |
| `--branch-name` | **Yes** | string | -- | Branch name |
| `--job-id` | **Yes** | string | -- | ID of the job to delete |

**Output Schema:**
```json
{
    "jobSummary": {
        "jobArn": "string",
        "jobId": "string",
        "commitId": "string",
        "commitMessage": "string",
        "commitTime": "timestamp",
        "startTime": "timestamp",
        "status": "string",
        "endTime": "timestamp",
        "jobType": "RELEASE|RETRY|MANUAL|WEB_HOOK"
    }
}
```

---

### 4.6 `create-deployment`

Creates a manual deployment for an Amplify app. Returns a pre-signed URL to upload a zip of your build artifacts.

**Synopsis:**
```bash
aws amplify create-deployment \
    --app-id <value> \
    --branch-name <value> \
    [--file-map <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-id` | **Yes** | string | -- | Unique ID of the Amplify app |
| `--branch-name` | **Yes** | string | -- | Branch name for the deployment |
| `--file-map` | No | map | None | Map of file names to MD5 hashes for differential uploads. Shorthand: `KeyName1=string,KeyName2=string` |

**Output Schema:**
```json
{
    "jobId": "string",
    "fileUploadUrls": {
        "string": "string"
    },
    "zipUploadUrl": "string"
}
```

---

### 4.7 `start-deployment`

Starts a deployment for a manually deployed app. After uploading artifacts to the URL returned by `create-deployment`, call this to start the deployment.

**Synopsis:**
```bash
aws amplify start-deployment \
    --app-id <value> \
    --branch-name <value> \
    [--job-id <value>] \
    [--source-url <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-id` | **Yes** | string | -- | Unique ID of the Amplify app |
| `--branch-name` | **Yes** | string | -- | Branch name for the deployment |
| `--job-id` | No | string | None | Job ID returned by `create-deployment` |
| `--source-url` | No | string | None | Source URL for the deployment |

**Output Schema:**
```json
{
    "jobSummary": {
        "jobArn": "string",
        "jobId": "string",
        "commitId": "string",
        "commitMessage": "string",
        "commitTime": "timestamp",
        "startTime": "timestamp",
        "status": "PENDING|PROVISIONING|RUNNING|FAILED|SUCCEED|CANCELLING|CANCELLED",
        "endTime": "timestamp",
        "jobType": "MANUAL"
    }
}
```

---

### 4.8 `get-artifact-url`

Returns the artifact info that corresponds to an artifact ID.

**Synopsis:**
```bash
aws amplify get-artifact-url \
    --artifact-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--artifact-id` | **Yes** | string | -- | Unique ID for the artifact |

**Output Schema:**
```json
{
    "artifactId": "string",
    "artifactUrl": "string"
}
```

---

### 4.9 `list-artifacts`

Returns a list of artifacts for a specific branch, job, and step. **Paginated operation.**

**Synopsis:**
```bash
aws amplify list-artifacts \
    --app-id <value> \
    --branch-name <value> \
    --job-id <value> \
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
| `--branch-name` | **Yes** | string | -- | Branch name |
| `--job-id` | **Yes** | string | -- | Job ID |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "artifacts": [
        {
            "artifactFileName": "string",
            "artifactId": "string"
        }
    ],
    "nextToken": "string"
}
```
