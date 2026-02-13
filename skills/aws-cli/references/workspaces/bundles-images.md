# Bundles & Images

### 2.1 `create-workspace-bundle`

Creates a custom WorkSpace bundle from a specified image.

**Synopsis:**
```bash
aws workspaces create-workspace-bundle \
    --bundle-name <value> \
    --bundle-description <value> \
    --image-id <value> \
    --compute-type <value> \
    --user-storage <value> \
    [--root-storage <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bundle-name` | **Yes** | string | -- | Name of the bundle (1-64 chars) |
| `--bundle-description` | **Yes** | string | -- | Description of the bundle (1-255 chars) |
| `--image-id` | **Yes** | string | -- | The image ID for the bundle |
| `--compute-type` | **Yes** | structure | -- | Compute type. Shorthand: `Name=VALUE\|STANDARD\|PERFORMANCE\|POWER\|GRAPHICS\|POWERPRO\|GRAPHICSPRO\|GRAPHICS_G4DN\|GRAPHICSPRO_G4DN` |
| `--user-storage` | **Yes** | structure | -- | User storage capacity. Shorthand: `Capacity=string` |
| `--root-storage` | No | structure | None | Root storage capacity. Shorthand: `Capacity=string` |
| `--tags` | No | list | None | Tags to associate. Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "WorkspaceBundle": {
        "BundleId": "string",
        "Name": "string",
        "Owner": "string",
        "Description": "string",
        "ImageId": "string",
        "RootStorage": {
            "Capacity": "string"
        },
        "UserStorage": {
            "Capacity": "string"
        },
        "ComputeType": {
            "Name": "VALUE|STANDARD|PERFORMANCE|POWER|GRAPHICS|POWERPRO|GRAPHICSPRO|GRAPHICS_G4DN|GRAPHICSPRO_G4DN"
        },
        "LastUpdatedTime": "timestamp",
        "CreationTime": "timestamp",
        "State": "AVAILABLE|PENDING|ERROR",
        "BundleType": "REGULAR|STANDBY"
    }
}
```

---

### 2.2 `delete-workspace-bundle`

Deletes the specified WorkSpace bundle.

**Synopsis:**
```bash
aws workspaces delete-workspace-bundle \
    [--bundle-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bundle-id` | No | string | None | The bundle ID to delete |

**Output Schema:**
```json
{}
```

---

### 2.3 `describe-workspace-bundles`

Describes the available WorkSpace bundles. **Paginated operation.**

**Synopsis:**
```bash
aws workspaces describe-workspace-bundles \
    [--bundle-ids <value>] \
    [--owner <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bundle-ids` | No | list(string) | None | One or more bundle IDs |
| `--owner` | No | string | None | Owner of the bundles: `AMAZON` or account ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Bundles": [
        {
            "BundleId": "string",
            "Name": "string",
            "Owner": "string",
            "Description": "string",
            "ImageId": "string",
            "RootStorage": {
                "Capacity": "string"
            },
            "UserStorage": {
                "Capacity": "string"
            },
            "ComputeType": {
                "Name": "string"
            },
            "LastUpdatedTime": "timestamp",
            "CreationTime": "timestamp",
            "State": "AVAILABLE|PENDING|ERROR",
            "BundleType": "REGULAR|STANDBY"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.4 `update-workspace-bundle`

Updates a WorkSpace bundle with a new image.

**Synopsis:**
```bash
aws workspaces update-workspace-bundle \
    [--bundle-id <value>] \
    [--image-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--bundle-id` | No | string | None | The bundle ID to update |
| `--image-id` | No | string | None | The new image ID for the bundle |

**Output Schema:**
```json
{}
```

---

### 2.5 `create-workspace-image`

Creates a new WorkSpace image from an existing WorkSpace.

**Synopsis:**
```bash
aws workspaces create-workspace-image \
    --name <value> \
    --description <value> \
    --workspace-id <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | The name of the new image |
| `--description` | **Yes** | string | -- | The description of the new image |
| `--workspace-id` | **Yes** | string | -- | The WorkSpace ID to create the image from |
| `--tags` | No | list | None | Tags to associate. Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "ImageId": "string",
    "Name": "string",
    "Description": "string",
    "OperatingSystem": {
        "Type": "WINDOWS|LINUX"
    },
    "State": "AVAILABLE|PENDING|ERROR",
    "RequiredTenancy": "DEFAULT|DEDICATED",
    "Created": "timestamp",
    "OwnerAccountId": "string"
}
```

---

### 2.6 `delete-workspace-image`

Deletes the specified WorkSpace image.

**Synopsis:**
```bash
aws workspaces delete-workspace-image \
    --image-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--image-id` | **Yes** | string | -- | The image ID to delete |

**Output Schema:**
```json
{}
```

---

### 2.7 `describe-workspace-images`

Describes the specified WorkSpace images or all images. **Paginated operation.**

**Synopsis:**
```bash
aws workspaces describe-workspace-images \
    [--image-ids <value>] \
    [--image-type <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--image-ids` | No | list(string) | None | One or more image IDs |
| `--image-type` | No | string | None | Filter by image type: `OWNED`, `SHARED` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Images": [
        {
            "ImageId": "string",
            "Name": "string",
            "Description": "string",
            "OperatingSystem": {
                "Type": "WINDOWS|LINUX"
            },
            "State": "AVAILABLE|PENDING|ERROR",
            "RequiredTenancy": "DEFAULT|DEDICATED",
            "ErrorCode": "string",
            "ErrorMessage": "string",
            "Created": "timestamp",
            "OwnerAccountId": "string",
            "Updates": {
                "UpdateAvailable": true|false,
                "Description": "string"
            },
            "ErrorDetails": [
                {
                    "ErrorCode": "string",
                    "ErrorMessage": "string"
                }
            ]
        }
    ],
    "NextToken": "string"
}
```

---

### 2.8 `copy-workspace-image`

Copies the specified WorkSpace image to another region. Images can only be copied within the same AWS partition.

**Synopsis:**
```bash
aws workspaces copy-workspace-image \
    --name <value> \
    --source-image-id <value> \
    --source-region <value> \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | The name of the image in the destination region |
| `--source-image-id` | **Yes** | string | -- | The image ID to copy |
| `--source-region` | **Yes** | string | -- | The source region of the image |
| `--description` | No | string | None | Description of the image in the destination region |
| `--tags` | No | list | None | Tags to associate. Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "ImageId": "string"
}
```
