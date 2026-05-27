# Keys

### 6.1 `create-key`

Creates an API key for frontend authentication with Location Service resources.

**Synopsis:**
```bash
aws location create-key \
    --key-name <value> \
    --restrictions <value> \
    [--description <value>] \
    [--expire-time <value>] \
    [--no-expiry | --no-no-expiry] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-name` | **Yes** | string | -- | API key name (1-100 chars) |
| `--restrictions` | **Yes** | structure | -- | Key restrictions (actions, resources, referers) |
| `--description` | No | string | None | Description (0-1000 chars) |
| `--expire-time` | No | timestamp | None | Expiration time (ISO 8601) |
| `--no-expiry` | No | boolean | None | No expiration (one of `expire-time` or `no-expiry` required) |
| `--tags` | No | map | None | Resource tags (max 50) |

**Restrictions Structure:**
```json
{
    "AllowActions": ["geo:GetMap*", "geo-places:*", "geo-routes:*"],
    "AllowResources": ["arn:aws:geo:..."],
    "AllowReferers": ["https://example.com/*"],
    "AllowAndroidApps": [{ "Package": "string", "CertificateFingerprint": "string" }],
    "AllowAppleApps": [{ "BundleId": "string" }]
}
```

**Output Schema:**
```json
{ "Key": "string", "KeyArn": "string", "KeyName": "string", "CreateTime": "timestamp" }
```

---

### 6.2 `delete-key`

**Synopsis:** `aws location delete-key --key-name <value> [--force-delete | --no-force-delete]`

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-name` | **Yes** | string | -- | Key to delete |
| `--force-delete` | No | boolean | false | Skip confirmation |

**Output:** None.

---

### 6.3 `describe-key`

**Synopsis:** `aws location describe-key --key-name <value>`

**Output Schema:**
```json
{
    "Key": "string", "KeyArn": "string", "KeyName": "string", "Description": "string",
    "Restrictions": { "AllowActions": [], "AllowResources": [], "AllowReferers": [] },
    "ExpireTime": "timestamp", "Tags": {},
    "CreateTime": "timestamp", "UpdateTime": "timestamp"
}
```

---

### 6.4 `list-keys`

**Paginated.** Synopsis: `aws location list-keys [--filter <value>] [--starting-token <value>] [--page-size <value>] [--max-items <value>]`

**Output Schema:**
```json
{ "Entries": [{ "KeyName": "string", "Description": "string", "Restrictions": {}, "ExpireTime": "timestamp", "CreateTime": "timestamp", "UpdateTime": "timestamp" }], "NextToken": "string" }
```

---

### 6.5 `update-key`

**Synopsis:**
```bash
aws location update-key \
    --key-name <value> \
    [--description <value>] \
    [--expire-time <value>] \
    [--no-expiry | --no-no-expiry] \
    [--restrictions <value>] \
    [--force-update | --no-force-update]
```

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-name` | **Yes** | string | -- | Key to update |
| `--description` | No | string | None | New description |
| `--expire-time` | No | timestamp | None | New expiration |
| `--no-expiry` | No | boolean | None | Remove expiration |
| `--restrictions` | No | structure | None | Updated restrictions |
| `--force-update` | No | boolean | false | Skip confirmation |

**Output Schema:**
```json
{ "KeyArn": "string", "KeyName": "string", "UpdateTime": "timestamp" }
```
