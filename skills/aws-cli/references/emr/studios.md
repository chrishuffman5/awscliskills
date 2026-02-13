# Studios

### 6.1 `create-studio`

Creates an EMR Studio (a web-based IDE for Jupyter notebooks).

**Synopsis:**
```bash
aws emr create-studio \
    --name <value> \
    --auth-mode <value> \
    --vpc-id <value> \
    --subnet-ids <value> \
    --service-role <value> \
    --workspace-security-group-id <value> \
    --engine-security-group-id <value> \
    --default-s3-location <value> \
    [--description <value>] \
    [--user-role <value>] \
    [--idp-auth-url <value>] \
    [--idp-relay-state-parameter-name <value>] \
    [--tags <value>] \
    [--trusted-identity-propagation-enabled | --no-trusted-identity-propagation-enabled] \
    [--idc-user-assignment <value>] \
    [--idc-instance-arn <value>] \
    [--encryption-key-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Studio name |
| `--auth-mode` | **Yes** | string | -- | `SSO` or `IAM` |
| `--vpc-id` | **Yes** | string | -- | VPC ID |
| `--subnet-ids` | **Yes** | list(string) | -- | Subnet IDs |
| `--service-role` | **Yes** | string | -- | IAM service role ARN |
| `--workspace-security-group-id` | **Yes** | string | -- | Workspace security group |
| `--engine-security-group-id` | **Yes** | string | -- | Engine security group |
| `--default-s3-location` | **Yes** | string | -- | Default S3 location for notebooks |
| `--description` | No | string | -- | Description |
| `--user-role` | No | string | -- | IAM user role ARN (for IAM mode) |
| `--tags` | No | list | -- | Tags |
| `--encryption-key-arn` | No | string | -- | KMS key ARN for encryption |

**Output Schema:**
```json
{
    "StudioId": "string",
    "Url": "string"
}
```

---

### 6.2 `delete-studio`

Deletes an EMR Studio.

**Synopsis:**
```bash
aws emr delete-studio \
    --studio-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--studio-id` | **Yes** | string | -- | Studio ID to delete |

No output on success.

---

### 6.3 `describe-studio`

Describes an EMR Studio.

**Synopsis:**
```bash
aws emr describe-studio \
    --studio-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--studio-id` | **Yes** | string | -- | Studio ID |

**Output Schema:**
```json
{
    "Studio": {
        "StudioId": "string",
        "StudioArn": "string",
        "Name": "string",
        "Description": "string",
        "AuthMode": "SSO|IAM",
        "VpcId": "string",
        "SubnetIds": ["string"],
        "ServiceRole": "string",
        "UserRole": "string",
        "WorkspaceSecurityGroupId": "string",
        "EngineSecurityGroupId": "string",
        "Url": "string",
        "CreationTime": "timestamp",
        "DefaultS3Location": "string",
        "Tags": [{"Key": "string", "Value": "string"}],
        "EncryptionKeyArn": "string"
    }
}
```

---

### 6.4 `list-studios`

Lists all EMR Studios. **Paginated operation.**

**Synopsis:**
```bash
aws emr list-studios \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "Studios": [
        {
            "StudioId": "string",
            "Name": "string",
            "VpcId": "string",
            "Url": "string",
            "AuthMode": "string",
            "CreationTime": "timestamp",
            "Description": "string"
        }
    ],
    "Marker": "string"
}
```

---

### 6.5 `update-studio`

Updates an EMR Studio configuration.

**Synopsis:**
```bash
aws emr update-studio \
    --studio-id <value> \
    [--name <value>] \
    [--description <value>] \
    [--subnet-ids <value>] \
    [--default-s3-location <value>] \
    [--encryption-key-arn <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--studio-id` | **Yes** | string | -- | Studio to update |
| `--name` | No | string | -- | New name |
| `--description` | No | string | -- | New description |
| `--subnet-ids` | No | list(string) | -- | New subnet IDs |
| `--default-s3-location` | No | string | -- | New default S3 location |
| `--encryption-key-arn` | No | string | -- | New KMS key ARN |

No output on success.

---

### 6.6 `create-studio-session-mapping`

Maps a user or group to an EMR Studio.

**Synopsis:**
```bash
aws emr create-studio-session-mapping \
    --studio-id <value> \
    --identity-type <value> \
    --session-policy-arn <value> \
    [--identity-id <value>] \
    [--identity-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--studio-id` | **Yes** | string | -- | Studio ID |
| `--identity-type` | **Yes** | string | -- | `USER` or `GROUP` |
| `--session-policy-arn` | **Yes** | string | -- | IAM session policy ARN |
| `--identity-id` | No | string | -- | IAM Identity Center identity ID |
| `--identity-name` | No | string | -- | Identity name |

No output on success.

---

### 6.7 `delete-studio-session-mapping`

Deletes a session mapping.

**Synopsis:**
```bash
aws emr delete-studio-session-mapping \
    --studio-id <value> \
    --identity-type <value> \
    [--identity-id <value>] \
    [--identity-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--studio-id` | **Yes** | string | -- | Studio ID |
| `--identity-type` | **Yes** | string | -- | `USER` or `GROUP` |
| `--identity-id` | No | string | -- | Identity ID |
| `--identity-name` | No | string | -- | Identity name |

No output on success.

---

### 6.8 `get-studio-session-mapping`

Gets a session mapping.

**Synopsis:**
```bash
aws emr get-studio-session-mapping \
    --studio-id <value> \
    --identity-type <value> \
    [--identity-id <value>] \
    [--identity-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--studio-id` | **Yes** | string | -- | Studio ID |
| `--identity-type` | **Yes** | string | -- | `USER` or `GROUP` |
| `--identity-id` | No | string | -- | Identity ID |
| `--identity-name` | No | string | -- | Identity name |

**Output Schema:**
```json
{
    "SessionMapping": {
        "StudioId": "string",
        "IdentityId": "string",
        "IdentityName": "string",
        "IdentityType": "USER|GROUP",
        "SessionPolicyArn": "string",
        "CreationTime": "timestamp",
        "LastModifiedTime": "timestamp"
    }
}
```

---

### 6.9 `list-studio-session-mappings`

Lists session mappings. **Paginated operation.**

**Synopsis:**
```bash
aws emr list-studio-session-mappings \
    [--studio-id <value>] \
    [--identity-type <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--studio-id` | No | string | -- | Filter by studio |
| `--identity-type` | No | string | -- | Filter: `USER` or `GROUP` |
| `--starting-token` | No | string | -- | Pagination token |
| `--page-size` | No | integer | -- | Items per page |
| `--max-items` | No | integer | -- | Maximum total items |

**Output Schema:**
```json
{
    "SessionMappings": [
        {
            "StudioId": "string",
            "IdentityId": "string",
            "IdentityName": "string",
            "IdentityType": "USER|GROUP",
            "SessionPolicyArn": "string",
            "CreationTime": "timestamp"
        }
    ],
    "Marker": "string"
}
```

---

### 6.10 `update-studio-session-mapping`

Updates a session mapping's policy.

**Synopsis:**
```bash
aws emr update-studio-session-mapping \
    --studio-id <value> \
    --identity-type <value> \
    --session-policy-arn <value> \
    [--identity-id <value>] \
    [--identity-name <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--studio-id` | **Yes** | string | -- | Studio ID |
| `--identity-type` | **Yes** | string | -- | `USER` or `GROUP` |
| `--session-policy-arn` | **Yes** | string | -- | New session policy ARN |
| `--identity-id` | No | string | -- | Identity ID |
| `--identity-name` | No | string | -- | Identity name |

No output on success.
