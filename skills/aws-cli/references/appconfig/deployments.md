# Deployments

### 5.1 `start-deployment`

Starts a configuration deployment to the designated targets.

**Synopsis:**
```bash
aws appconfig start-deployment \
    --application-id <value> \
    --environment-id <value> \
    --deployment-strategy-id <value> \
    --configuration-profile-id <value> \
    --configuration-version <value> \
    [--description <value>] \
    [--tags <value>] \
    [--kms-key-identifier <value>] \
    [--dynamic-extension-parameters <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application ID |
| `--environment-id` | **Yes** | string | -- | Environment ID |
| `--deployment-strategy-id` | **Yes** | string | -- | Deployment strategy ID |
| `--configuration-profile-id` | **Yes** | string | -- | Configuration profile ID |
| `--configuration-version` | **Yes** | string | -- | Version to deploy (1-1024 chars) |
| `--description` | No | string | None | Description (0-1024 chars) |
| `--tags` | No | map | None | Tags (max 50) |
| `--kms-key-identifier` | No | string | None | KMS key for encryption (1-2048 chars) |
| `--dynamic-extension-parameters` | No | map | None | Parameters for PRE_START_DEPLOYMENT extension actions (1-10) |

**Output Schema:**
```json
{
    "ApplicationId": "string",
    "EnvironmentId": "string",
    "DeploymentStrategyId": "string",
    "ConfigurationProfileId": "string",
    "DeploymentNumber": "integer",
    "ConfigurationName": "string",
    "ConfigurationLocationUri": "string",
    "ConfigurationVersion": "string",
    "Description": "string",
    "DeploymentDurationInMinutes": "integer",
    "GrowthType": "LINEAR|EXPONENTIAL",
    "GrowthFactor": "float",
    "FinalBakeTimeInMinutes": "integer",
    "State": "BAKING|VALIDATING|DEPLOYING|COMPLETE|ROLLING_BACK|ROLLED_BACK|REVERTED",
    "EventLog": [
        {
            "EventType": "PERCENTAGE_UPDATED|ROLLBACK_STARTED|ROLLBACK_COMPLETED|BAKE_TIME_STARTED|DEPLOYMENT_STARTED|DEPLOYMENT_COMPLETED|REVERT_COMPLETED",
            "TriggeredBy": "USER|APPCONFIG|CLOUDWATCH_ALARM|INTERNAL_ERROR",
            "Description": "string",
            "ActionInvocations": [
                {
                    "ExtensionIdentifier": "string",
                    "ActionName": "string",
                    "Uri": "string",
                    "RoleArn": "string",
                    "ErrorMessage": "string",
                    "ErrorCode": "string",
                    "InvocationId": "string"
                }
            ],
            "OccurredAt": "timestamp"
        }
    ],
    "PercentageComplete": "float",
    "StartedAt": "timestamp",
    "CompletedAt": "timestamp",
    "AppliedExtensions": [
        {
            "ExtensionId": "string",
            "ExtensionAssociationId": "string",
            "VersionNumber": "integer",
            "Parameters": {}
        }
    ],
    "KmsKeyArn": "string",
    "KmsKeyIdentifier": "string",
    "VersionLabel": "string"
}
```

---

### 5.2 `get-deployment`

Retrieves deployment details.

**Synopsis:**
```bash
aws appconfig get-deployment \
    --application-id <value> \
    --environment-id <value> \
    --deployment-number <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application ID |
| `--environment-id` | **Yes** | string | -- | Environment ID |
| `--deployment-number` | **Yes** | integer | -- | Deployment sequence number |

**Output Schema:**
```json
{
    "ApplicationId": "string",
    "EnvironmentId": "string",
    "DeploymentStrategyId": "string",
    "ConfigurationProfileId": "string",
    "DeploymentNumber": "integer",
    "ConfigurationName": "string",
    "ConfigurationLocationUri": "string",
    "ConfigurationVersion": "string",
    "Description": "string",
    "DeploymentDurationInMinutes": "integer",
    "GrowthType": "LINEAR|EXPONENTIAL",
    "GrowthFactor": "float",
    "FinalBakeTimeInMinutes": "integer",
    "State": "BAKING|VALIDATING|DEPLOYING|COMPLETE|ROLLING_BACK|ROLLED_BACK|REVERTED",
    "EventLog": [],
    "PercentageComplete": "float",
    "StartedAt": "timestamp",
    "CompletedAt": "timestamp",
    "AppliedExtensions": [],
    "KmsKeyArn": "string",
    "KmsKeyIdentifier": "string",
    "VersionLabel": "string"
}
```

---

### 5.3 `list-deployments`

Lists deployments for an environment. **Paginated operation.**

**Synopsis:**
```bash
aws appconfig list-deployments \
    --application-id <value> \
    --environment-id <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application ID |
| `--environment-id` | **Yes** | string | -- | Environment ID |
| `--max-results` | No | integer | None | Max results per page (1-50) |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "Items": [
        {
            "DeploymentNumber": "integer",
            "ConfigurationName": "string",
            "ConfigurationVersion": "string",
            "DeploymentDurationInMinutes": "integer",
            "GrowthType": "LINEAR|EXPONENTIAL",
            "GrowthFactor": "float",
            "FinalBakeTimeInMinutes": "integer",
            "State": "BAKING|VALIDATING|DEPLOYING|COMPLETE|ROLLING_BACK|ROLLED_BACK|REVERTED",
            "PercentageComplete": "float",
            "StartedAt": "timestamp",
            "CompletedAt": "timestamp",
            "VersionLabel": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 5.4 `stop-deployment`

Stops a deployment. This API action works only on deployments that are in a DEPLOYING state. The stop action attempts to cancel the deployment, resulting in a ROLLED_BACK state.

**Synopsis:**
```bash
aws appconfig stop-deployment \
    --application-id <value> \
    --environment-id <value> \
    --deployment-number <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application ID |
| `--environment-id` | **Yes** | string | -- | Environment ID |
| `--deployment-number` | **Yes** | integer | -- | Deployment sequence number to stop |

**Output Schema:**
```json
{
    "ApplicationId": "string",
    "EnvironmentId": "string",
    "DeploymentStrategyId": "string",
    "ConfigurationProfileId": "string",
    "DeploymentNumber": "integer",
    "ConfigurationName": "string",
    "ConfigurationVersion": "string",
    "State": "ROLLING_BACK|ROLLED_BACK",
    "EventLog": [],
    "PercentageComplete": "float",
    "StartedAt": "timestamp",
    "CompletedAt": "timestamp"
}
```
