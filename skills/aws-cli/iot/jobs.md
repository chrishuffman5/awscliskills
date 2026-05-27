# Jobs

## 6.1 `create-job`

Creates a job for device execution. Specify either `--document` or `--document-source`.

**Synopsis:**
```bash
aws iot create-job \
    --job-id <value> \
    --targets <value> \
    [--document-source <value>] \
    [--document <value>] \
    [--description <value>] \
    [--target-selection <value>] \
    [--presigned-url-config <value>] \
    [--job-executions-rollout-config <value>] \
    [--abort-config <value>] \
    [--timeout-config <value>] \
    [--tags <value>] \
    [--namespace-id <value>] \
    [--job-template-arn <value>] \
    [--job-executions-retry-config <value>] \
    [--document-parameters <value>] \
    [--scheduling-config <value>] \
    [--destination-package-versions <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | Unique job ID (1-64 chars) |
| `--targets` | **Yes** | list | -- | Thing/thing group ARNs (min 1) |
| `--document-source` | No | string | None | S3 URL for job document |
| `--document` | No | string | None | Job document JSON (max 32768 chars) |
| `--description` | No | string | None | Job description (max 2028 chars) |
| `--target-selection` | No | string | SNAPSHOT | `CONTINUOUS` or `SNAPSHOT` |
| `--presigned-url-config` | No | structure | None | Pre-signed URL config (roleArn, expiresInSec: 60-3600) |
| `--job-executions-rollout-config` | No | structure | None | Rollout config (maximumPerMinute or exponentialRate) |
| `--abort-config` | No | structure | None | Abort criteria list |
| `--timeout-config` | No | structure | None | Timeout in minutes (1-10080) |
| `--tags` | No | list | None | Tags |
| `--namespace-id` | No | string | None | Job namespace ID |
| `--job-template-arn` | No | string | None | Job template ARN |
| `--job-executions-retry-config` | No | structure | None | Retry criteria (failureType, numberOfRetries: 0-10) |
| `--document-parameters` | No | map | None | Template parameters |
| `--scheduling-config` | No | structure | None | Schedule config (startTime, endTime, maintenanceWindows) |
| `--destination-package-versions` | No | list | None | Package version ARNs to install (max 25) |

**Output Schema:**
```json
{
    "jobArn": "string",
    "jobId": "string",
    "description": "string"
}
```

---

## 6.2 `describe-job`

Describes a job.

**Synopsis:**
```bash
aws iot describe-job \
    --job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | Job ID |

**Output Schema:**
```json
{
    "documentSource": "string",
    "job": {
        "jobArn": "string",
        "jobId": "string",
        "targetSelection": "CONTINUOUS|SNAPSHOT",
        "status": "IN_PROGRESS|CANCELED|COMPLETED|DELETION_IN_PROGRESS|SCHEDULED",
        "forceCanceled": "boolean",
        "reasonCode": "string",
        "comment": "string",
        "targets": ["string"],
        "description": "string",
        "presignedUrlConfig": {},
        "jobExecutionsRolloutConfig": {},
        "abortConfig": {},
        "createdAt": "timestamp",
        "lastUpdatedAt": "timestamp",
        "completedAt": "timestamp",
        "jobProcessDetails": {
            "processingTargets": ["string"],
            "numberOfCanceledThings": "integer",
            "numberOfSucceededThings": "integer",
            "numberOfFailedThings": "integer",
            "numberOfRejectedThings": "integer",
            "numberOfQueuedThings": "integer",
            "numberOfInProgressThings": "integer",
            "numberOfRemovedThings": "integer",
            "numberOfTimedOutThings": "integer"
        },
        "timeoutConfig": {},
        "namespaceId": "string",
        "jobTemplateArn": "string",
        "jobExecutionsRetryConfig": {},
        "documentParameters": {},
        "isConcurrent": "boolean",
        "schedulingConfig": {},
        "scheduledJobRollouts": [],
        "destinationPackageVersions": ["string"]
    }
}
```

