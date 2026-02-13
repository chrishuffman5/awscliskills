# CHAP & Tags

### 9.1 `update-chap-credentials`

Updates the CHAP (Challenge-Handshake Authentication Protocol) credentials for an iSCSI target. When updated, all existing connections on the target are closed and initiators must reconnect.

**Synopsis:**
```bash
aws storagegateway update-chap-credentials \
    --target-arn <value> \
    --secret-to-authenticate-initiator <value> \
    --initiator-name <value> \
    [--secret-to-authenticate-target <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--target-arn` | **Yes** | string | -- | iSCSI volume target ARN (50-800 chars) |
| `--secret-to-authenticate-initiator` | **Yes** | string | -- | Secret for initiator authentication (12-16 bytes UTF-8, 1-100 chars) |
| `--initiator-name` | **Yes** | string | -- | iSCSI initiator name (1-255 chars, pattern: `[0-9a-z:.-]+`) |
| `--secret-to-authenticate-target` | No | string | None | Secret for mutual CHAP (12-16 bytes UTF-8) |

**Output Schema:**
```json
{
    "TargetARN": "string",
    "InitiatorName": "string"
}
```

---

### 9.2 `describe-chap-credentials`

Returns CHAP credentials for a specified iSCSI target.

**Synopsis:**
```bash
aws storagegateway describe-chap-credentials \
    --target-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--target-arn` | **Yes** | string | -- | iSCSI volume target ARN (50-800 chars) |

**Output Schema:**
```json
{
    "ChapCredentials": [
        {
            "TargetARN": "string",
            "SecretToAuthenticateInitiator": "string",
            "InitiatorName": "string",
            "SecretToAuthenticateTarget": "string"
        }
    ]
}
```

---

### 9.3 `delete-chap-credentials`

Deletes CHAP credentials for a specified iSCSI target and initiator pair.

**Synopsis:**
```bash
aws storagegateway delete-chap-credentials \
    --target-arn <value> \
    --initiator-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--target-arn` | **Yes** | string | -- | iSCSI volume target ARN |
| `--initiator-name` | **Yes** | string | -- | iSCSI initiator name |

**Output Schema:**
```json
{
    "TargetARN": "string",
    "InitiatorName": "string"
}
```

---

### 9.4 `add-tags-to-resource`

Adds tags to a Storage Gateway resource. Up to 50 tags per resource. Supported for gateways, volumes, tapes, and file shares.

**Synopsis:**
```bash
aws storagegateway add-tags-to-resource \
    --resource-arn <value> \
    --tags <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN (50-500 chars) |
| `--tags` | **Yes** | list | -- | Tags to add. Shorthand: `Key=string,Value=string ...` |

**Output Schema:**
```json
{
    "ResourceARN": "string"
}
```

---

### 9.5 `remove-tags-from-resource`

Removes tags from a Storage Gateway resource.

**Synopsis:**
```bash
aws storagegateway remove-tags-from-resource \
    --resource-arn <value> \
    --tag-keys <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |
| `--tag-keys` | **Yes** | list(string) | -- | Tag keys to remove |

**Output Schema:**
```json
{
    "ResourceARN": "string"
}
```

---

### 9.6 `list-tags-for-resource`

Lists tags for a Storage Gateway resource. **Paginated operation.**

**Synopsis:**
```bash
aws storagegateway list-tags-for-resource \
    --resource-arn <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | Resource ARN |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "ResourceARN": "string",
    "Marker": "string",
    "Tags": [
        {
            "Key": "string",
            "Value": "string"
        }
    ]
}
```
