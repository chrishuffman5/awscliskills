# Replication Tasks

### 3.1 `create-replication-task`

Creates a replication task using the specified parameters.

**Synopsis:**
```bash
aws dms create-replication-task \
    --replication-task-identifier <value> \
    --source-endpoint-arn <value> \
    --target-endpoint-arn <value> \
    --replication-instance-arn <value> \
    --migration-type <value> \
    --table-mappings <value> \
    [--replication-task-settings <value>] \
    [--cdc-start-time <value>] \
    [--cdc-start-position <value>] \
    [--cdc-stop-position <value>] \
    [--tags <value>] \
    [--task-data <value>] \
    [--resource-identifier <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replication-task-identifier` | **Yes** | string | -- | Task identifier (1-255 alphanumeric/hyphens, starts with letter) |
| `--source-endpoint-arn` | **Yes** | string | -- | ARN of the source endpoint |
| `--target-endpoint-arn` | **Yes** | string | -- | ARN of the target endpoint |
| `--replication-instance-arn` | **Yes** | string | -- | ARN of the replication instance |
| `--migration-type` | **Yes** | string | -- | `full-load`, `cdc`, or `full-load-and-cdc` |
| `--table-mappings` | **Yes** | string | -- | Table mappings in JSON (or `file://` path) |
| `--replication-task-settings` | No | string | -- | Task settings in JSON |
| `--cdc-start-time` | No | timestamp | -- | CDC start time (cannot use with `--cdc-start-position`) |
| `--cdc-start-position` | No | string | -- | CDC start position (cannot use with `--cdc-start-time`) |
| `--cdc-stop-position` | No | string | -- | CDC stop position |
| `--tags` | No | list | -- | Tags: `key=string,value=string ...` |
| `--task-data` | No | string | -- | Supplemental migration data |
| `--resource-identifier` | No | string | Auto-generated | Friendly ARN identifier |

**Output Schema:**
```json
{
    "ReplicationTask": {
        "ReplicationTaskIdentifier": "string",
        "SourceEndpointArn": "string",
        "TargetEndpointArn": "string",
        "ReplicationInstanceArn": "string",
        "MigrationType": "full-load|cdc|full-load-and-cdc",
        "TableMappings": "string",
        "ReplicationTaskSettings": "string",
        "Status": "string",
        "LastFailureMessage": "string",
        "StopReason": "string",
        "ReplicationTaskCreationDate": "timestamp",
        "ReplicationTaskStartDate": "timestamp",
        "CdcStartPosition": "string",
        "CdcStopPosition": "string",
        "RecoveryCheckpoint": "string",
        "ReplicationTaskArn": "string",
        "ReplicationTaskStats": {
            "FullLoadProgressPercent": "integer",
            "ElapsedTimeMillis": "long",
            "TablesLoaded": "integer",
            "TablesLoading": "integer",
            "TablesQueued": "integer",
            "TablesErrored": "integer",
            "FreshStartDate": "timestamp",
            "StartDate": "timestamp",
            "StopDate": "timestamp",
            "FullLoadStartDate": "timestamp",
            "FullLoadFinishDate": "timestamp"
        },
        "TaskData": "string",
        "TargetReplicationInstanceArn": "string"
    }
}
```

---

### 3.2 `delete-replication-task`

Deletes the specified replication task.

**Synopsis:**
```bash
aws dms delete-replication-task \
    --replication-task-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replication-task-arn` | **Yes** | string | -- | ARN of the replication task to delete |

**Output Schema:** Same as `create-replication-task`.

---

### 3.3 `describe-replication-tasks`

Returns information about replication tasks. **Paginated operation.**

