# Jobs, Suites & Tests

### 4.1 `get-job`

Gets information about a job.

**Synopsis:**
```bash
aws devicefarm get-job \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the job |

**Output Schema:**
```json
{
    "job": {
        "arn": "string",
        "name": "string",
        "type": "string",
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
        "device": {
            "arn": "string",
            "name": "string",
            "manufacturer": "string",
            "model": "string",
            "platform": "ANDROID|IOS",
            "os": "string",
            "formFactor": "PHONE|TABLET"
        },
        "instanceArn": "string",
        "deviceMinutes": {
            "total": "double",
            "metered": "double",
            "unmetered": "double"
        },
        "videoEndpoint": "string",
        "videoCapture": "boolean"
    }
}
```

---

### 4.2 `list-jobs`

Gets information about jobs for a given test run. **Paginated operation.**

**Synopsis:**
```bash
aws devicefarm list-jobs \
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
    "jobs": [
        {
            "arn": "string",
            "name": "string",
            "type": "string",
            "created": "timestamp",
            "status": "string",
            "result": "string",
            "started": "timestamp",
            "stopped": "timestamp",
            "counters": {},
            "device": {},
            "deviceMinutes": {}
        }
    ],
    "nextToken": "string"
}
```

---

### 4.3 `stop-job`

Initiates a stop request for the current job.

**Synopsis:**
```bash
aws devicefarm stop-job \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the job to stop |

**Output Schema:**
```json
{
    "job": {
        "arn": "string",
        "name": "string",
        "type": "string",
        "created": "timestamp",
        "status": "STOPPING|COMPLETED",
        "result": "string",
        "started": "timestamp",
        "stopped": "timestamp",
        "counters": {},
        "device": {},
        "deviceMinutes": {}
    }
}
```

---

### 4.4 `get-suite`

Gets information about a suite.

**Synopsis:**
```bash
aws devicefarm get-suite \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the suite |

**Output Schema:**
```json
{
    "suite": {
        "arn": "string",
        "name": "string",
        "type": "string",
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
        "deviceMinutes": {
            "total": "double",
            "metered": "double",
            "unmetered": "double"
        }
    }
}
```

---

### 4.5 `list-suites`

Gets information about test suites for a given job. **Paginated operation.**

**Synopsis:**
```bash
aws devicefarm list-suites \
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
| `--arn` | **Yes** | string | -- | ARN of the job |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "suites": [
        {
            "arn": "string",
            "name": "string",
            "type": "string",
            "created": "timestamp",
            "status": "string",
            "result": "string",
            "started": "timestamp",
            "stopped": "timestamp",
            "counters": {},
            "deviceMinutes": {}
        }
    ],
    "nextToken": "string"
}
```

---

### 4.6 `get-test`

Gets information about a test.

**Synopsis:**
```bash
aws devicefarm get-test \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the test |

**Output Schema:**
```json
{
    "test": {
        "arn": "string",
        "name": "string",
        "type": "string",
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
        "deviceMinutes": {
            "total": "double",
            "metered": "double",
            "unmetered": "double"
        }
    }
}
```

---

### 4.7 `list-tests`

Gets information about tests in a given test suite. **Paginated operation.**

**Synopsis:**
```bash
aws devicefarm list-tests \
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
| `--arn` | **Yes** | string | -- | ARN of the suite |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "tests": [
        {
            "arn": "string",
            "name": "string",
            "type": "string",
            "created": "timestamp",
            "status": "string",
            "result": "string",
            "started": "timestamp",
            "stopped": "timestamp",
            "counters": {},
            "deviceMinutes": {},
            "message": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 4.8 `list-samples`

Gets information about samples for a given job. **Paginated operation.**

**Synopsis:**
```bash
aws devicefarm list-samples \
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
| `--arn` | **Yes** | string | -- | ARN of the job |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "samples": [
        {
            "arn": "string",
            "type": "CPU|MEMORY|THREADS|RX_RATE|TX_RATE|RX|TX|NATIVE_FRAMES|NATIVE_FPS|NATIVE_MIN_DRAWTIME|NATIVE_AVG_DRAWTIME|NATIVE_MAX_DRAWTIME|OPENGL_FRAMES|OPENGL_FPS|OPENGL_MIN_DRAWTIME|OPENGL_AVG_DRAWTIME|OPENGL_MAX_DRAWTIME",
            "url": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 4.9 `list-artifacts`

Gets information about artifacts. **Paginated operation.**

**Synopsis:**
```bash
aws devicefarm list-artifacts \
    --arn <value> \
    --type <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of a run, job, suite, or test |
| `--type` | **Yes** | string | -- | Artifact category: `FILE`, `LOG`, `SCREENSHOT` |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "artifacts": [
        {
            "arn": "string",
            "name": "string",
            "type": "UNKNOWN|SCREENSHOT|DEVICE_LOG|MESSAGE_LOG|VIDEO_LOG|RESULT_LOG|SERVICE_LOG|WEBKIT_LOG|INSTRUMENTATION_OUTPUT|EXERCISER_MONKEY_OUTPUT|CALABASH_JSON_OUTPUT|CALABASH_PRETTY_OUTPUT|CALABASH_STANDARD_OUTPUT|CALABASH_JAVA_XML_OUTPUT|AUTOMATION_OUTPUT|APPIUM_SERVER_OUTPUT|APPIUM_JAVA_OUTPUT|APPIUM_JAVA_XML_OUTPUT|APPIUM_PYTHON_OUTPUT|APPIUM_PYTHON_XML_OUTPUT|EXPLORER_EVENT_LOG|EXPLORER_SUMMARY_LOG|APPLICATION_CRASH_REPORT|XCTEST_LOG|VIDEO|CUSTOMER_ARTIFACT|CUSTOMER_ARTIFACT_LOG|TESTSPEC_OUTPUT",
            "extension": "string",
            "url": "string"
        }
    ],
    "nextToken": "string"
}
```
