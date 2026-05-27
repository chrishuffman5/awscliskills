# Directories

### 3.1 `register-workspace-directory`

Registers the specified directory for use with Amazon WorkSpaces.

**Synopsis:**
```bash
aws workspaces register-workspace-directory \
    [--directory-id <value>] \
    [--subnet-ids <value>] \
    [--enable-work-docs | --no-enable-work-docs] \
    [--enable-self-service | --no-enable-self-service] \
    [--tenancy <value>] \
    [--tags <value>] \
    [--workspace-directory-name <value>] \
    [--workspace-directory-description <value>] \
    [--user-identity-type <value>] \
    [--workspace-type <value>] \
    [--active-directory-config <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | No | string | None | The directory ID to register (for AD Connector or Microsoft AD) |
| `--subnet-ids` | No | list(string) | None | Subnet IDs of the VPC (exactly 2 subnets in different AZs) |
| `--enable-work-docs` | No | boolean | false | Enable Amazon WorkDocs for the directory |
| `--enable-self-service` | No | boolean | false | Enable self-service capabilities |
| `--tenancy` | No | string | `SHARED` | Tenancy: `DEDICATED` or `SHARED` |
| `--tags` | No | list | None | Tags to associate. Shorthand: `Key=string,Value=string ...` |
| `--workspace-directory-name` | No | string | None | Name for the WorkSpace directory |
| `--workspace-directory-description` | No | string | None | Description for the WorkSpace directory |
| `--user-identity-type` | No | string | None | Identity type: `CUSTOMER_MANAGED`, `AWS_DIRECTORY_SERVICE` |
| `--workspace-type` | No | string | None | WorkSpace type: `PERSONAL`, `POOLS` |
| `--active-directory-config` | No | structure | None | Active directory configuration |

**Output Schema:**
```json
{
    "DirectoryId": "string",
    "State": "REGISTERING|REGISTERED|DEREGISTERING|DEREGISTERED|ERROR"
}
```

---

### 3.2 `deregister-workspace-directory`

Deregisters the specified directory. This operation is asynchronous and returns before the directory is deregistered.

**Synopsis:**
```bash
aws workspaces deregister-workspace-directory \
    --directory-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-id` | **Yes** | string | -- | The directory ID to deregister |

**Output Schema:**
```json
{}
```

---

### 3.3 `describe-workspace-directories`

Describes the specified WorkSpace directories or all directories. **Paginated operation.**

**Synopsis:**
```bash
aws workspaces describe-workspace-directories \
    [--directory-ids <value>] \
    [--workspace-directory-names <value>] \
    [--limit <value>] \
    [--starting-token <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--directory-ids` | No | list(string) | None | One or more directory IDs (max 25) |
| `--workspace-directory-names` | No | list(string) | None | Filter by directory names |
| `--limit` | No | integer | None | Maximum number of items to return |
| `--starting-token` | No | string | None | Pagination token |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Directories": [
        {
            "DirectoryId": "string",
            "Alias": "string",
            "DirectoryName": "string",
            "RegistrationCode": "string",
            "SubnetIds": ["string"],
            "DnsIpAddresses": ["string"],
            "CustomerUserName": "string",
            "IamRoleId": "string",
            "DirectoryType": "SIMPLE_AD|AD_CONNECTOR|CUSTOMER_MANAGED",
            "WorkspaceSecurityGroupId": "string",
            "State": "REGISTERING|REGISTERED|DEREGISTERING|DEREGISTERED|ERROR",
            "WorkspaceCreationProperties": {
                "EnableWorkDocs": true|false,
                "EnableInternetAccess": true|false,
                "DefaultOu": "string",
                "CustomSecurityGroupId": "string",
                "UserEnabledAsLocalAdministrator": true|false,
                "EnableMaintenanceMode": true|false,
                "InstanceIamRoleArn": "string"
            },
            "WorkspaceAccessProperties": {
                "DeviceTypeWindows": "ALLOW|DENY",
                "DeviceTypeOsx": "ALLOW|DENY",
                "DeviceTypeWeb": "ALLOW|DENY",
                "DeviceTypeIos": "ALLOW|DENY",
                "DeviceTypeAndroid": "ALLOW|DENY",
                "DeviceTypeChromeOs": "ALLOW|DENY",
                "DeviceTypeZeroClient": "ALLOW|DENY",
                "DeviceTypeLinux": "ALLOW|DENY"
            },
            "Tenancy": "DEDICATED|SHARED",
            "SelfservicePermissions": {
                "RestartWorkspace": "ENABLED|DISABLED",
                "IncreaseVolumeSize": "ENABLED|DISABLED",
                "ChangeComputeType": "ENABLED|DISABLED",
                "SwitchRunningMode": "ENABLED|DISABLED",
                "RebuildWorkspace": "ENABLED|DISABLED"
            },
            "SamlProperties": {
                "Status": "DISABLED|ENABLED|ENABLED_WITH_DIRECTORY_LOGIN_FALLBACK",
                "UserAccessUrl": "string",
                "RelayStateParameterName": "string"
            },
            "CertificateBasedAuthProperties": {
                "Status": "DISABLED|ENABLED",
                "CertificateAuthorityArn": "string"
            },
            "WorkspaceDirectoryName": "string",
            "WorkspaceDirectoryDescription": "string",
            "UserIdentityType": "CUSTOMER_MANAGED|AWS_DIRECTORY_SERVICE",
            "WorkspaceType": "PERSONAL|POOLS",
            "ErrorMessage": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.4 `modify-workspace-creation-properties`

Modifies the default workspace creation properties for the specified directory.

**Synopsis:**
```bash
aws workspaces modify-workspace-creation-properties \
    --resource-id <value> \
    --workspace-creation-properties <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-id` | **Yes** | string | -- | The directory ID |
| `--workspace-creation-properties` | **Yes** | structure | -- | Default creation properties |

**Creation Properties Structure:**
```json
{
    "EnableWorkDocs": true|false,
    "EnableInternetAccess": true|false,
    "DefaultOu": "string",
    "CustomSecurityGroupId": "string",
    "UserEnabledAsLocalAdministrator": true|false,
    "EnableMaintenanceMode": true|false,
    "InstanceIamRoleArn": "string"
}
```

**Output Schema:**
```json
{}
```

---

### 3.5 `modify-workspace-access-properties`

Modifies the access properties for a WorkSpace directory.

**Synopsis:**
```bash
aws workspaces modify-workspace-access-properties \
    --resource-id <value> \
    --workspace-access-properties <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-id` | **Yes** | string | -- | The directory ID |
| `--workspace-access-properties` | **Yes** | structure | -- | Access properties for device types |

**Access Properties Structure:**
```json
{
    "DeviceTypeWindows": "ALLOW|DENY",
    "DeviceTypeOsx": "ALLOW|DENY",
    "DeviceTypeWeb": "ALLOW|DENY",
    "DeviceTypeIos": "ALLOW|DENY",
    "DeviceTypeAndroid": "ALLOW|DENY",
    "DeviceTypeChromeOs": "ALLOW|DENY",
    "DeviceTypeZeroClient": "ALLOW|DENY",
    "DeviceTypeLinux": "ALLOW|DENY"
}
```

**Output Schema:**
```json
{}
```

---

### 3.6 `modify-selfservice-permissions`

Modifies the self-service WorkSpace management capabilities for users.

**Synopsis:**
```bash
aws workspaces modify-selfservice-permissions \
    --resource-id <value> \
    --selfservice-permissions <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-id` | **Yes** | string | -- | The directory ID |
| `--selfservice-permissions` | **Yes** | structure | -- | Self-service permissions |

**Selfservice Permissions Structure:**
```json
{
    "RestartWorkspace": "ENABLED|DISABLED",
    "IncreaseVolumeSize": "ENABLED|DISABLED",
    "ChangeComputeType": "ENABLED|DISABLED",
    "SwitchRunningMode": "ENABLED|DISABLED",
    "RebuildWorkspace": "ENABLED|DISABLED"
}
```

**Output Schema:**
```json
{}
```

---

### 3.7 `modify-client-properties`

Modifies the client properties of the specified resource.

**Synopsis:**
```bash
aws workspaces modify-client-properties \
    --resource-id <value> \
    --client-properties <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-id` | **Yes** | string | -- | The resource ID (directory ID) |
| `--client-properties` | **Yes** | structure | -- | Client properties. Shorthand: `ReconnectEnabled=ENABLED\|DISABLED,LogUploadEnabled=ENABLED\|DISABLED` |

**Output Schema:**
```json
{}
```

---

### 3.8 `describe-client-properties`

Describes the client properties for the specified resources.

**Synopsis:**
```bash
aws workspaces describe-client-properties \
    --resource-ids <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-ids` | **Yes** | list(string) | -- | One or more resource IDs (directory IDs) |

**Output Schema:**
```json
{
    "ClientPropertiesList": [
        {
            "ResourceId": "string",
            "ClientProperties": {
                "ReconnectEnabled": "ENABLED|DISABLED",
                "LogUploadEnabled": "ENABLED|DISABLED"
            }
        }
    ]
}
```