**Synopsis:**
```bash
aws dms describe-replication-tasks \
    [--filters <value>] \
    [--without-settings | --no-without-settings] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | list | -- | Filters: `replication-task-arn`, `replication-task-id`, `migration-type`, `endpoint-arn`, `replication-instance-arn` |
| `--without-settings` | No | boolean | false | Omit task settings to reduce overhead |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "Marker": "string",
    "ReplicationTasks": [
        {
            "ReplicationTaskIdentifier": "string",
            "SourceEndpointArn": "string",
            "TargetEndpointArn": "string",
            "ReplicationInstanceArn": "string",
            "MigrationType": "string",
            "TableMappings": "string",
            "ReplicationTaskSettings": "string",
            "Status": "string",
            "LastFailureMessage": "string",
            "StopReason": "string",
            "ReplicationTaskCreationDate": "timestamp",
            "ReplicationTaskStartDate": "timestamp",
            "CdcStartPosition": "string",
            "CdcStopPosition": "string",
            "RecoveryCheckpoint": "string",
            "ReplicationTaskArn": "string",
            "ReplicationTaskStats": {}
        }
    ]
}
```

---

### 3.4 `modify-replication-task`

Modifies the specified replication task.

**Synopsis:**
```bash
aws dms modify-replication-task \
    --replication-task-arn <value> \
    [--replication-task-identifier <value>] \
    [--migration-type <value>] \
    [--table-mappings <value>] \
    [--replication-task-settings <value>] \
    [--cdc-start-time <value>] \
    [--cdc-start-position <value>] \
    [--cdc-stop-position <value>] \
    [--task-data <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replication-task-arn` | **Yes** | string | -- | ARN of the replication task |
| `--replication-task-identifier` | No | string | -- | New task identifier |
| `--migration-type` | No | string | -- | New migration type |
| `--table-mappings` | No | string | -- | New table mappings |
| `--replication-task-settings` | No | string | -- | New task settings |
| `--cdc-start-time` | No | timestamp | -- | New CDC start time |
| `--cdc-start-position` | No | string | -- | New CDC start position |
| `--cdc-stop-position` | No | string | -- | New CDC stop position |
| `--task-data` | No | string | -- | New supplemental task data |

**Output Schema:** Same as `create-replication-task`.

---

### 3.5 `move-replication-task`

Moves a replication task from its current replication instance to a different target replication instance.

**Synopsis:**
```bash
aws dms move-replication-task \
    --replication-task-arn <value> \
    --target-replication-instance-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replication-task-arn` | **Yes** | string | -- | ARN of the task to move |
| `--target-replication-instance-arn` | **Yes** | string | -- | ARN of the target replication instance |

**Output Schema:** Same as `create-replication-task`.

---

### 3.6 `start-replication-task`

Starts the replication task.

**Synopsis:**
```bash
aws dms start-replication-task \
    --replication-task-arn <value> \
    --start-replication-task-type <value> \
    [--cdc-start-time <value>] \
    [--cdc-start-position <value>] \
    [--cdc-stop-position <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replication-task-arn` | **Yes** | string | -- | ARN of the replication task |
| `--start-replication-task-type` | **Yes** | string | -- | `start-replication`, `resume-processing`, or `reload-target` |
| `--cdc-start-time` | No | timestamp | -- | CDC start time |
| `--cdc-start-position` | No | string | -- | CDC start position |
| `--cdc-stop-position` | No | string | -- | CDC stop position |

**Output Schema:** Same as `create-replication-task`.

---

### 3.7 `stop-replication-task`

Stops the replication task.

**Synopsis:**
```bash
aws dms stop-replication-task \
    --replication-task-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replication-task-arn` | **Yes** | string | -- | ARN of the replication task to stop |

**Output Schema:** Same as `create-replication-task`.

---

### 3.8 `reload-tables`

Reloads the target database table with the source data.

**Synopsis:**
```bash
aws dms reload-tables \
    --replication-task-arn <value> \
    --tables-to-reload <value> \
    [--reload-option <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replication-task-arn` | **Yes** | string | -- | ARN of the replication task |
| `--tables-to-reload` | **Yes** | list | -- | Tables to reload: `SchemaName=string,TableName=string ...` |
| `--reload-option` | No | string | `data-reload` | `data-reload` or `validate-only` |

**Output Schema:**
```json
{
    "ReplicationTaskArn": "string"
}
```

---

### 3.9 `describe-table-statistics`

Returns table statistics on the database migration task. **Paginated operation.**

