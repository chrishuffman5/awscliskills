# Backend Environments

### 5.1 `create-backend-environment`

Creates a new backend environment for an Amplify app.

**Synopsis:**
```bash
aws amplify create-backend-environment \
    --app-id <value> \
    --environment-name <value> \
    [--stack-name <value>] \
    [--deployment-artifacts <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-id` | **Yes** | string | -- | Unique ID of the Amplify app |
| `--environment-name` | **Yes** | string | -- | Name of the backend environment |
| `--stack-name` | No | string | None | CloudFormation stack name for the backend environment |
| `--deployment-artifacts` | No | string | None | Name of the deployment artifacts |

**Output Schema:**
```json
{
    "backendEnvironment": {
        "backendEnvironmentArn": "string",
        "environmentName": "string",
        "stackName": "string",
        "deploymentArtifacts": "string",
        "createTime": "timestamp",
        "updateTime": "timestamp"
    }
}
```

---

### 5.2 `delete-backend-environment`

Deletes a backend environment for an Amplify app.

**Synopsis:**
```bash
aws amplify delete-backend-environment \
    --app-id <value> \
    --environment-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-id` | **Yes** | string | -- | Unique ID of the Amplify app |
| `--environment-name` | **Yes** | string | -- | Name of the backend environment to delete |

**Output Schema:**
```json
{
    "backendEnvironment": {
        "backendEnvironmentArn": "string",
        "environmentName": "string",
        "stackName": "string",
        "deploymentArtifacts": "string",
        "createTime": "timestamp",
        "updateTime": "timestamp"
    }
}
```

---

### 5.3 `get-backend-environment`

Returns a backend environment for an Amplify app.

**Synopsis:**
```bash
aws amplify get-backend-environment \
    --app-id <value> \
    --environment-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-id` | **Yes** | string | -- | Unique ID of the Amplify app |
| `--environment-name` | **Yes** | string | -- | Name of the backend environment |

**Output Schema:**
```json
{
    "backendEnvironment": {
        "backendEnvironmentArn": "string",
        "environmentName": "string",
        "stackName": "string",
        "deploymentArtifacts": "string",
        "createTime": "timestamp",
        "updateTime": "timestamp"
    }
}
```

---

### 5.4 `list-backend-environments`

Lists the backend environments for an Amplify app. **Paginated operation.**

**Synopsis:**
```bash
aws amplify list-backend-environments \
    --app-id <value> \
    [--environment-name <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-id` | **Yes** | string | -- | Unique ID of the Amplify app |
| `--environment-name` | No | string | None | Filter by environment name |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "backendEnvironments": [
        {
            "backendEnvironmentArn": "string",
            "environmentName": "string",
            "stackName": "string",
            "deploymentArtifacts": "string",
            "createTime": "timestamp",
            "updateTime": "timestamp"
        }
    ],
    "nextToken": "string"
}
```
