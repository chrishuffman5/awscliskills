# Delegated Admin

### 6.1 `register-delegated-administrator`

Enables a member account to be a delegated administrator for an AWS service that supports Organizations integration.

**Synopsis:**
```bash
aws organizations register-delegated-administrator \
    --account-id <value> \
    --service-principal <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | 12-digit account ID of the member account |
| `--service-principal` | **Yes** | string | -- | Service principal (e.g., `config.amazonaws.com`, `guardduty.amazonaws.com`) |

**Output Schema:**
```json
{}
```

---

### 6.2 `deregister-delegated-administrator`

Removes the specified member account as a delegated administrator for the specified AWS service.

**Synopsis:**
```bash
aws organizations deregister-delegated-administrator \
    --account-id <value> \
    --service-principal <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | 12-digit account ID |
| `--service-principal` | **Yes** | string | -- | Service principal to deregister |

**Output Schema:**
```json
{}
```

---

### 6.3 `list-delegated-administrators`

Lists the AWS accounts designated as delegated administrators. **Paginated operation.**

**Synopsis:**
```bash
aws organizations list-delegated-administrators \
    [--service-principal <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--service-principal` | No | string | None | Filter by service principal |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "DelegatedAdministrators": [
        {
            "Id": "string",
            "Arn": "string",
            "Email": "string",
            "Name": "string",
            "Status": "ACTIVE|SUSPENDED|PENDING_CLOSURE",
            "JoinedMethod": "INVITED|CREATED",
            "JoinedTimestamp": "timestamp",
            "DelegationEnabledDate": "timestamp"
        }
    ],
    "NextToken": "string"
}
```

---

### 6.4 `list-delegated-services-for-account`

Lists the AWS services for which the specified account is a delegated administrator. **Paginated operation.**

**Synopsis:**
```bash
aws organizations list-delegated-services-for-account \
    --account-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--account-id` | **Yes** | string | -- | 12-digit account ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "DelegatedServices": [
        {
            "ServicePrincipal": "string",
            "DelegationEnabledDate": "timestamp"
        }
    ],
    "NextToken": "string"
}
```
