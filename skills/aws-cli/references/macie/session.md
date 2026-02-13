# Session

### 1.1 `enable-macie`

Enables Amazon Macie and specifies configuration settings for a Macie account.

**Synopsis:**
```bash
aws macie2 enable-macie \
    [--client-token <value>] \
    [--finding-publishing-frequency <value>] \
    [--status <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--client-token` | No | string | None | Idempotency token |
| `--finding-publishing-frequency` | No | string | `SIX_HOURS` | Publishing frequency: `FIFTEEN_MINUTES`, `ONE_HOUR`, `SIX_HOURS` |
| `--status` | No | string | `ENABLED` | Status: `ENABLED` or `PAUSED` |

**Output:** None (HTTP 200 on success)

---

### 1.2 `disable-macie`

Disables Amazon Macie and deletes Macie resources for the account.

**Synopsis:**
```bash
aws macie2 disable-macie \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output:** None (HTTP 200 on success)

---

### 1.3 `get-macie-session`

Retrieves information about the current status and configuration settings for an Amazon Macie account.

**Synopsis:**
```bash
aws macie2 get-macie-session \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** None required.

**Output Schema:**
```json
{
    "CreatedAt": "timestamp",
    "FindingPublishingFrequency": "FIFTEEN_MINUTES|ONE_HOUR|SIX_HOURS",
    "ServiceRole": "string",
    "Status": "ENABLED|PAUSED",
    "UpdatedAt": "timestamp"
}
```

---

### 1.4 `update-macie-session`

Updates the status and configuration settings for an Amazon Macie account.

**Synopsis:**
```bash
aws macie2 update-macie-session \
    [--finding-publishing-frequency <value>] \
    [--status <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--finding-publishing-frequency` | No | string | None | Publishing frequency: `FIFTEEN_MINUTES`, `ONE_HOUR`, `SIX_HOURS` |
| `--status` | No | string | None | Status: `ENABLED` or `PAUSED` |

**Output:** None (HTTP 200 on success)
