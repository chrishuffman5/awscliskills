# App Blocks

### 5.1 `create-app-block`

Creates an app block. App blocks store details about the virtual hard disk containing application files.

**Synopsis:**
```bash
aws appstream create-app-block \
    --name <value> \
    --source-s3-location <value> \
    [--description <value>] \
    [--display-name <value>] \
    [--setup-script-details <value>] \
    [--post-setup-script-details <value>] \
    [--packaging-type <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Unique name for the app block |
| `--source-s3-location` | **Yes** | structure | -- | S3 location of the app block source. Shorthand: `S3Bucket=string,S3Key=string` |
| `--description` | No | string | -- | Description of the app block |
| `--display-name` | No | string | -- | Display name |
| `--setup-script-details` | No | structure | -- | Setup script details. Shorthand: `ScriptS3Location={S3Bucket=string,S3Key=string},ExecutablePath=string,ExecutableParameters=string,TimeoutInSeconds=integer` |
| `--post-setup-script-details` | No | structure | -- | Post-setup script details (same structure as setup script) |
| `--packaging-type` | No | string | `CUSTOM` | Packaging type: `CUSTOM`, `APPSTREAM2` |
| `--tags` | No | map | -- | Tags as key-value pairs |

**Output Schema:**
```json
{
    "AppBlock": {
        "Name": "string",
        "Arn": "string",
        "Description": "string",
        "DisplayName": "string",
        "SourceS3Location": {
            "S3Bucket": "string",
            "S3Key": "string"
        },
        "SetupScriptDetails": {
            "ScriptS3Location": {
                "S3Bucket": "string",
                "S3Key": "string"
            },
            "ExecutablePath": "string",
            "ExecutableParameters": "string",
            "TimeoutInSeconds": "integer"
        },
        "PostSetupScriptDetails": {
            "ScriptS3Location": {
                "S3Bucket": "string",
                "S3Key": "string"
            },
            "ExecutablePath": "string",
            "ExecutableParameters": "string",
            "TimeoutInSeconds": "integer"
        },
        "PackagingType": "CUSTOM|APPSTREAM2",
        "State": "INACTIVE|ACTIVE",
        "AppBlockErrors": [
            {
                "ErrorCode": "string",
                "ErrorMessage": "string"
            }
        ],
        "CreatedTime": "timestamp"
    }
}
```

---

### 5.2 `delete-app-block`

Deletes an app block.

**Synopsis:**
```bash
aws appstream delete-app-block \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the app block to delete |

**Output Schema:**
```json
{}
```

---

### 5.3 `describe-app-blocks`

Describes app blocks.

**Synopsis:**
```bash
aws appstream describe-app-blocks \
    [--arns <value>] \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arns` | No | list(string) | -- | ARNs of the app blocks to describe |
| `--next-token` | No | string | -- | Pagination token |
| `--max-results` | No | integer | -- | Maximum number of results |

