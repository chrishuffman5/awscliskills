# Domains

### 6.1 `register-mail-domain`

Registers a new mail domain with WorkMail and SES.

**Synopsis:**
```bash
aws workmail register-mail-domain \
    --organization-id <value> \
    --domain-name <value> \
    [--client-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--domain-name` | **Yes** | string | -- | Domain name (3-209 chars) |
| `--client-token` | No | string | Auto | Idempotency token |

**Output:** None

---

### 6.2 `deregister-mail-domain`

Deregisters a mail domain from a WorkMail organization.

**Synopsis:**
```bash
aws workmail deregister-mail-domain \
    --organization-id <value> \
    --domain-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--domain-name` | **Yes** | string | -- | Domain name to deregister |

**Output:** None

---

### 6.3 `get-mail-domain`

Gets mail domain details including DNS verification status.

**Synopsis:**
```bash
aws workmail get-mail-domain \
    --organization-id <value> \
    --domain-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--domain-name` | **Yes** | string | -- | Domain name (3-209 chars) |

**Output Schema:**
```json
{
    "Records": [
        {
            "Type": "string",
            "Hostname": "string",
            "Value": "string"
        }
    ],
    "IsTestDomain": "boolean",
    "IsDefault": "boolean",
    "OwnershipVerificationStatus": "PENDING|VERIFIED|FAILED",
    "DkimVerificationStatus": "PENDING|VERIFIED|FAILED"
}
```

---

### 6.4 `list-mail-domains`

Lists mail domains for an organization. **Paginated operation.**

**Synopsis:**
```bash
aws workmail list-mail-domains \
    --organization-id <value> \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Size of each page |
| `--max-items` | No | integer | None | Max total items |

**Output Schema:**
```json
{
    "MailDomains": [
        {
            "DomainName": "string",
            "DefaultDomain": "boolean"
        }
    ],
    "NextToken": "string"
}
```

---

### 6.5 `update-default-mail-domain`

Sets the default mail domain for an organization.

**Synopsis:**
```bash
aws workmail update-default-mail-domain \
    --organization-id <value> \
    --domain-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--domain-name` | **Yes** | string | -- | Domain name to set as default |

**Output:** None

---

### 6.6 `put-inbound-dmarc-settings`

Enables or disables DMARC enforcement for inbound email.

**Synopsis:**
```bash
aws workmail put-inbound-dmarc-settings \
    --organization-id <value> \
    --enforced | --no-enforced \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--enforced` | **Yes** | boolean | -- | Whether to enforce DMARC |

**Output:** None

---

### 6.7 `describe-inbound-dmarc-settings`

Describes inbound DMARC enforcement settings.

**Synopsis:**
```bash
aws workmail describe-inbound-dmarc-settings \
    --organization-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |

**Output Schema:**
```json
{
    "Enforced": "boolean"
}
```
