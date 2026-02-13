# Environments

### 1.1 `create-environment`

Creates a new Amazon MWAA environment.

**Synopsis:**
```bash
aws mwaa create-environment \
    --name <value> \
    --execution-role-arn <value> \
    --source-bucket-arn <value> \
    --dag-s3-path <value> \
    --network-configuration <value> \
    [--plugins-s3-path <value>] \
    [--plugins-s3-object-version <value>] \
    [--requirements-s3-path <value>] \
    [--requirements-s3-object-version <value>] \
    [--startup-script-s3-path <value>] \
    [--startup-script-s3-object-version <value>] \
    [--airflow-configuration-options <value>] \
    [--environment-class <value>] \
    [--max-workers <value>] \
    [--min-workers <value>] \
    [--schedulers <value>] \
    [--min-webservers <value>] \
    [--max-webservers <value>] \
    [--kms-key <value>] \
    [--airflow-version <value>] \
    [--logging-configuration <value>] \
    [--weekly-maintenance-window-start <value>] \
    [--tags <value>] \
    [--webserver-access-mode <value>] \
    [--endpoint-management <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Environment name (1-80 chars, starts with letter) |
| `--execution-role-arn` | **Yes** | string | -- | IAM execution role ARN for the environment |
| `--source-bucket-arn` | **Yes** | string | -- | S3 bucket ARN for DAG code and supporting files |
| `--dag-s3-path` | **Yes** | string | -- | Relative path to DAGs folder on S3 (e.g., `dags`) |
| `--network-configuration` | **Yes** | structure | -- | VPC networking: SubnetIds (2 required), SecurityGroupIds (1-5) |
| `--plugins-s3-path` | No | string | None | Path to `plugins.zip` on S3 |
| `--plugins-s3-object-version` | No | string | None | S3 version ID of `plugins.zip` |
| `--requirements-s3-path` | No | string | None | Path to `requirements.txt` on S3 |
| `--requirements-s3-object-version` | No | string | None | S3 version ID of `requirements.txt` |
| `--startup-script-s3-path` | No | string | None | Path to startup shell script on S3 |
| `--startup-script-s3-object-version` | No | string | None | S3 version ID of startup script |
| `--airflow-configuration-options` | No | map | None | Key-value pairs for Apache Airflow configuration overrides |
| `--environment-class` | No | string | `mw1.small` | Size: `mw1.micro`, `mw1.small`, `mw1.medium`, `mw1.large`, `mw1.xlarge`, `mw1.2xlarge` |
| `--max-workers` | No | integer | 10 | Maximum number of workers (min: 1) |
| `--min-workers` | No | integer | 1 | Minimum number of workers (min: 1) |
| `--schedulers` | No | integer | 2 | Number of schedulers (max: 5) |
| `--min-webservers` | No | integer | 2 | Minimum number of web servers |
| `--max-webservers` | No | integer | 2 | Maximum number of web servers |
| `--kms-key` | No | string | None | KMS key ARN for encryption (AWS-owned key used if not specified) |
| `--airflow-version` | No | string | latest | Apache Airflow version (e.g., `2.10.3`, `2.9.2`) |
| `--logging-configuration` | No | structure | None | CloudWatch Logs configuration per log type |
| `--weekly-maintenance-window-start` | No | string | random | Maintenance window in `DAY:HH:MM` UTC format (e.g., `TUE:03:30`) |
| `--tags` | No | map | None | Key-value tag pairs |
| `--webserver-access-mode` | No | string | `PRIVATE_ONLY` | Access mode: `PRIVATE_ONLY` or `PUBLIC_ONLY` |
| `--endpoint-management` | No | string | `SERVICE` | VPC endpoint management: `SERVICE` or `CUSTOMER` |

**Network Configuration Structure:**
```json
{
    "SubnetIds": ["subnet-aaa", "subnet-bbb"],
    "SecurityGroupIds": ["sg-ccc"]
}
```

**Logging Configuration Structure:**
```json
{
    "DagProcessingLogs": {
        "Enabled": true,
        "LogLevel": "INFO"
    },
    "SchedulerLogs": {
        "Enabled": true,
        "LogLevel": "INFO"
    },
    "WebserverLogs": {
        "Enabled": true,
        "LogLevel": "INFO"
    },
    "WorkerLogs": {
        "Enabled": true,
        "LogLevel": "INFO"
    },
    "TaskLogs": {
        "Enabled": true,
        "LogLevel": "INFO"
    }
}
```

Log levels: `CRITICAL`, `ERROR`, `WARNING`, `INFO`, `DEBUG`

**Output Schema:**
```json
{
    "Arn": "string"
}
```

---

### 1.2 `get-environment`

Retrieves details about an Amazon MWAA environment.

**Synopsis:**
```bash
aws mwaa get-environment \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Environment name (1-80 chars) |

