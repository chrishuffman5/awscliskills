# Testing

### 24.1 `create-test-case`

Creates a test case for the specified instance.

**Synopsis:**
```bash
aws connect create-test-case \
    --instance-id <value> \
    --name <value> \
    --steps <value> \
    [--description <value>] \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--name` | **Yes** | string | -- | Test case name |
| `--steps` | **Yes** | list | -- | Test steps |
| `--description` | No | string | None | Description |
| `--tags` | No | map | None | Tags (max 50) |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "TestCaseId": "string",
    "TestCaseArn": "string"
}
```

---

### 24.2 `describe-test-case`

Describes a test case.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--test-case-id` | **Yes** | string | -- | Test case ID |

---

### 24.3 `list-test-cases`

Lists test cases. **Paginated operation.**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results |

---

### 24.4 `update-test-case`

Updates a test case.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--test-case-id` | **Yes** | string | -- | Test case ID |
| `--name` | No | string | None | Updated name |
| `--description` | No | string | None | Updated description |
| `--steps` | No | list | None | Updated steps |

**Output:** None

---

### 24.5 `delete-test-case`

Deletes a test case.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--test-case-id` | **Yes** | string | -- | Test case ID |

**Output:** None

---

### 24.6 `search-test-cases`

Searches test cases. **Paginated operation.**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results (1-100) |
| `--search-criteria` | No | structure | None | Search criteria |

---

### 24.7 `start-test-case-execution`

Starts executing a test case.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--test-case-id` | **Yes** | string | -- | Test case ID |
| `--client-token` | No | string | Auto | Idempotency token |

**Output Schema:**
```json
{
    "TestCaseExecutionId": "string",
    "TestCaseExecutionArn": "string"
}
```

---

### 24.8 `stop-test-case-execution`

Stops a running test case execution.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--test-case-execution-id` | **Yes** | string | -- | Execution ID |

**Output:** None

---

### 24.9 `list-test-case-executions`

Lists test case executions. **Paginated operation.**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--test-case-id` | **Yes** | string | -- | Test case ID |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results |

---

### 24.10 `list-test-case-execution-records`

Lists execution records. **Paginated operation.**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--test-case-execution-id` | **Yes** | string | -- | Execution ID |
| `--next-token` | No | string | None | Pagination token |
| `--max-results` | No | integer | None | Max results |

---

### 24.11 `get-test-case-execution-summary`

Gets a summary of a test case execution.

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-id` | **Yes** | string | -- | Instance ID or ARN |
| `--test-case-execution-id` | **Yes** | string | -- | Execution ID |

**Output Schema:**
```json
{
    "TestCaseExecutionSummary": {
        "TestCaseExecutionId": "string",
        "TestCaseId": "string",
        "Status": "string",
        "StartTime": "timestamp",
        "EndTime": "timestamp",
        "TotalSteps": "integer",
        "PassedSteps": "integer",
        "FailedSteps": "integer"
    }
}
```
