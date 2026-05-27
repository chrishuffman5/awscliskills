# Jobs

### 7.1 `describe-jobs`

Returns a list of DRS jobs. You can optionally filter by job ID. **Paginated operation.**

**Synopsis:**
```bash
aws drs describe-jobs \
    --filters <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | **Yes** | structure | -- | Filters for jobs |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Maximum items |

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
            "type": "LAUNCH|TERMINATE|CREATE_CONVERTED_SNAPSHOT",
            "initiatedBy": "START_RECOVERY|START_DRILL|FAILBACK|DIAGNOSTIC|TERMINATE_RECOVERY_INSTANCES|TARGET_ACCOUNT|CREATE_NETWORK_RECOVERY|UPDATE_NETWORK_RECOVERY|ASSOCIATE_NETWORK_RECOVERY",
            "creationDateTime": "string",
            "endDateTime": "string",
            "status": "PENDING|STARTED|COMPLETED",
            "participatingServers": [
                {
                    "sourceServerID": "string",
                    "recoveryInstanceID": "string",
                    "launchStatus": "PENDING|IN_PROGRESS|LAUNCHED|FAILED|TERMINATED",
                    "launchActionsStatus": {
                        "ssmAgentDiscoveryDatetime": "string",
                        "runs": [
                            {
                                "action": {},
                                "runId": "string",
                                "status": "IN_PROGRESS|SUCCEEDED|FAILED"
                            }
                        ]
                    }
                }
            ],
            "participatingResources": [
                {
                    "participatingResourceID": {
                        "sourceNetworkID": "string"
                    },
                    "launchStatus": "PENDING|IN_PROGRESS|LAUNCHED|FAILED|TERMINATED"
                }
            ],
            "tags": {}
        }
    ],
    "nextToken": "string"
}
```

---

### 7.2 `delete-job`

Deletes a single DRS job by ID.

**Synopsis:**
```bash
aws drs delete-job \
    --job-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--job-id` | **Yes** | string | -- | Job ID to delete |

**Output Schema:**
```json
{}
```

---

### 7.3 `describe-job-log-items`

Retrieves a detailed job log with pagination. **Paginated operation.**

**Synopsis:**
```bash
aws drs describe-job-log-items \
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
| `--job-id` | **Yes** | string | -- | Job ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Maximum items |

**Output Schema:**
```json
{
    "items": [
        {
            "logDateTime": "string",
            "event": "JOB_START|SERVER_SKIPPED|CLEANUP_START|CLEANUP_END|CLEANUP_FAIL|SNAPSHOT_START|SNAPSHOT_END|SNAPSHOT_FAIL|USING_PREVIOUS_SNAPSHOT|USING_PREVIOUS_SNAPSHOT_FAILED|CONVERSION_START|CONVERSION_END|CONVERSION_FAIL|LAUNCH_START|LAUNCH_FAILED|JOB_CANCEL|JOB_END|DEPLOY_NETWORK_CONFIGURATION_START|DEPLOY_NETWORK_CONFIGURATION_END|DEPLOY_NETWORK_CONFIGURATION_FAILED|UPDATE_NETWORK_CONFIGURATION_START|UPDATE_NETWORK_CONFIGURATION_END|UPDATE_NETWORK_CONFIGURATION_FAILED|UPDATE_LAUNCH_TEMPLATE_START|UPDATE_LAUNCH_TEMPLATE_END|UPDATE_LAUNCH_TEMPLATE_FAILED|NETWORK_RECOVERY_FAIL",
            "eventData": {
                "sourceServerID": "string",
                "conversionServerID": "string",
                "targetInstanceID": "string",
                "rawError": "string",
                "eventResourceData": {}
            }
        }
    ],
    "nextToken": "string"
}
```

---

### 7.4 `list-staging-accounts`

Returns an array of staging accounts for existing extended source servers. **Paginated operation.**

**Synopsis:**
```bash
aws drs list-staging-accounts \
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
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Maximum items |

**Output Schema:**
```json
{
    "accounts": [
        {
            "accountID": "string"
        }
    ],
    "nextToken": "string"
}
```
