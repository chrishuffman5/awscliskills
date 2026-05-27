# Configuration Profiles

### 2.1 `create-configuration-profile`

Creates a configuration profile. A configuration profile defines the source of configuration data and validators.

**Synopsis:**
```bash
aws appconfig create-configuration-profile \
    --application-id <value> \
    --name <value> \
    --location-uri <value> \
    [--description <value>] \
    [--retrieval-role-arn <value>] \
    [--validators <value>] \
    [--tags <value>] \
    [--type <value>] \
    [--kms-key-identifier <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application ID |
| `--name` | **Yes** | string | -- | Configuration profile name (1-128 chars) |
| `--location-uri` | **Yes** | string | -- | URI: `hosted`, `ssm-parameter://`, `s3://`, `secretsmanager://`, `codepipeline://`, `ssm-document://` (1-2048 chars) |
| `--description` | No | string | None | Description (0-1024 chars) |
| `--retrieval-role-arn` | No | string | None | IAM role ARN for accessing configuration source (20-2048 chars) |
| `--validators` | No | list | None | Validation methods (max 2) |
| `--tags` | No | map | None | Tags (max 50) |
| `--type` | No | string | None | `AWS.AppConfig.FeatureFlags` or `AWS.Freeform` |
| `--kms-key-identifier` | No | string | None | KMS key for encrypting hosted configurations (1-2048 chars) |

**Validators structure:**
```json
[
    {
        "Type": "JSON_SCHEMA|LAMBDA",
        "Content": "string"
    }
]
```

**Output Schema:**
```json
{
    "ApplicationId": "string",
    "Id": "string",
    "Name": "string",
    "Description": "string",
    "LocationUri": "string",
    "RetrievalRoleArn": "string",
    "Validators": [
        {
            "Type": "JSON_SCHEMA|LAMBDA",
            "Content": "string"
        }
    ],
    "Type": "string",
    "KmsKeyArn": "string",
    "KmsKeyIdentifier": "string"
}
```

---

### 2.2 `get-configuration-profile`

Retrieves configuration profile details.

**Synopsis:**
```bash
aws appconfig get-configuration-profile \
    --application-id <value> \
    --configuration-profile-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application ID |
| `--configuration-profile-id` | **Yes** | string | -- | Configuration profile ID |

**Output Schema:**
```json
{
    "ApplicationId": "string",
    "Id": "string",
    "Name": "string",
    "Description": "string",
    "LocationUri": "string",
    "RetrievalRoleArn": "string",
    "Validators": [
        {
            "Type": "JSON_SCHEMA|LAMBDA",
            "Content": "string"
        }
    ],
    "Type": "string",
    "KmsKeyArn": "string",
    "KmsKeyIdentifier": "string"
}
```

---

### 2.3 `list-configuration-profiles`

Lists configuration profiles for an application. **Paginated operation.**

**Synopsis:**
```bash
aws appconfig list-configuration-profiles \
    --application-id <value> \
    [--max-results <value>] \
    [--next-token <value>] \
    [--type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application ID |
| `--max-results` | No | integer | None | Max results per page (1-50) |
| `--next-token` | No | string | None | Pagination token |
| `--type` | No | string | None | Filter by type: `AWS.AppConfig.FeatureFlags` or `AWS.Freeform` |

**Output Schema:**
```json
{
    "Items": [
        {
            "ApplicationId": "string",
            "Id": "string",
            "Name": "string",
            "LocationUri": "string",
            "ValidatorTypes": ["JSON_SCHEMA|LAMBDA"],
            "Type": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.4 `update-configuration-profile`

Updates a configuration profile.

**Synopsis:**
```bash
aws appconfig update-configuration-profile \
    --application-id <value> \
    --configuration-profile-id <value> \
    [--name <value>] \
    [--description <value>] \
    [--retrieval-role-arn <value>] \
    [--validators <value>] \
    [--kms-key-identifier <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application ID |
| `--configuration-profile-id` | **Yes** | string | -- | Configuration profile ID |
| `--name` | No | string | None | Updated name (1-128 chars) |
| `--description` | No | string | None | Updated description (0-1024 chars) |
| `--retrieval-role-arn` | No | string | None | Updated IAM role ARN |
| `--validators` | No | list | None | Updated validators (max 2) |
| `--kms-key-identifier` | No | string | None | Updated KMS key identifier |

**Output Schema:**
```json
{
    "ApplicationId": "string",
    "Id": "string",
    "Name": "string",
    "Description": "string",
    "LocationUri": "string",
    "RetrievalRoleArn": "string",
    "Validators": [
        {
            "Type": "JSON_SCHEMA|LAMBDA",
            "Content": "string"
        }
    ],
    "Type": "string",
    "KmsKeyArn": "string",
    "KmsKeyIdentifier": "string"
}
```

---

### 2.5 `delete-configuration-profile`

Deletes a configuration profile. Deleting a configuration profile does not delete a configuration from a host.

**Synopsis:**
```bash
aws appconfig delete-configuration-profile \
    --application-id <value> \
    --configuration-profile-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--application-id` | **Yes** | string | -- | Application ID |
| `--configuration-profile-id` | **Yes** | string | -- | Configuration profile ID |

**Output:** None
