# Connect Plugins & Workers

> Commands in this file use the `aws kafkaconnect` namespace.

## 10.1 `create-custom-plugin`

Creates a custom plugin for Kafka Connect.

**Synopsis:**
```bash
aws kafkaconnect create-custom-plugin \
    --content-type <value> \
    --location <value> \
    --name <value> \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--content-type` | **Yes** | string | -- | Plugin file type: `JAR` or `ZIP` |
| `--location` | **Yes** | structure | -- | S3 location of the plugin file |
| `--name` | **Yes** | string | -- | Plugin name (1-128 chars) |
| `--description` | No | string | None | Description (max 1024 chars) |
| `--tags` | No | map | None | Key-value tags |

**Location Structure:**
```json
{
    "s3Location": {
        "bucketArn": "arn:aws:s3:::my-bucket",
        "fileKey": "plugins/my-plugin.jar",
        "objectVersion": "string"
    }
}
```

**Output Schema:**
```json
{
    "customPluginArn": "string",
    "customPluginState": "CREATING|CREATE_FAILED|ACTIVE|UPDATING|UPDATE_FAILED|DELETING",
    "name": "string",
    "revision": "long"
}
```

---

## 10.2 `delete-custom-plugin`

Deletes a custom plugin.

**Synopsis:**
```bash
aws kafkaconnect delete-custom-plugin \
    --custom-plugin-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--custom-plugin-arn` | **Yes** | string | -- | ARN of the custom plugin to delete |

**Output Schema:**
```json
{
    "customPluginArn": "string",
    "customPluginState": "CREATING|CREATE_FAILED|ACTIVE|UPDATING|UPDATE_FAILED|DELETING"
}
```

---

## 10.3 `describe-custom-plugin`

Returns details for the specified custom plugin.

**Synopsis:**
```bash
aws kafkaconnect describe-custom-plugin \
    --custom-plugin-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--custom-plugin-arn` | **Yes** | string | -- | ARN of the custom plugin |

**Output Schema:**
```json
{
    "creationTime": "timestamp",
    "customPluginArn": "string",
    "customPluginState": "CREATING|CREATE_FAILED|ACTIVE|UPDATING|UPDATE_FAILED|DELETING",
    "description": "string",
    "latestRevision": {
        "contentType": "JAR|ZIP",
        "creationTime": "timestamp",
        "description": "string",
        "fileDescription": {
            "fileMd5": "string",
            "fileSize": "long"
        },
        "location": {
            "s3Location": {
                "bucketArn": "string",
                "fileKey": "string",
                "objectVersion": "string"
            }
        },
        "revision": "long"
    },
    "name": "string",
    "stateDescription": {
        "code": "string",
        "message": "string"
    }
}
```

---

## 10.4 `list-custom-plugins`

Lists all custom plugins. **Paginated operation.**

**Synopsis:**
```bash
aws kafkaconnect list-custom-plugins \
    [--name-prefix <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name-prefix` | No | string | None | Filter by plugin name prefix |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "customPlugins": [
        {
            "creationTime": "timestamp",
            "customPluginArn": "string",
            "customPluginState": "string",
            "description": "string",
            "latestRevision": {
                "contentType": "string",
                "creationTime": "timestamp",
                "description": "string",
                "revision": "long"
            },
            "name": "string"
        }
    ],
    "nextToken": "string"
}
```

---

## 10.5 `create-worker-configuration`

Creates a worker configuration for Kafka Connect.

**Synopsis:**
```bash
aws kafkaconnect create-worker-configuration \
    --name <value> \
    --properties-file-content <value> \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Worker configuration name (1-128 chars) |
| `--properties-file-content` | **Yes** | string | -- | Base64-encoded properties file content |
| `--description` | No | string | None | Description (max 1024 chars) |
| `--tags` | No | map | None | Key-value tags |

**Output Schema:**
```json
{
    "creationTime": "timestamp",
    "latestRevision": {
        "creationTime": "timestamp",
        "description": "string",
        "revision": "long"
    },
    "name": "string",
    "workerConfigurationArn": "string",
    "workerConfigurationState": "ACTIVE|DELETING"
}
```

---

## 10.6 `delete-worker-configuration`

Deletes a worker configuration.

**Synopsis:**
```bash
aws kafkaconnect delete-worker-configuration \
    --worker-configuration-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--worker-configuration-arn` | **Yes** | string | -- | ARN of the worker configuration to delete |

**Output Schema:**
```json
{
    "workerConfigurationArn": "string",
    "workerConfigurationState": "ACTIVE|DELETING"
}
```

---

## 10.7 `describe-worker-configuration`

Returns details for the specified worker configuration.

**Synopsis:**
```bash
aws kafkaconnect describe-worker-configuration \
    --worker-configuration-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--worker-configuration-arn` | **Yes** | string | -- | ARN of the worker configuration |

**Output Schema:**
```json
{
    "creationTime": "timestamp",
    "description": "string",
    "latestRevision": {
        "creationTime": "timestamp",
        "description": "string",
        "propertiesFileContent": "string",
        "revision": "long"
    },
    "name": "string",
    "workerConfigurationArn": "string",
    "workerConfigurationState": "ACTIVE|DELETING"
}
```

---

## 10.8 `list-worker-configurations`

Lists all worker configurations. **Paginated operation.**

**Synopsis:**
```bash
aws kafkaconnect list-worker-configurations \
    [--name-prefix <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name-prefix` | No | string | None | Filter by name prefix |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "workerConfigurations": [
        {
            "creationTime": "timestamp",
            "description": "string",
            "latestRevision": {
                "creationTime": "timestamp",
                "description": "string",
                "revision": "long"
            },
            "name": "string",
            "workerConfigurationArn": "string",
            "workerConfigurationState": "string"
        }
    ],
    "nextToken": "string"
}
```

---

## 10.9 `tag-resource`

Adds tags to a Kafka Connect resource.

**Synopsis:**
```bash
aws kafkaconnect tag-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |
| `--tags` | **Yes** | map | -- | Key-value tags to add |

**Output Schema:**

None (HTTP 200 on success).

---

## 10.10 `untag-resource`

Removes tags from a Kafka Connect resource.

**Synopsis:**
```bash
aws kafkaconnect untag-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output Schema:**

None (HTTP 200 on success).

---

## 10.11 `list-tags-for-resource`

Lists tags for a Kafka Connect resource.

**Synopsis:**
```bash
aws kafkaconnect list-tags-for-resource \
    --resource-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | ARN of the resource |

**Output Schema:**
```json
{
    "tags": {
        "string": "string"
    }
}
```
