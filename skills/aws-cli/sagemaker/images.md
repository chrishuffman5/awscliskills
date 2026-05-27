# Images

## 1. `create-image`

Creates a custom SageMaker image.

**Synopsis:**
```bash
aws sagemaker create-image \
    --image-name <value> \
    --role-arn <value> \
    [--display-name <value>] \
    [--description <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--image-name` | **Yes** | string | -- | Image name (1-63 chars) |
| `--role-arn` | **Yes** | string | -- | IAM role ARN |
| `--display-name` | No | string | -- | Display name (1-128 chars) |
| `--description` | No | string | -- | Description (max 512 chars) |
| `--tags` | No | list | -- | Key-value tags |

**Output Schema:**
```json
{
    "ImageArn": "string"
}
```

---

## 2. `describe-image` / `list-images` / `update-image` / `delete-image`

```bash
aws sagemaker describe-image --image-name <value>
aws sagemaker list-images [--creation-time-after <value>] [--creation-time-before <value>] [--name-contains <value>] [--sort-by <value>] [--sort-order <value>]
aws sagemaker update-image --image-name <value> [--display-name <value>] [--description <value>] [--role-arn <value>]
aws sagemaker delete-image --image-name <value>
```

**describe-image Output:**
```json
{
    "CreationTime": "timestamp",
    "Description": "string",
    "DisplayName": "string",
    "FailureReason": "string",
    "ImageArn": "string",
    "ImageName": "string",
    "ImageStatus": "Creating|Created|CreateFailed|Updating|UpdateFailed|Deleting|DeleteFailed",
    "LastModifiedTime": "timestamp",
    "RoleArn": "string"
}
```

---

## 3. `create-image-version`

Creates a version of a SageMaker image from a container image in ECR.

```bash
aws sagemaker create-image-version \
    --image-name <value> \
    --base-image <value> \
    [--aliases <value>] \
    [--vendor-guidance <value>] \
    [--job-type <value>] \
    [--ml-framework <value>] \
    [--programming-lang <value>] \
    [--processor <value>] \
    [--horovod | --no-horovod] \
    [--release-notes <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--image-name` | **Yes** | string | -- | Image name |
| `--base-image` | **Yes** | string | -- | ECR container image URI |
| `--aliases` | No | list | -- | Version aliases |
| `--vendor-guidance` | No | string | -- | `NOT_PROVIDED`, `STABLE`, `TO_BE_ARCHIVED`, `ARCHIVED` |
| `--job-type` | No | string | -- | `TRAINING`, `INFERENCE`, `NOTEBOOK_KERNEL` |
| `--processor` | No | string | -- | `CPU`, `GPU` |

**Output Schema:**
```json
{
    "ImageVersionArn": "string"
}
```

---

## 4. `describe-image-version` / `list-image-versions` / `update-image-version` / `delete-image-version`

```bash
aws sagemaker describe-image-version --image-name <value> [--version <value>] [--alias <value>]
aws sagemaker list-image-versions --image-name <value> [--creation-time-after <value>] [--creation-time-before <value>] [--sort-by <value>] [--sort-order <value>]
aws sagemaker update-image-version --image-name <value> [--version <value>] [--alias <value>] [--aliases-to-add <value>] [--aliases-to-delete <value>] [--vendor-guidance <value>]
aws sagemaker delete-image-version --image-name <value> [--version <value>] [--alias <value>]
```

---

## 5. `create-app-image-config`

Creates an app image configuration for JupyterLab or KernelGateway.

```bash
aws sagemaker create-app-image-config \
    --app-image-config-name <value> \
    [--kernel-gateway-image-config <value>] \
    [--jupyter-lab-app-image-config <value>] \
    [--code-editor-app-image-config <value>] \
    [--tags <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--app-image-config-name` | **Yes** | string | -- | Config name (max 63 chars) |
| `--kernel-gateway-image-config` | No | structure | -- | Kernel specs and file system config |
| `--jupyter-lab-app-image-config` | No | structure | -- | JupyterLab container config |
| `--code-editor-app-image-config` | No | structure | -- | Code Editor container config |
| `--tags` | No | list | -- | Key-value tags |

**Output Schema:**
```json
{
    "AppImageConfigArn": "string"
}
```

---

## 6. `describe-app-image-config` / `list-app-image-configs` / `update-app-image-config` / `delete-app-image-config`

```bash
aws sagemaker describe-app-image-config --app-image-config-name <value>
aws sagemaker list-app-image-configs [--name-contains <value>] [--creation-time-before <value>] [--creation-time-after <value>] [--sort-by <value>] [--sort-order <value>]
aws sagemaker update-app-image-config --app-image-config-name <value> [--kernel-gateway-image-config <value>] [--jupyter-lab-app-image-config <value>]
aws sagemaker delete-app-image-config --app-image-config-name <value>
```
