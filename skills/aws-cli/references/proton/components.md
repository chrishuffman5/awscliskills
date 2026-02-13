# Components

### 6.1 `create-component`

Creates a Proton component. Components allow you to provision and manage resources beyond what is defined in the service template.

**Synopsis:**
```bash
aws proton create-component \
    --name <value> \
    --template-file <value> \
    --manifest <value> \
    [--description <value>] \
    [--service-name <value>] \
    [--service-instance-name <value>] \
    [--environment-name <value>] \
    [--service-spec <value>] \
    [--client-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Component name |
| `--template-file` | **Yes** | string | -- | CloudFormation or Terraform template. Use `file://` |
| `--manifest` | **Yes** | string | -- | Manifest file. Use `file://` |
| `--description` | No | string | None | Description |
| `--service-name` | No | string | None | Service name (for service-attached components) |
| `--service-instance-name` | No | string | None | Service instance name |
| `--environment-name` | No | string | None | Environment name (for environment-level components) |
| `--service-spec` | No | string | None | Updated service spec |
| `--client-token` | No | string | None | Idempotency token |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "component": {
        "arn": "string",
        "name": "string",
        "description": "string",
        "createdAt": "timestamp",
        "lastModifiedAt": "timestamp",
        "lastDeploymentAttemptedAt": "timestamp",
        "lastDeploymentSucceededAt": "timestamp",
        "deploymentStatus": "IN_PROGRESS|FAILED|SUCCEEDED|DELETE_IN_PROGRESS|DELETE_FAILED|DELETE_COMPLETE|CANCELLING|CANCELLED",
        "deploymentStatusMessage": "string",
        "environmentName": "string",
        "serviceName": "string",
        "serviceInstanceName": "string",
        "serviceSpec": "string",
        "lastClientRequestToken": "string",
        "lastAttemptedDeploymentId": "string",
        "lastSucceededDeploymentId": "string"
    }
}
```

---

### 6.2 `update-component`

Updates a component.

**Synopsis:**
```bash
aws proton update-component \
    --name <value> \
    --deployment-type <value> \
    [--description <value>] \
    [--template-file <value>] \
    [--service-name <value>] \
    [--service-instance-name <value>] \
    [--service-spec <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Component name |
| `--deployment-type` | **Yes** | string | -- | `NONE` or `CURRENT_VERSION` |
| `--description` | No | string | None | Updated description |
| `--template-file` | No | string | None | Updated template file |
| `--service-name` | No | string | None | Service name |
| `--service-instance-name` | No | string | None | Service instance name |
| `--service-spec` | No | string | None | Updated service spec |
| `--client-token` | No | string | None | Idempotency token |

**Output Schema:** Same as `create-component`.

---

### 6.3 `delete-component`

Deletes a component.

**Synopsis:**
```bash
aws proton delete-component \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Component name |

**Output Schema:** Same as `create-component` with `deploymentStatus` set to `DELETE_IN_PROGRESS`.

---

### 6.4 `get-component`

Gets a component.

**Synopsis:**
```bash
aws proton get-component \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Component name |

**Output Schema:** Same as `create-component`.

---

### 6.5 `list-components`

Lists components with optional filters. **Paginated operation.**

**Synopsis:**
```bash
aws proton list-components \
    [--service-name <value>] \
    [--service-instance-name <value>] \
    [--environment-name <value>] \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-name` | No | string | None | Filter by service name |
| `--service-instance-name` | No | string | None | Filter by service instance name |
| `--environment-name` | No | string | None | Filter by environment name |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "components": [
        {
            "arn": "string",
            "name": "string",
            "description": "string",
            "createdAt": "timestamp",
            "lastModifiedAt": "timestamp",
            "lastDeploymentAttemptedAt": "timestamp",
            "lastDeploymentSucceededAt": "timestamp",
            "deploymentStatus": "string",
            "deploymentStatusMessage": "string",
            "environmentName": "string",
            "serviceName": "string",
            "serviceInstanceName": "string",
            "lastAttemptedDeploymentId": "string",
            "lastSucceededDeploymentId": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 6.6 `cancel-component-deployment`

Cancels an in-progress component deployment.

**Synopsis:**
```bash
aws proton cancel-component-deployment \
    --component-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--component-name` | **Yes** | string | -- | Component name |

**Output Schema:** Same as `create-component`.

---

### 6.7 `list-component-outputs`

Lists outputs for a component. **Paginated operation.**

**Synopsis:**
```bash
aws proton list-component-outputs \
    --component-name <value> \
    [--deployment-id <value>] \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--component-name` | **Yes** | string | -- | Component name |
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

### 6.8 `list-component-provisioned-resources`

Lists provisioned resources for a component. **Paginated operation.**

**Synopsis:**
```bash
aws proton list-component-provisioned-resources \
    --component-name <value> \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--component-name` | **Yes** | string | -- | Component name |
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
