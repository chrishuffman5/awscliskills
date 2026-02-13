# Suppression

### 6.1 `put-suppressed-destination`

Adds an email address to the account-level suppression list. Emails to suppressed addresses are automatically dropped.

**Synopsis:**
```bash
aws sesv2 put-suppressed-destination \
    --email-address <value> \
    --reason <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--email-address` | **Yes** | string | -- | Email address to suppress |
| `--reason` | **Yes** | string | -- | Reason for suppression: `BOUNCE` or `COMPLAINT` |

**Output Schema:**
```json
{}
```

---

### 6.2 `get-suppressed-destination`

Retrieves information about a specific suppressed email address.

**Synopsis:**
```bash
aws sesv2 get-suppressed-destination \
    --email-address <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--email-address` | **Yes** | string | -- | Suppressed email address to look up |

**Output Schema:**
```json
{
    "SuppressedDestination": {
        "EmailAddress": "string",
        "Reason": "BOUNCE|COMPLAINT",
        "LastUpdateTime": "timestamp",
        "Attributes": {
            "MessageId": "string",
            "FeedbackId": "string"
        }
    }
}
```

---

### 6.3 `delete-suppressed-destination`

Removes an email address from the account-level suppression list.

**Synopsis:**
```bash
aws sesv2 delete-suppressed-destination \
    --email-address <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--email-address` | **Yes** | string | -- | Email address to remove from suppression list |

**Output Schema:**
```json
{}
```

---

### 6.4 `list-suppressed-destinations`

Lists email addresses on the account-level suppression list. Supports filtering by reason and date range. **Paginated operation.**

**Synopsis:**
```bash
aws sesv2 list-suppressed-destinations \
    [--reasons <value>] \
    [--start-date <value>] \
    [--end-date <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--reasons` | No | list(string) | None | Filter by reason: `BOUNCE`, `COMPLAINT` |
| `--start-date` | No | timestamp | None | Filter by start date (ISO 8601) |
| `--end-date` | No | timestamp | None | Filter by end date (ISO 8601) |
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "SuppressedDestinationSummaries": [
        {
            "EmailAddress": "string",
            "Reason": "BOUNCE|COMPLAINT",
            "LastUpdateTime": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 6.5 `put-account-suppression-attributes`

Configures which suppression reasons are enabled at the account level.

**Synopsis:**
```bash
aws sesv2 put-account-suppression-attributes \
    [--suppressed-reasons <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--suppressed-reasons` | No | list(string) | None | Reasons to enable: `BOUNCE`, `COMPLAINT`. Pass empty list to disable all |

**Output Schema:**
```json
{}
```
