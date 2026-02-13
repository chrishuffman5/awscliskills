# Security Account Configuration

> **Note:** CodeGuru Security reached end of support in November 2025. These commands use `aws codeguru-security`.

### 6.1 `get-account-configuration`

Returns the account-level configuration for CodeGuru Security. Uses `aws codeguru-security`.

**Synopsis:**
```bash
aws codeguru-security get-account-configuration \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| -- | -- | -- | -- | No required parameters |

**Output Schema:**
```json
{
    "encryptionConfig": {
        "kmsKeyArn": "string"
    }
}
```

---

### 6.2 `update-account-configuration`

Updates the account-level configuration for CodeGuru Security. Uses `aws codeguru-security`.

**Synopsis:**
```bash
aws codeguru-security update-account-configuration \
    --encryption-config <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--encryption-config` | **Yes** | structure | -- | Encryption configuration. Shorthand: `kmsKeyArn=string` |

**Output Schema:**
```json
{
    "encryptionConfig": {
        "kmsKeyArn": "string"
    }
}
```
