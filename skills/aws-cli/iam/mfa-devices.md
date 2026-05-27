# MFA Devices

### 10.1 `create-virtual-mfa-device`

Creates a virtual MFA device.

**Synopsis:**
```bash
aws iam create-virtual-mfa-device \
    --virtual-mfa-device-name <value> \
    --outfile <value> \
    --bootstrap-method <value> \
    [--path <value>] \
    [--tags <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--virtual-mfa-device-name` | **Yes** | string | -- | Device name (1-226 chars) |
| `--outfile` | **Yes** | string | -- | Path to save the bootstrap data (QR code PNG or base32 seed) |
| `--bootstrap-method` | **Yes** | string | -- | `QRCodePNG` or `Base32StringSeed` |
| `--path` | No | string | `/` | Path prefix |
| `--tags` | No | list | None | Tags (max 50) |

**Output Schema:**
```json
{
    "VirtualMFADevice": {
        "SerialNumber": "string",
        "Base32StringSeed": "blob",
        "QRCodePNG": "blob",
        "User": { "UserName": "string", "Arn": "string" },
        "EnableDate": "timestamp",
        "Tags": [{ "Key": "string", "Value": "string" }]
    }
}
```

---

### 10.2 `enable-mfa-device`

Enables an MFA device for a user. Requires two consecutive authentication codes.

**Synopsis:**
```bash
aws iam enable-mfa-device \
    --user-name <value> \
    --serial-number <value> \
    --authentication-code1 <value> \
    --authentication-code2 <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--user-name` | **Yes** | string | -- | User name |
| `--serial-number` | **Yes** | string | -- | Serial number (ARN for virtual, serial for hardware) |
| `--authentication-code1` | **Yes** | string | -- | First MFA code (6 digits) |
| `--authentication-code2` | **Yes** | string | -- | Second consecutive MFA code (6 digits) |

**Output:** None on success.

---

### 10.3 `deactivate-mfa-device`

Deactivates an MFA device and removes its association with a user.

**Synopsis:**
```bash
aws iam deactivate-mfa-device --user-name <value> --serial-number <value>
```

**Output:** None on success.

---

### 10.4 `delete-virtual-mfa-device`

Deletes a virtual MFA device. Must be deactivated first.

**Synopsis:**
```bash
aws iam delete-virtual-mfa-device --serial-number <value>
```

**Output:** None on success.

---

### 10.5 `list-mfa-devices`

Lists MFA devices for a user. **Paginated.**

**Synopsis:**
```bash
aws iam list-mfa-devices [--user-name <value>] [--starting-token <value>] [--max-items <value>]
```

**Output Schema:**
```json
{
    "MFADevices": [
        {
            "UserName": "string",
            "SerialNumber": "string",
            "EnableDate": "timestamp"
        }
    ],
    "IsTruncated": true|false,
    "Marker": "string"
}
```

---

### 10.6 `list-virtual-mfa-devices`

Lists all virtual MFA devices in the account. **Paginated.**

**Synopsis:**
```bash
aws iam list-virtual-mfa-devices \
    [--assignment-status <value>] \
    [--starting-token <value>] \
    [--max-items <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--assignment-status` | No | string | `Any` | `Assigned`, `Unassigned`, or `Any` |

**Output Schema:**
```json
{
    "VirtualMFADevices": [
        {
            "SerialNumber": "string",
            "User": { "UserName": "string", "Arn": "string" },
            "EnableDate": "timestamp"
        }
    ],
    "IsTruncated": true|false,
    "Marker": "string"
}
```

---

### 10.7 `resync-mfa-device`

Resynchronizes an MFA device with its IAM resource object.

**Synopsis:**
```bash
aws iam resync-mfa-device \
    --user-name <value> \
    --serial-number <value> \
    --authentication-code1 <value> \
    --authentication-code2 <value>
```

**Output:** None on success.

---

### 10.8 `get-mfa-device`

Gets information about an MFA device.

**Synopsis:**
```bash
aws iam get-mfa-device --serial-number <value> [--user-name <value>]
```

**Output Schema:**
```json
{
    "UserName": "string",
    "SerialNumber": "string",
    "EnableDate": "timestamp",
    "Certifications": { "string": "string" }
}
```

---