**Output Schema:**
```json
{
    "Environment": {
        "Name": "string",
        "Status": "CREATING|CREATE_FAILED|AVAILABLE|UPDATING|DELETING|DELETED|UNAVAILABLE|UPDATE_FAILED|ROLLING_BACK|CREATING_SNAPSHOT|PENDING|MAINTENANCE",
        "Arn": "string",
        "CreatedAt": "timestamp",
        "WebserverUrl": "string",
        "ExecutionRoleArn": "string",
        "ServiceRoleArn": "string",
        "KmsKey": "string",
        "AirflowVersion": "string",
        "SourceBucketArn": "string",
        "DagS3Path": "string",
        "PluginsS3Path": "string",
        "PluginsS3ObjectVersion": "string",
        "RequirementsS3Path": "string",
        "RequirementsS3ObjectVersion": "string",
        "StartupScriptS3Path": "string",
        "StartupScriptS3ObjectVersion": "string",
        "AirflowConfigurationOptions": {
            "key": "string"
        },
        "EnvironmentClass": "string",
        "MaxWorkers": "integer",
        "MinWorkers": "integer",
        "Schedulers": "integer",
        "MinWebservers": "integer",
        "MaxWebservers": "integer",
        "NetworkConfiguration": {
            "SubnetIds": ["string"],
            "SecurityGroupIds": ["string"]
        },
        "LoggingConfiguration": {
            "DagProcessingLogs": {
                "Enabled": "boolean",
                "LogLevel": "CRITICAL|ERROR|WARNING|INFO|DEBUG",
                "CloudWatchLogGroupArn": "string"
            },
            "SchedulerLogs": {
                "Enabled": "boolean",
                "LogLevel": "string",
                "CloudWatchLogGroupArn": "string"
            },
            "WebserverLogs": {
                "Enabled": "boolean",
                "LogLevel": "string",
                "CloudWatchLogGroupArn": "string"
            },
            "WorkerLogs": {
                "Enabled": "boolean",
                "LogLevel": "string",
                "CloudWatchLogGroupArn": "string"
            },
            "TaskLogs": {
                "Enabled": "boolean",
                "LogLevel": "string",
                "CloudWatchLogGroupArn": "string"
            }
        },
        "LastUpdate": {
            "Status": "SUCCESS|PENDING|FAILED",
            "CreatedAt": "timestamp",
            "Error": {
                "ErrorCode": "string",
                "ErrorMessage": "string"
            },
            "Source": "string"
        },
        "WeeklyMaintenanceWindowStart": "string",
        "Tags": {
            "key": "string"
        },
        "WebserverAccessMode": "PRIVATE_ONLY|PUBLIC_ONLY",
        "WebserverVpcEndpointService": "string",
        "DatabaseVpcEndpointService": "string",
        "CeleryExecutorQueue": "string",
        "EndpointManagement": "CUSTOMER|SERVICE"
    }
}
```

---

### 1.3 `update-environment`

Updates an Amazon MWAA environment.

**Synopsis:**
```bash
aws mwaa update-environment \
    --name <value> \
    [--execution-role-arn <value>] \
    [--source-bucket-arn <value>] \
    [--dag-s3-path <value>] \
    [--plugins-s3-path <value>] \
    [--plugins-s3-object-version <value>] \
    [--requirements-s3-path <value>] \
    [--requirements-s3-object-version <value>] \
    [--startup-script-s3-path <value>] \
    [--startup-script-s3-object-version <value>] \
    [--airflow-configuration-options <value>] \
    [--environment-class <value>] \
    [--max-workers <value>] \
    [--min-workers <value>] \
    [--schedulers <value>] \
    [--min-webservers <value>] \
    [--max-webservers <value>] \
    [--airflow-version <value>] \
    [--logging-configuration <value>] \
    [--weekly-maintenance-window-start <value>] \
    [--webserver-access-mode <value>] \
    [--network-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Environment name (1-80 chars) |
| `--execution-role-arn` | No | string | unchanged | IAM execution role ARN |
| `--source-bucket-arn` | No | string | unchanged | S3 bucket ARN for DAG code |
| `--dag-s3-path` | No | string | unchanged | Relative path to DAGs folder |
| `--plugins-s3-path` | No | string | unchanged | Path to `plugins.zip` on S3 |
| `--plugins-s3-object-version` | No | string | unchanged | S3 version ID of `plugins.zip` |
| `--requirements-s3-path` | No | string | unchanged | Path to `requirements.txt` on S3 |
| `--requirements-s3-object-version` | No | string | unchanged | S3 version ID of `requirements.txt` |
| `--startup-script-s3-path` | No | string | unchanged | Path to startup script on S3 |
| `--startup-script-s3-object-version` | No | string | unchanged | S3 version ID of startup script |
| `--airflow-configuration-options` | No | map | unchanged | Airflow configuration overrides |
| `--environment-class` | No | string | unchanged | Environment size class |
| `--max-workers` | No | integer | unchanged | Maximum number of workers |
| `--min-workers` | No | integer | unchanged | Minimum number of workers |
| `--schedulers` | No | integer | unchanged | Number of schedulers (max: 5) |
| `--min-webservers` | No | integer | unchanged | Minimum web servers |
| `--max-webservers` | No | integer | unchanged | Maximum web servers |
| `--airflow-version` | No | string | unchanged | Apache Airflow version |
| `--logging-configuration` | No | structure | unchanged | CloudWatch Logs configuration |
| `--weekly-maintenance-window-start` | No | string | unchanged | Maintenance window (`DAY:HH:MM`) |
| `--webserver-access-mode` | No | string | unchanged | `PRIVATE_ONLY` or `PUBLIC_ONLY` |
| `--network-configuration` | No | structure | unchanged | VPC security group IDs to update |

**Output Schema:**
```json
{
    "Arn": "string"
}
```

---

### 1.4 `delete-environment`

Deletes an Amazon MWAA environment.

**Synopsis:**
```bash
aws mwaa delete-environment \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Environment name to delete |

**Output Schema:**
```json
{}
```

---

### 1.5 `list-environments`

Lists all Amazon MWAA environments in a region. **Paginated operation.**

**Synopsis:**
```bash
aws mwaa list-environments \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Environments": ["string"],
    "NextToken": "string"
}
```
