# Runs

### 3.1 `schedule-run`

Schedules a run (test execution).

**Synopsis:**
```bash
aws devicefarm schedule-run \
    --project-arn <value> \
    --test <value> \
    [--app-arn <value>] \
    [--device-pool-arn <value>] \
    [--device-selection-configuration <value>] \
    [--name <value>] \
    [--configuration <value>] \
    [--execution-configuration <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project-arn` | **Yes** | string | -- | ARN of the project |
| `--test` | **Yes** | structure | -- | Test configuration. Shorthand: `type=string,testPackageArn=string,testSpecArn=string,filter=string,parameters={KeyName1=string,KeyName2=string}` |
| `--app-arn` | No | string | None | ARN of the app to test |
| `--device-pool-arn` | No | string | None | ARN of the device pool (required if no device-selection-configuration) |
| `--device-selection-configuration` | No | structure | None | Device selection configuration (alternative to device-pool-arn) |
| `--name` | No | string | None | Name of the run |
| `--configuration` | No | structure | None | Run configuration (locale, location, network, etc.) |
| `--execution-configuration` | No | structure | None | Execution configuration. Shorthand: `jobTimeoutMinutes=integer,accountsCleanup=boolean,appPackagesCleanup=boolean,videoCapture=boolean,skipAppResign=boolean` |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |

**Test Types:** `BUILTIN_FUZZ`, `BUILTIN_EXPLORER`, `WEB_PERFORMANCE_PROFILE`, `APPIUM_JAVA_JUNIT`, `APPIUM_JAVA_TESTNG`, `APPIUM_PYTHON`, `APPIUM_NODE`, `APPIUM_RUBY`, `APPIUM_WEB_JAVA_JUNIT`, `APPIUM_WEB_JAVA_TESTNG`, `APPIUM_WEB_PYTHON`, `APPIUM_WEB_NODE`, `APPIUM_WEB_RUBY`, `CALABASH`, `INSTRUMENTATION`, `UIAUTOMATION`, `UIAUTOMATOR`, `XCTEST`, `XCTEST_UI`, `REMOTE_ACCESS_RECORD`, `REMOTE_ACCESS_REPLAY`

**Output Schema:**
```json
{
    "run": {
        "arn": "string",
        "name": "string",
        "type": "string",
        "platform": "ANDROID|IOS",
        "created": "timestamp",
        "status": "PENDING|PENDING_CONCURRENCY|PENDING_DEVICE|PROCESSING|SCHEDULING|PREPARING|RUNNING|COMPLETED|STOPPING",
        "result": "PENDING|PASSED|WARNED|FAILED|SKIPPED|ERRORED|STOPPED",
        "started": "timestamp",
        "stopped": "timestamp",
        "counters": {
            "total": "integer",
            "passed": "integer",
            "failed": "integer",
            "warned": "integer",
            "errored": "integer",
            "stopped": "integer",
            "skipped": "integer"
        },
        "message": "string",
        "totalJobs": "integer",
        "completedJobs": "integer",
        "billingMethod": "METERED|UNMETERED",
        "deviceMinutes": {
            "total": "double",
            "metered": "double",
            "unmetered": "double"
        },
        "networkProfile": {},
        "parsingResultUrl": "string",
        "resultCode": "PARSING_FAILED|VPC_ENDPOINT_SETUP_FAILED",
        "seed": "integer",
        "appUpload": "string",
        "eventCount": "integer",
        "jobTimeoutMinutes": "integer",
        "devicePoolArn": "string",
        "locale": "string",
        "radios": {},
        "location": {},
        "customerArtifactPaths": {},
        "webUrl": "string",
        "skipAppResign": "boolean",
        "testSpecArn": "string",
        "deviceSelectionResult": {}
    }
}
```

---

### 3.2 `stop-run`

Initiates a stop request for the current test run.

