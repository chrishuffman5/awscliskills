# Test Grid (Selenium)

### 10.1 `create-test-grid-project`

Creates a Selenium testing project for browser-based testing.

**Synopsis:**
```bash
aws devicefarm create-test-grid-project \
    --name <value> \
    [--description <value>] \
    [--vpc-config <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the test grid project |
| `--description` | No | string | None | Description of the project |
| `--vpc-config` | No | structure | None | VPC configuration. JSON: `{"securityGroupIds":["string"],"subnetIds":["string"],"vpcId":"string"}` |
| `--tags` | No | list | None | Tags. Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "testGridProject": {
        "arn": "string",
        "name": "string",
        "description": "string",
        "vpcConfig": {
            "securityGroupIds": ["string"],
            "subnetIds": ["string"],
            "vpcId": "string"
        },
        "created": "timestamp"
    }
}
```

---

### 10.2 `delete-test-grid-project`

Deletes a Selenium testing project and all associated data.

**Synopsis:**
```bash
aws devicefarm delete-test-grid-project \
    --project-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project-arn` | **Yes** | string | -- | ARN of the test grid project to delete |

**Output Schema:**
```json
{}
```

---

### 10.3 `get-test-grid-project`

Returns information about a test grid project.

**Synopsis:**
```bash
aws devicefarm get-test-grid-project \
    --project-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project-arn` | **Yes** | string | -- | ARN of the test grid project |

**Output Schema:**
```json
{
    "testGridProject": {
        "arn": "string",
        "name": "string",
        "description": "string",
        "vpcConfig": {
            "securityGroupIds": ["string"],
            "subnetIds": ["string"],
            "vpcId": "string"
        },
        "created": "timestamp"
    }
}
```

---

### 10.4 `list-test-grid-projects`

Returns information about all test grid projects. **Paginated operation.**

**Synopsis:**
```bash
aws devicefarm list-test-grid-projects \
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
    "testGridProjects": [
        {
            "arn": "string",
            "name": "string",
            "description": "string",
            "vpcConfig": {},
            "created": "timestamp"
        }
    ],
    "nextToken": "string"
}
```

---

### 10.5 `update-test-grid-project`

Updates a test grid project.

**Synopsis:**
```bash
aws devicefarm update-test-grid-project \
    --project-arn <value> \
    [--name <value>] \
    [--description <value>] \
    [--vpc-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project-arn` | **Yes** | string | -- | ARN of the test grid project to update |
| `--name` | No | string | None | Updated name |
| `--description` | No | string | None | Updated description |
| `--vpc-config` | No | structure | None | Updated VPC configuration |

**Output Schema:**
```json
{
    "testGridProject": {
        "arn": "string",
        "name": "string",
        "description": "string",
        "vpcConfig": {
            "securityGroupIds": ["string"],
            "subnetIds": ["string"],
            "vpcId": "string"
        },
        "created": "timestamp"
    }
}
```

---

### 10.6 `create-test-grid-url`

Creates a signed, time-limited URL for a Selenium test grid session.

**Synopsis:**
```bash
aws devicefarm create-test-grid-url \
    --project-arn <value> \
    --expires-in-seconds <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project-arn` | **Yes** | string | -- | ARN of the test grid project |
| `--expires-in-seconds` | **Yes** | integer | -- | URL lifetime in seconds (60-900) |

**Output Schema:**
```json
{
    "url": "string",
    "expires": "timestamp"
}
```

---

### 10.7 `get-test-grid-session`

Returns a test grid session.

**Synopsis:**
```bash
aws devicefarm get-test-grid-session \
    [--project-arn <value>] \
    [--session-id <value>] \
    [--session-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project-arn` | No | string | None | ARN of the project (use with session-id) |
| `--session-id` | No | string | None | Session ID (use with project-arn) |
| `--session-arn` | No | string | None | ARN of the session (alternative to project-arn + session-id) |

**Output Schema:**
```json
{
    "testGridSession": {
        "arn": "string",
        "status": "ACTIVE|CLOSED|ERRORED",
        "created": "timestamp",
        "ended": "timestamp",
        "billingMinutes": "double",
        "seleniumProperties": "string"
    }
}
```

---

### 10.8 `list-test-grid-sessions`

Returns test grid sessions for a project. **Paginated operation.**

**Synopsis:**
```bash
aws devicefarm list-test-grid-sessions \
    --project-arn <value> \
    [--status <value>] \
    [--creation-time-after <value>] \
    [--creation-time-before <value>] \
    [--end-time-after <value>] \
    [--end-time-before <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--project-arn` | **Yes** | string | -- | ARN of the project |
| `--status` | No | string | None | Filter by status: `ACTIVE`, `CLOSED`, `ERRORED` |
| `--creation-time-after` | No | timestamp | None | Filter sessions created after this time |
| `--creation-time-before` | No | timestamp | None | Filter sessions created before this time |
| `--end-time-after` | No | timestamp | None | Filter sessions ended after this time |
| `--end-time-before` | No | timestamp | None | Filter sessions ended before this time |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "testGridSessions": [
        {
            "arn": "string",
            "status": "ACTIVE|CLOSED|ERRORED",
            "created": "timestamp",
            "ended": "timestamp",
            "billingMinutes": "double",
            "seleniumProperties": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 10.9 `list-test-grid-session-actions`

Returns a list of actions taken in a test grid session. **Paginated operation.**

**Synopsis:**
```bash
aws devicefarm list-test-grid-session-actions \
    --session-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--session-arn` | **Yes** | string | -- | ARN of the test grid session |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "actions": [
        {
            "action": "string",
            "started": "timestamp",
            "duration": "long",
            "statusCode": "string",
            "requestMethod": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 10.10 `list-test-grid-session-artifacts`

Returns a list of artifacts for a test grid session. **Paginated operation.**

**Synopsis:**
```bash
aws devicefarm list-test-grid-session-artifacts \
    --session-arn <value> \
    [--type <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--session-arn` | **Yes** | string | -- | ARN of the test grid session |
| `--type` | No | string | None | Filter by type: `VIDEO`, `LOG` |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "artifacts": [
        {
            "filename": "string",
            "type": "UNKNOWN|VIDEO|SELENIUM_LOG",
            "url": "string"
        }
    ],
    "nextToken": "string"
}
```
