# Identity Center

### 8.1 `create-lake-formation-identity-center-configuration`

Creates an integration between Lake Formation and IAM Identity Center.

**Synopsis:**
```bash
aws lakeformation create-lake-formation-identity-center-configuration \
    [--catalog-id <value>] \
    [--instance-arn <value>] \
    [--external-filtering <value>] \
    [--share-recipients <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--catalog-id` | No | string | account ID | Data Catalog identifier |
| `--instance-arn` | No | string | None | IAM Identity Center instance ARN |
| `--external-filtering` | No | structure | None | External filtering configuration. `{"Status":"ENABLED|DISABLED","AuthorizedTargets":["string"]}` |
| `--share-recipients` | No | list | None | List of principals to share with |

**Output Schema:**
```json
{
    "ApplicationArn": "string"
}
```

---

### 8.2 `describe-lake-formation-identity-center-configuration`

Describes the Identity Center integration configuration.

**Synopsis:**
```bash
aws lakeformation describe-lake-formation-identity-center-configuration \
    [--catalog-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--catalog-id` | No | string | account ID | Data Catalog identifier |

**Output Schema:**
```json
{
    "CatalogId": "string",
    "InstanceArn": "string",
    "ApplicationArn": "string",
    "ExternalFiltering": {
        "Status": "ENABLED|DISABLED",
        "AuthorizedTargets": ["string"]
    },
    "ShareRecipients": [
        {
            "DataLakePrincipalIdentifier": "string"
        }
    ],
    "ResourceShare": "string"
}
```

---

### 8.3 `update-lake-formation-identity-center-configuration`

Updates the Identity Center integration configuration.

**Synopsis:**
```bash
aws lakeformation update-lake-formation-identity-center-configuration \
    [--catalog-id <value>] \
    [--application-status <value>] \
    [--external-filtering <value>] \
    [--share-recipients <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--catalog-id` | No | string | account ID | Data Catalog identifier |
| `--application-status` | No | string | unchanged | `ENABLED` or `DISABLED` |
| `--external-filtering` | No | structure | unchanged | External filtering configuration |
| `--share-recipients` | No | list | unchanged | Updated share recipients |

**Output:** None

---

### 8.4 `delete-lake-formation-identity-center-configuration`

Deletes the Identity Center integration configuration.

**Synopsis:**
```bash
aws lakeformation delete-lake-formation-identity-center-configuration \
    [--catalog-id <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--catalog-id` | No | string | account ID | Data Catalog identifier |

**Output:** None
