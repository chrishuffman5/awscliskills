# Entitlements

### 4.1 `grant-flow-entitlements`

Grants entitlements on a flow, allowing other AWS accounts to subscribe to the flow's content.

**Synopsis:**
```bash
aws mediaconnect grant-flow-entitlements \
    --flow-arn <value> \
    --entitlements <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--flow-arn` | **Yes** | string | -- | ARN of the flow |
| `--entitlements` | **Yes** | list | -- | Entitlements to grant |

**Entitlement Structure:**

| Field | Required | Type | Description |
|-------|----------|------|-------------|
| `Name` | **Yes** | string | Entitlement name (unique within flow) |
| `Subscribers` | **Yes** | list | AWS account IDs to share with |
| `Description` | No | string | Entitlement description |
| `DataTransferSubscriberFeePercent` | No | integer | Fee percentage billed to subscriber (0-100) |
| `EntitlementStatus` | No | string | `ENABLED` or `DISABLED` |
| `Encryption` | No | structure | Encryption config |

**Encryption Structure:**

| Field | Required | Type | Description |
|-------|----------|------|-------------|
| `RoleArn` | **Yes** | string | IAM role ARN for encryption |
| `Algorithm` | No | string | `aes128`, `aes192`, `aes256` |
| `KeyType` | No | string | `speke`, `static-key`, `srt-password` |
| `SecretArn` | No | string | Secrets Manager ARN (for static-key) |

**Output Schema:**
```json
{
    "FlowArn": "string",
    "Entitlements": [
        {
            "EntitlementArn": "string",
            "Name": "string",
            "Description": "string",
            "Subscribers": ["string"],
            "DataTransferSubscriberFeePercent": "integer",
            "EntitlementStatus": "ENABLED|DISABLED",
            "Encryption": {}
        }
    ]
}
```

---

### 4.2 `update-flow-entitlement`

Updates an entitlement on a flow.

**Synopsis:**
```bash
aws mediaconnect update-flow-entitlement \
    --flow-arn <value> \
    --entitlement-arn <value> \
    [--description <value>] \
    [--encryption <value>] \
    [--entitlement-status <value>] \
    [--subscribers <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--flow-arn` | **Yes** | string | -- | ARN of the flow |
| `--entitlement-arn` | **Yes** | string | -- | ARN of the entitlement to update |
| `--description` | No | string | None | Updated description |
| `--encryption` | No | structure | None | Updated encryption config |
| `--entitlement-status` | No | string | None | `ENABLED` or `DISABLED` |
| `--subscribers` | No | list | None | Updated subscriber account IDs |

**Output Schema:**
```json
{
    "FlowArn": "string",
    "Entitlement": { "..." }
}
```

---

### 4.3 `revoke-flow-entitlement`

Revokes an entitlement from a flow.

**Synopsis:**
```bash
aws mediaconnect revoke-flow-entitlement \
    --flow-arn <value> \
    --entitlement-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--flow-arn` | **Yes** | string | -- | ARN of the flow |
| `--entitlement-arn` | **Yes** | string | -- | ARN of the entitlement to revoke |

**Output Schema:**
```json
{
    "FlowArn": "string",
    "EntitlementArn": "string"
}
```

---

### 4.4 `list-entitlements`

Lists all entitlements granted to the account. **Paginated operation.**

**Synopsis:**
```bash
aws mediaconnect list-entitlements \
    [--max-results <value>] \
    [--next-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--max-results` | No | integer | None | Max results per page |
| `--next-token` | No | string | None | Pagination token |

**Output Schema:**
```json
{
    "Entitlements": [
        {
            "EntitlementArn": "string",
            "EntitlementName": "string",
            "DataTransferSubscriberFeePercent": "integer"
        }
    ],
    "NextToken": "string"
}
```
