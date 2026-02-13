# Domain Registration (`route53domains`)

> **Note:** All `route53domains` commands must be run in the `us-east-1` region.

### 8.1 `register-domain`

Registers a new domain name. Route 53 automatically creates a hosted zone and assigns nameservers.

**Synopsis:**
```bash
aws route53domains register-domain \
    --domain-name <value> \
    --duration-in-years <value> \
    --admin-contact <value> \
    --registrant-contact <value> \
    --tech-contact <value> \
    [--idn-lang-code <value>] \
    [--auto-renew | --no-auto-renew] \
    [--privacy-protect-admin-contact | --no-privacy-protect-admin-contact] \
    [--privacy-protect-registrant-contact | --no-privacy-protect-registrant-contact] \
    [--privacy-protect-tech-contact | --no-privacy-protect-tech-contact] \
    [--billing-contact <value>] \
    [--privacy-protect-billing-contact | --no-privacy-protect-billing-contact] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Domain name (max 255 chars) |
| `--duration-in-years` | **Yes** | integer | -- | Registration period (1-10 years) |
| `--admin-contact` | **Yes** | structure | -- | Admin contact (see ContactDetail below) |
| `--registrant-contact` | **Yes** | structure | -- | Registrant contact |
| `--tech-contact` | **Yes** | structure | -- | Technical contact |
| `--idn-lang-code` | No | string | None | IDN language code |
| `--auto-renew` / `--no-auto-renew` | No | boolean | true | Enable auto-renewal |
| `--privacy-protect-admin-contact` | No | boolean | true | Hide admin contact in WHOIS |
| `--privacy-protect-registrant-contact` | No | boolean | true | Hide registrant in WHOIS |
| `--privacy-protect-tech-contact` | No | boolean | true | Hide tech contact in WHOIS |
| `--billing-contact` | No | structure | None | Billing contact |
| `--privacy-protect-billing-contact` | No | boolean | None | Hide billing contact in WHOIS |

**ContactDetail Structure:**
```json
{
    "FirstName": "string",
    "LastName": "string",
    "ContactType": "PERSON|COMPANY|ASSOCIATION|PUBLIC_BODY|RESELLER",
    "OrganizationName": "string",
    "AddressLine1": "string",
    "AddressLine2": "string",
    "City": "string",
    "State": "string",
    "CountryCode": "string",
    "ZipCode": "string",
    "PhoneNumber": "string",
    "Email": "string",
    "Fax": "string",
    "ExtraParams": [
        {
            "Name": "string",
            "Value": "string"
        }
    ]
}
```

**Output Schema:**
```json
{
    "OperationId": "string"
}
```

> Use `get-operation-detail` with the `OperationId` to check registration status.

---

### 8.2 `transfer-domain`

Transfers a domain from another registrar to Route 53.

**Synopsis:**
```bash
aws route53domains transfer-domain \
    --domain-name <value> \
    --duration-in-years <value> \
    --admin-contact <value> \
    --registrant-contact <value> \
    --tech-contact <value> \
    [--idn-lang-code <value>] \
    [--nameservers <value>] \
    [--auth-code <value>] \
    [--auto-renew | --no-auto-renew] \
    [--privacy-protect-admin-contact | --no-privacy-protect-admin-contact] \
    [--privacy-protect-registrant-contact | --no-privacy-protect-registrant-contact] \
    [--privacy-protect-tech-contact | --no-privacy-protect-tech-contact] \
    [--billing-contact <value>] \
    [--privacy-protect-billing-contact | --no-privacy-protect-billing-contact] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Domain to transfer (max 255 chars) |
