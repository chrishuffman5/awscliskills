# Infrastructure

### 7.1 `create-infrastructure-configuration`

Creates a new infrastructure configuration. This defines the build environment for Image Builder.

**Synopsis:**
```bash
aws imagebuilder create-infrastructure-configuration \
    --name <value> \
    --instance-profile-name <value> \
    [--description <value>] \
    [--instance-types <value>] \
    [--security-group-ids <value>] \
    [--subnet-id <value>] \
    [--logging <value>] \
    [--key-pair <value>] \
    [--terminate-instance-on-failure | --no-terminate-instance-on-failure] \
    [--sns-topic-arn <value>] \
    [--instance-metadata-options <value>] \
    [--resource-tags <value>] \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the configuration |
| `--instance-profile-name` | **Yes** | string | -- | IAM instance profile name for build instances |
| `--description` | No | string | -- | Description |
| `--instance-types` | No | list(string) | None | Instance types for the build (e.g., `m5.large`) |
| `--security-group-ids` | No | list(string) | None | Security group IDs |
| `--subnet-id` | No | string | -- | Subnet ID for the build instance |
| `--logging` | No | structure | None | Logging configuration. Shorthand: `s3Logs={s3BucketName=string,s3KeyPrefix=string}` |
| `--key-pair` | No | string | -- | EC2 key pair for SSH access |
| `--terminate-instance-on-failure` | No | boolean | true | Terminate build instance on failure |
| `--sns-topic-arn` | No | string | -- | SNS topic ARN for build notifications |
| `--instance-metadata-options` | No | structure | None | Instance metadata options. Shorthand: `httpTokens=required\|optional,httpPutResponseHopLimit=integer` |
| `--resource-tags` | No | map | None | Tags to apply to build resources |
| `--tags` | No | map | None | Tags for the configuration |
| `--client-token` | No | string | auto-generated | Idempotency token |

**Output Schema:**
```json
{
    "requestId": "string",
    "clientToken": "string",
    "infrastructureConfigurationArn": "string"
}
```

---

### 7.2 `get-infrastructure-configuration`

Gets an infrastructure configuration.

**Synopsis:**
```bash
aws imagebuilder get-infrastructure-configuration \
    --infrastructure-configuration-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--infrastructure-configuration-arn` | **Yes** | string | -- | ARN of the infrastructure configuration |

**Output Schema:**
```json
{
    "requestId": "string",
    "infrastructureConfiguration": {
        "arn": "string",
        "name": "string",
        "description": "string",
        "instanceTypes": ["string"],
        "instanceProfileName": "string",
        "securityGroupIds": ["string"],
        "subnetId": "string",
        "logging": {
            "s3Logs": {
                "s3BucketName": "string",
                "s3KeyPrefix": "string"
            }
        },
        "keyPair": "string",
        "terminateInstanceOnFailure": "boolean",
        "snsTopicArn": "string",
        "dateCreated": "string",
        "dateUpdated": "string",
        "resourceTags": {},
        "instanceMetadataOptions": {
            "httpTokens": "required|optional",
            "httpPutResponseHopLimit": "integer"
        },
        "tags": {}
    }
}
```

---

### 7.3 `list-infrastructure-configurations`

Lists infrastructure configurations. **Paginated operation.**

**Synopsis:**
```bash
aws imagebuilder list-infrastructure-configurations \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filters` | No | list | None | Filters |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "requestId": "string",
    "infrastructureConfigurationSummaryList": [
        {
            "arn": "string",
            "name": "string",
            "description": "string",
            "dateCreated": "string",
            "dateUpdated": "string",
            "resourceTags": {},
            "tags": {},
            "instanceTypes": ["string"],
            "instanceProfileName": "string"
        }
    ],
    "nextToken": "string"
}
```

---

### 7.4 `update-infrastructure-configuration`

Updates an infrastructure configuration.

**Synopsis:**
```bash
aws imagebuilder update-infrastructure-configuration \
    --infrastructure-configuration-arn <value> \
    --instance-profile-name <value> \
    [--description <value>] \
    [--instance-types <value>] \
    [--security-group-ids <value>] \
    [--subnet-id <value>] \
    [--logging <value>] \
    [--key-pair <value>] \
    [--terminate-instance-on-failure | --no-terminate-instance-on-failure] \
    [--sns-topic-arn <value>] \
    [--instance-metadata-options <value>] \
    [--resource-tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--infrastructure-configuration-arn` | **Yes** | string | -- | ARN of the configuration to update |
| `--instance-profile-name` | **Yes** | string | -- | IAM instance profile name |
| `--description` | No | string | -- | Updated description |
| `--instance-types` | No | list(string) | None | Instance types |
| `--security-group-ids` | No | list(string) | None | Security group IDs |
| `--subnet-id` | No | string | -- | Subnet ID |
| `--logging` | No | structure | None | Logging configuration |
| `--key-pair` | No | string | -- | EC2 key pair |
| `--terminate-instance-on-failure` | No | boolean | -- | Terminate on failure |
| `--sns-topic-arn` | No | string | -- | SNS topic ARN |
| `--instance-metadata-options` | No | structure | None | Instance metadata options |
| `--resource-tags` | No | map | None | Resource tags |
| `--client-token` | No | string | auto-generated | Idempotency token |

**Output Schema:**
```json
{
    "requestId": "string",
    "clientToken": "string",
    "infrastructureConfigurationArn": "string"
}
```

---

### 7.5 `delete-infrastructure-configuration`

Deletes an infrastructure configuration.

**Synopsis:**
```bash
aws imagebuilder delete-infrastructure-configuration \
    --infrastructure-configuration-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--infrastructure-configuration-arn` | **Yes** | string | -- | ARN of the configuration to delete |

**Output Schema:**
```json
{
    "requestId": "string",
    "infrastructureConfigurationArn": "string"
}
```