---

## 6.3 `list-jobs`

Lists jobs. **Paginated operation.**

**Synopsis:**
```bash
aws iot list-jobs \
    [--status <value>] \
    [--target-selection <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--thing-group-name <value>] \
    [--thing-group-id <value>] \
    [--namespace-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--status` | No | string | None | Filter: `IN_PROGRESS`, `CANCELED`, `COMPLETED`, `DELETION_IN_PROGRESS`, `SCHEDULED` |
| `--target-selection` | No | string | None | Filter: `CONTINUOUS` or `SNAPSHOT` |
| `--max-results` | No | integer | None | Max results (1-250) |
| `--next-token` | No | string | None | Pagination token |
| `--thing-group-name` | No | string | None | Filter by thing group |
| `--thing-group-id` | No | string | None | Filter by thing group ID |
| `--namespace-id` | No | string | None | Filter by namespace |

**Output Schema:**
```json
{
    "jobs": [
        {
            "jobArn": "string",
            "jobId": "string",
            "thingGroupId": "string",
            "targetSelection": "CONTINUOUS|SNAPSHOT",
            "status": "string",
            "createdAt": "timestamp",
            "lastUpdatedAt": "timestamp",
            "completedAt": "timestamp",
            "isConcurrent": "boolean"
        }
    ],
    "nextToken": "string"
}
```

---

## 6.4 `update-job`

Updates a job.

**Synopsis:**
```bash
aws iot update-job \
    --job-id <value> \
    [--description <value>] \
    [--presigned-url-config <value>] \
    [--job-executions-rollout-config <value>] \
    [--abort-config <value>] \
    [--timeout-config <value>] \
    [--namespace-id <value>] \
    [--job-executions-retry-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | Job ID |
| `--description` | No | string | None | Updated description |
| `--presigned-url-config` | No | structure | None | Updated URL config |
| `--job-executions-rollout-config` | No | structure | None | Updated rollout config |
| `--abort-config` | No | structure | None | Updated abort config |
| `--timeout-config` | No | structure | None | Updated timeout |
| `--namespace-id` | No | string | None | Namespace ID |
| `--job-executions-retry-config` | No | structure | None | Updated retry config |

**Output:** None

---

## 6.5 `cancel-job`

Cancels a job.

**Synopsis:**
```bash
aws iot cancel-job \
    --job-id <value> \
    [--reason-code <value>] \
    [--comment <value>] \
    [--force | --no-force] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | Job ID |
| `--reason-code` | No | string | None | Reason code |
| `--comment` | No | string | None | Comment (max 2028 chars) |
| `--force` | No | boolean | false | Force cancel (even IN_PROGRESS executions) |

**Output Schema:**
```json
{
    "jobArn": "string",
    "jobId": "string",
    "description": "string"
}
```

---

## 6.6 `delete-job`

Deletes a job and its executions.

**Synopsis:**
```bash
aws iot delete-job \
    --job-id <value> \
    [--force | --no-force] \
    [--namespace-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | Job ID |
| `--force` | No | boolean | false | Force delete (even if IN_PROGRESS) |
| `--namespace-id` | No | string | None | Namespace ID |

**Output:** None

---

## 6.7 `get-job-document`

Gets a job document.

**Synopsis:**
```bash
aws iot get-job-document \
    --job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | Job ID |

**Output Schema:**
```json
{
    "document": "string"
}
```

---

## 6.8 `create-job-template`

Creates a job template from an existing job or configuration.

**Synopsis:**
```bash
aws iot create-job-template \
    --job-template-id <value> \
    --description <value> \
    [--job-arn <value>] \
    [--document-source <value>] \
    [--document <value>] \
    [--presigned-url-config <value>] \
    [--job-executions-rollout-config <value>] \
    [--abort-config <value>] \
    [--timeout-config <value>] \
    [--tags <value>] \
    [--job-executions-retry-config <value>] \
    [--maintenance-windows <value>] \
    [--destination-package-versions <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-template-id` | **Yes** | string | -- | Template ID (1-64 chars) |
