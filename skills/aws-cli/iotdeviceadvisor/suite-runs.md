# Suite Runs

### 2.1 `start-suite-run`

Starts a test suite run against a device.

**Synopsis:**
```bash
aws iotdeviceadvisor start-suite-run \
    --suite-definition-id <value> \
    --suite-run-configuration <value> \
    [--suite-definition-version <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--suite-definition-id` | **Yes** | string | -- | Suite definition ID (12-36 chars) |
| `--suite-run-configuration` | **Yes** | structure | -- | Run configuration |
| `--suite-definition-version` | No | string | None | Specific version (2-255 chars) |
| `--tags` | No | map | None | Key-value tag pairs (max 50) |

**SuiteRunConfiguration:**
```json
{
    "primaryDevice": {
        "thingArn": "string",
        "certificateArn": "string",
        "deviceRoleArn": "string"
    },
    "selectedTestList": ["string"],
    "parallelRun": true
}
```

- `primaryDevice` (required) — Must include at least `thingArn` or `certificateArn`
- `selectedTestList` (optional) — Specific test case IDs to run (max 100)
- `parallelRun` (optional) — Run tests in parallel

**Output Schema:**
```json
{
    "suiteRunId": "string",
    "suiteRunArn": "string",
    "createdAt": "timestamp",
    "endpoint": "string"
}
```

---

### 2.2 `get-suite-run`

Gets the details and test results of a suite run.

**Synopsis:**
```bash
aws iotdeviceadvisor get-suite-run \
    --suite-definition-id <value> \
    --suite-run-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--suite-definition-id` | **Yes** | string | -- | Suite definition ID (12-36 chars) |
| `--suite-run-id` | **Yes** | string | -- | Suite run ID (12-36 chars) |

**Output Schema:**
```json
{
    "suiteDefinitionId": "string",
    "suiteDefinitionVersion": "string",
    "suiteRunId": "string",
    "suiteRunArn": "string",
    "suiteRunConfiguration": {
        "primaryDevice": {
            "thingArn": "string",
            "certificateArn": "string",
            "deviceRoleArn": "string"
        },
        "selectedTestList": ["string"],
        "parallelRun": "boolean"
    },
    "testResult": {
        "groups": [
            {
                "groupId": "string",
                "groupName": "string",
                "tests": [
                    {
                        "testCaseRunId": "string",
                        "testCaseDefinitionId": "string",
                        "testCaseDefinitionName": "string",
                        "status": "PASS|FAIL|CANCELED|PENDING|RUNNING|STOPPING|STOPPED|PASS_WITH_WARNINGS|ERROR",
                        "startTime": "timestamp",
                        "endTime": "timestamp",
                        "logUrl": "string",
                        "warnings": "string",
                        "failure": "string",
                        "testScenarios": [
                            {
                                "testCaseScenarioId": "string",
                                "testCaseScenarioType": "Advanced|Basic",
                                "status": "string",
                                "failure": "string",
                                "systemMessage": "string"
                            }
                        ]
                    }
                ]
            }
        ]
    },
    "startTime": "timestamp",
    "endTime": "timestamp",
    "status": "PASS|FAIL|CANCELED|PENDING|RUNNING|STOPPING|STOPPED|PASS_WITH_WARNINGS|ERROR",
    "errorReason": "string",
    "tags": {}
}
```

---

### 2.3 `get-suite-run-report`

Gets a pre-signed URL to download the qualification report for a completed suite run.

**Synopsis:**
```bash
aws iotdeviceadvisor get-suite-run-report \
    --suite-definition-id <value> \
    --suite-run-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--suite-definition-id` | **Yes** | string | -- | Suite definition ID (12-36 chars) |
| `--suite-run-id` | **Yes** | string | -- | Suite run ID (12-36 chars) |

**Output Schema:**
```json
{
    "qualificationReportDownloadUrl": "string"
}
```

---

### 2.4 `stop-suite-run`

Stops a running test suite.

**Synopsis:**
```bash
aws iotdeviceadvisor stop-suite-run \
    --suite-definition-id <value> \
    --suite-run-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--suite-definition-id` | **Yes** | string | -- | Suite definition ID (12-36 chars) |
| `--suite-run-id` | **Yes** | string | -- | Suite run ID to stop (12-36 chars) |

**Output:** None

---

### 2.5 `list-suite-runs`

Lists test suite runs. Can filter by suite definition. **Paginated operation.**

**Synopsis:**
```bash
aws iotdeviceadvisor list-suite-runs \
    [--suite-definition-id <value>] \
    [--suite-definition-version <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--suite-definition-id` | No | string | None | Filter by suite definition (12-36 chars) |
| `--suite-definition-version` | No | string | None | Filter by version (requires suite-definition-id) |
| `--max-results` | No | integer | None | Max results per page (1-50) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "nextToken": "string",
    "suiteRunsList": [
        {
            "suiteDefinitionId": "string",
            "suiteDefinitionVersion": "string",
            "suiteDefinitionName": "string",
            "suiteRunId": "string",
            "createdAt": "timestamp",
            "startedAt": "timestamp",
            "endAt": "timestamp",
            "status": "PASS|FAIL|CANCELED|PENDING|RUNNING|STOPPING|STOPPED|PASS_WITH_WARNINGS|ERROR",
            "passed": "integer",
            "failed": "integer"
        }
    ]
}
```
