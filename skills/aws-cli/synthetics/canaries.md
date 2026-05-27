# Canaries

### 1.1 `create-canary`

Creates a canary. Canaries are scripts that monitor your endpoints and APIs from the outside-in.

**Synopsis:**
```bash
aws synthetics create-canary \
    --name <value> \
    --code <value> \
    --artifact-s3-location <value> \
    --execution-role-arn <value> \
    --schedule <value> \
    --runtime-version <value> \
    [--run-config <value>] \
    [--success-retention-period-in-days <value>] \
    [--failure-retention-period-in-days <value>] \
    [--vpc-config <value>] \
    [--tags <value>] \
    [--artifact-config <value>] \
    [--provisioned-resource-cleanup <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | The name of the canary (1-21 chars, lowercase letters, numbers, hyphens) |
| `--code` | **Yes** | structure | -- | Canary code configuration |
| `--artifact-s3-location` | **Yes** | string | -- | S3 location for canary artifacts (e.g., `s3://bucket/prefix`) |
| `--execution-role-arn` | **Yes** | string | -- | IAM role ARN for the canary |
| `--schedule` | **Yes** | structure | -- | Schedule expression. Shorthand: `Expression=string,DurationInSeconds=long` |
| `--runtime-version` | **Yes** | string | -- | Runtime version (e.g., `syn-nodejs-puppeteer-9.0`) |
| `--run-config` | No | structure | None | Runtime configuration (timeout, memory, environment variables) |
| `--success-retention-period-in-days` | No | integer | 31 | Days to retain successful run artifacts (1-455) |
| `--failure-retention-period-in-days` | No | integer | 31 | Days to retain failed run artifacts (1-455) |
| `--vpc-config` | No | structure | None | VPC configuration. Shorthand: `SubnetIds=string,string,SecurityGroupIds=string,string` |
| `--tags` | No | map | None | Tags. Shorthand: `KeyName1=string,KeyName2=string` |
| `--artifact-config` | No | structure | None | Artifact configuration (S3 encryption) |
| `--provisioned-resource-cleanup` | No | string | None | Cleanup behavior: `AUTOMATIC`, `OFF` |

**Code Structure:**
```json
{
    "S3Bucket": "string",
    "S3Key": "string",
    "S3Version": "string",
    "ZipFile": "blob",
    "Handler": "string"
}
```

**Run Config Structure:**
```json
{
    "TimeoutInSeconds": "integer",
    "MemoryInMB": "integer",
    "ActiveTracing": true|false,
    "EnvironmentVariables": {
        "string": "string"
    }
}
```

**Output Schema:**
```json
{
    "Canary": {
        "Id": "string",
        "Name": "string",
        "Code": {
            "SourceLocationArn": "string",
            "Handler": "string"
        },
        "ExecutionRoleArn": "string",
        "Schedule": {
            "Expression": "string",
            "DurationInSeconds": "long"
        },
        "RunConfig": {
            "TimeoutInSeconds": "integer",
            "MemoryInMB": "integer",
            "ActiveTracing": true|false
        },
        "SuccessRetentionPeriodInDays": "integer",
        "FailureRetentionPeriodInDays": "integer",
        "Status": {
            "State": "CREATING|READY|STARTING|RUNNING|UPDATING|STOPPING|STOPPED|ERROR|DELETING",
            "StateReason": "string",
            "StateReasonCode": "INVALID_PERMISSIONS|CREATE_PENDING|CREATE_IN_PROGRESS|CREATE_FAILED|UPDATE_PENDING|UPDATE_IN_PROGRESS|UPDATE_COMPLETE|ROLLBACK_COMPLETE|ROLLBACK_FAILED|DELETE_IN_PROGRESS|DELETE_FAILED|SYNC_DELETE_IN_PROGRESS"
        },
        "Timeline": {
            "Created": "timestamp",
            "LastModified": "timestamp",
            "LastStarted": "timestamp",
            "LastStopped": "timestamp"
        },
        "ArtifactS3Location": "string",
        "EngineArn": "string",
        "RuntimeVersion": "string",
        "VpcConfig": {
            "VpcId": "string",
            "SubnetIds": ["string"],
            "SecurityGroupIds": ["string"]
        },
        "Tags": {
            "string": "string"
        },
        "ArtifactConfig": {
            "S3Encryption": {
                "EncryptionMode": "SSE_S3|SSE_KMS",
                "KmsKeyArn": "string"
            }
        },
        "ProvisionedResourceCleanup": "AUTOMATIC|OFF"
    }
}
```

