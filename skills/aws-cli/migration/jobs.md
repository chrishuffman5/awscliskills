# Jobs

### 8.1 `describe-jobs`

Describes migration jobs (launch and terminate). **Paginated.**

**Synopsis:**
```bash
aws mgn describe-jobs \
    [--filters <value>] \
    [--account-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | structure | None | Filter criteria (see below) |
| `--account-id` | No | string | None | Account ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Filters Structure:**
```json
{
    "jobIDs": ["string"],
    "fromDate": "string",
    "toDate": "string"
}
```

**Output Schema:**
```json
{
    "items": [
        {
            "jobID": "string",
            "arn": "string",
            "type": "LAUNCH|TERMINATE",
            "initiatedBy": "START_TEST|START_CUTOVER|DIAGNOSTIC|TERMINATE",
            "status": "PENDING|STARTED|COMPLETED",
            "creationDateTime": "string",
            "endDateTime": "string",
            "participatingServers": [
                {
                    "sourceServerID": "string",
                    "launchStatus": "PENDING|IN_PROGRESS|LAUNCHED|FAILED|TERMINATED",
                    "launchedEc2InstanceID": "string",
                    "postLaunchActionsStatus": {
                        "ssmAgentDiscoveryDatetime": "string",
                        "postLaunchActionsLaunchStatusList": [
                            {
                                "ssmDocument": {},
                                "ssmDocumentType": "AUTOMATION|COMMAND",
                                "executionID": "string",
                                "executionStatus": "string",
                                "failureReason": "string"
                            }
                        ]
                    }
                }
            ],
            "tags": {"key": "value"}
        }
    ],
    "nextToken": "string"
}
```

---

### 8.2 `describe-job-log-items`

Describes job log items for a specific job. **Paginated.**

**Synopsis:**
```bash
aws mgn describe-job-log-items \
    --job-id <value> \
    [--account-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | Job ID |
| `--account-id` | No | string | None | Account ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "items": [
        {
            "logDateTime": "string",
            "event": "JOB_START|SERVER_SKIPPED|CLEANUP_START|CLEANUP_END|CLEANUP_FAIL|SNAPSHOT_START|SNAPSHOT_END|SNAPSHOT_FAIL|USING_PREVIOUS_SNAPSHOT|CONVERSION_START|CONVERSION_END|CONVERSION_FAIL|LAUNCH_START|LAUNCH_FAILED|JOB_CANCEL|JOB_END",
            "eventData": {
                "sourceServerID": "string",
                "conversionServerID": "string",
                "targetInstanceID": "string",
                "rawError": "string"
            }
        }
    ],
    "nextToken": "string"
}
```

---

### 8.3 `delete-job`

Deletes a job record.

**Synopsis:**
```bash
aws mgn delete-job \
    --job-id <value> \
    [--account-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | Job ID |
| `--account-id` | No | string | None | Account ID |

**Output:** None