| `--description` | **Yes** | string | -- | Template description (max 2028 chars) |
| `--job-arn` | No | string | None | ARN of existing job to use as template |
| `--document-source` | No | string | None | S3 URL of job document |
| `--document` | No | string | None | Job document JSON |
| `--presigned-url-config` | No | structure | None | Pre-signed URL config |
| `--job-executions-rollout-config` | No | structure | None | Rollout config |
| `--abort-config` | No | structure | None | Abort config |
| `--timeout-config` | No | structure | None | Timeout config |
| `--tags` | No | list | None | Tags |
| `--job-executions-retry-config` | No | structure | None | Retry config |
| `--maintenance-windows` | No | list | None | Maintenance windows |
| `--destination-package-versions` | No | list | None | Package version ARNs |

**Output Schema:**
```json
{
    "jobTemplateArn": "string",
    "jobTemplateId": "string"
}
```

---

## 6.9 `describe-job-template`

Describes a job template.

**Synopsis:**
```bash
aws iot describe-job-template \
    --job-template-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-template-id` | **Yes** | string | -- | Template ID |

**Output Schema:**
```json
{
    "jobTemplateArn": "string",
    "jobTemplateId": "string",
    "description": "string",
    "documentSource": "string",
    "document": "string",
    "createdAt": "timestamp",
    "presignedUrlConfig": {},
    "jobExecutionsRolloutConfig": {},
    "abortConfig": {},
    "timeoutConfig": {},
    "jobExecutionsRetryConfig": {},
    "maintenanceWindows": [],
    "destinationPackageVersions": ["string"]
}
```

---

## 6.10 `list-job-templates`

Lists job templates. **Paginated operation.**