---

### 1.2 `delete-canary`

Permanently deletes the specified canary. If the canary is running, you must stop it before deleting (unless you use `--delete-lambda`).

**Synopsis:**
```bash
aws synthetics delete-canary \
    --name <value> \
    [--delete-lambda | --no-delete-lambda] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | The name or ARN of the canary to delete |
| `--delete-lambda` | No | boolean | false | Also delete the Lambda function and layers used by the canary |

**Output Schema:**
```json
{}
```

---

### 1.3 `get-canary`

Retrieves complete information about one canary.

**Synopsis:**
```bash
aws synthetics get-canary \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | The name or ARN of the canary |

**Output Schema:**
```json
{
    "Canary": {
        "Id": "string",
        "Name": "string",
        "Code": {
            "SourceLocationArn": "string",
            "Handler": "string"
        },
        "ExecutionRoleArn": "string",
        "Schedule": {
            "Expression": "string",
            "DurationInSeconds": "long"
        },
        "RunConfig": {
            "TimeoutInSeconds": "integer",
            "MemoryInMB": "integer",
            "ActiveTracing": true|false
        },
        "SuccessRetentionPeriodInDays": "integer",
        "FailureRetentionPeriodInDays": "integer",
        "Status": {
            "State": "CREATING|READY|STARTING|RUNNING|UPDATING|STOPPING|STOPPED|ERROR|DELETING",
            "StateReason": "string",
            "StateReasonCode": "string"
        },
        "Timeline": {
            "Created": "timestamp",
            "LastModified": "timestamp",
            "LastStarted": "timestamp",
            "LastStopped": "timestamp"
        },
        "ArtifactS3Location": "string",
        "EngineArn": "string",
        "RuntimeVersion": "string",
        "VpcConfig": {
            "VpcId": "string",
            "SubnetIds": ["string"],
            "SecurityGroupIds": ["string"]
        },
        "Tags": {
            "string": "string"
        },
        "ArtifactConfig": {
            "S3Encryption": {
                "EncryptionMode": "SSE_S3|SSE_KMS",
                "KmsKeyArn": "string"
            }
        },
        "ProvisionedResourceCleanup": "AUTOMATIC|OFF"
    }
}
```

---

### 1.4 `describe-canaries`

Retrieves a list of canaries with full details. **Paginated operation.**

