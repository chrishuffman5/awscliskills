# Licenses

### 2.1 `create-license`

Creates a new license.

**Synopsis:**
```bash
aws license-manager create-license \
    --license-name <value> \
    --product-name <value> \
    --product-sku <value> \
    --issuer <value> \
    --home-region <value> \
    --validity <value> \
    --entitlements <value> \
    --beneficiary <value> \
    --consumption-configuration <value> \
    --client-token <value> \
    [--license-metadata <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--license-name` | **Yes** | string | -- | License name |
| `--product-name` | **Yes** | string | -- | Product name |
| `--product-sku` | **Yes** | string | -- | Product SKU |
| `--issuer` | **Yes** | structure | -- | License issuer. Shorthand: `Name=string,SignKey=string` |
| `--home-region` | **Yes** | string | -- | Home Region for the license |
| `--validity` | **Yes** | structure | -- | Date/time range (ISO 8601). Shorthand: `Begin=string,End=string` |
| `--entitlements` | **Yes** | list | -- | License entitlements (Name, Value, MaxCount, Unit, etc.) |
| `--beneficiary` | **Yes** | string | -- | License beneficiary |
| `--consumption-configuration` | **Yes** | structure | -- | Consumption configuration (renew type, provisional/borrow) |
| `--client-token` | **Yes** | string | -- | Idempotency token (max 2048 chars) |
| `--license-metadata` | No | list | None | Key/value pairs with license information |
| `--tags` | No | list | None | Tags (Key/Value pairs) |

**Entitlement Structure:**
```json
{
    "Name": "string",
    "Value": "string",
    "MaxCount": "long",
    "Overage": "boolean",
    "Unit": "Count|None|Seconds|Milliseconds|Bytes|Kilobytes|Megabytes|Gigabytes|Terabytes|Bits|Percent|Count/Second",
    "AllowCheckIn": "boolean"
}
```

**Consumption Configuration:**
```json
{
    "RenewType": "None|Weekly|Monthly",
    "ProvisionalConfiguration": {
        "MaxTimeToLiveInMinutes": "integer"
    },
    "BorrowConfiguration": {
        "AllowEarlyCheckIn": "boolean",
        "MaxTimeToLiveInMinutes": "integer"
    }
}
```

**Output Schema:**
```json
{
    "LicenseArn": "string",
    "Status": "AVAILABLE|PENDING_AVAILABLE|DEACTIVATED|SUSPENDED|EXPIRED|PENDING_DELETE|DELETED",
    "Version": "string"
}
```

---

### 2.2 `delete-license`

Deletes a license.

**Synopsis:**
```bash
aws license-manager delete-license \
    --license-arn <value> \
    --source-version <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--license-arn` | **Yes** | string | -- | ARN of the license |
| `--source-version` | **Yes** | string | -- | Current version of the license |

**Output Schema:**
```json
{
    "Status": "PENDING_DELETE|DELETED",
    "DeletionDate": "string"
}
```

---

### 2.3 `get-license`

Gets license details.

**Synopsis:**
```bash
aws license-manager get-license \
    --license-arn <value> \
    [--version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--license-arn` | **Yes** | string | -- | ARN of the license |
| `--version` | No | string | None | License version |

**Output Schema:**
```json
{
    "License": {
        "LicenseArn": "string",
        "LicenseName": "string",
        "ProductName": "string",
        "ProductSKU": "string",
        "Issuer": {
            "Name": "string",
            "SignKey": "string",
            "KeyFingerprint": "string"
        },
        "HomeRegion": "string",
        "Status": "AVAILABLE|PENDING_AVAILABLE|DEACTIVATED|SUSPENDED|EXPIRED|PENDING_DELETE|DELETED",
        "Validity": {
            "Begin": "string",
            "End": "string"
        },
        "Beneficiary": "string",
        "Entitlements": [
            {
                "Name": "string",
                "Value": "string",
                "MaxCount": "long",
                "Overage": "boolean",
                "Unit": "string",
                "AllowCheckIn": "boolean"
            }
        ],
        "ConsumptionConfiguration": {
            "RenewType": "None|Weekly|Monthly",
            "ProvisionalConfiguration": {},
            "BorrowConfiguration": {}
        },
        "LicenseMetadata": [
            {
                "Name": "string",
                "Value": "string"
            }
        ],
        "CreateTime": "string",
        "Version": "string"
    }
}
```

---

### 2.4 `list-licenses`

Lists licenses. **Paginated operation.**

**Synopsis:**
```bash
aws license-manager list-licenses \
    [--license-arns <value>] \
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
| `--license-arns` | No | list(string) | None | ARNs to filter by |
| `--filters` | No | list | None | Filters: `ProductSKU`, `Status`, `KeyFingerprint`, `Issuer`, `Beneficiary` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Licenses": [
        {
            "LicenseArn": "string",
            "LicenseName": "string",
            "ProductName": "string",
            "ProductSKU": "string",
            "Issuer": {},
            "HomeRegion": "string",
            "Status": "string",
            "Validity": {},
            "Beneficiary": "string",
            "Entitlements": [],
            "ConsumptionConfiguration": {},
            "LicenseMetadata": [],
            "CreateTime": "string",
            "Version": "string"
        }
    ],
    "NextToken": "string"
}
```

---

### 2.5 `create-license-version`

Creates a new version of the specified license.

**Synopsis:**
```bash
aws license-manager create-license-version \
    --license-arn <value> \
    --license-name <value> \
    --product-name <value> \
    --issuer <value> \
    --home-region <value> \
    --validity <value> \
    --entitlements <value> \
    --consumption-configuration <value> \
    --status <value> \
    --client-token <value> \
    [--license-metadata <value>] \
    [--source-version <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--license-arn` | **Yes** | string | -- | ARN of the license |
