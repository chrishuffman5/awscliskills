# Analytics Applications

### 6.1 `create-application`

Creates an Amazon Kinesis Data Analytics application (Apache Flink, SQL, or Zeppelin).

**Synopsis:**
```bash
aws kinesisanalyticsv2 create-application \
    --application-name <value> \
    --runtime-environment <value> \
    --service-execution-role <value> \
    [--application-description <value>] \
    [--application-configuration <value>] \
    [--cloud-watch-logging-options <value>] \
    [--tags <value>] \
    [--application-mode <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | **Yes** | string | -- | Application name (1-128 chars, pattern: `[a-zA-Z0-9_.-]+`) |
| `--runtime-environment` | **Yes** | string | -- | Runtime: `SQL-1_0`, `FLINK-1_6`, `FLINK-1_8`, `FLINK-1_11`, `FLINK-1_13`, `FLINK-1_15`, `FLINK-1_18`, `FLINK-1_19`, `FLINK-1_20`, `ZEPPELIN-FLINK-1_0`, `ZEPPELIN-FLINK-2_0`, `ZEPPELIN-FLINK-3_0` |
| `--service-execution-role` | **Yes** | string | -- | IAM role ARN for the application |
| `--application-description` | No | string | None | Description (0-1024 chars) |
| `--application-configuration` | No | structure | None | Application configuration (see below) |
| `--cloud-watch-logging-options` | No | list | None | CloudWatch log stream ARNs |
| `--tags` | No | list | None | Tags (max 200 total, 50 user-defined) |
| `--application-mode` | No | string | `STREAMING` | `STREAMING` or `INTERACTIVE` |

**Flink Configuration Structure:**
```json
{
    "FlinkApplicationConfiguration": {
        "CheckpointConfiguration": {
            "ConfigurationType": "DEFAULT|CUSTOM",
            "CheckpointingEnabled": true,
            "CheckpointInterval": 60000,
            "MinPauseBetweenCheckpoints": 5000
        },
        "MonitoringConfiguration": {
            "ConfigurationType": "DEFAULT|CUSTOM",
            "MetricsLevel": "APPLICATION|TASK|OPERATOR|PARALLELISM",
            "LogLevel": "INFO|WARN|ERROR|DEBUG"
        },
        "ParallelismConfiguration": {
            "ConfigurationType": "DEFAULT|CUSTOM",
            "Parallelism": 1,
            "ParallelismPerKPU": 1,
            "AutoScalingEnabled": true
        }
    },
    "ApplicationCodeConfiguration": {
        "CodeContent": {
            "S3ContentLocation": {
                "BucketARN": "string",
                "FileKey": "string",
                "ObjectVersion": "string"
            }
        },
        "CodeContentType": "ZIPFILE"
    }
}
```

**Output Schema:**
```json
{
    "ApplicationDetail": {
        "ApplicationARN": "string",
        "ApplicationName": "string",
        "ApplicationDescription": "string",
        "RuntimeEnvironment": "string",
        "ServiceExecutionRole": "string",
        "ApplicationStatus": "DELETING|STARTING|STOPPING|READY|RUNNING|UPDATING|AUTOSCALING|FORCE_STOPPING|ROLLING_BACK|MAINTENANCE|ROLLED_BACK",
        "ApplicationVersionId": "long",
        "CreateTimestamp": "timestamp",
        "LastUpdateTimestamp": "timestamp",
        "ApplicationMode": "STREAMING|INTERACTIVE",
        "ApplicationConfigurationDescription": {},
        "CloudWatchLoggingOptionDescriptions": [
            {
                "CloudWatchLoggingOptionId": "string",
                "LogStreamARN": "string"
            }
        ]
    }
}
```

---

### 6.2 `delete-application`

Deletes an analytics application, including all snapshots.

**Synopsis:**
```bash
aws kinesisanalyticsv2 delete-application \
    --application-name <value> \
    --create-timestamp <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | **Yes** | string | -- | Name of the application to delete |
| `--create-timestamp` | **Yes** | timestamp | -- | Creation timestamp of the application |

**Output:** None

---

### 6.3 `describe-application`

Returns details about an analytics application.