**Synopsis:**
```bash
aws devicefarm stop-run \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the run to stop |

**Output Schema:**
```json
{
    "run": {
        "arn": "string",
        "name": "string",
        "type": "string",
        "platform": "ANDROID|IOS",
        "created": "timestamp",
        "status": "STOPPING|COMPLETED",
        "result": "PENDING|PASSED|WARNED|FAILED|SKIPPED|ERRORED|STOPPED",
        "started": "timestamp",
        "stopped": "timestamp",
        "counters": {},
        "totalJobs": "integer",
        "completedJobs": "integer",
        "deviceMinutes": {}
    }
}
```

---

### 3.3 `delete-run`

Deletes the run, given the run ARN.

**Synopsis:**
```bash
aws devicefarm delete-run \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the run to delete |

**Output Schema:**
```json
{}
```

---

### 3.4 `get-run`

Gets information about a run.

**Synopsis:**
```bash
aws devicefarm get-run \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the run |

**Output Schema:**
```json
{
    "run": {
        "arn": "string",
        "name": "string",
        "type": "string",
        "platform": "ANDROID|IOS",
        "created": "timestamp",
        "status": "PENDING|PENDING_CONCURRENCY|PENDING_DEVICE|PROCESSING|SCHEDULING|PREPARING|RUNNING|COMPLETED|STOPPING",
        "result": "PENDING|PASSED|WARNED|FAILED|SKIPPED|ERRORED|STOPPED",
        "started": "timestamp",
        "stopped": "timestamp",
        "counters": {
            "total": "integer",
            "passed": "integer",
            "failed": "integer",
            "warned": "integer",
            "errored": "integer",
            "stopped": "integer",
            "skipped": "integer"
        },
        "message": "string",
        "totalJobs": "integer",
        "completedJobs": "integer",
        "billingMethod": "METERED|UNMETERED",
        "deviceMinutes": {
            "total": "double",
            "metered": "double",
            "unmetered": "double"
        },
        "networkProfile": {
            "arn": "string",
            "name": "string",
            "type": "CURATED|PRIVATE"
        },
        "jobTimeoutMinutes": "integer",
        "devicePoolArn": "string",
        "webUrl": "string",
        "skipAppResign": "boolean",
        "deviceSelectionResult": {
            "filters": [],
            "matchedDevicesCount": "integer",
            "maxDevices": "integer"
        }
    }
}
```

---

### 3.5 `list-runs`

Gets information about runs, given a project ARN. **Paginated operation.**

**Synopsis:**
```bash
aws devicefarm list-runs \
    --arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the project |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "runs": [
        {
            "arn": "string",
            "name": "string",
            "type": "string",
            "platform": "ANDROID|IOS",
            "created": "timestamp",
            "status": "string",
            "result": "string",
            "started": "timestamp",
            "stopped": "timestamp",
            "counters": {},
            "totalJobs": "integer",
            "completedJobs": "integer",
            "deviceMinutes": {}
        }
    ],
    "nextToken": "string"
}
```

---

### 3.6 `list-unique-problems`

Gets information about unique problems for a run. **Paginated operation.**

**Synopsis:**
```bash
aws devicefarm list-unique-problems \
    --arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the run |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "uniqueProblems": {
        "PASSED": [
            {
                "message": "string",
                "problems": [
                    {
                        "run": {"arn": "string", "name": "string"},
                        "job": {"arn": "string", "name": "string"},
                        "suite": {"arn": "string", "name": "string"},
                        "test": {"arn": "string", "name": "string"},
                        "device": {
                            "arn": "string",
                            "name": "string",
                            "model": "string",
                            "platform": "ANDROID|IOS",
                            "os": "string"
                        },
                        "result": "PENDING|PASSED|WARNED|FAILED|SKIPPED|ERRORED|STOPPED",
                        "message": "string"
                    }
                ]
            }
        ],
        "FAILED": [],
        "WARNED": [],
        "ERRORED": [],
        "SKIPPED": [],
        "STOPPED": []
    },
    "nextToken": "string"
}
```
