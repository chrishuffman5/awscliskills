# Environments

### 3.1 `create-environment`

Creates an environment for an application. An environment is a logical deployment group of AppConfig targets, such as applications in a Beta or Production environment.

**Synopsis:**
```bash
aws appconfig create-environment \
    --application-id <value> \
    --name <value> \
    [--description <value>] \
    [--monitors <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application ID |
| `--name` | **Yes** | string | -- | Environment name (1-64 chars) |
| `--description` | No | string | None | Description (0-1024 chars) |
| `--monitors` | No | list | None | CloudWatch alarms to monitor during deployment (max 5) |
| `--tags` | No | map | None | Tags (max 50) |

**Monitors structure:**
```json
[
    {
        "AlarmArn": "string",
        "AlarmRoleArn": "string"
    }
]
```

**Output Schema:**
```json
{
    "ApplicationId": "string",
    "Id": "string",
    "Name": "string",
    "Description": "string",
    "State": "READY_FOR_DEPLOYMENT|DEPLOYING|ROLLING_BACK|ROLLED_BACK|REVERTED",
    "Monitors": [
        {
            "AlarmArn": "string",
            "AlarmRoleArn": "string"
        }
    ]
}
```

---

### 3.2 `get-environment`

Retrieves environment details.

**Synopsis:**
```bash
aws appconfig get-environment \
    --application-id <value> \
    --environment-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application ID |
| `--environment-id` | **Yes** | string | -- | Environment ID |

**Output Schema:**
```json
{
    "ApplicationId": "string",
    "Id": "string",
    "Name": "string",
    "Description": "string",
    "State": "READY_FOR_DEPLOYMENT|DEPLOYING|ROLLING_BACK|ROLLED_BACK|REVERTED",
    "Monitors": [
        {
            "AlarmArn": "string",
            "AlarmRoleArn": "string"
        }
    ]
}
```

---

### 3.3 `list-environments`

Lists environments for an application. **Paginated operation.**

**Synopsis:**
```bash
aws appconfig list-environments \
    --application-id <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application ID |
| `--max-results` | No | integer | None | Max results per page (1-50) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "Items": [
        {
            "ApplicationId": "string",
            "Id": "string",
            "Name": "string",
            "Description": "string",
            "State": "READY_FOR_DEPLOYMENT|DEPLOYING|ROLLING_BACK|ROLLED_BACK|REVERTED",
            "Monitors": []
        }
    ],
    "NextToken": "string"
}
```

---

### 3.4 `update-environment`

Updates an environment.

**Synopsis:**
```bash
aws appconfig update-environment \
    --application-id <value> \
    --environment-id <value> \
    [--name <value>] \
    [--description <value>] \
    [--monitors <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application ID |
| `--environment-id` | **Yes** | string | -- | Environment ID |
| `--name` | No | string | None | Updated name (1-64 chars) |
| `--description` | No | string | None | Updated description (0-1024 chars) |
| `--monitors` | No | list | None | Updated CloudWatch alarms (max 5) |

**Output Schema:**
```json
{
    "ApplicationId": "string",
    "Id": "string",
    "Name": "string",
    "Description": "string",
    "State": "READY_FOR_DEPLOYMENT|DEPLOYING|ROLLING_BACK|ROLLED_BACK|REVERTED",
    "Monitors": [
        {
            "AlarmArn": "string",
            "AlarmRoleArn": "string"
        }
    ]
}
```

---

### 3.5 `delete-environment`

Deletes an environment.

**Synopsis:**
```bash
aws appconfig delete-environment \
    --application-id <value> \
    --environment-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application ID |
| `--environment-id` | **Yes** | string | -- | Environment ID |

**Output:** None
