# Builds & Scripts

### 1.1 `create-build`

Creates a new custom game server build resource. Optionally uploads build files from an S3 location.

**Synopsis:**
```bash
aws gamelift create-build \
    [--name <value>] \
    [--build-version <value>] \
    [--storage-location <value>] \
    [--operating-system <value>] \
    [--server-sdk-version <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | No | string | None | Descriptive label for the build (1-1024 chars) |
| `--build-version` | No | string | None | Version information for the build (1-1024 chars) |
| `--storage-location` | No | structure | None | S3 location of build files. Shorthand: `Bucket=string,Key=string,RoleArn=string,ObjectVersion=string` |
| `--operating-system` | No | string | None | OS for game binaries: `AMAZON_LINUX`, `AMAZON_LINUX_2`, `AMAZON_LINUX_2023`, `WINDOWS_2012`, `WINDOWS_2016`, `WINDOWS_2022` |
| `--server-sdk-version` | No | string | `4.0.2` | Server SDK version (pattern: `^\d+\.\d+\.\d+$`, max 128 chars) |
| `--tags` | No | list | None | Tags for the build (max 200). Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "Build": {
        "BuildId": "string",
        "BuildArn": "string",
        "Name": "string",
        "Version": "string",
        "Status": "INITIALIZED|READY|FAILED",
        "SizeOnDisk": "long",
        "OperatingSystem": "string",
        "CreationTime": "timestamp",
        "ServerSdkVersion": "string"
    },
    "UploadCredentials": {
        "AccessKeyId": "string",
        "SecretAccessKey": "string",
        "SessionToken": "string"
    },
    "StorageLocation": {
        "Bucket": "string",
        "Key": "string",
        "RoleArn": "string",
        "ObjectVersion": "string"
    }
}
```

---

### 1.2 `delete-build`

Deletes a build resource and all associated files. A build in `READY` status can only be deleted if no fleets reference it.

**Synopsis:**
```bash
aws gamelift delete-build \
    --build-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--build-id` | **Yes** | string | -- | Build ID or ARN to delete |

**Output Schema:**
```json
None
```

---

### 1.3 `describe-build`

Retrieves properties for a game server build resource.

**Synopsis:**
```bash
aws gamelift describe-build \
    --build-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--build-id` | **Yes** | string | -- | Build ID or ARN to retrieve |

**Output Schema:**
```json
{
    "Build": {
        "BuildId": "string",
        "BuildArn": "string",
        "Name": "string",
        "Version": "string",
        "Status": "INITIALIZED|READY|FAILED",
        "SizeOnDisk": "long",
        "OperatingSystem": "string",
        "CreationTime": "timestamp",
        "ServerSdkVersion": "string"
    }
}
```

---

### 1.4 `list-builds`

Retrieves build resources for all builds in the account. **Paginated.**

