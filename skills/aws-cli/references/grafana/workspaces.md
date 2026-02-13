# Workspaces

### 1.1 `create-workspace`

Creates a new Amazon Managed Grafana workspace.

**Synopsis:**
```bash
aws grafana create-workspace \
    --account-access-type <value> \
    --authentication-providers <value> \
    --permission-type <value> \
    [--workspace-name <value>] \
    [--workspace-description <value>] \
    [--workspace-data-sources <value>] \
    [--workspace-notification-destinations <value>] \
    [--workspace-organizational-units <value>] \
    [--workspace-role-arn <value>] \
    [--stack-set-name <value>] \
    [--organization-role-name <value>] \
    [--configuration <value>] \
    [--grafana-version <value>] \
    [--network-access-control <value>] \
    [--vpc-configuration <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-access-type` | **Yes** | string | -- | Account access: `CURRENT_ACCOUNT`, `ORGANIZATION` |
| `--authentication-providers` | **Yes** | list(string) | -- | Auth providers: `AWS_SSO`, `SAML` |
| `--permission-type` | **Yes** | string | -- | Permission type: `SERVICE_MANAGED`, `CUSTOMER_MANAGED` |
| `--workspace-name` | No | string | None | Name of the workspace |
| `--workspace-description` | No | string | None | Description of the workspace |
| `--workspace-data-sources` | No | list(string) | None | Data sources to enable |
| `--workspace-notification-destinations` | No | list(string) | None | Notification destinations: `SNS` |
| `--workspace-organizational-units` | No | list(string) | None | Organizational units (for ORGANIZATION access) |
| `--workspace-role-arn` | No | string | None | IAM role ARN for the workspace |
| `--stack-set-name` | No | string | None | CloudFormation stack set name |
| `--organization-role-name` | No | string | None | Organization role name |
| `--configuration` | No | string | None | Workspace configuration JSON |
| `--grafana-version` | No | string | None | Grafana version (e.g., `9.4`, `10.4`) |
| `--network-access-control` | No | structure | None | Network access control. Shorthand: `prefixListIds=string,string,vpceIds=string,string` |
| `--vpc-configuration` | No | structure | None | VPC configuration. Shorthand: `securityGroupIds=string,string,subnetIds=string,string` |
| `--tags` | No | map | None | Tags. Shorthand: `KeyName1=string,KeyName2=string` |

**Output Schema:**
```json
{
    "workspace": {
        "accountAccessType": "CURRENT_ACCOUNT|ORGANIZATION",
        "authentication": {
            "providers": ["AWS_SSO|SAML"],
            "samlConfigurationStatus": "CONFIGURED|NOT_CONFIGURED"
        },
        "created": "timestamp",
        "dataSources": ["string"],
        "description": "string",
        "endpoint": "string",
        "freeTrialConsumed": true|false,
        "freeTrialExpiration": "timestamp",
        "grafanaToken": "string",
        "grafanaVersion": "string",
        "id": "string",
        "licenseExpiration": "timestamp",
        "licenseType": "ENTERPRISE|ENTERPRISE_FREE_TRIAL",
        "modified": "timestamp",
        "name": "string",
        "networkAccessControl": {
            "prefixListIds": ["string"],
            "vpceIds": ["string"]
        },
        "notificationDestinations": ["SNS"],
        "organizationRoleName": "string",
        "organizationalUnits": ["string"],
        "permissionType": "SERVICE_MANAGED|CUSTOMER_MANAGED",
        "stackSetName": "string",
        "status": "ACTIVE|CREATING|DELETING|FAILED|UPDATING|UPGRADING|DELETION_FAILED|CREATION_FAILED|UPDATE_FAILED|UPGRADE_FAILED|LICENSE_REMOVAL_FAILED|VERSION_UPDATING|VERSION_UPDATE_FAILED",
        "tags": {
            "string": "string"
        },
        "vpcConfiguration": {
            "securityGroupIds": ["string"],
            "subnetIds": ["string"]
        },
        "workspaceRoleArn": "string"
    }
}
```

---

### 1.2 `delete-workspace`

Deletes an Amazon Managed Grafana workspace.

**Synopsis:**
```bash
aws grafana delete-workspace \
    --workspace-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | The workspace ID to delete |

**Output Schema:**
```json
{
    "workspace": {
        "accountAccessType": "string",
        "authentication": {},
        "created": "timestamp",
        "dataSources": [],
        "description": "string",
        "endpoint": "string",
        "grafanaVersion": "string",
        "id": "string",
        "modified": "timestamp",
        "name": "string",
        "permissionType": "string",
        "status": "string",
        "tags": {}
    }
}
```

---

### 1.3 `describe-workspace`

Displays information about one Amazon Managed Grafana workspace.

**Synopsis:**
```bash
aws grafana describe-workspace \
    --workspace-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | The workspace ID |

