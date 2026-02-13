# Access Grants

### 3.1 `create-access-grants-instance`

Creates an S3 Access Grants instance, which serves as a logical grouping for access grants.

**Synopsis:**
```bash
aws s3control create-access-grants-instance \
    --account-id <value> \
    [--identity-center-arn <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--identity-center-arn` | No | string | None | ARN of the IAM Identity Center instance to associate |
| `--tags` | No | list | None | Key-value tags. Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "CreatedAt": "timestamp",
    "AccessGrantsInstanceId": "string",
    "AccessGrantsInstanceArn": "string",
    "IdentityCenterArn": "string",
    "IdentityCenterInstanceArn": "string",
    "IdentityCenterApplicationArn": "string"
}
```

---

### 3.2 `delete-access-grants-instance`

Deletes the S3 Access Grants instance. All access grants and locations must be deleted first.

**Synopsis:**
```bash
aws s3control delete-access-grants-instance \
    --account-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |

**Output:** None

---

### 3.3 `get-access-grants-instance`

Retrieves the S3 Access Grants instance details.

**Synopsis:**
```bash
aws s3control get-access-grants-instance \
    --account-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |

**Output Schema:**
```json
{
    "AccessGrantsInstanceArn": "string",
    "AccessGrantsInstanceId": "string",
    "IdentityCenterArn": "string",
    "IdentityCenterInstanceArn": "string",
    "IdentityCenterApplicationArn": "string",
    "CreatedAt": "timestamp"
}
```

---

### 3.4 `list-access-grants-instances`

Lists the S3 Access Grants instances. **Paginated.**

**Synopsis:**
```bash
aws s3control list-access-grants-instances \
    --account-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "AccessGrantsInstancesList": [
        {
            "AccessGrantsInstanceId": "string",
            "AccessGrantsInstanceArn": "string",
            "IdentityCenterArn": "string",
            "IdentityCenterInstanceArn": "string",
            "IdentityCenterApplicationArn": "string",
            "CreatedAt": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.5 `get-access-grants-instance-for-prefix`

Retrieves the Access Grants instance that contains a particular S3 prefix.

**Synopsis:**
```bash
aws s3control get-access-grants-instance-for-prefix \
    --account-id <value> \
    --s3-prefix <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--s3-prefix` | **Yes** | string | -- | S3 prefix (e.g., `s3://bucket/prefix/`) |

**Output Schema:**
```json
{
    "AccessGrantsInstanceArn": "string",
    "AccessGrantsInstanceId": "string"
}
```

---

### 3.6 `get-access-grants-instance-resource-policy`

Returns the resource policy of the S3 Access Grants instance.

**Synopsis:**
```bash
aws s3control get-access-grants-instance-resource-policy \
    --account-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |

**Output Schema:**
```json
{
    "Policy": "string",
    "Organization": "string",
    "CreatedAt": "timestamp"
}
```

---

### 3.7 `put-access-grants-instance-resource-policy`

Updates the resource policy of the S3 Access Grants instance.

**Synopsis:**
```bash
aws s3control put-access-grants-instance-resource-policy \
    --account-id <value> \
    --policy <value> \
    [--organization <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--policy` | **Yes** | string | -- | JSON resource policy document |
| `--organization` | No | string | None | Organization ID for cross-account access |

**Output Schema:**
```json
{
    "Policy": "string",
    "Organization": "string",
    "CreatedAt": "timestamp"
}
```

---

### 3.8 `delete-access-grants-instance-resource-policy`

Deletes the resource policy of the S3 Access Grants instance.

**Synopsis:**
```bash
aws s3control delete-access-grants-instance-resource-policy \
    --account-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |

**Output:** None

---

### 3.9 `associate-access-grants-identity-center`

Associates the S3 Access Grants instance with an IAM Identity Center instance.

**Synopsis:**
```bash
aws s3control associate-access-grants-identity-center \
    --account-id <value> \
    --identity-center-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--identity-center-arn` | **Yes** | string | -- | ARN of IAM Identity Center instance |

**Output:** None

---

### 3.10 `dissociate-access-grants-identity-center`

Dissociates the S3 Access Grants instance from the IAM Identity Center instance.

**Synopsis:**
```bash
aws s3control dissociate-access-grants-identity-center \
    --account-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |

**Output:** None

---

### 3.11 `create-access-grants-location`

Registers an S3 location (bucket or prefix) with the Access Grants instance.

**Synopsis:**
```bash
aws s3control create-access-grants-location \
    --account-id <value> \
    --location-scope <value> \
    --iam-role-arn <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--location-scope` | **Yes** | string | -- | S3 URI for the location (e.g., `s3://bucket/prefix/`) |
| `--iam-role-arn` | **Yes** | string | -- | IAM role ARN that Access Grants assumes to vend credentials |
| `--tags` | No | list | None | Key-value tags. Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "CreatedAt": "timestamp",
    "AccessGrantsLocationId": "string",
    "AccessGrantsLocationArn": "string",
    "LocationScope": "string",
    "IAMRoleArn": "string"
}
```

---

### 3.12 `delete-access-grants-location`

Deletes a registered location from the Access Grants instance.

**Synopsis:**
```bash
aws s3control delete-access-grants-location \
    --account-id <value> \
    --access-grants-location-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--access-grants-location-id` | **Yes** | string | -- | Location ID to delete |

**Output:** None

---

### 3.13 `get-access-grants-location`

Retrieves details of a registered location.

**Synopsis:**
```bash
aws s3control get-access-grants-location \
    --account-id <value> \
    --access-grants-location-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--access-grants-location-id` | **Yes** | string | -- | Location ID |

**Output Schema:**
```json
{
    "CreatedAt": "timestamp",
    "AccessGrantsLocationId": "string",
    "AccessGrantsLocationArn": "string",
    "LocationScope": "string",
    "IAMRoleArn": "string"
}
```

---

### 3.14 `list-access-grants-locations`

Lists the registered locations in the Access Grants instance. **Paginated.**

**Synopsis:**
```bash
aws s3control list-access-grants-locations \
    --account-id <value> \
    [--location-scope <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--location-scope` | No | string | None | Filter by S3 prefix |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "AccessGrantsLocationsList": [
        {
            "CreatedAt": "timestamp",
            "AccessGrantsLocationId": "string",
            "AccessGrantsLocationArn": "string",
            "LocationScope": "string",
            "IAMRoleArn": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.15 `update-access-grants-location`

Updates a registered location's IAM role.

**Synopsis:**
```bash
aws s3control update-access-grants-location \
    --account-id <value> \
    --access-grants-location-id <value> \
    --iam-role-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--access-grants-location-id` | **Yes** | string | -- | Location ID to update |
| `--iam-role-arn` | **Yes** | string | -- | New IAM role ARN |

**Output Schema:**
```json
{
    "CreatedAt": "timestamp",
    "AccessGrantsLocationId": "string",
    "AccessGrantsLocationArn": "string",
    "LocationScope": "string",
    "IAMRoleArn": "string"
}
```

---

### 3.16 `create-access-grant`

Creates an access grant that gives a grantee access to your S3 data.

**Synopsis:**
```bash
aws s3control create-access-grant \
    --account-id <value> \
    --access-grants-location-id <value> \
    --grantee <value> \
    --permission <value> \
    [--access-grants-location-configuration <value>] \
    [--application-arn <value>] \
    [--s3-prefix-type <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--access-grants-location-id` | **Yes** | string | -- | Location ID for the grant |
| `--grantee` | **Yes** | structure | -- | Grantee identity. Shorthand: `GranteeType=IAM\|DIRECTORY_USER\|DIRECTORY_GROUP,GranteeIdentifier=string` |
| `--permission` | **Yes** | string | -- | Permission: `READ`, `WRITE`, or `READWRITE` |
| `--access-grants-location-configuration` | No | structure | None | Sub-prefix. Shorthand: `S3SubPrefix=string` |
| `--application-arn` | No | string | None | IAM Identity Center application ARN |
| `--s3-prefix-type` | No | string | None | Only value: `Object` |
| `--tags` | No | list | None | Key-value tags |

**Output Schema:**
```json
{
    "CreatedAt": "timestamp",
    "AccessGrantId": "string",
    "AccessGrantArn": "string",
    "Grantee": {
        "GranteeType": "DIRECTORY_USER|DIRECTORY_GROUP|IAM",
        "GranteeIdentifier": "string"
    },
    "AccessGrantsLocationId": "string",
    "AccessGrantsLocationConfiguration": {
        "S3SubPrefix": "string"
    },
    "Permission": "READ|WRITE|READWRITE",
    "ApplicationArn": "string",
    "GrantScope": "string"
}
```

---

### 3.17 `delete-access-grant`

Deletes an access grant.

**Synopsis:**
```bash
aws s3control delete-access-grant \
    --account-id <value> \
    --access-grant-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--access-grant-id` | **Yes** | string | -- | Access grant ID to delete |

**Output:** None

---

### 3.18 `get-access-grant`

Retrieves details of an access grant.

**Synopsis:**
```bash
aws s3control get-access-grant \
    --account-id <value> \
    --access-grant-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--access-grant-id` | **Yes** | string | -- | Access grant ID |

**Output Schema:**
```json
{
    "CreatedAt": "timestamp",
    "AccessGrantId": "string",
    "AccessGrantArn": "string",
    "Grantee": {
        "GranteeType": "DIRECTORY_USER|DIRECTORY_GROUP|IAM",
        "GranteeIdentifier": "string"
    },
    "Permission": "READ|WRITE|READWRITE",
    "AccessGrantsLocationId": "string",
    "AccessGrantsLocationConfiguration": {
        "S3SubPrefix": "string"
    },
    "GrantScope": "string",
    "ApplicationArn": "string"
}
```

---

### 3.19 `list-access-grants`

Lists access grants in the Access Grants instance. **Paginated.**

**Synopsis:**
```bash
aws s3control list-access-grants \
    --account-id <value> \
    [--grantee-type <value>] \
    [--grantee-identifier <value>] \
    [--permission <value>] \
    [--grant-scope <value>] \
    [--application-arn <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--grantee-type` | No | string | None | Filter by grantee type: `DIRECTORY_USER`, `DIRECTORY_GROUP`, `IAM` |
| `--grantee-identifier` | No | string | None | Filter by grantee identifier |
| `--permission` | No | string | None | Filter by permission: `READ`, `WRITE`, `READWRITE` |
| `--grant-scope` | No | string | None | Filter by grant scope (S3 prefix) |
| `--application-arn` | No | string | None | Filter by application ARN |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "AccessGrantsList": [
        {
            "CreatedAt": "timestamp",
            "AccessGrantId": "string",
            "AccessGrantArn": "string",
            "Grantee": {
                "GranteeType": "string",
                "GranteeIdentifier": "string"
            },
            "Permission": "string",
            "AccessGrantsLocationId": "string",
            "AccessGrantsLocationConfiguration": {
                "S3SubPrefix": "string"
            },
            "GrantScope": "string",
            "ApplicationArn": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.20 `list-caller-access-grants`

Lists the access grants that the caller has been granted. **Paginated.**

**Synopsis:**
```bash
aws s3control list-caller-access-grants \
    --account-id <value> \
    [--grant-scope <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--grant-scope` | No | string | None | Filter by S3 prefix |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "CallerAccessGrantsList": [
        {
            "Permission": "string",
            "GrantScope": "string",
            "ApplicationArn": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 3.21 `get-data-access`

Returns temporary credentials for accessing S3 data via Access Grants.

**Synopsis:**
```bash
aws s3control get-data-access \
    --account-id <value> \
    --target <value> \
    --permission <value> \
    [--duration-seconds <value>] \
    [--privilege <value>] \
    [--target-type <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | AWS account ID (12-digit) |
| `--target` | **Yes** | string | -- | S3 URI target (e.g., `s3://bucket/prefix/*`) |
| `--permission` | **Yes** | string | -- | Permission: `READ`, `WRITE`, or `READWRITE` |
| `--duration-seconds` | No | integer | 3600 | Credential duration (900-43200 seconds) |
| `--privilege` | No | string | None | Privilege level: `Minimal` or `Default` |
| `--target-type` | No | string | None | Target type: `Object` |

**Output Schema:**
```json
{
    "Credentials": {
        "AccessKeyId": "string",
        "SecretAccessKey": "string",
        "SessionToken": "string",
        "Expiration": "timestamp"
    },
    "MatchedGrantTarget": "string"
}
```