| `--duration-in-years` | **Yes** | integer | -- | Registration period (1-10 years) |
| `--admin-contact` | **Yes** | structure | -- | Admin contact |
| `--registrant-contact` | **Yes** | structure | -- | Registrant contact |
| `--tech-contact` | **Yes** | structure | -- | Technical contact |
| `--nameservers` | No | list | None | Nameservers. Shorthand: `Name=string,GlueIps=string,string ...` |
| `--auth-code` | No | string | None | Auth code from current registrar (max 1024 chars) |
| `--auto-renew` / `--no-auto-renew` | No | boolean | true | Enable auto-renewal |
| `--privacy-protect-admin-contact` | No | boolean | true | WHOIS privacy for admin |
| `--privacy-protect-registrant-contact` | No | boolean | true | WHOIS privacy for registrant |
| `--privacy-protect-tech-contact` | No | boolean | true | WHOIS privacy for tech |

**Output Schema:**
```json
{
    "OperationId": "string"
}
```

---

### 8.3 `renew-domain`

Renews a domain registration for the specified number of years.

**Synopsis:**
```bash
aws route53domains renew-domain \
    --domain-name <value> \
    --current-expiry-year <value> \
    [--duration-in-years <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Domain name (max 255 chars) |
| `--current-expiry-year` | **Yes** | integer | -- | Current expiration year |
| `--duration-in-years` | No | integer | 1 | Renewal period (1-10 years) |

**Output Schema:**
```json
{
    "OperationId": "string"
}
```

---

### 8.4 `check-domain-availability`

Checks whether a domain name is available for registration.

**Synopsis:**
```bash
aws route53domains check-domain-availability \
    --domain-name <value> \
    [--idn-lang-code <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Domain name to check (max 255 chars) |
| `--idn-lang-code` | No | string | None | IDN language code |

**Output Schema:**
```json
{
    "Availability": "AVAILABLE|AVAILABLE_RESERVED|AVAILABLE_PREORDER|UNAVAILABLE|UNAVAILABLE_PREMIUM|UNAVAILABLE_RESTRICTED|RESERVED|DONT_KNOW|INVALID_NAME_FOR_TLD|PENDING"
}
```

**Availability Values:**

| Value | Description |
|-------|-------------|
| `AVAILABLE` | Domain is available for registration |
| `AVAILABLE_RESERVED` | Available under specific conditions |
| `AVAILABLE_PREORDER` | Available for preorder |
| `UNAVAILABLE` | Not available |
| `UNAVAILABLE_PREMIUM` | Premium domain, not available |
| `UNAVAILABLE_RESTRICTED` | Forbidden |
| `RESERVED` | Reserved for another entity |
| `DONT_KNOW` | Registry did not reply definitively |
| `INVALID_NAME_FOR_TLD` | Invalid for the TLD |
| `PENDING` | Registry did not respond in time |

---

### 8.5 `check-domain-transferability`

Checks whether a domain can be transferred to Route 53.

**Synopsis:**
```bash
aws route53domains check-domain-transferability \
    --domain-name <value> \
    [--auth-code <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Domain name (max 255 chars) |
| `--auth-code` | No | string | None | Auth code from current registrar (max 1024 chars) |

**Output Schema:**
```json
{
    "Transferability": {
        "Transferable": "TRANSFERABLE|UNTRANSFERABLE|DONT_KNOW|DOMAIN_IN_OWN_ACCOUNT|DOMAIN_IN_ANOTHER_ACCOUNT|PREMIUM_DOMAIN"
    }
}
```

---

### 8.6 `get-domain-detail`

Gets detailed information about a specified domain.

**Synopsis:**
```bash
aws route53domains get-domain-detail \
    --domain-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Domain name (max 255 chars) |

**Output Schema:**
```json
{
    "DomainName": "string",
    "Nameservers": [
        {
            "Name": "string",
            "GlueIps": ["string"]
        }
    ],
    "AutoRenew": true|false,
    "AdminContact": { "..." },
    "RegistrantContact": { "..." },
    "TechContact": { "..." },
    "BillingContact": { "..." },
    "AdminPrivacy": true|false,
    "RegistrantPrivacy": true|false,
    "TechPrivacy": true|false,
    "BillingPrivacy": true|false,
    "RegistrarName": "string",
    "WhoIsServer": "string",
    "RegistrarUrl": "string",
    "AbuseContactEmail": "string",
    "AbuseContactPhone": "string",
    "CreationDate": "timestamp",
    "UpdatedDate": "timestamp",
    "ExpirationDate": "timestamp",
    "Reseller": "string",
    "DnssecKeys": [
        {
            "Algorithm": "integer",
            "Flags": "integer",
            "PublicKey": "string",
            "DigestType": "integer",
            "Digest": "string",
            "KeyTag": "integer",
            "Id": "string"
        }
    ],
    "StatusList": ["string"]
}
```

---

### 8.7 `list-domains`

Lists all domains registered with Route 53. **Paginated operation.**

**Synopsis:**
```bash
aws route53domains list-domains \
    [--filter-conditions <value>] \
    [--sort-condition <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--filter-conditions` | No | list | None | Filter by `DomainName` or `Expiry`. Operators: `LE`, `GE`, `BEGINS_WITH` |
| `--sort-condition` | No | structure | None | Sort by `DomainName` or `Expiry`. Order: `ASC` or `DESC` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Domains": [
        {
            "DomainName": "string",
            "AutoRenew": true|false,
            "TransferLock": true|false,
            "Expiry": "timestamp"
        }
    ],
    "NextPageMarker": "string"
}
```

---

### 8.8 `update-domain-nameservers`

Replaces the nameservers for a registered domain.

**Synopsis:**
```bash
aws route53domains update-domain-nameservers \
    --domain-name <value> \
    --nameservers <value> \
    [--fi-auth-key <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Domain name (max 255 chars) |
| `--nameservers` | **Yes** | list | -- | Nameservers. Shorthand: `Name=string,GlueIps=string,string ...` |

**Output Schema:**
```json
{
    "OperationId": "string"
}
```

---

### 8.9 `update-domain-contact`

Updates contact information for a domain.

**Synopsis:**
```bash
aws route53domains update-domain-contact \
    --domain-name <value> \
    [--admin-contact <value>] \
    [--registrant-contact <value>] \
    [--tech-contact <value>] \
    [--billing-contact <value>] \
    [--consent <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Domain name (max 255 chars) |
| `--admin-contact` | No | structure | None | Updated admin contact |
| `--registrant-contact` | No | structure | None | Updated registrant contact |
| `--tech-contact` | No | structure | None | Updated tech contact |
| `--billing-contact` | No | structure | None | Updated billing contact |
| `--consent` | No | structure | None | Consent: `MaxPrice=double` |

**Output Schema:**
```json
{
    "OperationId": "string"
}
```

---

### 8.10 `enable-domain-auto-renew`

Enables automatic renewal for a registered domain.

**Synopsis:**
```bash
aws route53domains enable-domain-auto-renew \
    --domain-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Domain name (max 255 chars) |

**Output:** None on success.

---

### 8.11 `disable-domain-auto-renew`

Disables automatic renewal for a registered domain.

**Synopsis:**
```bash
aws route53domains disable-domain-auto-renew \
    --domain-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Domain name (max 255 chars) |

**Output:** None on success.

---

### 8.12 `enable-domain-transfer-lock`

Enables the transfer lock to prevent unauthorized domain transfers.

**Synopsis:**
```bash
aws route53domains enable-domain-transfer-lock \
    --domain-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Domain name (max 255 chars) |

**Output Schema:**
```json
{
    "OperationId": "string"
}
```

---

### 8.13 `disable-domain-transfer-lock`

Disables the transfer lock, allowing the domain to be transferred.

**Synopsis:**
```bash
aws route53domains disable-domain-transfer-lock \
    --domain-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Domain name (max 255 chars) |

**Output Schema:**
```json
{
    "OperationId": "string"
}
```

---

### 8.14 `get-operation-detail`

Gets the status of a domain operation (registration, transfer, renewal, etc.).

**Synopsis:**
```bash
aws route53domains get-operation-detail \
    --operation-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--operation-id` | **Yes** | string | -- | Operation ID (max 255 chars) |

**Output Schema:**
```json
{
    "OperationId": "string",
    "Status": "SUBMITTED|IN_PROGRESS|ERROR|SUCCESSFUL|FAILED",
    "Message": "string",
    "DomainName": "string",
    "Type": "REGISTER_DOMAIN|DELETE_DOMAIN|TRANSFER_IN_DOMAIN|UPDATE_DOMAIN_CONTACT|UPDATE_NAMESERVER|CHANGE_PRIVACY_PROTECTION|DOMAIN_LOCK|ENABLE_AUTORENEW|DISABLE_AUTORENEW|ADD_DNSSEC|REMOVE_DNSSEC|EXPIRE_DOMAIN|TRANSFER_OUT_DOMAIN|CHANGE_DOMAIN_OWNER|RENEW_DOMAIN|PUSH_DOMAIN|INTERNAL_TRANSFER_OUT_DOMAIN|INTERNAL_TRANSFER_IN_DOMAIN|RELEASE_TO_GANDI|TRANSFER_ON_RENEW",
    "SubmittedDate": "timestamp",
    "LastUpdatedDate": "timestamp",
    "StatusFlag": "PENDING_ACCEPTANCE|PENDING_CUSTOMER_ACTION|PENDING_AUTHORIZATION|PENDING_PAYMENT_VERIFICATION|PENDING_SUPPORT_CASE"
}
```

---

### 8.15 `list-operations`

Lists recent domain operations. **Paginated operation.**

**Synopsis:**
```bash
aws route53domains list-operations \
    [--submitted-since <value>] \
    [--status <value>] \
    [--type <value>] \
    [--sort-by <value>] \
    [--sort-order <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--submitted-since` | No | timestamp | None | Filter by submission date |
| `--status` | No | list(string) | None | Filter: `SUBMITTED`, `IN_PROGRESS`, `ERROR`, `SUCCESSFUL`, `FAILED` |
| `--type` | No | list(string) | None | Filter by operation type |
| `--sort-by` | No | string | None | `SubmittedDate` |
| `--sort-order` | No | string | None | `ASC` or `DESC` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Operations": [
        {
            "OperationId": "string",
            "Status": "SUBMITTED|IN_PROGRESS|ERROR|SUCCESSFUL|FAILED",
            "Type": "string",
            "SubmittedDate": "timestamp",
            "DomainName": "string",
            "Message": "string",
            "StatusFlag": "string",
            "LastUpdatedDate": "timestamp"
        }
    ],
    "NextPageMarker": "string"
}
```

---

### 8.16 `list-prices`

Lists registration prices for domain TLDs. **Paginated operation.**

**Synopsis:**
```bash
aws route53domains list-prices \
    [--tld <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--tld` | No | string | None | Specific TLD to price (e.g., `com`, `net`) |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Prices": [
        {
            "Name": "string",
            "RegistrationPrice": {
                "Price": "double",
                "Currency": "string"
            },
            "TransferPrice": {
                "Price": "double",
                "Currency": "string"
            },
            "RenewalPrice": {
                "Price": "double",
                "Currency": "string"
            },
            "ChangeOwnershipPrice": {
                "Price": "double",
                "Currency": "string"
            },
            "RestorationPrice": {
                "Price": "double",
                "Currency": "string"
            }
        }
    ],
    "NextPageMarker": "string"
}
```

---

### 8.17 `delete-domain`

Deletes a registered domain. This operation is irreversible.

**Synopsis:**
```bash
aws route53domains delete-domain \
    --domain-name <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--domain-name` | **Yes** | string | -- | Domain name (max 255 chars) |

**Output Schema:**
```json
{
    "OperationId": "string"
}
```

---