**Output Schema:**
```json
{
    "workspace": {
        "accountAccessType": "CURRENT_ACCOUNT|ORGANIZATION",
        "authentication": {
            "providers": ["AWS_SSO|SAML"],
            "samlConfigurationStatus": "CONFIGURED|NOT_CONFIGURED"
        },
        "created": "timestamp",
        "dataSources": ["string"],
        "description": "string",
        "endpoint": "string",
        "freeTrialConsumed": true|false,
        "freeTrialExpiration": "timestamp",
        "grafanaToken": "string",
        "grafanaVersion": "string",
        "id": "string",
        "licenseExpiration": "timestamp",
        "licenseType": "ENTERPRISE|ENTERPRISE_FREE_TRIAL",
        "modified": "timestamp",
        "name": "string",
        "networkAccessControl": {
            "prefixListIds": ["string"],
            "vpceIds": ["string"]
        },
        "notificationDestinations": ["SNS"],
        "organizationRoleName": "string",
        "organizationalUnits": ["string"],
        "permissionType": "SERVICE_MANAGED|CUSTOMER_MANAGED",
        "stackSetName": "string",
        "status": "string",
        "tags": {},
        "vpcConfiguration": {
            "securityGroupIds": ["string"],
            "subnetIds": ["string"]
        },
        "workspaceRoleArn": "string"
    }
}
```

---

### 1.4 `list-workspaces`

Returns a list of Amazon Managed Grafana workspaces. **Paginated operation.**

**Synopsis:**
```bash
aws grafana list-workspaces \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "workspaces": [
        {
            "authentication": {
                "providers": ["AWS_SSO|SAML"],
                "samlConfigurationStatus": "CONFIGURED|NOT_CONFIGURED"
            },
            "created": "timestamp",
            "description": "string",
            "endpoint": "string",
            "grafanaToken": "string",
            "grafanaVersion": "string",
            "id": "string",
            "licenseType": "string",
            "modified": "timestamp",
            "name": "string",
            "notificationDestinations": [],
            "status": "string",
            "tags": {}
        }
    ],
    "nextToken": "string"
}
```

---

### 1.5 `update-workspace`

Modifies an existing Amazon Managed Grafana workspace.

**Synopsis:**
```bash
aws grafana update-workspace \
    --workspace-id <value> \
    [--workspace-name <value>] \
    [--workspace-description <value>] \
    [--account-access-type <value>] \
    [--permission-type <value>] \
    [--workspace-data-sources <value>] \
    [--workspace-notification-destinations <value>] \
    [--workspace-organizational-units <value>] \
    [--workspace-role-arn <value>] \
    [--stack-set-name <value>] \
    [--organization-role-name <value>] \
    [--network-access-control <value>] \
    [--vpc-configuration <value>] \
    [--remove-network-access-configuration | --no-remove-network-access-configuration] \
    [--remove-vpc-configuration | --no-remove-vpc-configuration] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | The workspace ID to update |
| `--workspace-name` | No | string | None | New name |
| `--workspace-description` | No | string | None | New description |
| `--account-access-type` | No | string | None | New account access type |
| `--permission-type` | No | string | None | New permission type |
| `--workspace-data-sources` | No | list(string) | None | Updated data sources |
| `--workspace-notification-destinations` | No | list(string) | None | Updated notification destinations |
| `--workspace-organizational-units` | No | list(string) | None | Updated organizational units |
| `--workspace-role-arn` | No | string | None | New workspace role ARN |
| `--stack-set-name` | No | string | None | New stack set name |
| `--organization-role-name` | No | string | None | New organization role name |
| `--network-access-control` | No | structure | None | Updated network access control |
| `--vpc-configuration` | No | structure | None | Updated VPC configuration |
| `--remove-network-access-configuration` | No | boolean | false | Remove network access control |
| `--remove-vpc-configuration` | No | boolean | false | Remove VPC configuration |

**Output Schema:**
```json
{
    "workspace": {
        "accountAccessType": "string",
        "authentication": {},
        "created": "timestamp",
        "dataSources": [],
        "description": "string",
        "endpoint": "string",
        "grafanaVersion": "string",
        "id": "string",
        "modified": "timestamp",
        "name": "string",
        "permissionType": "string",
        "status": "string",
        "tags": {}
    }
}
```

---

### 1.6 `describe-workspace-configuration`

Gets the current configuration of the workspace.

**Synopsis:**
```bash
aws grafana describe-workspace-configuration \
    --workspace-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | The workspace ID |

**Output Schema:**
```json
{
    "configuration": "string",
    "grafanaVersion": "string"
}
```

---

### 1.7 `update-workspace-configuration`

Updates the configuration of the workspace. Configuration is a JSON string containing plugin management and unified alerting settings.

**Synopsis:**
```bash
aws grafana update-workspace-configuration \
    --workspace-id <value> \
    --configuration <value> \
    [--grafana-version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | **Yes** | string | -- | The workspace ID |
| `--configuration` | **Yes** | string | -- | Configuration JSON string |
| `--grafana-version` | No | string | None | Grafana version to use |

**Configuration Example:**
```json
{
    "plugins": {
        "pluginAdminEnabled": true
    },
    "unifiedAlerting": {
        "enabled": true
    }
}
```

**Output Schema:**
```json
{}
```

---

### 1.8 `list-versions`

Lists available Grafana versions for creating or updating workspaces. **Paginated operation.**

**Synopsis:**
```bash
aws grafana list-versions \
    [--workspace-id <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--workspace-id` | No | string | None | Workspace ID to filter compatible versions |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "grafanaVersions": ["string"],
    "nextToken": "string"
}
```
