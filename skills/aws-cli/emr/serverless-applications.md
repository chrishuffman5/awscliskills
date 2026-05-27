# Serverless — Applications (`aws emr-serverless`)

### 14.1 `create-application`

Creates an EMR Serverless application.

**Synopsis:**
```bash
aws emr-serverless create-application \
    --release-label <value> \
    --type <value> \
    [--name <value>] \
    [--client-token <value>] \
    [--initial-capacity <value>] \
    [--maximum-capacity <value>] \
    [--auto-start-configuration <value>] \
    [--auto-stop-configuration <value>] \
    [--network-configuration <value>] \
    [--architecture <value>] \
    [--image-configuration <value>] \
    [--worker-type-specifications <value>] \
    [--runtime-configuration <value>] \
    [--monitoring-configuration <value>] \
    [--interactive-configuration <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--release-label` | **Yes** | string | -- | EMR release (e.g., `emr-7.0.0`) |
| `--type` | **Yes** | string | -- | Application type: `SPARK` or `HIVE` |
| `--name` | No | string | -- | Application name |
| `--client-token` | No | string | -- | Idempotency token |
| `--initial-capacity` | No | map | -- | Pre-initialized capacity per worker type |
| `--maximum-capacity` | No | structure | -- | Max capacity limits |
| `--auto-start-configuration` | No | structure | -- | Auto-start. Shorthand: `enabled=boolean` |
| `--auto-stop-configuration` | No | structure | -- | Auto-stop. Shorthand: `enabled=boolean,idleTimeoutMinutes=integer` |
| `--network-configuration` | No | structure | -- | VPC config. Shorthand: `subnetIds=string,string,securityGroupIds=string,string` |
| `--architecture` | No | string | `X86_64` | `X86_64` or `ARM64` |
| `--image-configuration` | No | structure | -- | Custom image config. Shorthand: `imageUri=string` |
| `--worker-type-specifications` | No | map | -- | Worker type specifications per worker type |
| `--runtime-configuration` | No | list | -- | Runtime configuration overrides |
| `--monitoring-configuration` | No | structure | -- | Monitoring configuration |
| `--interactive-configuration` | No | structure | -- | Interactive configuration. Shorthand: `studioEnabled=boolean,livyEndpointEnabled=boolean` |
| `--tags` | No | map | -- | Tags |

**Maximum Capacity Structure:**
```json
{
    "cpu": "string",
    "memory": "string",
    "disk": "string"
}
```

**Output Schema:**
```json
{
    "applicationId": "string",
    "name": "string",
    "arn": "string"
}
```

---

### 14.2 `delete-application`

Deletes an EMR Serverless application. Application must be in `CREATED` or `STOPPED` state.

**Synopsis:**
```bash
aws emr-serverless delete-application \
    --application-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application ID to delete |

No output on success.

---

### 14.3 `get-application`

Gets details about an EMR Serverless application.

**Synopsis:**
```bash
aws emr-serverless get-application \
    --application-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application ID |

**Output Schema:**
```json
{
    "application": {
        "applicationId": "string",
        "name": "string",
        "arn": "string",
        "releaseLabel": "string",
        "type": "SPARK|HIVE",
        "state": "CREATING|CREATED|STARTING|STARTED|STOPPING|STOPPED|TERMINATED",
        "stateDetails": "string",
        "initialCapacity": {},
        "maximumCapacity": {},
        "createdAt": "timestamp",
        "updatedAt": "timestamp",
        "tags": {},
        "autoStartConfiguration": {
            "enabled": "boolean"
        },
        "autoStopConfiguration": {
            "enabled": "boolean",
            "idleTimeoutMinutes": "integer"
        },
        "networkConfiguration": {
            "subnetIds": ["string"],
            "securityGroupIds": ["string"]
        },
        "architecture": "X86_64|ARM64",
        "imageConfiguration": {},
        "workerTypeSpecifications": {},
        "runtimeConfiguration": [],
        "monitoringConfiguration": {},
        "interactiveConfiguration": {}
    }
}
```

---

### 14.4 `list-applications`

Lists EMR Serverless applications. **Paginated operation.**

**Synopsis:**
```bash
aws emr-serverless list-applications \
    [--states <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--states` | No | list(string) | -- | Filter: `CREATING`, `CREATED`, `STARTING`, `STARTED`, `STOPPING`, `STOPPED`, `TERMINATED` |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "applications": [
        {
            "id": "string",
            "name": "string",
            "arn": "string",
            "releaseLabel": "string",
            "type": "string",
            "state": "string",
            "stateDetails": "string",
            "createdAt": "timestamp",
            "updatedAt": "timestamp",
            "architecture": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 14.5 `update-application`

Updates an EMR Serverless application.

**Synopsis:**
```bash
aws emr-serverless update-application \
    --application-id <value> \
    [--client-token <value>] \
    [--initial-capacity <value>] \
    [--maximum-capacity <value>] \
    [--auto-start-configuration <value>] \
    [--auto-stop-configuration <value>] \
    [--network-configuration <value>] \
    [--architecture <value>] \
    [--image-configuration <value>] \
    [--worker-type-specifications <value>] \
    [--runtime-configuration <value>] \
    [--monitoring-configuration <value>] \
    [--interactive-configuration <value>] \
    [--release-label <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application ID to update |
| `--initial-capacity` | No | map | -- | Updated initial capacity |
| `--maximum-capacity` | No | structure | -- | Updated max capacity |
| `--auto-start-configuration` | No | structure | -- | Updated auto-start config |
| `--auto-stop-configuration` | No | structure | -- | Updated auto-stop config |
| `--network-configuration` | No | structure | -- | Updated network config |
| `--architecture` | No | string | -- | Updated architecture |
| `--release-label` | No | string | -- | Updated release label |

**Output Schema:**
```json
{
    "application": {
        "applicationId": "string",
        "name": "string",
        "arn": "string"
    }
}
```

---

### 14.6 `start-application`

Pre-initializes an application by starting its resources.

**Synopsis:**
```bash
aws emr-serverless start-application \
    --application-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application ID to start |

No output on success.

---

### 14.7 `stop-application`

Stops an application and releases its resources.

**Synopsis:**
```bash
aws emr-serverless stop-application \
    --application-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application ID to stop |

No output on success.