**Synopsis:**
```bash
aws gamelift list-builds \
    [--status <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--status` | No | string | None | Filter by status: `INITIALIZED`, `READY`, `FAILED` |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Builds": [
        {
            "BuildId": "string",
            "BuildArn": "string",
            "Name": "string",
            "Version": "string",
            "Status": "INITIALIZED|READY|FAILED",
            "SizeOnDisk": "long",
            "OperatingSystem": "string",
            "CreationTime": "timestamp",
            "ServerSdkVersion": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.5 `update-build`

Updates metadata for a build resource.

**Synopsis:**
```bash
aws gamelift update-build \
    --build-id <value> \
    [--name <value>] \
    [--build-version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--build-id` | **Yes** | string | -- | Build ID or ARN to update |
| `--name` | No | string | None | New descriptive label (1-1024 chars) |
| `--build-version` | No | string | None | New version information (1-1024 chars) |

**Output Schema:**
```json
{
    "Build": {
        "BuildId": "string",
        "BuildArn": "string",
        "Name": "string",
        "Version": "string",
        "Status": "INITIALIZED|READY|FAILED",
        "SizeOnDisk": "long",
        "OperatingSystem": "string",
        "CreationTime": "timestamp",
        "ServerSdkVersion": "string"
    }
}
```

---

### 1.6 `upload-build`

Uploads a game server build to GameLift. Creates the build resource and uploads files from a local directory. This is the recommended way to create builds.

**Synopsis:**
```bash
aws gamelift upload-build \
    --name <value> \
    --build-version <value> \
    --build-root <value> \
    [--operating-system <value>] \
    [--server-sdk-version <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Descriptive label for the build |
| `--build-version` | **Yes** | string | -- | Version information for the build |
| `--build-root` | **Yes** | string | -- | Local directory path containing build files |
| `--operating-system` | No | string | None | OS for game binaries: `AMAZON_LINUX`, `AMAZON_LINUX_2`, `AMAZON_LINUX_2023`, `WINDOWS_2012`, `WINDOWS_2016`, `WINDOWS_2022` |
| `--server-sdk-version` | No | string | `4.0.2` | Server SDK version |

**Output Schema:**
```json
{
    "Build": {
        "BuildId": "string",
        "BuildArn": "string",
        "Name": "string",
        "Version": "string",
        "Status": "INITIALIZED|READY|FAILED",
        "SizeOnDisk": "long",
        "OperatingSystem": "string",
        "CreationTime": "timestamp",
        "ServerSdkVersion": "string"
    }
}
```

---

### 1.7 `request-upload-credentials`

Retrieves a fresh set of upload credentials and S3 storage location for a previously created build.

**Synopsis:**
```bash
aws gamelift request-upload-credentials \
    --build-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--build-id` | **Yes** | string | -- | Build ID or ARN |

**Output Schema:**
```json
{
    "UploadCredentials": {
        "AccessKeyId": "string",
        "SecretAccessKey": "string",
        "SessionToken": "string"
    },
    "StorageLocation": {
        "Bucket": "string",
        "Key": "string",
        "RoleArn": "string",
        "ObjectVersion": "string"
    }
}
```

---

### 1.8 `create-script`

Creates a new Realtime Servers script resource.

**Synopsis:**
```bash
aws gamelift create-script \
    [--name <value>] \
    [--script-version <value>] \
    [--storage-location <value>] \
    [--zip-file <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | No | string | None | Descriptive label for the script (1-1024 chars) |
| `--script-version` | No | string | None | Version information (1-1024 chars) |
| `--storage-location` | No | structure | None | S3 location. Shorthand: `Bucket=string,Key=string,RoleArn=string,ObjectVersion=string` |
| `--zip-file` | No | blob | None | Local zip file with script content (fileb://path) |
| `--tags` | No | list | None | Tags (max 200). Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "Script": {
        "ScriptId": "string",
        "ScriptArn": "string",
        "Name": "string",
        "Version": "string",
        "SizeOnDisk": "long",
        "CreationTime": "timestamp",
        "StorageLocation": {
            "Bucket": "string",
            "Key": "string",
            "RoleArn": "string",
            "ObjectVersion": "string"
        }
    }
}
```

---

### 1.9 `delete-script`

Deletes a Realtime Servers script resource.

**Synopsis:**
```bash
aws gamelift delete-script \
    --script-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--script-id` | **Yes** | string | -- | Script ID or ARN to delete |

**Output Schema:**
```json
None
```

---

### 1.10 `describe-script`

Retrieves properties for a Realtime Servers script.

**Synopsis:**
```bash
aws gamelift describe-script \
    --script-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--script-id` | **Yes** | string | -- | Script ID or ARN |

**Output Schema:**
```json
{
    "Script": {
        "ScriptId": "string",
        "ScriptArn": "string",
        "Name": "string",
        "Version": "string",
        "SizeOnDisk": "long",
        "CreationTime": "timestamp",
        "StorageLocation": {
            "Bucket": "string",
            "Key": "string",
            "RoleArn": "string",
            "ObjectVersion": "string"
        }
    }
}
```

---

### 1.11 `list-scripts`

Retrieves all Realtime Servers scripts in the account. **Paginated.**

**Synopsis:**
```bash
aws gamelift list-scripts \
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
    "Scripts": [
        {
            "ScriptId": "string",
            "ScriptArn": "string",
            "Name": "string",
            "Version": "string",
            "SizeOnDisk": "long",
            "CreationTime": "timestamp",
            "StorageLocation": {}
        }
    ],
    "NextToken": "string"
}
```

---

### 1.12 `update-script`

Updates metadata and content for a Realtime Servers script.

**Synopsis:**
```bash
aws gamelift update-script \
    --script-id <value> \
    [--name <value>] \
    [--script-version <value>] \
    [--storage-location <value>] \
    [--zip-file <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--script-id` | **Yes** | string | -- | Script ID or ARN to update |
| `--name` | No | string | None | New descriptive label |
| `--script-version` | No | string | None | New version information |
| `--storage-location` | No | structure | None | New S3 location for script content |
| `--zip-file` | No | blob | None | New zip file with script content |

**Output Schema:**
```json
{
    "Script": {
        "ScriptId": "string",
        "ScriptArn": "string",
        "Name": "string",
        "Version": "string",
        "SizeOnDisk": "long",
        "CreationTime": "timestamp",
        "StorageLocation": {}
    }
}
```