**Synopsis:**
```bash
aws iot list-job-templates \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--max-results` | No | integer | None | Max results (1-250) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "jobTemplates": [
        {
            "jobTemplateArn": "string",
            "jobTemplateId": "string",
            "description": "string",
            "createdAt": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

## 6.11 `delete-job-template`

Deletes a job template.

**Synopsis:**
```bash
aws iot delete-job-template \
    --job-template-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-template-id` | **Yes** | string | -- | Template ID |

**Output:** None

---

## 6.12 `describe-managed-job-template`

Describes an AWS managed job template.

**Synopsis:**
```bash
aws iot describe-managed-job-template \
    --template-name <value> \
    [--template-version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--template-name` | **Yes** | string | -- | Managed template name |
| `--template-version` | No | string | None | Template version |

**Output Schema:**
```json
{
    "templateName": "string",
    "templateArn": "string",
    "description": "string",
    "templateVersion": "string",
    "environments": ["string"],
    "documentParameters": [
        {
            "key": "string",
            "description": "string",
            "regex": "string",
            "example": "string",
            "optional": "boolean"
        }
    ],
    "document": "string"
}
```

---

## 6.13 `list-managed-job-templates`

Lists AWS managed job templates.

**Synopsis:**
```bash
aws iot list-managed-job-templates \
    [--template-name <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--template-name` | No | string | None | Filter by template name |
| `--max-results` | No | integer | None | Max results |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "managedJobTemplates": [
        {
            "templateArn": "string",
            "templateName": "string",
            "description": "string",
            "environments": ["string"],
            "templateVersion": "string"
        }
    ],
    "nextToken": "string"
}
```

---

## 6.14 `describe-job-execution`

Describes a job execution on a specific thing (control plane).

**Synopsis:**
```bash
aws iot describe-job-execution \
    --job-id <value> \
    --thing-name <value> \
    [--execution-number <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | Job ID |
| `--thing-name` | **Yes** | string | -- | Thing name |
| `--execution-number` | No | long | None | Execution number |

**Output Schema:**
```json
{
    "execution": {
        "jobId": "string",
        "status": "QUEUED|IN_PROGRESS|SUCCEEDED|FAILED|TIMED_OUT|REJECTED|REMOVED|CANCELED",
        "forceCanceled": "boolean",
        "statusDetails": {"detailsMap": {}},
        "thingArn": "string",
        "queuedAt": "timestamp",
        "startedAt": "timestamp",
        "lastUpdatedAt": "timestamp",
        "executionNumber": "long",
        "versionNumber": "long",
        "approximateSecondsBeforeTimedOut": "long"
    }
}
```

---

## 6.15 `list-job-executions-for-job`

Lists executions for a job. **Paginated operation.**

**Synopsis:**
```bash
aws iot list-job-executions-for-job \
    --job-id <value> \
    [--status <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | Job ID |
| `--status` | No | string | None | Filter by status |
| `--max-results` | No | integer | None | Max results |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "executionSummaries": [
        {
            "thingArn": "string",
            "jobExecutionSummary": {
                "status": "string",
                "queuedAt": "timestamp",
                "startedAt": "timestamp",
                "lastUpdatedAt": "timestamp",
                "executionNumber": "long",
                "retryAttempt": "integer"
            }
        }
    ],
    "nextToken": "string"
}
```

---

## 6.16 `list-job-executions-for-thing`

Lists job executions for a thing. **Paginated operation.**

**Synopsis:**
```bash
aws iot list-job-executions-for-thing \
    --thing-name <value> \
    [--status <value>] \
    [--namespace-id <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--job-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--thing-name` | **Yes** | string | -- | Thing name |
| `--status` | No | string | None | Filter by status |
| `--namespace-id` | No | string | None | Namespace ID |
| `--max-results` | No | integer | None | Max results |
| `--next-token` | No | string | None | Pagination token |
| `--job-id` | No | string | None | Filter by job ID |

**Output Schema:**
```json
{
    "executionSummaries": [
        {
            "jobId": "string",
            "jobExecutionSummary": {
                "status": "string",
                "queuedAt": "timestamp",
                "startedAt": "timestamp",
                "lastUpdatedAt": "timestamp",
                "executionNumber": "long",
                "retryAttempt": "integer"
            }
        }
    ],
    "nextToken": "string"
}
```

---

## 6.17 `cancel-job-execution`

Cancels a job execution on a specific device.

**Synopsis:**
```bash
aws iot cancel-job-execution \
    --job-id <value> \
    --thing-name <value> \
    [--force | --no-force] \
    [--expected-version <value>] \
    [--status-details <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | Job ID |
| `--thing-name` | **Yes** | string | -- | Thing name |
| `--force` | No | boolean | false | Force cancel |
| `--expected-version` | No | long | None | Expected version |
| `--status-details` | No | map | None | Status details |

**Output:** None

---

## 6.18 `delete-job-execution`

Deletes a job execution record.

**Synopsis:**
```bash
aws iot delete-job-execution \
    --job-id <value> \
    --thing-name <value> \
    --execution-number <value> \
    [--force | --no-force] \
    [--namespace-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | Job ID |
| `--thing-name` | **Yes** | string | -- | Thing name |
| `--execution-number` | **Yes** | long | -- | Execution number |
| `--force` | No | boolean | false | Force delete |
| `--namespace-id` | No | string | None | Namespace ID |

**Output:** None

---

## 6.19 `associate-targets-with-job`

Associates thing groups with a continuous job.

**Synopsis:**
```bash
aws iot associate-targets-with-job \
    --targets <value> \
    --job-id <value> \
    [--comment <value>] \
    [--namespace-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--targets` | **Yes** | list | -- | Thing group ARNs to associate |
| `--job-id` | **Yes** | string | -- | Job ID |
| `--comment` | No | string | None | Comment |
| `--namespace-id` | No | string | None | Namespace ID |

**Output Schema:**
```json
{
    "jobArn": "string",
    "jobId": "string",
    "description": "string"
}
```
