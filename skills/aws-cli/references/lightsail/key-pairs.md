# Key Pairs

### 12.1 `create-key-pair`

Creates an SSH key pair.

**Synopsis:**
```bash
aws lightsail create-key-pair \
    --key-pair-name <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-pair-name` | **Yes** | string | -- | Name for the key pair |
| `--tags` | No | list | None | Tags |

**Output Schema:**
```json
{
    "keyPair": {
        "name": "string",
        "arn": "string",
        "supportCode": "string",
        "createdAt": "timestamp",
        "location": {
            "availabilityZone": "string",
            "regionName": "string"
        },
        "resourceType": "KeyPair",
        "tags": [],
        "fingerprint": "string"
    },
    "publicKeyBase64": "string",
    "privateKeyBase64": "string",
    "operation": {
        "id": "string",
        "resourceName": "string",
        "resourceType": "KeyPair",
        "operationType": "CreateKeyPair",
        "status": "NotStarted|Started|Failed|Completed|Succeeded",
        "isTerminal": true|false
    }
}
```

---

### 12.2 `delete-key-pair`

Deletes a key pair.

**Synopsis:**
```bash
aws lightsail delete-key-pair \
    --key-pair-name <value> \
    [--expected-fingerprint <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-pair-name` | **Yes** | string | -- | Name of the key pair to delete |
| `--expected-fingerprint` | No | string | None | Expected fingerprint for verification |

**Output Schema:**
```json
{
    "operation": {
        "id": "string",
        "resourceName": "string",
        "resourceType": "KeyPair",
        "operationType": "DeleteKeyPair",
        "status": "NotStarted|Started|Failed|Completed|Succeeded",
        "isTerminal": true|false
    }
}
```

---

### 12.3 `get-key-pair`

Returns information about a specific key pair.

**Synopsis:**
```bash
aws lightsail get-key-pair \
    --key-pair-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-pair-name` | **Yes** | string | -- | Name of the key pair |

**Output Schema:**
```json
{
    "keyPair": {
        "name": "string",
        "arn": "string",
        "supportCode": "string",
        "createdAt": "timestamp",
        "location": {
            "availabilityZone": "string",
            "regionName": "string"
        },
        "resourceType": "KeyPair",
        "tags": [],
        "fingerprint": "string"
    }
}
```

---

### 12.4 `get-key-pairs`

Returns information about all key pairs. **Paginated operation.**

**Synopsis:**
```bash
aws lightsail get-key-pairs \
    [--page-token <value>] \
    [--include-default-key-pair | --no-include-default-key-pair] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--page-token` | No | string | None | Pagination token |
| `--include-default-key-pair` | No | boolean | false | Include the default key pair |

**Output Schema:**
```json
{
    "keyPairs": [
        {
            "name": "string",
            "arn": "string",
            "fingerprint": "string",
            "createdAt": "timestamp"
        }
    ],
    "nextPageToken": "string"
}
```

---

### 12.5 `import-key-pair`

Imports a public key from a local machine.

**Synopsis:**
```bash
aws lightsail import-key-pair \
    --key-pair-name <value> \
    --public-key-base64 <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-pair-name` | **Yes** | string | -- | Name for the imported key pair |
| `--public-key-base64` | **Yes** | string | -- | Base64-encoded public key |

**Output Schema:**
```json
{
    "operation": {
        "id": "string",
        "resourceName": "string",
        "resourceType": "KeyPair",
        "operationType": "ImportKeyPair",
        "status": "NotStarted|Started|Failed|Completed|Succeeded",
        "isTerminal": true|false
    }
}
```

---

### 12.6 `download-default-key-pair`

Downloads the default SSH key pair.

**Synopsis:**
```bash
aws lightsail download-default-key-pair \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

No required parameters.

**Output Schema:**
```json
{
    "publicKeyBase64": "string",
    "privateKeyBase64": "string",
    "createdAt": "timestamp"
}
```

---

### 12.7 `delete-known-host-keys`

Deletes the known host key or certificate used by the Amazon Lightsail browser-based SSH or RDP clients to authenticate an instance.

**Synopsis:**
```bash
aws lightsail delete-known-host-keys \
    --instance-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--instance-name` | **Yes** | string | -- | Name of the instance |

**Output Schema:**
```json
{
    "operations": [
        {
            "id": "string",
            "resourceName": "string",
            "resourceType": "Instance",
            "operationType": "DeleteKnownHostKeys",
            "status": "NotStarted|Started|Failed|Completed|Succeeded",
            "isTerminal": true|false
        }
    ]
}
```
