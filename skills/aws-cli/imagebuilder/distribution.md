# Distribution

### 8.1 `create-distribution-configuration`

Creates a new distribution configuration. Defines how and where images are distributed after they are built.

**Synopsis:**
```bash
aws imagebuilder create-distribution-configuration \
    --name <value> \
    --distributions <value> \
    [--description <value>] \
    [--tags <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Name of the configuration |
| `--distributions` | **Yes** | list | -- | Distribution settings per region |
| `--description` | No | string | -- | Description |
| `--tags` | No | map | None | Tags |
| `--client-token` | No | string | auto-generated | Idempotency token |

**Distribution Structure:**
```json
{
    "region": "string",
    "amiDistributionConfiguration": {
        "name": "string",
        "description": "string",
        "targetAccountIds": ["string"],
        "amiTags": {
            "string": "string"
        },
        "kmsKeyId": "string",
        "launchPermission": {
            "userIds": ["string"],
            "userGroups": ["string"],
            "organizationArns": ["string"],
            "organizationalUnitArns": ["string"]
        }
    },
    "containerDistributionConfiguration": {
        "description": "string",
        "containerTags": ["string"],
        "targetRepository": {
            "service": "ECR",
            "repositoryName": "string"
        }
    },
    "licenseConfigurationArns": ["string"],
    "launchTemplateConfigurations": [
        {
            "launchTemplateId": "string",
            "accountId": "string",
            "setDefaultVersion": "boolean"
        }
    ],
    "s3ExportConfiguration": {
        "roleName": "string",
        "diskImageFormat": "VMDK|RAW|VHD",
        "s3Bucket": "string",
        "s3Prefix": "string"
    }
}
```

**Output Schema:**
```json
{
    "requestId": "string",
    "clientToken": "string",
    "distributionConfigurationArn": "string"
}
```

---

### 8.2 `get-distribution-configuration`

Gets a distribution configuration.

**Synopsis:**
```bash
aws imagebuilder get-distribution-configuration \
    --distribution-configuration-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--distribution-configuration-arn` | **Yes** | string | -- | ARN of the distribution configuration |

**Output Schema:**
```json
{
    "requestId": "string",
    "distributionConfiguration": {
        "arn": "string",
        "name": "string",
        "description": "string",
        "distributions": [
            {
                "region": "string",
                "amiDistributionConfiguration": {},
                "containerDistributionConfiguration": {},
                "licenseConfigurationArns": ["string"],
                "launchTemplateConfigurations": [],
                "s3ExportConfiguration": {}
            }
        ],
        "timeoutMinutes": "integer",
        "dateCreated": "string",
        "dateUpdated": "string",
        "tags": {}
    }
}
```

---

### 8.3 `list-distribution-configurations`

Lists distribution configurations. **Paginated operation.**

**Synopsis:**
```bash
aws imagebuilder list-distribution-configurations \
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
    "distributionConfigurationSummaryList": [
        {
            "arn": "string",
            "name": "string",
            "description": "string",
            "dateCreated": "string",
            "dateUpdated": "string",
            "tags": {},
            "regions": ["string"]
        }
    ],
    "nextToken": "string"
}
```

---

### 8.4 `update-distribution-configuration`

Updates a distribution configuration.

**Synopsis:**
```bash
aws imagebuilder update-distribution-configuration \
    --distribution-configuration-arn <value> \
    --distributions <value> \
    [--description <value>] \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--distribution-configuration-arn` | **Yes** | string | -- | ARN of the configuration to update |
| `--distributions` | **Yes** | list | -- | Updated distribution settings |
| `--description` | No | string | -- | Updated description |
| `--client-token` | No | string | auto-generated | Idempotency token |

**Output Schema:**
```json
{
    "requestId": "string",
    "clientToken": "string",
    "distributionConfigurationArn": "string"
}
```

---

### 8.5 `delete-distribution-configuration`

Deletes a distribution configuration.

**Synopsis:**
```bash
aws imagebuilder delete-distribution-configuration \
    --distribution-configuration-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--distribution-configuration-arn` | **Yes** | string | -- | ARN of the configuration to delete |

**Output Schema:**
```json
{
    "requestId": "string",
    "distributionConfigurationArn": "string"
}
```
