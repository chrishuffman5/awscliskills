# Organizations

### 1.1 `create-organization`

Creates a new WorkMail organization.

**Synopsis:**
```bash
aws workmail create-organization \
    --alias <value> \
    [--directory-id <value>] \
    [--client-token <value>] \
    [--domains <value>] \
    [--kms-key-arn <value>] \
    [--enable-interoperability | --no-enable-interoperability] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--alias` | **Yes** | string | -- | Organization alias (1-62 chars) |
| `--directory-id` | No | string | None | AWS Directory Service directory ID |
| `--client-token` | No | string | Auto | Idempotency token |
| `--domains` | No | list | None | Email domains to associate (max 5) |
| `--kms-key-arn` | No | string | None | KMS key ARN for encryption |
| `--enable-interoperability` | No | boolean | false | Enable Exchange interoperability (requires AD Connector) |

**Domain structure:**
```json
[
    {
        "DomainName": "example.com",
        "HostedZoneId": "Z1234567890ABC"
    }
]
```

**Output Schema:**
```json
{
    "OrganizationId": "string"
}
```

---

### 1.2 `describe-organization`

Describes a WorkMail organization including state, directory, and domain information.

**Synopsis:**
```bash
aws workmail describe-organization \
    --organization-id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID (format: `m-[0-9a-f]{32}`) |

**Output Schema:**
```json
{
    "OrganizationId": "string",
    "Alias": "string",
    "State": "string",
    "DirectoryId": "string",
    "DirectoryType": "string",
    "DefaultMailDomain": "string",
    "CompletedDate": "timestamp",
    "ErrorMessage": "string",
    "ARN": "string",
    "MigrationAdmin": "string",
    "InteroperabilityEnabled": "boolean"
}
```

---

### 1.3 `list-organizations`

Lists WorkMail organizations. **Paginated operation.**

**Synopsis:**
```bash
aws workmail list-organizations \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Size of each page |
| `--max-items` | No | integer | None | Max total items to return |

**Output Schema:**
```json
{
    "OrganizationSummaries": [
        {
            "OrganizationId": "string",
            "Alias": "string",
            "DefaultMailDomain": "string",
            "ErrorMessage": "string",
            "State": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 1.4 `delete-organization`

Deletes a WorkMail organization and optionally its directory.

**Synopsis:**
```bash
aws workmail delete-organization \
    --organization-id <value> \
    --delete-directory | --no-delete-directory \
    [--client-token <value>] \
    [--force-delete | --no-force-delete] \
    [--delete-identity-center-application | --no-delete-identity-center-application] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--organization-id` | **Yes** | string | -- | Organization ID |
| `--delete-directory` | **Yes** | boolean | -- | Whether to delete the associated directory |
| `--client-token` | No | string | Auto | Idempotency token |
| `--force-delete` | No | boolean | false | Force delete even with enabled users |
| `--delete-identity-center-application` | No | boolean | false | Delete IAM Identity Center application |

**Output Schema:**
```json
{
    "OrganizationId": "string",
    "State": "string"
}
```
