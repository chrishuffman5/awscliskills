# Key Replication

### 4.1 `add-key-replication-regions`

Adds replication regions to an existing key.

**Synopsis:**
```bash
aws payment-cryptography add-key-replication-regions \
    --key-identifier <value> \
    --replication-regions <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-identifier` | **Yes** | string | -- | KeyARN or alias of the key |
| `--replication-regions` | **Yes** | list(string) | -- | AWS Regions to add (e.g., `us-east-1 eu-west-1`) |

**Output Schema:**
```json
{
    "Key": {
        "KeyArn": "string",
        "KeyAttributes": {},
        "KeyCheckValue": "string",
        "KeyCheckValueAlgorithm": "string",
        "Enabled": "boolean",
        "Exportable": "boolean",
        "KeyState": "string",
        "KeyOrigin": "string",
        "CreateTimestamp": "timestamp",
        "MultiRegionKeyType": "PRIMARY|REPLICA",
        "PrimaryRegion": "string",
        "ReplicationStatus": {
            "region": {
                "Status": "IN_PROGRESS|SYNCHRONIZED|FAILED|DELETE_IN_PROGRESS",
                "StatusMessage": "string"
            }
        },
        "UsingDefaultReplicationRegions": "boolean"
    }
}
```

---

### 4.2 `remove-key-replication-regions`

Removes replication regions from a key.

**Synopsis:**
```bash
aws payment-cryptography remove-key-replication-regions \
    --key-identifier <value> \
    --replication-regions <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-identifier` | **Yes** | string | -- | KeyARN or alias of the key |
| `--replication-regions` | **Yes** | list(string) | -- | AWS Regions to remove |

**Output Schema:**
```json
{
    "Key": {
        "KeyArn": "string",
        "KeyAttributes": {},
        "KeyCheckValue": "string",
        "Enabled": "boolean",
        "Exportable": "boolean",
        "KeyState": "string",
        "KeyOrigin": "string",
        "CreateTimestamp": "timestamp",
        "MultiRegionKeyType": "string",
        "PrimaryRegion": "string",
        "ReplicationStatus": {},
        "UsingDefaultReplicationRegions": "boolean"
    }
}
```

---

### 4.3 `get-default-key-replication-regions`

Returns the list of AWS Regions where default key replication is enabled for the account.

**Synopsis:**
```bash
aws payment-cryptography get-default-key-replication-regions \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| (no command-specific parameters) | -- | -- | -- | -- |

**Output Schema:**
```json
{
    "EnabledReplicationRegions": ["string"]
}
```

---

### 4.4 `enable-default-key-replication-regions`

Enables default key replication regions for the account. New keys will automatically replicate to these regions.

**Synopsis:**
```bash
aws payment-cryptography enable-default-key-replication-regions \
    --replication-regions <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replication-regions` | **Yes** | list(string) | -- | AWS Regions to enable as defaults (e.g., `us-east-1 eu-west-1`) |

**Output Schema:**
```json
{
    "EnabledReplicationRegions": ["string"]
}
```

---

### 4.5 `disable-default-key-replication-regions`

Disables default key replication regions for the account. New keys will no longer auto-replicate to these regions.

**Synopsis:**
```bash
aws payment-cryptography disable-default-key-replication-regions \
    --replication-regions <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--replication-regions` | **Yes** | list(string) | -- | AWS Regions to disable |

**Output Schema:**
```json
{
    "EnabledReplicationRegions": ["string"]
}
```
