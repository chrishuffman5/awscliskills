# Field-Level Encryption

### 15.1 `create-field-level-encryption-config`

Creates a field-level encryption configuration.

**Synopsis:**
```bash
aws cloudfront create-field-level-encryption-config \
    --field-level-encryption-config <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--field-level-encryption-config` | **Yes** | structure | Field-level encryption configuration |

**Config structure:**

| Field | Required | Type | Description |
|-------|----------|------|-------------|
| `CallerReference` | **Yes** | string | Unique value to prevent replay |
| `ContentTypeProfileConfig` | **Yes** | structure | Content type profiles for encryption |
| `QueryArgProfileConfig` | **Yes** | structure | Query argument profiles for encryption |
| `Comment` | No | string | Description |

**Output Schema:**
```json
{
    "FieldLevelEncryption": {
        "Id": "string",
        "LastModifiedTime": "timestamp",
        "FieldLevelEncryptionConfig": { "..." }
    },
    "Location": "string",
    "ETag": "string"
}
```

---

### 15.2 `create-field-level-encryption-profile`

Creates a field-level encryption profile.

**Synopsis:**
```bash
aws cloudfront create-field-level-encryption-profile \
    --field-level-encryption-profile-config <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--field-level-encryption-profile-config` | **Yes** | structure | Profile configuration |

**Config structure:**

| Field | Required | Type | Description |
|-------|----------|------|-------------|
| `Name` | **Yes** | string | Profile name |
| `CallerReference` | **Yes** | string | Unique value to prevent replay |
| `EncryptionEntities` | **Yes** | structure | Encryption entities (fields to encrypt + public key mappings) |
| `Comment` | No | string | Description |

**Output Schema:**
```json
{
    "FieldLevelEncryptionProfile": {
        "Id": "string",
        "LastModifiedTime": "timestamp",
        "FieldLevelEncryptionProfileConfig": { "..." }
    },
    "Location": "string",
    "ETag": "string"
}
```

---

### 15.3 `get-field-level-encryption` / `get-field-level-encryption-config`

Gets a field-level encryption configuration (or just the config portion).

**Synopsis:**
```bash
aws cloudfront get-field-level-encryption --id <value>
aws cloudfront get-field-level-encryption-config --id <value>
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--id` | **Yes** | string | Field-level encryption config ID |

---

### 15.4 `get-field-level-encryption-profile` / `get-field-level-encryption-profile-config`

Gets a field-level encryption profile (or just the config portion).

**Synopsis:**
```bash
aws cloudfront get-field-level-encryption-profile --id <value>
aws cloudfront get-field-level-encryption-profile-config --id <value>
```

**Parameters:**

| Parameter | Required | Type | Description |
|-----------|----------|------|-------------|
| `--id` | **Yes** | string | Profile ID |

---

### 15.5 `list-field-level-encryption-configs` / `list-field-level-encryption-profiles`

Lists field-level encryption configurations or profiles.

**Synopsis:**
```bash
aws cloudfront list-field-level-encryption-configs [--marker <value>] [--max-items <value>]
aws cloudfront list-field-level-encryption-profiles [--marker <value>] [--max-items <value>]
```

---

### 15.6 `update-field-level-encryption-config` / `update-field-level-encryption-profile`

Updates field-level encryption configuration or profile.

**Synopsis:**
```bash
aws cloudfront update-field-level-encryption-config --id <value> --field-level-encryption-config <value> --if-match <value>
aws cloudfront update-field-level-encryption-profile --id <value> --field-level-encryption-profile-config <value> --if-match <value>
```

---

### 15.7 `delete-field-level-encryption-config` / `delete-field-level-encryption-profile`

Deletes field-level encryption configuration or profile.

**Synopsis:**
```bash
aws cloudfront delete-field-level-encryption-config --id <value> --if-match <value>
aws cloudfront delete-field-level-encryption-profile --id <value> --if-match <value>
```

---