**Synopsis:**
```bash
aws kinesisanalyticsv2 describe-application \
    --application-name <value> \
    [--include-additional-details | --no-include-additional-details] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | **Yes** | string | -- | Name of the application |
| `--include-additional-details` | No | boolean | false | Include VPC and code content details |

**Output Schema:**
```json
{
    "ApplicationDetail": {
        "ApplicationARN": "string",
        "ApplicationName": "string",
        "ApplicationDescription": "string",
        "RuntimeEnvironment": "string",
        "ServiceExecutionRole": "string",
        "ApplicationStatus": "string",
        "ApplicationVersionId": "long",
        "CreateTimestamp": "timestamp",
        "LastUpdateTimestamp": "timestamp",
        "ApplicationMode": "STREAMING|INTERACTIVE",
        "ApplicationConfigurationDescription": {
            "SqlApplicationConfigurationDescription": {
                "InputDescriptions": [],
                "OutputDescriptions": [],
                "ReferenceDataSourceDescriptions": []
            },
            "FlinkApplicationConfigurationDescription": {
                "CheckpointConfigurationDescription": {},
                "MonitoringConfigurationDescription": {},
                "ParallelismConfigurationDescription": {},
                "JobPlanDescription": "string"
            },
            "RunConfigurationDescription": {
                "ApplicationRestoreConfigurationDescription": {
                    "ApplicationRestoreType": "SKIP_RESTORE_FROM_SNAPSHOT|RESTORE_FROM_LATEST_SNAPSHOT|RESTORE_FROM_CUSTOM_SNAPSHOT",
                    "SnapshotName": "string"
                },
                "FlinkRunConfigurationDescription": {
                    "AllowNonRestoredState": "boolean"
                }
            },
            "ApplicationCodeConfigurationDescription": {
                "CodeContentType": "PLAINTEXT|ZIPFILE",
                "CodeContentDescription": {
                    "TextContent": "string",
                    "CodeMD5": "string",
                    "CodeSize": "long",
                    "S3ApplicationCodeLocationDescription": {}
                }
            },
            "VpcConfigurationDescriptions": [
                {
                    "VpcConfigurationId": "string",
                    "VpcId": "string",
                    "SubnetIds": ["string"],
                    "SecurityGroupIds": ["string"]
                }
            ]
        },
        "CloudWatchLoggingOptionDescriptions": []
    }
}
```

---

### 6.4 `list-applications`

Returns a list of analytics applications. **Paginated operation.**

**Synopsis:**
```bash
aws kinesisanalyticsv2 list-applications \
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
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ApplicationSummaries": [
        {
            "ApplicationName": "string",
            "ApplicationARN": "string",
            "ApplicationStatus": "string",
            "ApplicationVersionId": "long",
            "RuntimeEnvironment": "string",
            "ApplicationMode": "STREAMING|INTERACTIVE"
        }
    ],
    "NextToken": "string"
}
```

---

### 6.5 `update-application`

Updates an analytics application configuration, code, or running parameters.

**Synopsis:**
```bash
aws kinesisanalyticsv2 update-application \
    --application-name <value> \
    [--current-application-version-id <value>] \
    [--application-configuration-update <value>] \
    [--service-execution-role-update <value>] \
    [--run-configuration-update <value>] \
    [--cloud-watch-logging-option-updates <value>] \
    [--conditional-token <value>] \
    [--runtime-environment-update <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | **Yes** | string | -- | Name of the application |
| `--current-application-version-id` | No | long | -- | Current application version ID |
| `--application-configuration-update` | No | structure | None | Configuration updates |
| `--service-execution-role-update` | No | string | None | New IAM role ARN |
| `--run-configuration-update` | No | structure | None | Runtime configuration updates |
| `--cloud-watch-logging-option-updates` | No | list | None | CloudWatch logging updates |
| `--conditional-token` | No | string | None | Conditional update token |
| `--runtime-environment-update` | No | string | None | New runtime environment |

**Output Schema:**
```json
{
    "ApplicationDetail": {
        "ApplicationARN": "string",
        "ApplicationName": "string",
        "ApplicationStatus": "string",
        "ApplicationVersionId": "long",
        "ApplicationConfigurationDescription": {}
    }
}
```

---

### 6.6 `start-application`

Starts an analytics application that is in `READY` status.

**Synopsis:**
```bash
aws kinesisanalyticsv2 start-application \
    --application-name <value> \
    [--run-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | **Yes** | string | -- | Name of the application to start |
| `--run-configuration` | No | structure | None | Run configuration (restore type, Flink run config) |

**Run Configuration Structure:**
```json
{
    "FlinkRunConfiguration": {
        "AllowNonRestoredState": true
    },
    "SqlRunConfigurations": [
        {
            "InputId": "string",
            "InputStartingPositionConfiguration": {
                "InputStartingPosition": "NOW|TRIM_HORIZON|LAST_STOPPED_POINT"
            }
        }
    ],
    "ApplicationRestoreConfiguration": {
        "ApplicationRestoreType": "SKIP_RESTORE_FROM_SNAPSHOT|RESTORE_FROM_LATEST_SNAPSHOT|RESTORE_FROM_CUSTOM_SNAPSHOT",
        "SnapshotName": "string"
    }
}
```

**Output:** None (application transitions to `STARTING` then `RUNNING`)

---

### 6.7 `stop-application`

Stops a running analytics application.

**Synopsis:**
```bash
aws kinesisanalyticsv2 stop-application \
    --application-name <value> \
    [--force | --no-force] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | **Yes** | string | -- | Name of the application to stop |
| `--force` | No | boolean | false | Force stop even if application is in an error state |

**Output:** None (application transitions to `STOPPING` then `READY`)

---

### 6.8 `rollback-application`

Rolls back an application to a previous version. Only available for `UPDATING`, `AUTOSCALING`, or `MAINTENANCE` status.

**Synopsis:**
```bash
aws kinesisanalyticsv2 rollback-application \
    --application-name <value> \
    --current-application-version-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | **Yes** | string | -- | Name of the application |
| `--current-application-version-id` | **Yes** | long | -- | Current version ID |

**Output Schema:**
```json
{
    "ApplicationDetail": {
        "ApplicationARN": "string",
        "ApplicationName": "string",
        "ApplicationStatus": "string",
        "ApplicationVersionId": "long"
    }
}
```

---

### 6.9 `describe-application-version`

Describes a specific version of an analytics application.

**Synopsis:**
```bash
aws kinesisanalyticsv2 describe-application-version \
    --application-name <value> \
    --application-version-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | **Yes** | string | -- | Name of the application |
| `--application-version-id` | **Yes** | long | -- | Version ID to describe |

**Output Schema:**
```json
{
    "ApplicationVersionDetail": {
        "ApplicationARN": "string",
        "ApplicationName": "string",
        "ApplicationVersionId": "long",
        "ApplicationStatus": "string",
        "RuntimeEnvironment": "string",
        "CreateTimestamp": "timestamp"
    }
}
```

---

### 6.10 `list-application-versions`

Lists all versions of an analytics application. **Paginated operation.**

**Synopsis:**
```bash
aws kinesisanalyticsv2 list-application-versions \
    --application-name <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | **Yes** | string | -- | Name of the application |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ApplicationVersionSummaries": [
        {
            "ApplicationVersionId": "long",
            "ApplicationStatus": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 6.11 `describe-application-operation`

Describes a specific operation performed on an analytics application.

**Synopsis:**
```bash
aws kinesisanalyticsv2 describe-application-operation \
    --application-name <value> \
    --operation-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | **Yes** | string | -- | Name of the application |
| `--operation-id` | **Yes** | string | -- | Operation ID to describe |

**Output Schema:**
```json
{
    "ApplicationOperationInfoDetail": {
        "Operation": "string",
        "StartTime": "timestamp",
        "EndTime": "timestamp",
        "OperationStatus": "IN_PROGRESS|CANCELLED|SUCCESSFUL|FAILED"
    }
}
```

---

### 6.12 `list-application-operations`

Lists operations performed on an analytics application. **Paginated operation.**

**Synopsis:**
```bash
aws kinesisanalyticsv2 list-application-operations \
    --application-name <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--operation <value>] \
    [--operation-status <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-name` | **Yes** | string | -- | Name of the application |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |
| `--operation` | No | string | None | Filter by operation type |
| `--operation-status` | No | string | None | Filter by status: `IN_PROGRESS`, `CANCELLED`, `SUCCESSFUL`, `FAILED` |

**Output Schema:**
```json
{
    "ApplicationOperationInfoList": [
        {
            "Operation": "string",
            "OperationId": "string",
            "StartTime": "timestamp",
            "EndTime": "timestamp",
            "OperationStatus": "IN_PROGRESS|CANCELLED|SUCCESSFUL|FAILED"
        }
    ],
    "NextToken": "string"
}
```
