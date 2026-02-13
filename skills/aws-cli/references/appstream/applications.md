# Applications

### 6.1 `create-application`

Creates an application within a specified app block.

**Synopsis:**
```bash
aws appstream create-application \
    --name <value> \
    --icon-s3-location <value> \
    --launch-path <value> \
    --platforms <value> \
    --instance-families <value> \
    --app-block-arn <value> \
    [--display-name <value>] \
    [--description <value>] \
    [--working-directory <value>] \
    [--launch-parameters <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Unique name for the application |
| `--icon-s3-location` | **Yes** | structure | -- | S3 location of the icon. Shorthand: `S3Bucket=string,S3Key=string` |
| `--launch-path` | **Yes** | string | -- | Path to the application executable |
| `--platforms` | **Yes** | list(string) | -- | Platforms: `WINDOWS`, `WINDOWS_SERVER_2016`, `WINDOWS_SERVER_2019`, `WINDOWS_SERVER_2022`, `AMAZON_LINUX2` |
| `--instance-families` | **Yes** | list(string) | -- | Instance families: `GENERAL_PURPOSE`, `GRAPHICS_G4DN`, `GRAPHICS_PRO`, `GRAPHICS_G5` |
| `--app-block-arn` | **Yes** | string | -- | ARN of the app block |
| `--display-name` | No | string | -- | Display name |
| `--description` | No | string | -- | Description |
| `--working-directory` | No | string | -- | Working directory for the application |
| `--launch-parameters` | No | string | -- | Launch parameters |
| `--tags` | No | map | -- | Tags as key-value pairs |

**Output Schema:**
```json
{
    "Application": {
        "Name": "string",
        "DisplayName": "string",
        "IconURL": "string",
        "IconS3Location": {
            "S3Bucket": "string",
            "S3Key": "string"
        },
        "LaunchPath": "string",
        "LaunchParameters": "string",
        "Enabled": "boolean",
        "Metadata": {
            "string": "string"
        },
        "WorkingDirectory": "string",
        "Description": "string",
        "Arn": "string",
        "AppBlockArn": "string",
        "Platforms": ["WINDOWS|WINDOWS_SERVER_2016|WINDOWS_SERVER_2019|WINDOWS_SERVER_2022|AMAZON_LINUX2"],
        "InstanceFamilies": ["GENERAL_PURPOSE|GRAPHICS_G4DN|GRAPHICS_PRO|GRAPHICS_G5"],
        "CreatedTime": "timestamp"
    }
}
```

---

### 6.2 `delete-application`

Deletes the specified application.

**Synopsis:**
```bash
aws appstream delete-application \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the application to delete |

**Output Schema:**
```json
{}
```

---

### 6.3 `describe-applications`

Describes applications.

**Synopsis:**
```bash
aws appstream describe-applications \
    [--arns <value>] \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arns` | No | list(string) | -- | ARNs of the applications to describe |
| `--next-token` | No | string | -- | Pagination token |
| `--max-results` | No | integer | -- | Maximum number of results |

**Output Schema:**
```json
{
    "Applications": [
        {
            "Name": "string",
            "DisplayName": "string",
            "IconURL": "string",
            "IconS3Location": {},
            "LaunchPath": "string",
            "LaunchParameters": "string",
            "Enabled": "boolean",
            "Metadata": {},
            "WorkingDirectory": "string",
            "Description": "string",
            "Arn": "string",
            "AppBlockArn": "string",
            "Platforms": ["string"],
            "InstanceFamilies": ["string"],
            "CreatedTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 6.4 `update-application`

Updates the specified application.

**Synopsis:**
```bash
aws appstream update-application \
    --name <value> \
    [--display-name <value>] \
    [--description <value>] \
    [--icon-s3-location <value>] \
    [--launch-path <value>] \
    [--working-directory <value>] \
    [--launch-parameters <value>] \
    [--app-block-arn <value>] \
    [--attributes-to-delete <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the application to update |
| `--display-name` | No | string | -- | Display name |
| `--description` | No | string | -- | Description |
| `--icon-s3-location` | No | structure | -- | S3 location of the icon |
| `--launch-path` | No | string | -- | Path to the application executable |
| `--working-directory` | No | string | -- | Working directory |
| `--launch-parameters` | No | string | -- | Launch parameters |
| `--app-block-arn` | No | string | -- | ARN of the app block |
| `--attributes-to-delete` | No | list(string) | -- | Attributes to delete: `LAUNCH_PARAMETERS`, `WORKING_DIRECTORY` |

**Output Schema:**
```json
{
    "Application": {
        "Name": "string",
        "DisplayName": "string",
        "IconURL": "string",
        "IconS3Location": {},
        "LaunchPath": "string",
        "LaunchParameters": "string",
        "Enabled": "boolean",
        "WorkingDirectory": "string",
        "Description": "string",
        "Arn": "string",
        "AppBlockArn": "string",
        "Platforms": ["string"],
        "InstanceFamilies": ["string"],
        "CreatedTime": "timestamp"
    }
}
```

---

### 6.5 `associate-application-fleet`

Associates an application with a fleet.

**Synopsis:**
```bash
aws appstream associate-application-fleet \
    --fleet-name <value> \
    --application-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fleet-name` | **Yes** | string | -- | Name of the fleet |
| `--application-arn` | **Yes** | string | -- | ARN of the application |

**Output Schema:**
```json
{
    "ApplicationFleetAssociation": {
        "FleetName": "string",
        "ApplicationArn": "string"
    }
}
```

---

### 6.6 `disassociate-application-fleet`

Disassociates an application from a fleet.

**Synopsis:**
```bash
aws appstream disassociate-application-fleet \
    --fleet-name <value> \
    --application-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fleet-name` | **Yes** | string | -- | Name of the fleet |
| `--application-arn` | **Yes** | string | -- | ARN of the application |

**Output Schema:**
```json
{}
```

---

### 6.7 `describe-application-fleet-associations`

Describes the associations between applications and fleets.

**Synopsis:**
```bash
aws appstream describe-application-fleet-associations \
    [--fleet-name <value>] \
    [--application-arn <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fleet-name` | No | string | -- | Name of the fleet to filter by |
| `--application-arn` | No | string | -- | ARN of the application to filter by |
| `--max-results` | No | integer | -- | Maximum number of results |
| `--next-token` | No | string | -- | Pagination token |

**Output Schema:**
```json
{
    "ApplicationFleetAssociations": [
        {
            "FleetName": "string",
            "ApplicationArn": "string"
        }
    ],
    "NextToken": "string"
}
```
