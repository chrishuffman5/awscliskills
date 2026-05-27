# Domains (Studio)

## 1. `create-domain`

Creates a SageMaker Studio domain.

**Synopsis:**
```bash
aws sagemaker create-domain \
    --domain-name <value> \
    --auth-mode <value> \
    --default-user-settings <value> \
    --subnet-ids <value> \
    --vpc-id <value> \
    [--app-network-access-type <value>] \
    [--home-efs-file-system-kms-key-id <value>] \
    [--kms-key-id <value>] \
    [--default-space-settings <value>] \
    [--domain-settings <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Domain name (max 63 chars) |
| `--auth-mode` | **Yes** | string | -- | `SSO` or `IAM` |
| `--default-user-settings` | **Yes** | structure | -- | Default settings for user profiles |
| `--subnet-ids` | **Yes** | list | -- | VPC subnet IDs (1-16) |
| `--vpc-id` | **Yes** | string | -- | VPC ID |
| `--app-network-access-type` | No | string | `PublicInternetOnly` | `PublicInternetOnly` or `VpcOnly` |
| `--home-efs-file-system-kms-key-id` | No | string | -- | KMS key for EFS encryption |
| `--kms-key-id` | No | string | -- | KMS key for EBS volumes |
| `--default-space-settings` | No | structure | -- | Default settings for spaces |
| `--domain-settings` | No | structure | -- | Docker access, RStudio, security group |
| `--tags` | No | list | -- | Key-value tags |

**Output Schema:**
```json
{
    "DomainArn": "string",
    "Url": "string"
}
```

---

## 2. `describe-domain`

Returns details about a Studio domain.

```bash
aws sagemaker describe-domain --domain-id <value>
```

**Output Schema:**
```json
{
    "DomainArn": "string",
    "DomainId": "string",
    "DomainName": "string",
    "HomeEfsFileSystemId": "string",
    "SingleSignOnManagedApplicationInstanceId": "string",
    "SingleSignOnApplicationArn": "string",
    "Status": "Deleting|Failed|InService|Pending|Updating|Update_Failed|Delete_Failed",
    "CreationTime": "timestamp",
    "LastModifiedTime": "timestamp",
    "FailureReason": "string",
    "SecurityGroupIdForDomainBoundary": "string",
    "AuthMode": "SSO|IAM",
    "DefaultUserSettings": {...},
    "DomainSettings": {...},
    "AppNetworkAccessType": "PublicInternetOnly|VpcOnly",
    "SubnetIds": ["string"],
    "Url": "string",
    "VpcId": "string",
    "KmsKeyId": "string",
    "DefaultSpaceSettings": {...},
    "AppSecurityGroupManagement": "Service|Customer",
    "TagPropagation": "ENABLED|DISABLED"
}
```

---

## 3. `list-domains`

Lists Studio domains. **Paginated operation.**

```bash
aws sagemaker list-domains \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

---

## 4. `update-domain`

Updates a Studio domain.

```bash
aws sagemaker update-domain \
    --domain-id <value> \
    [--default-user-settings <value>] \
    [--domain-settings-for-update <value>] \
    [--app-security-group-management <value>] \
    [--default-space-settings <value>] \
    [--subnet-ids <value>] \
    [--app-network-access-type <value>] \
    [--tag-propagation <value>]
```

**Output Schema:**
```json
{
    "DomainArn": "string"
}
```

---

## 5. `delete-domain`

Deletes a Studio domain.

```bash
aws sagemaker delete-domain \
    --domain-id <value> \
    [--retention-policy <value>]
```

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-id` | **Yes** | string | -- | Domain ID |
| `--retention-policy` | No | structure | -- | `HomeEfsFileSystem`: `Retain` or `Delete` |

**Output:** None

---

## User Profiles

### 6. `create-user-profile`

Creates a user profile in a Studio domain.

```bash
aws sagemaker create-user-profile \
    --domain-id <value> \
    --user-profile-name <value> \
    [--single-sign-on-user-identifier <value>] \
    [--single-sign-on-user-value <value>] \
    [--user-settings <value>] \
    [--tags <value>]
