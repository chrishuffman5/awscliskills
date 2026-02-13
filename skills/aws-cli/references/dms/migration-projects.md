# Migration Projects

Migration projects combine data providers, instance profiles, and transformation rules for schema conversion and homogeneous migrations.

### 7.1 `create-migration-project`

Creates a migration project.

**Synopsis:**
```bash
aws dms create-migration-project \
    --source-data-provider-descriptors <value> \
    --target-data-provider-descriptors <value> \
    --instance-profile-identifier <value> \
    [--migration-project-name <value>] \
    [--transformation-rules <value>] \
    [--description <value>] \
    [--tags <value>] \
    [--schema-conversion-application-attributes <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--source-data-provider-descriptors` | **Yes** | list | -- | Source data provider descriptors |
| `--target-data-provider-descriptors` | **Yes** | list | -- | Target data provider descriptors |
| `--instance-profile-identifier` | **Yes** | string | -- | Associated instance profile identifier |
| `--migration-project-name` | No | string | -- | User-friendly name |
| `--transformation-rules` | No | string | -- | JSON transformation rules |
| `--description` | No | string | -- | Description |
| `--tags` | No | list | -- | Tags |
| `--schema-conversion-application-attributes` | No | structure | -- | S3 bucket config for schema conversion |

**Data Provider Descriptor Structure:**
```json
[
    {
        "DataProviderIdentifier": "string",
        "SecretsManagerSecretId": "string",
        "SecretsManagerAccessRoleArn": "string"
    }
]
```

**Output Schema:**
```json
{
    "MigrationProject": {
        "MigrationProjectName": "string",
        "MigrationProjectArn": "string",
        "MigrationProjectCreationTime": "timestamp",
        "SourceDataProviderDescriptors": [
            {
                "SecretsManagerSecretId": "string",
                "SecretsManagerAccessRoleArn": "string",
                "DataProviderName": "string",
                "DataProviderArn": "string"
            }
        ],
        "TargetDataProviderDescriptors": [],
        "InstanceProfileArn": "string",
        "InstanceProfileName": "string",
        "TransformationRules": "string",
        "Description": "string",
        "SchemaConversionApplicationAttributes": {
            "S3BucketPath": "string",
            "S3BucketRoleArn": "string"
        }
    }
}
```

---

### 7.2 `delete-migration-project`

Deletes the specified migration project.

**Synopsis:**
```bash
aws dms delete-migration-project \
    --migration-project-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--migration-project-identifier` | **Yes** | string | -- | Migration project identifier or ARN |

**Output Schema:** Same as `create-migration-project`.

---

### 7.3 `describe-migration-projects`

Returns a paginated list of migration projects. **Paginated operation.**

**Synopsis:**
```bash
aws dms describe-migration-projects \
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
| `--filters` | No | list | -- | Filters: `migration-project-identifier`, `migration-project-name`, `instance-profile-identifier` |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "Marker": "string",
    "MigrationProjects": [
        {
            "MigrationProjectName": "string",
            "MigrationProjectArn": "string",
            "MigrationProjectCreationTime": "timestamp",
            "SourceDataProviderDescriptors": [],
            "TargetDataProviderDescriptors": [],
            "InstanceProfileArn": "string",
            "InstanceProfileName": "string",
            "TransformationRules": "string",
            "Description": "string"
        }
    ]
}
```

---

### 7.4 `modify-migration-project`

Modifies the specified migration project.

**Synopsis:**
```bash
aws dms modify-migration-project \
    --migration-project-identifier <value> \
    [--migration-project-name <value>] \
    [--source-data-provider-descriptors <value>] \
    [--target-data-provider-descriptors <value>] \
    [--instance-profile-identifier <value>] \
    [--transformation-rules <value>] \
    [--description <value>] \
    [--schema-conversion-application-attributes <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--migration-project-identifier` | **Yes** | string | -- | Migration project identifier or ARN |
| `--migration-project-name` | No | string | -- | New name |
| `--source-data-provider-descriptors` | No | list | -- | New source data provider descriptors |
| `--target-data-provider-descriptors` | No | list | -- | New target data provider descriptors |
| `--instance-profile-identifier` | No | string | -- | New instance profile |
| `--transformation-rules` | No | string | -- | New transformation rules |
| `--description` | No | string | -- | New description |

**Output Schema:** Same as `create-migration-project`.

---

### 7.5 `create-data-provider`

Creates a data provider using the provided settings. A data provider stores connection information about your database.

**Synopsis:**
```bash
aws dms create-data-provider \
    --engine <value> \
    --settings <value> \
    [--data-provider-name <value>] \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--engine` | **Yes** | string | -- | Database engine type |
| `--settings` | **Yes** | structure | -- | Engine-specific connection settings |
| `--data-provider-name` | No | string | -- | User-friendly name |
| `--description` | No | string | -- | Description |
| `--tags` | No | list | -- | Tags |

**Output Schema:**
```json
{
    "DataProvider": {
        "DataProviderName": "string",
        "DataProviderArn": "string",
        "DataProviderCreationTime": "timestamp",
        "Description": "string",
        "Engine": "string",
        "Settings": {}
    }
}
```

---

### 7.6 `delete-data-provider`

Deletes the specified data provider.

**Synopsis:**
```bash
aws dms delete-data-provider \
    --data-provider-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--data-provider-identifier` | **Yes** | string | -- | Data provider identifier or ARN |

