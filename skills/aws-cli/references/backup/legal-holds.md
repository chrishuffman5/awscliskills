# Legal Holds

### 11.1 `create-legal-hold`

Creates a legal hold to prevent recovery points from being deleted. Recovery points under a legal hold cannot be deleted even if their retention period expires.

**Synopsis:**
```bash
aws backup create-legal-hold \
    --title <value> \
    --description <value> \
    [--idempotency-token <value>] \
    [--recovery-point-selection <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--title` | **Yes** | string | -- | Legal hold title |
| `--description` | **Yes** | string | -- | Legal hold description |
| `--idempotency-token` | No | string | None | Idempotency token |
| `--recovery-point-selection` | No | structure | None | Criteria for selecting recovery points |
| `--tags` | No | map | None | Tags |

**Recovery Point Selection Structure:**
```json
{
    "VaultNames": ["string"],
    "ResourceIdentifiers": ["string"],
    "DateRange": {
        "FromDate": "timestamp",
        "ToDate": "timestamp"
    }
}
```

**Output Schema:**
```json
{
    "Title": "string",
    "Status": "CREATING|ACTIVE|CANCELING|CANCELED",
    "Description": "string",
    "LegalHoldId": "string",
    "LegalHoldArn": "string",
    "CreationDate": "timestamp",
    "RecoveryPointSelection": {}
}
```

---

### 11.2 `cancel-legal-hold`

Cancels a legal hold, allowing affected recovery points to expire normally.

**Synopsis:**
```bash
aws backup cancel-legal-hold \
    --legal-hold-id <value> \
    --cancel-description <value> \
    [--retain-record-in-days <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--legal-hold-id` | **Yes** | string | -- | Legal hold ID |
| `--cancel-description` | **Yes** | string | -- | Reason for cancellation |
| `--retain-record-in-days` | No | long | None | Days to retain the hold record |

**Output:** None

---

### 11.3 `get-legal-hold`

Returns details of a legal hold.

**Synopsis:**
```bash
aws backup get-legal-hold \
    --legal-hold-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--legal-hold-id` | **Yes** | string | -- | Legal hold ID |

**Output Schema:**
```json
{
    "Title": "string",
    "Status": "CREATING|ACTIVE|CANCELING|CANCELED",
    "Description": "string",
    "CancelDescription": "string",
    "LegalHoldId": "string",
    "LegalHoldArn": "string",
    "CreationDate": "timestamp",
    "CancellationDate": "timestamp",
    "RetainRecordUntil": "timestamp",
    "RecoveryPointSelection": {}
}
```

---

### 11.4 `list-legal-holds`

Lists all legal holds. **Paginated operation.**

**Synopsis:**
```bash
aws backup list-legal-holds \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Output Schema:**
```json
{
    "NextToken": "string",
    "LegalHolds": [
        {
            "Title": "string",
            "Status": "CREATING|ACTIVE|CANCELING|CANCELED",
            "Description": "string",
            "LegalHoldId": "string",
            "LegalHoldArn": "string",
            "CreationDate": "timestamp",
            "CancellationDate": "timestamp"
        }
    ]
}
```