**Synopsis:**
```bash
aws synthetics describe-canaries \
    [--names <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--names` | No | list(string) | None | Filter by canary names |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call (max 20) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Canaries": [
        {
            "Id": "string",
            "Name": "string",
            "Code": {},
            "ExecutionRoleArn": "string",
            "Schedule": {},
            "RunConfig": {},
            "SuccessRetentionPeriodInDays": "integer",
            "FailureRetentionPeriodInDays": "integer",
            "Status": {},
            "Timeline": {},
            "ArtifactS3Location": "string",
            "EngineArn": "string",
            "RuntimeVersion": "string",
            "VpcConfig": {},
            "Tags": {},
            "ArtifactConfig": {},
            "ProvisionedResourceCleanup": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.5 `update-canary`

Updates the configuration of a canary that has already been created.

**Synopsis:**
```bash
aws synthetics update-canary \
    --name <value> \
    [--code <value>] \
    [--execution-role-arn <value>] \
    [--runtime-version <value>] \
    [--schedule <value>] \
    [--run-config <value>] \
    [--success-retention-period-in-days <value>] \
    [--failure-retention-period-in-days <value>] \
    [--vpc-config <value>] \
    [--artifact-s3-location <value>] \
    [--artifact-config <value>] \
    [--provisioned-resource-cleanup <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | The name or ARN of the canary to update |
| `--code` | No | structure | None | Updated code configuration |
| `--execution-role-arn` | No | string | None | New execution role ARN |
| `--runtime-version` | No | string | None | New runtime version |
| `--schedule` | No | structure | None | Updated schedule |
| `--run-config` | No | structure | None | Updated runtime configuration |
| `--success-retention-period-in-days` | No | integer | None | New success retention (1-455 days) |
| `--failure-retention-period-in-days` | No | integer | None | New failure retention (1-455 days) |
| `--vpc-config` | No | structure | None | Updated VPC configuration |
| `--artifact-s3-location` | No | string | None | New S3 artifact location |
| `--artifact-config` | No | structure | None | Updated artifact configuration |
| `--provisioned-resource-cleanup` | No | string | None | Cleanup behavior: `AUTOMATIC`, `OFF` |

**Output Schema:**
```json
{}
```

---

### 1.6 `start-canary`

Starts a canary so that it begins running according to its schedule.

**Synopsis:**
```bash
aws synthetics start-canary \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | The name or ARN of the canary to start |

**Output Schema:**
```json
{}
```

---

### 1.7 `stop-canary`

Stops the canary to prevent all future runs. The canary is not deleted.

**Synopsis:**
```bash
aws synthetics stop-canary \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | The name or ARN of the canary to stop |

**Output Schema:**
```json
{}
```

---

### 1.8 `start-canary-dry-run`

Starts a dry run of a canary. A dry run is a test run that validates the canary configuration without creating permanent resources.

**Synopsis:**
```bash
aws synthetics start-canary-dry-run \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | The name or ARN of the canary |

**Output Schema:**
```json
{
    "DryRunConfig": {
        "DryRunId": "string"
    }
}
```

---

### 1.9 `get-canary-runs`

Retrieves a list of runs for a specified canary. **Paginated operation.**

**Synopsis:**
```bash
aws synthetics get-canary-runs \
    --name <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | The name or ARN of the canary |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call (max 100) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "CanaryRuns": [
        {
            "Id": "string",
            "Name": "string",
            "Status": {
                "State": "RUNNING|PASSED|FAILED",
                "StateReason": "string",
                "StateReasonCode": "CANARY_FAILURE|EXECUTION_FAILURE"
            },
            "Timeline": {
                "Started": "timestamp",
                "Completed": "timestamp"
            },
            "ArtifactS3Location": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.10 `describe-canaries-last-run`

Returns information about the last run of each canary. **Paginated operation.**

**Synopsis:**
```bash
aws synthetics describe-canaries-last-run \
    [--names <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--names` | No | list(string) | None | Filter by canary names |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call (max 100) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "CanariesLastRun": [
        {
            "CanaryName": "string",
            "LastRun": {
                "Id": "string",
                "Name": "string",
                "Status": {
                    "State": "RUNNING|PASSED|FAILED",
                    "StateReason": "string",
                    "StateReasonCode": "CANARY_FAILURE|EXECUTION_FAILURE"
                },
                "Timeline": {
                    "Started": "timestamp",
                    "Completed": "timestamp"
                },
                "ArtifactS3Location": "string"
            }
        }
    ],
    "NextToken": "string"
}
```

---

### 1.11 `describe-runtime-versions`

Returns a list of Synthetics canary runtime versions. **Paginated operation.**

**Synopsis:**
```bash
aws synthetics describe-runtime-versions \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call (max 100) |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "RuntimeVersions": [
        {
            "VersionName": "string",
            "Description": "string",
            "ReleaseDate": "timestamp",
            "DeprecationDate": "timestamp"
        }
    ],
    "NextToken": "string"
}
```
