# Images

### 3.1 `describe-images`

Describes one or more images. Returns information about available public, private, and shared images.

**Synopsis:**
```bash
aws appstream describe-images \
    [--names <value>] \
    [--arns <value>] \
    [--type <value>] \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--names` | No | list(string) | -- | Names of the images to describe |
| `--arns` | No | list(string) | -- | ARNs of the images to describe |
| `--type` | No | string | -- | Image type filter: `PUBLIC`, `PRIVATE`, `SHARED` |
| `--next-token` | No | string | -- | Pagination token |
| `--max-results` | No | integer | -- | Maximum number of results (0-25) |

**Output Schema:**
```json
{
    "Images": [
        {
            "Name": "string",
            "Arn": "string",
            "BaseImageArn": "string",
            "DisplayName": "string",
            "State": "PENDING|AVAILABLE|FAILED|COPYING|DELETING|CREATING|IMPORTING",
            "Visibility": "PUBLIC|PRIVATE|SHARED",
            "ImageBuilderSupported": "boolean",
            "ImageBuilderName": "string",
            "Platform": "WINDOWS|WINDOWS_SERVER_2016|WINDOWS_SERVER_2019|WINDOWS_SERVER_2022|AMAZON_LINUX2",
            "Description": "string",
            "StateChangeReason": {
                "Code": "INTERNAL_ERROR|IMAGE_BUILDER_NOT_AVAILABLE|IMAGE_COPY_FAILURE",
                "Message": "string"
            },
            "Applications": [
                {
                    "Name": "string",
                    "DisplayName": "string",
                    "IconURL": "string",
                    "LaunchPath": "string",
                    "LaunchParameters": "string",
                    "Enabled": "boolean",
                    "Metadata": {
                        "string": "string"
                    }
                }
            ],
            "CreatedTime": "timestamp",
            "PublicBaseImageReleasedDate": "timestamp",
            "AppstreamAgentVersion": "string",
            "ImagePermissions": {
                "allowFleet": "boolean",
                "allowImageBuilder": "boolean"
            },
            "ImageErrors": [
                {
                    "ErrorCode": "string",
                    "ErrorMessage": "string",
                    "ErrorTimestamp": "timestamp"
                }
            ]
        }
    ],
    "NextToken": "string"
}
```

---

### 3.2 `delete-image`

Deletes the specified image. The image must not be in use by any fleets or image builders.

**Synopsis:**
```bash
aws appstream delete-image \
    --name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the image to delete |

**Output Schema:**
```json
{
    "Image": {
        "Name": "string",
        "Arn": "string",
        "State": "PENDING|AVAILABLE|FAILED|COPYING|DELETING|CREATING|IMPORTING",
        "Visibility": "PUBLIC|PRIVATE|SHARED",
        "Platform": "string",
        "CreatedTime": "timestamp"
    }
}
```

---

### 3.3 `copy-image`

Copies the specified image to the specified region.

**Synopsis:**
```bash
aws appstream copy-image \
    --source-image-name <value> \
    --destination-image-name <value> \
    --destination-region <value> \
    [--destination-image-description <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-image-name` | **Yes** | string | -- | Name of the source image |
| `--destination-image-name` | **Yes** | string | -- | Name for the destination image |
| `--destination-region` | **Yes** | string | -- | Destination AWS region |
| `--destination-image-description` | No | string | -- | Description for the destination image |

**Output Schema:**
```json
{
    "DestinationImageName": "string"
}
```

---

### 3.4 `describe-image-permissions`

Describes the permissions for the specified private image.

**Synopsis:**
```bash
aws appstream describe-image-permissions \
    --name <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--shared-aws-account-ids <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the private image |
| `--max-results` | No | integer | -- | Maximum number of results (0-500) |
| `--next-token` | No | string | -- | Pagination token |
| `--shared-aws-account-ids` | No | list(string) | -- | AWS account IDs to filter by |

**Output Schema:**
```json
{
    "Name": "string",
    "SharedImagePermissionsList": [
        {
            "sharedAccountId": "string",
            "imagePermissions": {
                "allowFleet": "boolean",
                "allowImageBuilder": "boolean"
            }
        }
    ],
    "NextToken": "string"
}
```

---

### 3.5 `update-image-permissions`

Updates image sharing permissions for the specified private image.

**Synopsis:**
```bash
aws appstream update-image-permissions \
    --name <value> \
    --shared-account-id <value> \
    --image-permissions <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the private image |
| `--shared-account-id` | **Yes** | string | -- | AWS account ID to share with |
| `--image-permissions` | **Yes** | structure | -- | Permissions. Shorthand: `allowFleet=boolean,allowImageBuilder=boolean` |

**Output Schema:**
```json
{}
```

---

### 3.6 `delete-image-permissions`

Deletes image sharing permissions for the specified private image.

**Synopsis:**
```bash
aws appstream delete-image-permissions \
    --name <value> \
    --shared-account-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the private image |
| `--shared-account-id` | **Yes** | string | -- | AWS account ID to remove sharing from |

**Output Schema:**
```json
{}
```

---

### 3.7 `create-updated-image`

Creates a new image from an existing base image with the latest AppStream 2.0 agent software and Windows updates.

**Synopsis:**
```bash
aws appstream create-updated-image \
    --existing-image-name <value> \
    --new-image-name <value> \
    [--new-image-description <value>] \
    [--new-image-display-name <value>] \
    [--new-image-tags <value>] \
    [--dry-run | --no-dry-run] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--existing-image-name` | **Yes** | string | -- | Name of the existing image |
| `--new-image-name` | **Yes** | string | -- | Name for the new image |
| `--new-image-description` | No | string | -- | Description for the new image |
| `--new-image-display-name` | No | string | -- | Display name for the new image |
| `--new-image-tags` | No | map | -- | Tags for the new image |
| `--dry-run` | No | boolean | false | Check if image can be updated without creating it |

**Output Schema:**
```json
{
    "image": {
        "Name": "string",
        "Arn": "string",
        "BaseImageArn": "string",
        "DisplayName": "string",
        "State": "PENDING|AVAILABLE|FAILED|COPYING|DELETING|CREATING|IMPORTING",
        "Visibility": "PUBLIC|PRIVATE|SHARED",
        "Platform": "string",
        "Description": "string",
        "CreatedTime": "timestamp",
        "AppstreamAgentVersion": "string"
    },
    "canUpdateImage": "boolean"
}
```
