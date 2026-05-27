# Grants

### 3.1 `create-grant`

Creates a license grant to distribute a license to another AWS account, organization, or OU.

**Synopsis:**
```bash
aws license-manager create-grant \
    --client-token <value> \
    --grant-name <value> \
    --license-arn <value> \
    --principals <value> \
    --home-region <value> \
    --allowed-operations <value> \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--client-token` | **Yes** | string | -- | Idempotency token (max 2048 chars) |
| `--grant-name` | **Yes** | string | -- | Grant name |
| `--license-arn` | **Yes** | string | -- | ARN of the license to grant |
| `--principals` | **Yes** | list(string) | -- | Grant principals (1 ARN: account, OU, or org) |
| `--home-region` | **Yes** | string | -- | Home Region of the grant |
| `--allowed-operations` | **Yes** | list(string) | -- | Allowed operations (1-8): `CreateGrant`, `CheckoutLicense`, `CheckoutBorrowLicense`, `CheckInLicense`, `ExtendConsumptionLicense`, `ListPurchasedLicenses`, `CreateToken` |
| `--tags` | No | list | None | Tags (Key/Value pairs) |

**Output Schema:**
```json
{
    "GrantArn": "string",
    "Status": "PENDING_WORKFLOW|PENDING_ACCEPT|REJECTED|ACTIVE|FAILED_WORKFLOW|DELETED|PENDING_DELETE|DISABLED|WORKFLOW_COMPLETED",
    "Version": "string"
}
```

---

### 3.2 `delete-grant`

Deletes a grant.

**Synopsis:**
```bash
aws license-manager delete-grant \
    --grant-arn <value> \
    --status-reason <value> \
    [--version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--grant-arn` | **Yes** | string | -- | ARN of the grant |
| `--status-reason` | **Yes** | string | -- | Reason for deletion |
| `--version` | No | string | None | Current version of the grant |

**Output Schema:**
```json
{
    "GrantArn": "string",
    "Status": "string",
    "Version": "string"
}
```

---

### 3.3 `get-grant`

Gets grant details.

**Synopsis:**
```bash
aws license-manager get-grant \
    --grant-arn <value> \
    [--version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--grant-arn` | **Yes** | string | -- | ARN of the grant |
| `--version` | No | string | None | Grant version |

**Output Schema:**
```json
{
    "Grant": {
        "GrantArn": "string",
        "GrantName": "string",
        "ParentArn": "string",
        "LicenseArn": "string",
        "GranteePrincipalArn": "string",
        "HomeRegion": "string",
        "GrantStatus": "string",
        "StatusReason": "string",
        "Version": "string",
        "GrantedOperations": ["string"],
        "Options": {
            "ActivationOverrideBehavior": "DISTRIBUTED_GRANTS_ONLY|ALL_GRANTS_PERMITTED_BY_ISSUER"
        }
    }
}
```

---

### 3.4 `create-grant-version`

Creates a new version of the specified grant.

**Synopsis:**
```bash
aws license-manager create-grant-version \
    --client-token <value> \
    --grant-arn <value> \
    [--grant-name <value>] \
    [--allowed-operations <value>] \
    [--status <value>] \
    [--status-reason <value>] \
    [--source-version <value>] \
    [--options <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--client-token` | **Yes** | string | -- | Idempotency token |
| `--grant-arn` | **Yes** | string | -- | ARN of the grant |
| `--grant-name` | No | string | None | Grant name |
| `--allowed-operations` | No | list(string) | None | New allowed operations |
| `--status` | No | string | None | New grant status |
| `--status-reason` | No | string | None | Status reason |
| `--source-version` | No | string | None | Current version |
| `--options` | No | structure | None | Grant options |

**Output Schema:**
```json
{
    "GrantArn": "string",
    "Status": "string",
    "Version": "string"
}
```

---

### 3.5 `list-distributed-grants`

Lists grants distributed by you. **Paginated operation.**

**Synopsis:**
```bash
aws license-manager list-distributed-grants \
    [--grant-arns <value>] \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--grant-arns` | No | list(string) | None | ARNs to filter by |
| `--filters` | No | list | None | Filters: `GranteePrincipalARN`, `LicenseArn`, `Status`, `GrantName` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Grants": [
        {
            "GrantArn": "string",
            "GrantName": "string",
            "ParentArn": "string",
            "LicenseArn": "string",
            "GranteePrincipalArn": "string",
            "HomeRegion": "string",
            "GrantStatus": "string",
            "Version": "string",
            "GrantedOperations": ["string"]
        }
    ],
    "NextToken": "string"
}
```

---

### 3.6 `list-received-grants`

Lists grants received by you. **Paginated operation.**

**Synopsis:**
```bash
aws license-manager list-received-grants \
    [--grant-arns <value>] \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--grant-arns` | No | list(string) | None | ARNs to filter by |
| `--filters` | No | list | None | Filters: `ParentArn`, `LicenseArn`, `Status`, `GrantName` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Grants": [],
    "NextToken": "string"
}
```

---

### 3.7 `list-received-grants-for-organization`

Lists grants received across the organization. **Paginated operation.**

**Synopsis:**
```bash
aws license-manager list-received-grants-for-organization \
    --license-arn <value> \
    [--filters <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--license-arn` | **Yes** | string | -- | ARN of the license |
| `--filters` | No | list | None | Filters to scope results |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Grants": [],
    "NextToken": "string"
}
```

---

### 3.8 `accept-grant`

Accepts a license grant.

**Synopsis:**
```bash
aws license-manager accept-grant \
    --grant-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--grant-arn` | **Yes** | string | -- | ARN of the grant to accept |

**Output Schema:**
```json
{
    "GrantArn": "string",
    "Status": "string",
    "Version": "string"
}
```

---

### 3.9 `reject-grant`

Rejects a license grant.

**Synopsis:**
```bash
aws license-manager reject-grant \
    --grant-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--grant-arn` | **Yes** | string | -- | ARN of the grant to reject |

**Output Schema:**
```json
{
    "GrantArn": "string",
    "Status": "string",
    "Version": "string"
}
```