**Synopsis:**
```bash
aws dms describe-table-statistics \
    --replication-task-arn <value> \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replication-task-arn` | **Yes** | string | -- | ARN of the replication task |
| `--filters` | No | list | -- | Filters: `schema-name`, `table-name`, `table-state` |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "ReplicationTaskArn": "string",
    "TableStatistics": [
        {
            "SchemaName": "string",
            "TableName": "string",
            "Inserts": "long",
            "Deletes": "long",
            "Updates": "long",
            "Ddls": "long",
            "AppliedInserts": "long",
            "AppliedDeletes": "long",
            "AppliedUpdates": "long",
            "AppliedDdls": "long",
            "FullLoadRows": "long",
            "FullLoadCondtnlChkFailedRows": "long",
            "FullLoadErrorRows": "long",
            "FullLoadStartTime": "timestamp",
            "FullLoadEndTime": "timestamp",
            "FullLoadReloaded": "boolean",
            "LastUpdateTime": "timestamp",
            "TableState": "string",
            "ValidationPendingRecords": "long",
            "ValidationFailedRecords": "long",
            "ValidationSuspendedRecords": "long",
            "ValidationState": "string",
            "ValidationStateDetails": "string"
        }
    ],
    "Marker": "string"
}
```

---

### 3.10 `start-replication-task-assessment`

Starts the replication task assessment for unsupported data types in the source database.

**Synopsis:**
```bash
aws dms start-replication-task-assessment \
    --replication-task-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replication-task-arn` | **Yes** | string | -- | ARN of the replication task |

**Output Schema:** Same as `create-replication-task`.

---

### 3.11 `start-replication-task-assessment-run`

Starts a new premigration assessment run for one or more individual assessments.

**Synopsis:**
```bash
aws dms start-replication-task-assessment-run \
    --replication-task-arn <value> \
    --service-access-role-arn <value> \
    --result-location-bucket <value> \
    --assessment-run-name <value> \
    [--result-location-folder <value>] \
    [--result-encryption-mode <value>] \
    [--result-kms-key-arn <value>] \
    [--include-only <value>] \
    [--exclude <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replication-task-arn` | **Yes** | string | -- | ARN of the replication task |
| `--service-access-role-arn` | **Yes** | string | -- | IAM role ARN for S3 results access |
| `--result-location-bucket` | **Yes** | string | -- | S3 bucket for assessment results |
| `--assessment-run-name` | **Yes** | string | -- | Unique name for this assessment run |
| `--result-location-folder` | No | string | -- | S3 folder prefix for results |
| `--result-encryption-mode` | No | string | `SSE_S3` | `SSE_S3` or `SSE_KMS` |
| `--result-kms-key-arn` | No | string | -- | KMS key ARN (required if `SSE_KMS`) |
| `--include-only` | No | list(string) | -- | Run only these assessments |
| `--exclude` | No | list(string) | -- | Exclude these assessments |
| `--tags` | No | list | -- | Tags |

**Output Schema:**
```json
{
    "ReplicationTaskAssessmentRun": {
        "ReplicationTaskAssessmentRunArn": "string",
        "ReplicationTaskArn": "string",
        "Status": "string",
        "ReplicationTaskAssessmentRunCreationDate": "timestamp",
        "AssessmentProgress": {
            "IndividualAssessmentCount": "integer",
            "IndividualAssessmentCompletedCount": "integer"
        },
        "LastFailureMessage": "string",
        "ServiceAccessRoleArn": "string",
        "ResultLocationBucket": "string",
        "ResultLocationFolder": "string",
        "ResultEncryptionMode": "string",
        "ResultKmsKeyArn": "string",
        "AssessmentRunName": "string",
        "IsLatestTaskAssessmentRun": "boolean",
        "ResultStatistic": {
            "Passed": "integer",
            "Failed": "integer",
            "Error": "integer",
            "Warning": "integer",
            "Cancelled": "integer"
        }
    }
}
```

---

### 3.12 `cancel-replication-task-assessment-run`

Cancels a single premigration assessment run.

**Synopsis:**
```bash
aws dms cancel-replication-task-assessment-run \
    --replication-task-assessment-run-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replication-task-assessment-run-arn` | **Yes** | string | -- | ARN of the assessment run to cancel |

**Output Schema:** Same as `start-replication-task-assessment-run`.

---

### 3.13 `delete-replication-task-assessment-run`

Deletes the record of a single premigration assessment run.

**Synopsis:**
```bash
aws dms delete-replication-task-assessment-run \
    --replication-task-assessment-run-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replication-task-assessment-run-arn` | **Yes** | string | -- | ARN of the assessment run to delete |

**Output Schema:** Same as `start-replication-task-assessment-run`.

---

### 3.14 `describe-replication-task-assessment-results`

Returns the task assessment results. **Paginated operation.**

**Synopsis:**
```bash
aws dms describe-replication-task-assessment-results \
    [--replication-task-arn <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replication-task-arn` | No | string | -- | ARN of the replication task (omit for all) |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "Marker": "string",
    "BucketName": "string",
    "ReplicationTaskAssessmentResults": [
        {
            "ReplicationTaskIdentifier": "string",
            "ReplicationTaskArn": "string",
            "ReplicationTaskLastAssessmentDate": "timestamp",
            "AssessmentStatus": "string",
            "AssessmentResultsFile": "string",
            "AssessmentResults": "string",
            "S3ObjectUrl": "string"
        }
    ]
}
```

---

### 3.15 `describe-replication-task-assessment-runs`

Returns a paginated list of premigration assessment runs. **Paginated operation.**

**Synopsis:**
```bash
aws dms describe-replication-task-assessment-runs \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | list | -- | Filters: `replication-task-assessment-run-arn`, `replication-task-arn`, `replication-instance-arn`, `status` |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "Marker": "string",
    "ReplicationTaskAssessmentRuns": [
        {
            "ReplicationTaskAssessmentRunArn": "string",
            "ReplicationTaskArn": "string",
            "Status": "string",
            "ReplicationTaskAssessmentRunCreationDate": "timestamp",
            "AssessmentProgress": {},
            "LastFailureMessage": "string",
            "ServiceAccessRoleArn": "string",
            "ResultLocationBucket": "string",
            "ResultLocationFolder": "string",
            "ResultEncryptionMode": "string",
            "ResultKmsKeyArn": "string",
            "AssessmentRunName": "string",
            "IsLatestTaskAssessmentRun": "boolean",
            "ResultStatistic": {}
        }
    ]
}
```

---

### 3.16 `describe-replication-task-individual-assessments`

Returns a paginated list of individual assessments based on filter settings. **Paginated operation.**

**Synopsis:**
```bash
aws dms describe-replication-task-individual-assessments \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | list | -- | Filters: `replication-task-assessment-run-arn`, `replication-task-individual-assessment-arn`, `status` |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "Marker": "string",
    "ReplicationTaskIndividualAssessments": [
        {
            "ReplicationTaskIndividualAssessmentArn": "string",
            "ReplicationTaskAssessmentRunArn": "string",
            "IndividualAssessmentName": "string",
            "Status": "string",
            "ReplicationTaskIndividualAssessmentStartDate": "timestamp"
        }
    ]
}
```

---

### 3.17 `describe-applicable-individual-assessments`

Lists individual assessments that you can specify for a new premigration assessment run. **Paginated operation.**

**Synopsis:**
```bash
aws dms describe-applicable-individual-assessments \
    [--replication-task-arn <value>] \
    [--replication-instance-arn <value>] \
    [--source-engine-name <value>] \
    [--target-engine-name <value>] \
    [--migration-type <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replication-task-arn` | No | string | -- | ARN of the replication task |
| `--replication-instance-arn` | No | string | -- | ARN of the replication instance |
| `--source-engine-name` | No | string | -- | Source engine name |
| `--target-engine-name` | No | string | -- | Target engine name |
| `--migration-type` | No | string | -- | Migration type |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "IndividualAssessmentNames": ["string"],
    "Marker": "string"
}
```
