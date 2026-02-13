# Account

### 4.1 `get-account-configuration`

Returns the account-level configuration for ACM, including the expiry events configuration that controls whether ACM sends certificate expiration notifications via EventBridge.

**Synopsis:**
```bash
aws acm get-account-configuration \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output Schema:**
```json
{
    "ExpiryEvents": {
        "DaysBeforeExpiry": "integer"
    }
}
```

- **DaysBeforeExpiry**: Number of days before certificate expiry to trigger an EventBridge event (1-45, default 45).

---

### 4.2 `put-account-configuration`

Sets the account-level configuration for ACM. Configures certificate expiry event notifications.

**Synopsis:**
```bash
aws acm put-account-configuration \
    --idempotency-token <value> \
    [--expiry-events <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--idempotency-token` | **Yes** | string | -- | Token for idempotent requests |
| `--expiry-events` | No | structure | None | Expiry event configuration. Shorthand: `DaysBeforeExpiry=integer` |

**Expiry Events Structure:**
```json
{
    "DaysBeforeExpiry": "integer"
}
```

- **DaysBeforeExpiry**: Number of days before expiry to send notification (1-45).

**Output:** None (HTTP 200 on success)