**Output Schema:**
```json
{
    "AppBlocks": [
        {
            "Name": "string",
            "Arn": "string",
            "Description": "string",
            "DisplayName": "string",
            "SourceS3Location": {
                "S3Bucket": "string",
                "S3Key": "string"
            },
            "SetupScriptDetails": {},
            "PostSetupScriptDetails": {},
            "PackagingType": "CUSTOM|APPSTREAM2",
            "State": "INACTIVE|ACTIVE",
            "AppBlockErrors": [],
            "CreatedTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 5.4 `create-app-block-builder`

Creates an app block builder. App block builders are used to package applications into app blocks.

**Synopsis:**
```bash
aws appstream create-app-block-builder \
    --name <value> \
    --instance-type <value> \
    --platform <value> \
    --vpc-config <value> \
    [--description <value>] \
    [--display-name <value>] \
    [--enable-default-internet-access | --no-enable-default-internet-access] \
    [--iam-role-arn <value>] \
    [--access-endpoints <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Unique name for the app block builder |
| `--instance-type` | **Yes** | string | -- | Instance type |
| `--platform` | **Yes** | string | -- | Platform: `WINDOWS_SERVER_2019` |
| `--vpc-config` | **Yes** | structure | -- | VPC configuration. Shorthand: `SubnetIds=string,string,SecurityGroupIds=string,string` |
| `--description` | No | string | -- | Description |
| `--display-name` | No | string | -- | Display name |
| `--enable-default-internet-access` | No | boolean | false | Enable default internet access |
| `--iam-role-arn` | No | string | -- | IAM role ARN |
| `--access-endpoints` | No | list | -- | Access endpoints |
| `--tags` | No | map | -- | Tags |

**Output Schema:**
```json
{
    "AppBlockBuilder": {
        "Arn": "string",
        "Name": "string",
        "DisplayName": "string",
        "Description": "string",
        "Platform": "WINDOWS_SERVER_2019",
        "InstanceType": "string",
        "EnableDefaultInternetAccess": "boolean",
        "IamRoleArn": "string",
        "VpcConfig": {
            "SubnetIds": ["string"],
            "SecurityGroupIds": ["string"]
        },
        "State": "STARTING|RUNNING|STOPPING|STOPPED",
        "CreatedTime": "timestamp",
        "StateChangeReason": {
            "Code": "INTERNAL_ERROR",
            "Message": "string"
        },
        "AccessEndpoints": [
            {
                "EndpointType": "STREAMING",
                "VpceId": "string"
            }
        ],
        "AppBlockBuilderErrors": [
            {
                "ErrorCode": "string",
                "ErrorMessage": "string",
                "ErrorTimestamp": "timestamp"
            }
        ]
    }
}
```

---

### 5.5 `delete-app-block-builder`

Deletes an app block builder. The builder must be in STOPPED state.

**Synopsis:**
```bash
aws appstream delete-app-block-builder \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the app block builder to delete |

**Output Schema:**
```json
{}
```

---

### 5.6 `describe-app-block-builders`

Describes app block builders.

**Synopsis:**
```bash
aws appstream describe-app-block-builders \
    [--names <value>] \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--names` | No | list(string) | -- | Names of the app block builders to describe |
| `--next-token` | No | string | -- | Pagination token |
| `--max-results` | No | integer | -- | Maximum number of results |

**Output Schema:**
```json
{
    "AppBlockBuilders": [
        {
            "Arn": "string",
            "Name": "string",
            "DisplayName": "string",
            "Description": "string",
            "Platform": "string",
            "InstanceType": "string",
            "EnableDefaultInternetAccess": "boolean",
            "IamRoleArn": "string",
            "VpcConfig": {},
            "State": "STARTING|RUNNING|STOPPING|STOPPED",
            "CreatedTime": "timestamp",
            "StateChangeReason": {},
            "AccessEndpoints": [],
            "AppBlockBuilderErrors": []
        }
    ],
    "NextToken": "string"
}
```

---

### 5.7 `update-app-block-builder`

Updates the specified app block builder.

**Synopsis:**
```bash
aws appstream update-app-block-builder \
    --name <value> \
    [--description <value>] \
    [--display-name <value>] \
    [--platform <value>] \
    [--instance-type <value>] \
    [--vpc-config <value>] \
    [--enable-default-internet-access | --no-enable-default-internet-access] \
    [--iam-role-arn <value>] \
    [--access-endpoints <value>] \
    [--attributes-to-delete <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the app block builder to update |
| `--description` | No | string | -- | Description |
| `--display-name` | No | string | -- | Display name |
| `--platform` | No | string | -- | Platform |
| `--instance-type` | No | string | -- | Instance type |
| `--vpc-config` | No | structure | -- | VPC configuration |
| `--enable-default-internet-access` | No | boolean | -- | Enable default internet access |
| `--iam-role-arn` | No | string | -- | IAM role ARN |
| `--access-endpoints` | No | list | -- | Access endpoints |
| `--attributes-to-delete` | No | list(string) | -- | Attributes to delete: `IAM_ROLE_ARN`, `ACCESS_ENDPOINTS`, `VPC_CONFIGURATION_SECURITY_GROUP_IDS` |

**Output Schema:**
```json
{
    "AppBlockBuilder": {
        "Arn": "string",
        "Name": "string",
        "DisplayName": "string",
        "Description": "string",
        "Platform": "string",
        "InstanceType": "string",
        "EnableDefaultInternetAccess": "boolean",
        "IamRoleArn": "string",
        "VpcConfig": {},
        "State": "STARTING|RUNNING|STOPPING|STOPPED",
        "CreatedTime": "timestamp",
        "StateChangeReason": {},
        "AccessEndpoints": [],
        "AppBlockBuilderErrors": []
    }
}
```

---

### 5.8 `start-app-block-builder`

Starts an app block builder.

**Synopsis:**
```bash
aws appstream start-app-block-builder \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the app block builder to start |

**Output Schema:**
```json
{
    "AppBlockBuilder": {
        "Arn": "string",
        "Name": "string",
        "State": "STARTING|RUNNING|STOPPING|STOPPED",
        "InstanceType": "string",
        "Platform": "string",
        "CreatedTime": "timestamp"
    }
}
```

---

### 5.9 `stop-app-block-builder`

Stops an app block builder.

**Synopsis:**
```bash
aws appstream stop-app-block-builder \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the app block builder to stop |

**Output Schema:**
```json
{
    "AppBlockBuilder": {
        "Arn": "string",
        "Name": "string",
        "State": "STARTING|RUNNING|STOPPING|STOPPED",
        "InstanceType": "string",
        "Platform": "string",
        "CreatedTime": "timestamp"
    }
}
```
