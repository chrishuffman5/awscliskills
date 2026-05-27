# Encryption

### 8.1 `get-encryption-key`

Gets the KMS key used to encrypt a specified resource type and scan type.

**Synopsis:**
```bash
aws inspector2 get-encryption-key \
    --scan-type <value> \
    --resource-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--scan-type` | **Yes** | string | -- | Scan type: `NETWORK`, `PACKAGE`, `CODE` |
| `--resource-type` | **Yes** | string | -- | Resource type: `AWS_EC2_INSTANCE`, `AWS_ECR_CONTAINER_IMAGE`, `AWS_ECR_REPOSITORY`, `AWS_LAMBDA_FUNCTION`, `CODE_REPOSITORY` |

**Output Schema:**
```json
{
    "kmsKeyId": "string"
}
```

---

### 8.2 `update-encryption-key`

Updates the KMS key used to encrypt a specified resource type and scan type.

**Synopsis:**
```bash
aws inspector2 update-encryption-key \
    --kms-key-id <value> \
    --scan-type <value> \
    --resource-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--kms-key-id` | **Yes** | string | -- | ARN of the KMS key to use for encryption |
| `--scan-type` | **Yes** | string | -- | Scan type: `NETWORK`, `PACKAGE`, `CODE` |
| `--resource-type` | **Yes** | string | -- | Resource type: `AWS_EC2_INSTANCE`, `AWS_ECR_CONTAINER_IMAGE`, `AWS_ECR_REPOSITORY`, `AWS_LAMBDA_FUNCTION`, `CODE_REPOSITORY` |

**Output Schema:** Empty on success.

---

### 8.3 `reset-encryption-key`

Resets encryption to the AWS-managed key for a specified resource type and scan type.

**Synopsis:**
```bash
aws inspector2 reset-encryption-key \
    --scan-type <value> \
    --resource-type <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--scan-type` | **Yes** | string | -- | Scan type: `NETWORK`, `PACKAGE`, `CODE` |
| `--resource-type` | **Yes** | string | -- | Resource type: `AWS_EC2_INSTANCE`, `AWS_ECR_CONTAINER_IMAGE`, `AWS_ECR_REPOSITORY`, `AWS_LAMBDA_FUNCTION`, `CODE_REPOSITORY` |

**Output Schema:** Empty on success.
