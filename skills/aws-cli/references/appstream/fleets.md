# Fleets

### 1.1 `create-fleet`

Creates a new fleet to stream applications.

**Synopsis:**
```bash
aws appstream create-fleet \
    --name <value> \
    --instance-type <value> \
    [--fleet-type <value>] \
    [--compute-capacity <value>] \
    [--image-name <value>] \
    [--image-arn <value>] \
    [--vpc-config <value>] \
    [--max-concurrent-sessions <value>] \
    [--disconnect-timeout-in-seconds <value>] \
    [--description <value>] \
    [--display-name <value>] \
    [--enable-default-internet-access | --no-enable-default-internet-access] \
    [--domain-join-info <value>] \
    [--idle-disconnect-timeout-in-seconds <value>] \
    [--iam-role-arn <value>] \
    [--stream-view <value>] \
    [--platform <value>] \
    [--max-sessions-per-instance <value>] \
    [--session-script-s3-location <value>] \
    [--usb-device-filter-strings <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Unique name for the fleet |
| `--instance-type` | **Yes** | string | -- | Instance type (e.g., `stream.standard.medium`, `stream.standard.large`) |
| `--fleet-type` | No | string | `ALWAYS_ON` | Fleet type: `ALWAYS_ON`, `ON_DEMAND`, `ELASTIC` |
| `--compute-capacity` | No | structure | -- | Desired capacity. Shorthand: `DesiredInstances=integer,DesiredSessions=integer` |
| `--image-name` | No | string | -- | Name of the image to use |
| `--image-arn` | No | string | -- | ARN of the image to use |
| `--vpc-config` | No | structure | -- | VPC configuration. Shorthand: `SubnetIds=string,string,SecurityGroupIds=string,string` |
| `--max-concurrent-sessions` | No | integer | -- | Max concurrent sessions for elastic fleets |
| `--disconnect-timeout-in-seconds` | No | integer | 900 | Time before disconnected session ends (60-360000) |
| `--description` | No | string | -- | Description of the fleet |
| `--display-name` | No | string | -- | Display name of the fleet |
| `--enable-default-internet-access` | No | boolean | false | Enable default internet access |
| `--domain-join-info` | No | structure | -- | AD domain join info. Shorthand: `DirectoryName=string,OrganizationalUnitDistinguishedName=string` |
| `--idle-disconnect-timeout-in-seconds` | No | integer | 0 | Time before idle session disconnects (60-3600, 0=disabled) |
| `--iam-role-arn` | No | string | -- | IAM role ARN for fleet instances |
| `--stream-view` | No | string | `APP` | Stream view: `APP`, `DESKTOP` |
| `--platform` | No | string | -- | Platform: `WINDOWS`, `WINDOWS_SERVER_2016`, `WINDOWS_SERVER_2019`, `WINDOWS_SERVER_2022`, `AMAZON_LINUX2` |
| `--max-sessions-per-instance` | No | integer | -- | Max sessions per instance (multi-session fleets) |
| `--session-script-s3-location` | No | structure | -- | S3 location of session scripts. Shorthand: `S3Bucket=string,S3Key=string` |
| `--usb-device-filter-strings` | No | list(string) | -- | USB device filter strings |
| `--tags` | No | map | -- | Tags as key-value pairs |

**Output Schema:**
```json
{
    "Fleet": {
        "Arn": "string",
        "Name": "string",
        "DisplayName": "string",
        "Description": "string",
        "ImageName": "string",
        "ImageArn": "string",
        "InstanceType": "string",
        "FleetType": "ALWAYS_ON|ON_DEMAND|ELASTIC",
        "ComputeCapacityStatus": {
            "Desired": "integer",
            "Running": "integer",
            "InUse": "integer",
            "Available": "integer",
            "DesiredUserSessions": "integer",
            "AvailableUserSessions": "integer",
            "ActiveUserSessions": "integer",
            "ActualUserSessions": "integer"
        },
        "MaxConcurrentSessions": "integer",
        "MaxUserDurationInSeconds": "integer",
        "DisconnectTimeoutInSeconds": "integer",
        "State": "STARTING|RUNNING|STOPPING|STOPPED",
        "VpcConfig": {
            "SubnetIds": ["string"],
            "SecurityGroupIds": ["string"]
        },
        "CreatedTime": "timestamp",
        "FleetErrors": [
            {
                "ErrorCode": "string",
                "ErrorMessage": "string"
            }
        ],
        "EnableDefaultInternetAccess": "boolean",
        "DomainJoinInfo": {
            "DirectoryName": "string",
            "OrganizationalUnitDistinguishedName": "string"
        },
        "IdleDisconnectTimeoutInSeconds": "integer",
        "IamRoleArn": "string",
        "StreamView": "APP|DESKTOP",
        "Platform": "WINDOWS|WINDOWS_SERVER_2016|WINDOWS_SERVER_2019|WINDOWS_SERVER_2022|AMAZON_LINUX2",
        "MaxSessionsPerInstance": "integer",
        "UsbDeviceFilterStrings": ["string"],
        "SessionScriptS3Location": {
            "S3Bucket": "string",
            "S3Key": "string"
        }
    }
}
```

---

### 1.2 `delete-fleet`

Deletes a fleet. The fleet must be stopped before it can be deleted.

**Synopsis:**
```bash
aws appstream delete-fleet \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the fleet to delete |

