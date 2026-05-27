# Agreements & Settings

### 2.1 `list-customer-agreements`

Lists all customer agreements. **Paginated operation.**

**Synopsis:**
```bash
aws artifact list-customer-agreements \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token from previous response |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "customerAgreements": [
        {
            "name": "string",
            "arn": "string",
            "id": "string",
            "agreementArn": "string",
            "awsAccountId": "string",
            "organizationArn": "string",
            "effectiveStart": "timestamp",
            "effectiveEnd": "timestamp",
            "state": "ACTIVE|CUSTOMER_TERMINATED|AWS_TERMINATED",
            "description": "string",
            "acceptanceTerms": ["string"],
            "terminateTerms": ["string"],
            "type": "CUSTOM|DEFAULT|MODIFIED"
        }
    ],
    "nextToken": "string"
}
```

---

### 2.2 `get-account-settings`

Retrieves account settings for AWS Artifact.

**Synopsis:**
```bash
aws artifact get-account-settings \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:** No required parameters.

**Output Schema:**
```json
{
    "accountSettings": {
        "notificationSubscriptionStatus": "SUBSCRIBED|NOT_SUBSCRIBED"
    }
}
```

---

### 2.3 `put-account-settings`

Updates account settings for AWS Artifact.

**Synopsis:**
```bash
aws artifact put-account-settings \
    [--notification-subscription-status <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--notification-subscription-status` | No | string | None | Notification subscription status: `SUBSCRIBED`, `NOT_SUBSCRIBED` |

**Output Schema:**
```json
{
    "accountSettings": {
        "notificationSubscriptionStatus": "SUBSCRIBED|NOT_SUBSCRIBED"
    }
}
```
