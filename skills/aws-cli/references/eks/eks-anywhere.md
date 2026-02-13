# EKS Anywhere

### 10.1 `create-eks-anywhere-subscription`

Creates an EKS Anywhere subscription for on-premises cluster support.

**Synopsis:**
```bash
aws eks create-eks-anywhere-subscription \
    --name <value> \
    --term <value> \
    [--license-quantity <value>] \
    [--license-type <value>] \
    [--auto-renew | --no-auto-renew] \
    [--client-request-token <value>] \
    [--tags <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--name` | **Yes** | string | -- | Subscription name |
| `--term` | **Yes** | structure | -- | Subscription term. Shorthand: `duration=integer,unit=MONTHS` |
| `--license-quantity` | No | integer | None | Number of licenses |
| `--license-type` | No | string | `Cluster` | `Cluster` |
| `--auto-renew` | No | boolean | true | Auto-renew subscription |
| `--client-request-token` | No | string | None | Idempotency token |
| `--tags` | No | map | None | Tags |

**Output Schema:**
```json
{
    "subscription": {
        "id": "string",
        "arn": "string",
        "createdAt": "timestamp",
        "effectiveDate": "timestamp",
        "expirationDate": "timestamp",
        "licenseQuantity": "integer",
        "licenseType": "Cluster",
        "term": {
            "duration": "integer",
            "unit": "MONTHS"
        },
        "status": "string",
        "autoRenew": true|false,
        "licenseArns": ["string"],
        "tags": {"string": "string"}
    }
}
```

---

### 10.2 `delete-eks-anywhere-subscription`

Deletes an EKS Anywhere subscription.

**Synopsis:**
```bash
aws eks delete-eks-anywhere-subscription \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Subscription ID |

**Output Schema:** Same subscription object.

---

### 10.3 `describe-eks-anywhere-subscription`

Describes an EKS Anywhere subscription.

**Synopsis:**
```bash
aws eks describe-eks-anywhere-subscription \
    --id <value> \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Subscription ID |

**Output Schema:** Same as `create-eks-anywhere-subscription` output.

---

### 10.4 `list-eks-anywhere-subscriptions`

Lists EKS Anywhere subscriptions. **Paginated operation.**

**Synopsis:**
```bash
aws eks list-eks-anywhere-subscriptions \
    [--include-status <value>] \
    [--starting-token <value>] \
    [--page-size <value>] \
    [--max-items <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--include-status` | No | list(string) | None | Filter by status |
| `--starting-token` | No | string | None | Pagination token |
| `--page-size` | No | integer | None | Items per page |
| `--max-items` | No | integer | None | Max items to return |

**Output Schema:**
```json
{
    "subscriptions": [
        {
            "id": "string",
            "arn": "string",
            "createdAt": "timestamp",
            "effectiveDate": "timestamp",
            "expirationDate": "timestamp",
            "licenseQuantity": "integer",
            "licenseType": "Cluster",
            "term": {},
            "status": "string",
            "autoRenew": true|false,
            "licenseArns": ["string"],
            "tags": {}
        }
    ],
    "nextToken": "string"
}
```

---

### 10.5 `update-eks-anywhere-subscription`

Updates an EKS Anywhere subscription.

**Synopsis:**
```bash
aws eks update-eks-anywhere-subscription \
    --id <value> \
    --auto-renew | --no-auto-renew \
    [--client-request-token <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--id` | **Yes** | string | -- | Subscription ID |
| `--auto-renew` | **Yes** | boolean | -- | Enable or disable auto-renew |
| `--client-request-token` | No | string | None | Idempotency token |

**Output Schema:** Same as `create-eks-anywhere-subscription` output.