```

**Output Schema:**
```json
{
    "UserProfileArn": "string"
}
```

---

### 7. `describe-user-profile`

```bash
aws sagemaker describe-user-profile \
    --domain-id <value> \
    --user-profile-name <value>
```

**Output Schema:**
```json
{
    "DomainId": "string",
    "UserProfileArn": "string",
    "UserProfileName": "string",
    "HomeEfsFileSystemUid": "string",
    "Status": "Deleting|Failed|InService|Pending|Updating|Update_Failed|Delete_Failed",
    "LastModifiedTime": "timestamp",
    "CreationTime": "timestamp",
    "FailureReason": "string",
    "SingleSignOnUserIdentifier": "string",
    "SingleSignOnUserValue": "string",
    "UserSettings": {...}
}
```

---

### 8. `list-user-profiles` / `update-user-profile` / `delete-user-profile`

```bash
aws sagemaker list-user-profiles [--sort-by <value>] [--sort-order <value>] [--domain-id-equals <value>] [--user-profile-name-contains <value>]
aws sagemaker update-user-profile --domain-id <value> --user-profile-name <value> [--user-settings <value>]
aws sagemaker delete-user-profile --domain-id <value> --user-profile-name <value>
```

---

## Spaces

### 9. `create-space`

Creates a shared space in a Studio domain.

```bash
aws sagemaker create-space \
    --domain-id <value> \
    --space-name <value> \
    [--tags <value>] \
    [--space-settings <value>] \
    [--ownership-settings <value>] \
    [--space-sharing-settings <value>] \
    [--space-display-name <value>]
```

**Output Schema:**
```json
{
    "SpaceArn": "string"
}
```

---

### 10. `describe-space` / `list-spaces` / `update-space` / `delete-space`

```bash
aws sagemaker describe-space --domain-id <value> --space-name <value>
aws sagemaker list-spaces [--sort-by <value>] [--sort-order <value>] [--domain-id-equals <value>] [--space-name-contains <value>]
aws sagemaker update-space --domain-id <value> --space-name <value> [--space-settings <value>] [--space-display-name <value>]
aws sagemaker delete-space --domain-id <value> --space-name <value>
```

---

## Apps

### 11. `create-app`

Creates an application in a domain (JupyterServer, KernelGateway, etc.).

```bash
aws sagemaker create-app \
    --domain-id <value> \
    --app-type <value> \
    --app-name <value> \
    [--user-profile-name <value>] \
    [--space-name <value>] \
    [--tags <value>] \
    [--resource-spec <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-id` | **Yes** | string | -- | Domain ID |
| `--app-type` | **Yes** | string | -- | `JupyterServer`, `KernelGateway`, `DetailedProfiler`, `TensorBoard`, `CodeEditor`, `JupyterLab`, `RStudioServerPro`, `RSessionGateway`, `Canvas` |
| `--app-name` | **Yes** | string | -- | App name (max 63 chars) |
| `--user-profile-name` | No | string | -- | User profile name (for user apps) |
| `--space-name` | No | string | -- | Space name (for shared apps) |
| `--resource-spec` | No | structure | -- | Instance type, SageMaker image, lifecycle config |

**Output Schema:**
```json
{
    "AppArn": "string"
}
```

---

### 12. `describe-app` / `list-apps` / `delete-app`

```bash
aws sagemaker describe-app --domain-id <value> --app-type <value> --app-name <value> [--user-profile-name <value>] [--space-name <value>]
aws sagemaker list-apps [--sort-by <value>] [--sort-order <value>] [--domain-id-equals <value>] [--user-profile-name-equals <value>] [--space-name-equals <value>]
aws sagemaker delete-app --domain-id <value> --app-type <value> --app-name <value> [--user-profile-name <value>] [--space-name <value>]
```

---

## 13. `create-presigned-domain-url`

Creates a presigned URL for accessing a Studio domain.

```bash
aws sagemaker create-presigned-domain-url \
    --domain-id <value> \
    --user-profile-name <value> \
    [--session-expiration-duration-in-seconds <value>] \
    [--expires-in-seconds <value>] \
    [--space-name <value>] \
    [--landing-uri <value>]
```

**Output Schema:**
```json
{
    "AuthorizedUrl": "string"
}
```
