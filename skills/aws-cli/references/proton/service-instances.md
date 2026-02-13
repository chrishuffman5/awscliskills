# Service Instances

### 4.1 `update-service-instance`

Updates a service instance.

**Synopsis:**
```bash
aws proton update-service-instance \
    --name <value> \
    --service-name <value> \
    --deployment-type <value> \
    [--spec <value>] \
    [--template-major-version <value>] \
    [--template-minor-version <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Service instance name |
| `--service-name` | **Yes** | string | -- | Service name |
| `--deployment-type` | **Yes** | string | -- | `NONE`, `CURRENT_VERSION`, `MINOR_VERSION`, or `MAJOR_VERSION` |
| `--spec` | No | string | None | Updated spec |
| `--template-major-version` | No | string | None | Target major version |
| `--template-minor-version` | No | string | None | Target minor version |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:**
```json
{
    "serviceInstance": {
        "arn": "string",
        "name": "string",
        "serviceName": "string",
        "environmentName": "string",
        "createdAt": "timestamp",
        "lastDeploymentAttemptedAt": "timestamp",
        "lastDeploymentSucceededAt": "timestamp",
        "templateName": "string",
        "templateMajorVersion": "string",
        "templateMinorVersion": "string",
        "deploymentStatus": "IN_PROGRESS|FAILED|SUCCEEDED|DELETE_IN_PROGRESS|DELETE_FAILED|DELETE_COMPLETE|CANCELLING|CANCELLED",
        "deploymentStatusMessage": "string",
        "spec": "string",
        "lastClientRequestToken": "string",
        "lastAttemptedDeploymentId": "string",
        "lastSucceededDeploymentId": "string"
    }
}
```

---

### 4.2 `get-service-instance`

Gets a service instance.

**Synopsis:**
```bash
aws proton get-service-instance \
    --name <value> \
    --service-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Service instance name |
| `--service-name` | **Yes** | string | -- | Service name |

**Output Schema:** Same as `update-service-instance`.

---

### 4.3 `list-service-instances`

Lists service instances with optional filters. **Paginated operation.**

**Synopsis:**
```bash
aws proton list-service-instances \
    [--service-name <value>] \
    [--filters <value>] \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-name` | No | string | None | Filter by service name |
| `--filters` | No | list | None | Filters. Shorthand: `key=string,value=string ...` |
| `--sort-by` | No | string | None | Sort by: `name`, `deploymentStatus`, `templateName`, `serviceName`, `environmentName`, `lastDeploymentAttemptedAt`, `createdAt` |
| `--sort-order` | No | string | None | `ASCENDING` or `DESCENDING` |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "serviceInstances": [
        {
            "arn": "string",
            "name": "string",
            "serviceName": "string",
            "environmentName": "string",
            "templateName": "string",
            "templateMajorVersion": "string",
            "templateMinorVersion": "string",
            "deploymentStatus": "string",
            "deploymentStatusMessage": "string",
            "createdAt": "timestamp",
            "lastDeploymentAttemptedAt": "timestamp",
            "lastDeploymentSucceededAt": "timestamp",
            "lastAttemptedDeploymentId": "string",
            "lastSucceededDeploymentId": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 4.4 `list-service-instance-outputs`

Lists outputs for a service instance. **Paginated operation.**

**Synopsis:**
```bash
aws proton list-service-instance-outputs \
    --service-instance-name <value> \
    --service-name <value> \
    [--deployment-id <value>] \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-instance-name` | **Yes** | string | -- | Service instance name |
| `--service-name` | **Yes** | string | -- | Service name |
| `--deployment-id` | No | string | None | Deployment ID |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "outputs": [
        {
            "key": "string",
            "valueString": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 4.5 `list-service-instance-provisioned-resources`

Lists provisioned resources for a service instance. **Paginated operation.**

**Synopsis:**
```bash
aws proton list-service-instance-provisioned-resources \
    --service-instance-name <value> \
    --service-name <value> \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-instance-name` | **Yes** | string | -- | Service instance name |
| `--service-name` | **Yes** | string | -- | Service name |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "provisionedResources": [
        {
            "identifier": "string",
            "name": "string",
            "provisioningEngine": "CLOUDFORMATION|TERRAFORM"
        }
    ],
    "nextToken": "string"
}
```
