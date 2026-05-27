# Replication

### 5.1 `replicate-secret-to-regions`

Replicates a secret to one or more additional AWS regions.

**Synopsis:**
```bash
aws secretsmanager replicate-secret-to-regions \
    --secret-id <value> \
    --add-replica-regions <value> \
    [--force-overwrite-replica-secret | --no-force-overwrite-replica-secret] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--secret-id` | **Yes** | string | -- | ARN or name of the secret (1-2048 chars) |
| `--add-replica-regions` | **Yes** | list | -- | Regions and optional KMS keys. Shorthand: `Region=string,KmsKeyId=string` |
| `--force-overwrite-replica-secret` | No | boolean | false | Overwrite existing secret with same name in destination region |

**Replica Region Structure:**
```json
[
    {
        "Region": "string",
        "KmsKeyId": "string"
    }
]
```

**Output Schema:**
```json
{
    "ARN": "string",
    "ReplicationStatus": [
        {
            "Region": "string",
            "KmsKeyId": "string",
            "Status": "InSync|Failed|InProgress",
            "StatusMessage": "string",
            "LastAccessedDate": "timestamp"
        }
    ]
}
```

---

### 5.2 `remove-regions-from-replication`

Removes replica secrets from specified regions. Must remove replicas before deleting a primary secret.

**Synopsis:**
```bash
aws secretsmanager remove-regions-from-replication \
    --secret-id <value> \
    --remove-replica-regions <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--secret-id` | **Yes** | string | -- | ARN or name of the secret (1-2048 chars) |
| `--remove-replica-regions` | **Yes** | list(string) | -- | Region codes to remove, e.g. `eu-west-1 us-west-2` |

**Output Schema:**
```json
{
    "ARN": "string",
    "ReplicationStatus": [
        {
            "Region": "string",
            "KmsKeyId": "string",
            "Status": "InSync|Failed|InProgress",
            "StatusMessage": "string",
            "LastAccessedDate": "timestamp"
        }
    ]
}
```

---

### 5.3 `stop-replication-to-replica`

Promotes a replica secret to a standalone primary secret in the replica region. Must be called from the replica region.

**Synopsis:**
```bash
aws secretsmanager stop-replication-to-replica \
    --secret-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--secret-id` | **Yes** | string | -- | Name or replica ARN of the secret (1-2048 chars). Must be called from the replica region |

**Output Schema:**
```json
{
    "ARN": "string"
}
```

---
