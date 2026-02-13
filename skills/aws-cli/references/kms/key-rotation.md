# Key Rotation

### 5.1 `enable-key-rotation`

Enables automatic annual rotation of the key material for a symmetric encryption KMS key.

**Synopsis:**
```bash
aws kms enable-key-rotation \
    --key-id <value> \
    [--rotation-period-in-days <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-id` | **Yes** | string | -- | Key ID or key ARN (1-2048 chars). Must be symmetric encryption key with AWS_KMS origin |
| `--rotation-period-in-days` | No | integer | `365` | Rotation period (90-2560 days) |

**Output:** None

---

### 5.2 `disable-key-rotation`

Disables automatic rotation of the key material.

**Synopsis:**
```bash
aws kms disable-key-rotation --key-id <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-id` | **Yes** | string | -- | Key ID or key ARN (1-2048 chars) |

**Output:** None

---

### 5.3 `get-key-rotation-status`

Returns whether automatic key rotation is enabled and the rotation period.

**Synopsis:**
```bash
aws kms get-key-rotation-status --key-id <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-id` | **Yes** | string | -- | Key ID or key ARN (1-2048 chars) |

**Output Schema:**
```json
{
    "KeyRotationEnabled": true|false,
    "KeyId": "string",
    "RotationPeriodInDays": "integer",
    "NextRotationDate": "timestamp",
    "OnDemandRotationStartDate": "timestamp"
}
```

---

### 5.4 `rotate-key-on-demand`

Immediately initiates rotation of key material for a symmetric encryption KMS key.

**Synopsis:**
```bash
aws kms rotate-key-on-demand --key-id <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-id` | **Yes** | string | -- | Key ID or key ARN (1-2048 chars) |

**Output Schema:**
```json
{
    "KeyId": "string"
}
```

---

### 5.5 `list-key-rotations`

Lists all completed key material rotations for a KMS key. **Paginated.**

**Synopsis:**
```bash
aws kms list-key-rotations \
    --key-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-id` | **Yes** | string | -- | Key ID or key ARN (1-2048 chars) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Rotations": [
        {
            "KeyId": "string",
            "RotationDate": "timestamp",
            "RotationType": "AUTOMATIC|ON_DEMAND",
            "KeyMaterialId": "string"
        }
    ],
    "NextMarker": "string",
    "Truncated": true|false
}
```

---
