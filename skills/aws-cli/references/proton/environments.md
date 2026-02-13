# Environments

### 1.1 `create-environment`

Creates a Proton environment from an environment template.

**Synopsis:**
```bash
aws proton create-environment \
    --name <value> \
    --template-name <value> \
    --template-major-version <value> \
    --spec <value> \
    [--template-minor-version <value>] \
    [--description <value>] \
    [--proton-service-role-arn <value>] \
    [--environment-account-connection-id <value>] \
    [--provisioning-repository <value>] \
    [--component-role-arn <value>] \
    [--codebuild-role-arn <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Environment name |
| `--template-name` | **Yes** | string | -- | Environment template name |
| `--template-major-version` | **Yes** | string | -- | Template major version |
| `--spec` | **Yes** | string | -- | Environment spec (YAML). Use `file://` for local files |
| `--template-minor-version` | No | string | None | Template minor version |
| `--description` | No | string | None | Description |
| `--proton-service-role-arn` | No | string | None | Proton service role ARN |
| `--environment-account-connection-id` | No | string | None | Cross-account connection ID |
| `--provisioning-repository` | No | structure | None | Self-managed provisioning repo. Shorthand: `provider=GITHUB|GITHUB_ENTERPRISE|BITBUCKET,name=string,branch=string` |
| `--component-role-arn` | No | string | None | IAM role for components |
| `--codebuild-role-arn` | No | string | None | CodeBuild role ARN |
| `--tags` | No | list | None | Tags. Shorthand: `key=string,value=string ...` |

**Output Schema:**
```json
{
    "environment": {
        "arn": "string",
        "name": "string",
        "description": "string",
        "createdAt": "timestamp",
        "lastDeploymentAttemptedAt": "timestamp",
        "lastDeploymentSucceededAt": "timestamp",
        "templateName": "string",
        "templateMajorVersion": "string",
        "templateMinorVersion": "string",
        "deploymentStatus": "IN_PROGRESS|FAILED|SUCCEEDED|DELETE_IN_PROGRESS|DELETE_FAILED|DELETE_COMPLETE|CANCELLING|CANCELLED",
        "deploymentStatusMessage": "string",
        "protonServiceRoleArn": "string",
        "environmentAccountConnectionId": "string",
        "environmentAccountId": "string",
        "provisioning": "CUSTOMER_MANAGED",
        "provisioningRepository": {
            "arn": "string",
            "provider": "string",
            "name": "string",
            "branch": "string"
        },
        "componentRoleArn": "string",
        "codebuildRoleArn": "string",
        "spec": "string",
        "lastAttemptedDeploymentId": "string",
        "lastSucceededDeploymentId": "string"
    }
}
```

---

### 1.2 `update-environment`

Updates an environment.

**Synopsis:**
```bash
aws proton update-environment \
    --name <value> \
    --deployment-type <value> \
    [--spec <value>] \
    [--template-major-version <value>] \
    [--template-minor-version <value>] \
    [--description <value>] \
    [--proton-service-role-arn <value>] \
    [--environment-account-connection-id <value>] \
    [--provisioning-repository <value>] \
    [--component-role-arn <value>] \
    [--codebuild-role-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Environment name |
| `--deployment-type` | **Yes** | string | -- | `NONE`, `CURRENT_VERSION`, `MINOR_VERSION`, or `MAJOR_VERSION` |
| `--spec` | No | string | None | Updated spec |
| `--template-major-version` | No | string | None | Target major version |
| `--template-minor-version` | No | string | None | Target minor version |
| `--description` | No | string | None | Updated description |
| `--proton-service-role-arn` | No | string | None | Updated service role ARN |
| `--environment-account-connection-id` | No | string | None | Updated connection ID |
| `--provisioning-repository` | No | structure | None | Updated provisioning repository |
| `--component-role-arn` | No | string | None | Updated component role ARN |
| `--codebuild-role-arn` | No | string | None | Updated CodeBuild role ARN |

**Output Schema:** Same as `create-environment`.

---

### 1.3 `delete-environment`

Deletes an environment.

**Synopsis:**
```bash
aws proton delete-environment \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Environment name |

**Output Schema:** Same environment object with `deploymentStatus` set to `DELETE_IN_PROGRESS`.

---

### 1.4 `get-environment`

Gets an environment.

**Synopsis:**
```bash
aws proton get-environment \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Environment name |

**Output Schema:** Same as `create-environment`.

---

### 1.5 `list-environments`

Lists environments. **Paginated operation.**

**Synopsis:**
```bash
aws proton list-environments \
    [--environment-templates <value>] \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-templates` | No | list | None | Filter by template. Shorthand: `templateName=string,majorVersion=string ...` |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "environments": [
        {
            "arn": "string",
            "name": "string",
            "description": "string",
            "createdAt": "timestamp",
            "lastDeploymentAttemptedAt": "timestamp",
            "lastDeploymentSucceededAt": "timestamp",
            "templateName": "string",
            "templateMajorVersion": "string",
            "templateMinorVersion": "string",
            "deploymentStatus": "string",
            "deploymentStatusMessage": "string",
            "protonServiceRoleArn": "string",
            "environmentAccountConnectionId": "string",
            "environmentAccountId": "string",
            "provisioning": "CUSTOMER_MANAGED",
            "componentRoleArn": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 1.6 `cancel-environment-deployment`

Cancels an in-progress environment deployment.

**Synopsis:**
```bash
aws proton cancel-environment-deployment \
    --environment-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-name` | **Yes** | string | -- | Environment name |

**Output Schema:** Same environment object.

---

### 1.7 `list-environment-outputs`

Lists environment outputs. **Paginated operation.**

**Synopsis:**
```bash
aws proton list-environment-outputs \
    --environment-name <value> \
    [--deployment-id <value>] \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-name` | **Yes** | string | -- | Environment name |
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

### 1.8 `list-environment-provisioned-resources`

Lists provisioned resources for an environment. **Paginated operation.**

**Synopsis:**
```bash
aws proton list-environment-provisioned-resources \
    --environment-name <value> \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--environment-name` | **Yes** | string | -- | Environment name |
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
