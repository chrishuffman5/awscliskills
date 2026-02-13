# Image Builders

### 4.1 `create-image-builder`

Creates a new image builder instance used to create custom images.

**Synopsis:**
```bash
aws appstream create-image-builder \
    --name <value> \
    --instance-type <value> \
    [--image-name <value>] \
    [--image-arn <value>] \
    [--description <value>] \
    [--display-name <value>] \
    [--vpc-config <value>] \
    [--enable-default-internet-access | --no-enable-default-internet-access] \
    [--domain-join-info <value>] \
    [--iam-role-arn <value>] \
    [--appstream-agent-version <value>] \
    [--access-endpoints <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Unique name for the image builder |
| `--instance-type` | **Yes** | string | -- | Instance type (e.g., `stream.standard.medium`) |
| `--image-name` | No | string | -- | Name of the image to use |
| `--image-arn` | No | string | -- | ARN of the image to use |
| `--description` | No | string | -- | Description of the image builder |
| `--display-name` | No | string | -- | Display name |
| `--vpc-config` | No | structure | -- | VPC configuration. Shorthand: `SubnetIds=string,string,SecurityGroupIds=string,string` |
| `--enable-default-internet-access` | No | boolean | false | Enable default internet access |
| `--domain-join-info` | No | structure | -- | AD domain join info. Shorthand: `DirectoryName=string,OrganizationalUnitDistinguishedName=string` |
| `--iam-role-arn` | No | string | -- | IAM role ARN for the image builder |
| `--appstream-agent-version` | No | string | `LATEST` | AppStream 2.0 agent version |
| `--access-endpoints` | No | list | -- | Access endpoints. Shorthand: `EndpointType=STREAMING,VpceId=string` |
| `--tags` | No | map | -- | Tags as key-value pairs |

**Output Schema:**
```json
{
    "ImageBuilder": {
        "Name": "string",
        "Arn": "string",
        "ImageArn": "string",
        "Description": "string",
        "DisplayName": "string",
        "VpcConfig": {
            "SubnetIds": ["string"],
            "SecurityGroupIds": ["string"]
        },
        "InstanceType": "string",
        "Platform": "WINDOWS|WINDOWS_SERVER_2016|WINDOWS_SERVER_2019|WINDOWS_SERVER_2022|AMAZON_LINUX2",
        "IamRoleArn": "string",
        "State": "PENDING|UPDATING_AGENT|RUNNING|STOPPING|STOPPED|REBOOTING|SNAPSHOTTING|DELETING|FAILED",
        "StateChangeReason": {
            "Code": "INTERNAL_ERROR|IMAGE_UNAVAILABLE",
            "Message": "string"
        },
        "CreatedTime": "timestamp",
        "EnableDefaultInternetAccess": "boolean",
        "DomainJoinInfo": {
            "DirectoryName": "string",
            "OrganizationalUnitDistinguishedName": "string"
        },
        "NetworkAccessConfiguration": {
            "EniPrivateIpAddress": "string",
            "EniId": "string"
        },
        "ImageBuilderErrors": [
            {
                "ErrorCode": "string",
                "ErrorMessage": "string",
                "ErrorTimestamp": "timestamp"
            }
        ],
        "AppstreamAgentVersion": "string",
        "AccessEndpoints": [
            {
                "EndpointType": "STREAMING",
                "VpceId": "string"
            }
        ]
    }
}
```

---

### 4.2 `delete-image-builder`

Deletes the specified image builder. The image builder must be in STOPPED state.

**Synopsis:**
```bash
aws appstream delete-image-builder \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the image builder to delete |

**Output Schema:**
```json
{
    "ImageBuilder": {
        "Name": "string",
        "Arn": "string",
        "State": "PENDING|UPDATING_AGENT|RUNNING|STOPPING|STOPPED|REBOOTING|SNAPSHOTTING|DELETING|FAILED",
        "InstanceType": "string",
        "Platform": "string",
        "CreatedTime": "timestamp"
    }
}
```

---

### 4.3 `describe-image-builders`

Describes one or more image builders.

**Synopsis:**
```bash
aws appstream describe-image-builders \
    [--names <value>] \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--names` | No | list(string) | -- | Names of the image builders to describe |
| `--max-results` | No | integer | -- | Maximum number of results |
| `--next-token` | No | string | -- | Pagination token |

**Output Schema:**
```json
{
    "ImageBuilders": [
        {
            "Name": "string",
            "Arn": "string",
            "ImageArn": "string",
            "Description": "string",
            "DisplayName": "string",
            "VpcConfig": {
                "SubnetIds": ["string"],
                "SecurityGroupIds": ["string"]
            },
            "InstanceType": "string",
            "Platform": "string",
            "IamRoleArn": "string",
            "State": "PENDING|UPDATING_AGENT|RUNNING|STOPPING|STOPPED|REBOOTING|SNAPSHOTTING|DELETING|FAILED",
            "StateChangeReason": {
                "Code": "string",
                "Message": "string"
            },
            "CreatedTime": "timestamp",
            "EnableDefaultInternetAccess": "boolean",
            "DomainJoinInfo": {},
            "NetworkAccessConfiguration": {},
            "ImageBuilderErrors": [],
            "AppstreamAgentVersion": "string",
            "AccessEndpoints": []
        }
    ],
    "NextToken": "string"
}
```

---

### 4.4 `start-image-builder`

Starts the specified image builder.

**Synopsis:**
```bash
aws appstream start-image-builder \
    --name <value> \
    [--appstream-agent-version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the image builder to start |
| `--appstream-agent-version` | No | string | -- | AppStream 2.0 agent version to use |

**Output Schema:**
```json
{
    "ImageBuilder": {
        "Name": "string",
        "Arn": "string",
        "State": "PENDING|UPDATING_AGENT|RUNNING|STOPPING|STOPPED|REBOOTING|SNAPSHOTTING|DELETING|FAILED",
        "InstanceType": "string",
        "Platform": "string",
        "CreatedTime": "timestamp"
    }
}
```

---

### 4.5 `stop-image-builder`

Stops the specified image builder.

**Synopsis:**
```bash
aws appstream stop-image-builder \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the image builder to stop |

**Output Schema:**
```json
{
    "ImageBuilder": {
        "Name": "string",
        "Arn": "string",
        "State": "PENDING|UPDATING_AGENT|RUNNING|STOPPING|STOPPED|REBOOTING|SNAPSHOTTING|DELETING|FAILED",
        "InstanceType": "string",
        "Platform": "string",
        "CreatedTime": "timestamp"
    }
}
```

---

### 4.6 `create-image-builder-streaming-url`

Creates a URL to start an image builder streaming session.

**Synopsis:**
```bash
aws appstream create-image-builder-streaming-url \
    --name <value> \
    [--validity <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the image builder |
| `--validity` | No | long | 14400 | Time in seconds the URL is valid |

**Output Schema:**
```json
{
    "StreamingURL": "string",
    "Expires": "timestamp"
}
```