**Output Schema:**
```json
{}
```

---

### 1.3 `describe-fleets`

Describes one or more fleets.

**Synopsis:**
```bash
aws appstream describe-fleets \
    [--names <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--names` | No | list(string) | -- | Names of the fleets to describe |
| `--next-token` | No | string | -- | Pagination token from previous response |

**Output Schema:**
```json
{
    "Fleets": [
        {
            "Arn": "string",
            "Name": "string",
            "DisplayName": "string",
            "Description": "string",
            "ImageName": "string",
            "ImageArn": "string",
            "InstanceType": "string",
            "FleetType": "ALWAYS_ON|ON_DEMAND|ELASTIC",
            "ComputeCapacityStatus": {
                "Desired": "integer",
                "Running": "integer",
                "InUse": "integer",
                "Available": "integer"
            },
            "State": "STARTING|RUNNING|STOPPING|STOPPED",
            "VpcConfig": {
                "SubnetIds": ["string"],
                "SecurityGroupIds": ["string"]
            },
            "CreatedTime": "timestamp",
            "FleetErrors": [],
            "EnableDefaultInternetAccess": "boolean",
            "DomainJoinInfo": {
                "DirectoryName": "string",
                "OrganizationalUnitDistinguishedName": "string"
            },
            "IdleDisconnectTimeoutInSeconds": "integer",
            "IamRoleArn": "string",
            "StreamView": "APP|DESKTOP",
            "Platform": "string",
            "MaxSessionsPerInstance": "integer"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.4 `update-fleet`

Updates the specified fleet. If the fleet is STOPPED, it can be started after the update. If RUNNING, changes take effect during the next instance replacement.

**Synopsis:**
```bash
aws appstream update-fleet \
    [--name <value>] \
    [--image-name <value>] \
    [--image-arn <value>] \
    [--instance-type <value>] \
    [--compute-capacity <value>] \
    [--vpc-config <value>] \
    [--max-concurrent-sessions <value>] \
    [--disconnect-timeout-in-seconds <value>] \
    [--description <value>] \
    [--display-name <value>] \
    [--enable-default-internet-access | --no-enable-default-internet-access] \
    [--domain-join-info <value>] \
    [--idle-disconnect-timeout-in-seconds <value>] \
    [--iam-role-arn <value>] \
    [--stream-view <value>] \
    [--platform <value>] \
    [--max-sessions-per-instance <value>] \
    [--session-script-s3-location <value>] \
    [--usb-device-filter-strings <value>] \
    [--attributes-to-delete <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | No | string | -- | Unique name of the fleet |
| `--image-name` | No | string | -- | Name of the image to use |
| `--image-arn` | No | string | -- | ARN of the image to use |
| `--instance-type` | No | string | -- | Instance type for fleet instances |
| `--compute-capacity` | No | structure | -- | Desired capacity |
| `--vpc-config` | No | structure | -- | VPC configuration |
| `--max-concurrent-sessions` | No | integer | -- | Max concurrent sessions |
| `--disconnect-timeout-in-seconds` | No | integer | -- | Disconnect timeout (60-360000) |
| `--description` | No | string | -- | Description of the fleet |
| `--display-name` | No | string | -- | Display name |
| `--enable-default-internet-access` | No | boolean | -- | Enable default internet access |
| `--domain-join-info` | No | structure | -- | AD domain join info |
| `--idle-disconnect-timeout-in-seconds` | No | integer | -- | Idle disconnect timeout |
| `--iam-role-arn` | No | string | -- | IAM role ARN |
| `--stream-view` | No | string | -- | Stream view: `APP`, `DESKTOP` |
| `--platform` | No | string | -- | Platform type |
| `--max-sessions-per-instance` | No | integer | -- | Max sessions per instance |
| `--session-script-s3-location` | No | structure | -- | Session script S3 location |
| `--usb-device-filter-strings` | No | list(string) | -- | USB device filter strings |
| `--attributes-to-delete` | No | list(string) | -- | Attributes to delete: `VPC_CONFIGURATION`, `VPC_CONFIGURATION_SECURITY_GROUP_IDS`, `DOMAIN_JOIN_INFO`, `IAM_ROLE_ARN`, `USB_DEVICE_FILTER_STRINGS`, `SESSION_SCRIPT_S3_LOCATION`, `MAX_SESSIONS_PER_INSTANCE` |

**Output Schema:**
```json
{
    "Fleet": {
        "Arn": "string",
        "Name": "string",
        "DisplayName": "string",
        "Description": "string",
        "ImageName": "string",
        "ImageArn": "string",
        "InstanceType": "string",
        "FleetType": "ALWAYS_ON|ON_DEMAND|ELASTIC",
        "ComputeCapacityStatus": {
            "Desired": "integer",
            "Running": "integer",
            "InUse": "integer",
            "Available": "integer"
        },
        "State": "STARTING|RUNNING|STOPPING|STOPPED",
        "VpcConfig": {},
        "CreatedTime": "timestamp",
        "FleetErrors": [],
        "EnableDefaultInternetAccess": "boolean",
        "DomainJoinInfo": {},
        "IdleDisconnectTimeoutInSeconds": "integer",
        "IamRoleArn": "string",
        "StreamView": "APP|DESKTOP",
        "Platform": "string"
    }
}
```

---

### 1.5 `start-fleet`

Starts the specified fleet.

**Synopsis:**
```bash
aws appstream start-fleet \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the fleet to start |

**Output Schema:**
```json
{}
```

---

### 1.6 `stop-fleet`

Stops the specified fleet.

**Synopsis:**
```bash
aws appstream stop-fleet \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the fleet to stop |

**Output Schema:**
```json
{}
```

---

### 1.7 `associate-fleet`

Associates the specified fleet with the specified stack.

**Synopsis:**
```bash
aws appstream associate-fleet \
    --fleet-name <value> \
    --stack-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fleet-name` | **Yes** | string | -- | Name of the fleet |
| `--stack-name` | **Yes** | string | -- | Name of the stack |

**Output Schema:**
```json
{}
```

---

### 1.8 `disassociate-fleet`

Disassociates the specified fleet from the specified stack.

**Synopsis:**
```bash
aws appstream disassociate-fleet \
    --fleet-name <value> \
    --stack-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fleet-name` | **Yes** | string | -- | Name of the fleet |
| `--stack-name` | **Yes** | string | -- | Name of the stack |

**Output Schema:**
```json
{}
```

---

### 1.9 `list-associated-fleets`

Lists the fleets associated with the specified stack.

**Synopsis:**
```bash
aws appstream list-associated-fleets \
    --stack-name <value> \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--stack-name` | **Yes** | string | -- | Name of the stack |
| `--next-token` | No | string | -- | Pagination token |

**Output Schema:**
```json
{
    "Names": ["string"],
    "NextToken": "string"
}
```

---

### 1.10 `list-associated-stacks`

Lists the stacks associated with the specified fleet.

**Synopsis:**
```bash
aws appstream list-associated-stacks \
    --fleet-name <value> \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--fleet-name` | **Yes** | string | -- | Name of the fleet |
| `--next-token` | No | string | -- | Pagination token |

**Output Schema:**
```json
{
    "Names": ["string"],
    "NextToken": "string"
}
```
