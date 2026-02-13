# Notebooks

## 1. `create-notebook-instance`

Creates a SageMaker notebook instance for Jupyter.

**Synopsis:**
```bash
aws sagemaker create-notebook-instance \
    --notebook-instance-name <value> \
    --instance-type <value> \
    --role-arn <value> \
    [--subnet-id <value>] \
    [--security-group-ids <value>] \
    [--kms-key-id <value>] \
    [--tags <value>] \
    [--lifecycle-config-name <value>] \
    [--direct-internet-access <value>] \
    [--volume-size-in-gb <value>] \
    [--accelerator-types <value>] \
    [--default-code-repository <value>] \
    [--additional-code-repositories <value>] \
    [--root-access <value>] \
    [--platform-identifier <value>] \
    [--instance-metadata-service-configuration <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--notebook-instance-name` | **Yes** | string | -- | Name (max 63 chars) |
| `--instance-type` | **Yes** | string | -- | `ml.t2.medium`, `ml.t3.medium`, `ml.m5.xlarge`, `ml.p3.2xlarge`, etc. |
| `--role-arn` | **Yes** | string | -- | IAM role ARN |
| `--subnet-id` | No | string | -- | VPC subnet ID |
| `--security-group-ids` | No | list | -- | VPC security groups (max 5) |
| `--kms-key-id` | No | string | -- | KMS key for encryption |
| `--lifecycle-config-name` | No | string | -- | Lifecycle configuration name |
| `--direct-internet-access` | No | string | `Enabled` | `Enabled` or `Disabled` |
| `--volume-size-in-gb` | No | integer | 5 | EBS volume size (5-16384 GB) |
| `--accelerator-types` | No | list | -- | Elastic Inference accelerator types |
| `--default-code-repository` | No | string | -- | Default Git repository |
| `--additional-code-repositories` | No | list | -- | Additional Git repos (max 3) |
| `--root-access` | No | string | `Enabled` | `Enabled` or `Disabled` |
| `--platform-identifier` | No | string | -- | Platform: `notebook-al1-v1`, `notebook-al2-v1`, `notebook-al2-v2` |
| `--instance-metadata-service-configuration` | No | structure | -- | `MinimumInstanceMetadataServiceVersion`: `1` or `2` |
| `--tags` | No | list | -- | Key-value tags |

**Output Schema:**
```json
{
    "NotebookInstanceArn": "string"
}
```

---

## 2. `describe-notebook-instance`

Returns details about a notebook instance.

```bash
aws sagemaker describe-notebook-instance --notebook-instance-name <value>
```

**Output Schema:**
```json
{
    "NotebookInstanceArn": "string",
    "NotebookInstanceName": "string",
    "NotebookInstanceStatus": "Pending|InService|Stopping|Stopped|Failed|Deleting|Updating",
    "FailureReason": "string",
    "Url": "string",
    "InstanceType": "string",
    "SubnetId": "string",
    "SecurityGroups": ["string"],
    "RoleArn": "string",
    "KmsKeyId": "string",
    "NetworkInterfaceId": "string",
    "LastModifiedTime": "timestamp",
    "CreationTime": "timestamp",
    "NotebookInstanceLifecycleConfigName": "string",
    "DirectInternetAccess": "Enabled|Disabled",
    "VolumeSizeInGB": "integer",
    "AcceleratorTypes": ["string"],
    "DefaultCodeRepository": "string",
    "AdditionalCodeRepositories": ["string"],
    "RootAccess": "Enabled|Disabled",
    "PlatformIdentifier": "string",
    "InstanceMetadataServiceConfiguration": {"MinimumInstanceMetadataServiceVersion": "string"}
}
```

---

## 3. `list-notebook-instances`

Lists notebook instances. **Paginated operation.**

```bash
aws sagemaker list-notebook-instances \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--name-contains <value>] \
    [--creation-time-before <value>] \
    [--creation-time-after <value>] \
    [--last-modified-time-before <value>] \
    [--last-modified-time-after <value>] \
    [--status-equals <value>] \
    [--notebook-instance-lifecycle-config-name-contains <value>] \
    [--default-code-repository-contains <value>] \
    [--additional-code-repository-equals <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

---

## 4. `update-notebook-instance`

Updates a notebook instance (instance type, role, volume, etc.).

```bash
aws sagemaker update-notebook-instance \
    --notebook-instance-name <value> \
    [--instance-type <value>] \
    [--role-arn <value>] \
    [--lifecycle-config-name <value>] \
    [--disassociate-lifecycle-config | --no-disassociate-lifecycle-config] \
    [--volume-size-in-gb <value>] \
    [--default-code-repository <value>] \
    [--additional-code-repositories <value>] \
    [--accelerator-types <value>] \
    [--disassociate-accelerator-types | --no-disassociate-accelerator-types] \
    [--disassociate-default-code-repository | --no-disassociate-default-code-repository] \
    [--disassociate-additional-code-repositories | --no-disassociate-additional-code-repositories] \
    [--root-access <value>] \
    [--instance-metadata-service-configuration <value>]
```

**Output:** None

---

## 5. `start-notebook-instance` / `stop-notebook-instance` / `delete-notebook-instance`

```bash
aws sagemaker start-notebook-instance --notebook-instance-name <value>
aws sagemaker stop-notebook-instance --notebook-instance-name <value>
aws sagemaker delete-notebook-instance --notebook-instance-name <value>
```

**Output:** None

---

## 6. `create-notebook-instance-lifecycle-config`

Creates a lifecycle configuration with startup and creation scripts.

```bash
aws sagemaker create-notebook-instance-lifecycle-config \
    --notebook-instance-lifecycle-config-name <value> \
    [--on-create <value>] \
    [--on-start <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--notebook-instance-lifecycle-config-name` | **Yes** | string | -- | Config name (max 63 chars) |
| `--on-create` | No | list | -- | Scripts run when instance is created (`Content`: base64-encoded script, max 16384 chars) |
| `--on-start` | No | list | -- | Scripts run each time instance starts |

**Output Schema:**
```json
{
    "NotebookInstanceLifecycleConfigArn": "string"
}
```

---

## 7. `describe-notebook-instance-lifecycle-config` / `list-notebook-instance-lifecycle-configs` / `update-notebook-instance-lifecycle-config` / `delete-notebook-instance-lifecycle-config`

```bash
aws sagemaker describe-notebook-instance-lifecycle-config --notebook-instance-lifecycle-config-name <value>
aws sagemaker list-notebook-instance-lifecycle-configs [--sort-by <value>] [--sort-order <value>] [--name-contains <value>]
aws sagemaker update-notebook-instance-lifecycle-config --notebook-instance-lifecycle-config-name <value> [--on-create <value>] [--on-start <value>]
aws sagemaker delete-notebook-instance-lifecycle-config --notebook-instance-lifecycle-config-name <value>
```

---

## 8. `create-presigned-notebook-instance-url`

Creates a presigned URL for accessing the Jupyter server on a notebook instance.

```bash
aws sagemaker create-presigned-notebook-instance-url \
    --notebook-instance-name <value> \
    [--session-expiration-duration-in-seconds <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--notebook-instance-name` | **Yes** | string | -- | Notebook instance name |
| `--session-expiration-duration-in-seconds` | No | integer | 43200 | URL validity (1800-43200 seconds) |

**Output Schema:**
```json
{
    "AuthorizedUrl": "string"
}
```