**Output Schema:** Same as `create-data-provider`.

---

### 7.7 `describe-data-providers`

Returns a paginated list of data providers. **Paginated operation.**

**Synopsis:**
```bash
aws dms describe-data-providers \
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
| `--filters` | No | list | -- | Filters: `data-provider-identifier`, `data-provider-name`, `engine` |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "Marker": "string",
    "DataProviders": [
        {
            "DataProviderName": "string",
            "DataProviderArn": "string",
            "DataProviderCreationTime": "timestamp",
            "Description": "string",
            "Engine": "string",
            "Settings": {}
        }
    ]
}
```

---

### 7.8 `modify-data-provider`

Modifies the specified data provider.

**Synopsis:**
```bash
aws dms modify-data-provider \
    --data-provider-identifier <value> \
    [--data-provider-name <value>] \
    [--description <value>] \
    [--engine <value>] \
    [--settings <value>] \
    [--exact-settings | --no-exact-settings] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--data-provider-identifier` | **Yes** | string | -- | Data provider identifier or ARN |
| `--data-provider-name` | No | string | -- | New name |
| `--description` | No | string | -- | New description |
| `--engine` | No | string | -- | New engine type |
| `--settings` | No | structure | -- | New settings |
| `--exact-settings` | No | boolean | -- | Use exact settings |

**Output Schema:** Same as `create-data-provider`.

---

### 7.9 `create-instance-profile`

Creates the instance profile using the specified parameters.

**Synopsis:**
```bash
aws dms create-instance-profile \
    [--availability-zone <value>] \
    [--kms-key-arn <value>] \
    [--publicly-accessible | --no-publicly-accessible] \
    [--tags <value>] \
    [--network-type <value>] \
    [--instance-profile-name <value>] \
    [--description <value>] \
    [--subnet-group-identifier <value>] \
    [--vpc-security-groups <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--availability-zone` | No | string | -- | Availability zone |
| `--kms-key-arn` | No | string | -- | KMS key ARN for encryption |
| `--publicly-accessible` | No | boolean | -- | Public accessibility |
| `--tags` | No | list | -- | Tags |
| `--network-type` | No | string | -- | Network type |
| `--instance-profile-name` | No | string | -- | User-friendly name |
| `--description` | No | string | -- | Description |
| `--subnet-group-identifier` | No | string | -- | Subnet group identifier |
| `--vpc-security-groups` | No | list(string) | -- | VPC security groups |

**Output Schema:**
```json
{
    "InstanceProfile": {
        "InstanceProfileArn": "string",
        "AvailabilityZone": "string",
        "KmsKeyArn": "string",
        "PubliclyAccessible": "boolean",
        "NetworkType": "string",
        "InstanceProfileName": "string",
        "Description": "string",
        "InstanceProfileCreationTime": "timestamp",
        "SubnetGroupIdentifier": "string",
        "VpcSecurityGroups": ["string"]
    }
}
```

---

### 7.10 `delete-instance-profile`

Deletes the specified instance profile.

**Synopsis:**
```bash
aws dms delete-instance-profile \
    --instance-profile-identifier <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-profile-identifier` | **Yes** | string | -- | Instance profile identifier or ARN |

**Output Schema:** Same as `create-instance-profile`.

---

### 7.11 `describe-instance-profiles`

Returns a paginated list of instance profiles. **Paginated operation.**

**Synopsis:**
```bash
aws dms describe-instance-profiles \
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
| `--filters` | No | list | -- | Filters: `instance-profile-identifier`, `instance-profile-name` |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per API call |
| `--max-items` | No | integer | -- | Total items to return |

**Output Schema:**
```json
{
    "Marker": "string",
    "InstanceProfiles": [
        {
            "InstanceProfileArn": "string",
            "AvailabilityZone": "string",
            "KmsKeyArn": "string",
            "PubliclyAccessible": "boolean",
            "NetworkType": "string",
            "InstanceProfileName": "string",
            "Description": "string",
            "InstanceProfileCreationTime": "timestamp",
            "SubnetGroupIdentifier": "string",
            "VpcSecurityGroups": ["string"]
        }
    ]
}
```

---

### 7.12 `modify-instance-profile`

Modifies the specified instance profile.

**Synopsis:**
```bash
aws dms modify-instance-profile \
    --instance-profile-identifier <value> \
    [--availability-zone <value>] \
    [--kms-key-arn <value>] \
    [--publicly-accessible | --no-publicly-accessible] \
    [--network-type <value>] \
    [--instance-profile-name <value>] \
    [--description <value>] \
    [--subnet-group-identifier <value>] \
    [--vpc-security-groups <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-profile-identifier` | **Yes** | string | -- | Instance profile identifier or ARN |
| `--availability-zone` | No | string | -- | New AZ |
| `--kms-key-arn` | No | string | -- | New KMS key |
| `--publicly-accessible` | No | boolean | -- | New public accessibility |
| `--network-type` | No | string | -- | New network type |
| `--instance-profile-name` | No | string | -- | New name |
| `--description` | No | string | -- | New description |
| `--subnet-group-identifier` | No | string | -- | New subnet group |
| `--vpc-security-groups` | No | list(string) | -- | New VPC security groups |

**Output Schema:** Same as `create-instance-profile`.
