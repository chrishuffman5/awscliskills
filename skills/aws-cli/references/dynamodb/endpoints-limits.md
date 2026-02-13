# Endpoints & Limits

### 16.1 `describe-endpoints`

Returns the regional endpoints for the DynamoDB service.

**Synopsis:**
```bash
aws dynamodb describe-endpoints \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output Schema:**
```json
{
    "Endpoints": [
        {
            "Address": "string",
            "CachePeriodInMinutes": "long"
        }
    ]
}
```

---

### 16.2 `describe-limits`

Returns the current provisioned-throughput quotas for the account.

**Synopsis:**
```bash
aws dynamodb describe-limits \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output Schema:**
```json
{
    "AccountMaxReadCapacityUnits": "long",
    "AccountMaxWriteCapacityUnits": "long",
    "TableMaxReadCapacityUnits": "long",
    "TableMaxWriteCapacityUnits": "long"
}
```

---
