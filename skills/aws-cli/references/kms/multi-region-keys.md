# Multi-Region Keys

### 6.1 `replicate-key`

Creates a replica of a multi-region primary key in a different AWS Region.

**Synopsis:**
```bash
aws kms replicate-key \
    --key-id <value> \
    --replica-region <value> \
    [--policy <value>] \
    [--bypass-policy-lockout-safety-check | --no-bypass-policy-lockout-safety-check] \
    [--description <value>] \
    [--tags <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-id` | **Yes** | string | -- | Multi-region primary key ID or key ARN (1-2048 chars) |
| `--replica-region` | **Yes** | string | -- | Target region (1-32 chars), e.g. `us-west-2` |
| `--policy` | No | string | Default key policy | Key policy for replica (1-131072 chars) |
| `--bypass-policy-lockout-safety-check` | No | boolean | `false` | Skip lockout safety check |
| `--description` | No | string | `""` | Replica key description (0-8192 chars) |
| `--tags` | No | list | None | Tags for the replica. Shorthand: `TagKey=string,TagValue=string ...` |

**Output Schema:**
```json
{
    "ReplicaKeyMetadata": {
        "AWSAccountId": "string",
        "KeyId": "string",
        "Arn": "string",
        "CreationDate": "timestamp",
        "Enabled": true|false,
        "Description": "string",
        "KeyUsage": "string",
        "KeyState": "string",
        "Origin": "string",
        "KeySpec": "string",
        "MultiRegion": true,
        "MultiRegionConfiguration": {
            "MultiRegionKeyType": "REPLICA",
            "PrimaryKey": { "Arn": "string", "Region": "string" },
            "ReplicaKeys": [{ "Arn": "string", "Region": "string" }]
        }
    },
    "ReplicaPolicy": "string",
    "ReplicaTags": [{ "TagKey": "string", "TagValue": "string" }]
}
```

---

### 6.2 `update-primary-region`

Changes the primary key of a multi-region key to a different region. The former primary becomes a replica.

**Synopsis:**
```bash
aws kms update-primary-region \
    --key-id <value> \
    --primary-region <value>
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--key-id` | **Yes** | string | -- | Current primary key ID or key ARN (1-2048 chars) |
| `--primary-region` | **Yes** | string | -- | Region of the replica to promote (1-32 chars) |

**Output:** None

---
