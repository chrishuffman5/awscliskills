# Serverless Namespaces (`aws redshift-serverless`)

### 14.1 `create-namespace`

Creates a new Redshift Serverless namespace (a collection of database objects and users).

**Synopsis:**
```bash
aws redshift-serverless create-namespace \
    --namespace-name <value> \
    [--admin-username <value>] \
    [--admin-user-password <value>] \
    [--db-name <value>] \
    [--default-iam-role-arn <value>] \
    [--iam-roles <value>] \
    [--kms-key-id <value>] \
    [--log-exports <value>] \
    [--manage-admin-password | --no-manage-admin-password] \
    [--admin-password-secret-kms-key-id <value>] \
    [--redshift-idc-application-arn <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--namespace-name` | **Yes** | string | -- | Namespace name (3-64 chars, lowercase, hyphens) |
| `--admin-username` | No | string | -- | Admin user name |
| `--admin-user-password` | No | string | -- | Admin user password (8-64 chars) |
| `--db-name` | No | string | `dev` | Default database name |
| `--default-iam-role-arn` | No | string | -- | Default IAM role ARN |
| `--iam-roles` | No | list(string) | -- | IAM role ARNs to associate |
| `--kms-key-id` | No | string | -- | KMS key for encryption |
| `--log-exports` | No | list(string) | -- | Log types: `useractivitylog`, `userlog`, `connectionlog` |
| `--manage-admin-password` | No | boolean | false | Use Secrets Manager for admin password |
| `--admin-password-secret-kms-key-id` | No | string | -- | KMS key for Secrets Manager secret |
| `--redshift-idc-application-arn` | No | string | -- | Identity Center application ARN |
| `--tags` | No | list | -- | Tags. Shorthand: `key=string,value=string ...` |

**Output Schema:**
```json
{
    "namespace": {
        "namespaceName": "string",
        "namespaceId": "string",
        "namespaceArn": "string",
        "adminUsername": "string",
        "dbName": "string",
        "status": "AVAILABLE|MODIFYING|DELETING",
        "creationDate": "timestamp",
        "kmsKeyId": "string",
        "defaultIamRoleArn": "string",
        "iamRoles": ["string"],
        "logExports": ["string"],
        "adminPasswordSecretArn": "string",
        "adminPasswordSecretKmsKeyId": "string"
    }
}
```

---

### 14.2 `delete-namespace`

Deletes a serverless namespace.

**Synopsis:**
```bash
aws redshift-serverless delete-namespace \
    --namespace-name <value> \
    [--final-snapshot-name <value>] \
    [--final-snapshot-retention-period <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--namespace-name` | **Yes** | string | -- | Namespace to delete |
| `--final-snapshot-name` | No | string | -- | Name of final snapshot to create |
| `--final-snapshot-retention-period` | No | integer | -- | Retention period for final snapshot |

**Output Schema:**
```json
{
    "namespace": {
        "namespaceName": "string",
        "namespaceId": "string",
        "namespaceArn": "string",
        "status": "DELETING"
    }
}
```

---

### 14.3 `get-namespace`

Returns information about a specific namespace.

**Synopsis:**
```bash
aws redshift-serverless get-namespace \
    --namespace-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--namespace-name` | **Yes** | string | -- | Namespace to describe |

**Output Schema:**
```json
{
    "namespace": {
        "namespaceName": "string",
        "namespaceId": "string",
        "namespaceArn": "string",
        "adminUsername": "string",
        "dbName": "string",
        "status": "AVAILABLE|MODIFYING|DELETING",
        "creationDate": "timestamp",
        "kmsKeyId": "string",
        "defaultIamRoleArn": "string",
        "iamRoles": ["string"],
        "logExports": ["string"],
        "adminPasswordSecretArn": "string",
        "adminPasswordSecretKmsKeyId": "string"
    }
}
```

---

### 14.4 `list-namespaces`

Lists all serverless namespaces. **Paginated operation.**

**Synopsis:**
```bash
aws redshift-serverless list-namespaces \
    [--next-token <value>] \
    [--max-results <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--next-token` | No | string | -- | Pagination token |
| `--max-results` | No | integer | -- | Maximum results (1-100) |

**Output Schema:**
```json
{
    "namespaces": [
        {
            "namespaceName": "string",
            "namespaceId": "string",
            "namespaceArn": "string",
            "adminUsername": "string",
            "dbName": "string",
            "status": "string",
            "creationDate": "timestamp",
            "kmsKeyId": "string",
            "defaultIamRoleArn": "string",
            "iamRoles": ["string"],
            "logExports": ["string"]
        }
    ],
    "nextToken": "string"
}
```

---

### 14.5 `update-namespace`

Updates a serverless namespace.

**Synopsis:**
```bash
aws redshift-serverless update-namespace \
    --namespace-name <value> \
    [--admin-username <value>] \
    [--admin-user-password <value>] \
    [--kms-key-id <value>] \
    [--default-iam-role-arn <value>] \
    [--iam-roles <value>] \
    [--log-exports <value>] \
    [--manage-admin-password | --no-manage-admin-password] \
    [--admin-password-secret-kms-key-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--namespace-name` | **Yes** | string | -- | Namespace to update |
| `--admin-username` | No | string | -- | New admin user name |
| `--admin-user-password` | No | string | -- | New admin password |
| `--kms-key-id` | No | string | -- | New KMS key |
| `--default-iam-role-arn` | No | string | -- | New default IAM role |
| `--iam-roles` | No | list(string) | -- | New IAM roles |
| `--log-exports` | No | list(string) | -- | New log export types |
| `--manage-admin-password` | No | boolean | -- | Use Secrets Manager for admin password |
| `--admin-password-secret-kms-key-id` | No | string | -- | KMS key for Secrets Manager secret |

**Output Schema:**
```json
{
    "namespace": {
        "namespaceName": "string",
        "namespaceId": "string",
        "namespaceArn": "string",
        "adminUsername": "string",
        "dbName": "string",
        "status": "MODIFYING",
        "kmsKeyId": "string",
        "defaultIamRoleArn": "string",
        "iamRoles": ["string"],
        "logExports": ["string"]
    }
}
```
