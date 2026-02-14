# Certificates

### 6.1 `associate-certificate`

Associates an ACM certificate with MediaConvert for DRM encryption workflows.

**Synopsis:**
```bash
aws mediaconvert associate-certificate \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the ACM certificate to associate |

**Output:** None

---

### 6.2 `disassociate-certificate`

Disassociates an ACM certificate from MediaConvert.

**Synopsis:**
```bash
aws mediaconvert disassociate-certificate \
    --arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--arn` | **Yes** | string | -- | ARN of the ACM certificate to disassociate |

**Output:** None