| `--license-name` | **Yes** | string | -- | License name |
| `--product-name` | **Yes** | string | -- | Product name |
| `--issuer` | **Yes** | structure | -- | License issuer |
| `--home-region` | **Yes** | string | -- | Home Region |
| `--validity` | **Yes** | structure | -- | Validity date range |
| `--entitlements` | **Yes** | list | -- | License entitlements |
| `--consumption-configuration` | **Yes** | structure | -- | Consumption configuration |
| `--status` | **Yes** | string | -- | License status |
| `--client-token` | **Yes** | string | -- | Idempotency token |
| `--license-metadata` | No | list | None | License metadata |
| `--source-version` | No | string | None | Current version to update from |

**Output Schema:**
```json
{
    "LicenseArn": "string",
    "Version": "string",
    "Status": "string"
}
```

---

### 2.6 `list-license-versions`

Lists all versions of a license. **Paginated operation.**

**Synopsis:**
```bash
aws license-manager list-license-versions \
    --license-arn <value> \
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
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Licenses": [],
    "NextToken": "string"
}
```

---

### 2.7 `get-license-usage`

Gets license usage information.

**Synopsis:**
```bash
aws license-manager get-license-usage \
    --license-arn <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--license-arn` | **Yes** | string | -- | ARN of the license |

**Output Schema:**
```json
{
    "LicenseUsage": {
        "EntitlementUsages": [
            {
                "Name": "string",
                "ConsumedValue": "string",
                "MaxCount": "string",
                "Unit": "string"
            }
        ]
    }
}
```

---

### 2.8 `check-in-license`

Checks in a borrowed license.

**Synopsis:**
```bash
aws license-manager check-in-license \
    --license-consumption-token <value> \
    [--beneficiary <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--license-consumption-token` | **Yes** | string | -- | License consumption token from checkout |
| `--beneficiary` | No | string | None | License beneficiary |

**Output:** None

---

### 2.9 `checkout-license`

Checks out a license for consumption.

**Synopsis:**
```bash
aws license-manager checkout-license \
    --product-sku <value> \
    --checkout-type <value> \
    --key-fingerprint <value> \
    --entitlements <value> \
    --client-token <value> \
    [--beneficiary <value>] \
    [--node-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--product-sku` | **Yes** | string | -- | Product SKU |
| `--checkout-type` | **Yes** | string | -- | `PROVISIONAL` or `PERPETUAL` |
| `--key-fingerprint` | **Yes** | string | -- | Key fingerprint identifying the license |
| `--entitlements` | **Yes** | list | -- | Entitlements to check out. Shorthand: `Name=string,Value=string,Unit=string` |
| `--client-token` | **Yes** | string | -- | Idempotency token |
| `--beneficiary` | No | string | None | License beneficiary |
| `--node-id` | No | string | None | Node ID |

**Output Schema:**
```json
{
    "CheckoutType": "PROVISIONAL|PERPETUAL",
    "LicenseConsumptionToken": "string",
    "EntitlementsAllowed": [
        {
            "Name": "string",
            "Value": "string",
            "Unit": "string"
        }
    ],
    "SignedToken": "string",
    "NodeId": "string",
    "IssuedAt": "string",
    "Expiration": "string",
    "LicenseArn": "string"
}
```

---

### 2.10 `checkout-borrow-license`

Checks out and borrows a license.

**Synopsis:**
```bash
aws license-manager checkout-borrow-license \
    --license-arn <value> \
    --entitlements <value> \
    --digital-signature-method <value> \
    --client-token <value> \
    [--node-id <value>] \
    [--checkout-metadata <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--license-arn` | **Yes** | string | -- | ARN of the license |
| `--entitlements` | **Yes** | list | -- | Entitlements to borrow |
| `--digital-signature-method` | **Yes** | string | -- | Digital signature method: `JWT_PS384` |
| `--client-token` | **Yes** | string | -- | Idempotency token |
| `--node-id` | No | string | None | Node ID |
| `--checkout-metadata` | No | list | None | Checkout metadata (Name/Value pairs) |

**Output Schema:**
```json
{
    "LicenseArn": "string",
    "LicenseConsumptionToken": "string",
    "EntitlementsAllowed": [],
    "NodeId": "string",
    "SignedToken": "string",
    "IssuedAt": "string",
    "Expiration": "string",
    "CheckoutMetadata": []
}
```

---

### 2.11 `extend-license-consumption`

Extends the consumption period of a license.

**Synopsis:**
```bash
aws license-manager extend-license-consumption \
    --license-consumption-token <value> \
    [--dry-run | --no-dry-run] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--license-consumption-token` | **Yes** | string | -- | License consumption token |
| `--dry-run` | No | boolean | false | Dry run to check validity without extending |

**Output Schema:**
```json
{
    "LicenseConsumptionToken": "string",
    "Expiration": "string"
}
```

---

### 2.12 `list-received-licenses`

Lists licenses received from other accounts. **Paginated operation.**

**Synopsis:**
```bash
aws license-manager list-received-licenses \
    [--license-arns <value>] \
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
| `--license-arns` | No | list(string) | None | ARNs to filter by |
| `--filters` | No | list | None | Filters: `ProductSKU`, `Status`, `KeyFingerprint`, `Issuer`, `Beneficiary` |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Licenses": [],
    "NextToken": "string"
}
```

---

### 2.13 `list-received-licenses-for-organization`

Lists licenses received across the organization. **Paginated operation.**

**Synopsis:**
```bash
aws license-manager list-received-licenses-for-organization \
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
| `--filters` | No | list | None | Filters to scope results |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per API call |
| `--max-items` | No | integer | None | Total items to return |

**Output Schema:**
```json
{
    "Licenses": [],
    "NextToken": "string"
}
```
