# Credentials

### 7.1 `get-temporary-glue-table-credentials`

Returns temporary credentials for accessing data in a Glue table registered with Lake Formation.

**Synopsis:**
```bash
aws lakeformation get-temporary-glue-table-credentials \
    --table-arn <value> \
    [--permissions <value>] \
    [--duration-seconds <value>] \
    [--audit-context <value>] \
    [--supported-permission-types <value>] \
    [--s3-path <value>] \
    [--query-session-context <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--table-arn` | **Yes** | string | -- | ARN of the Glue table |
| `--permissions` | No | list(string) | None | Permissions for vended credentials (e.g., `SELECT`, `INSERT`) |
| `--duration-seconds` | No | integer | 3600 | Duration in seconds (900-43200) |
| `--audit-context` | No | structure | None | Context for audit logging |
| `--supported-permission-types` | No | list(string) | None | `COLUMN_PERMISSION`, `CELL_FILTER_PERMISSION`, `NESTED_PERMISSION`, `NESTED_CELL_PERMISSION` |
| `--s3-path` | No | string | None | Specific S3 path for credentials |
| `--query-session-context` | No | structure | None | Query session context |

**Output Schema:**
```json
{
    "AccessKeyId": "string",
    "SecretAccessKey": "string",
    "SessionToken": "string",
    "Expiration": "timestamp",
    "VendedS3Path": ["string"]
}
```

---

### 7.2 `get-temporary-glue-partition-credentials`

Returns temporary credentials for accessing data in a specific partition of a Glue table.

**Synopsis:**
```bash
aws lakeformation get-temporary-glue-partition-credentials \
    --table-arn <value> \
    --partition <value> \
    [--permissions <value>] \
    [--duration-seconds <value>] \
    [--audit-context <value>] \
    [--supported-permission-types <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--table-arn` | **Yes** | string | -- | ARN of the Glue table |
| `--partition` | **Yes** | structure | -- | Partition values. `{"Values": ["string"]}` |
| `--permissions` | No | list(string) | None | Permissions for credentials |
| `--duration-seconds` | No | integer | 3600 | Duration in seconds (900-43200) |
| `--audit-context` | No | structure | None | Audit logging context |
| `--supported-permission-types` | No | list(string) | None | Supported permission types |

**Output Schema:**
```json
{
    "AccessKeyId": "string",
    "SecretAccessKey": "string",
    "SessionToken": "string",
    "Expiration": "timestamp"
}
```

---

### 7.3 `get-temporary-data-location-credentials`

Returns temporary credentials for accessing a registered S3 data location.

**Synopsis:**
```bash
aws lakeformation get-temporary-data-location-credentials \
    --resource-arn <value> \
    [--duration-seconds <value>] \
    [--audit-context <value>] \
    [--permissions <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--resource-arn` | **Yes** | string | -- | S3 ARN of the registered location |
| `--duration-seconds` | No | integer | 3600 | Duration in seconds (900-43200) |
| `--audit-context` | No | structure | None | Audit logging context |
| `--permissions` | No | list(string) | None | `DATA_LOCATION_ACCESS` |

**Output Schema:**
```json
{
    "AccessKeyId": "string",
    "SecretAccessKey": "string",
    "SessionToken": "string",
    "Expiration": "timestamp"
}
```

---

### 7.4 `assume-decorated-role-with-saml`

Assumes an IAM role decorated with Lake Formation session tags using a SAML assertion.

**Synopsis:**
```bash
aws lakeformation assume-decorated-role-with-saml \
    --saml-assertion <value> \
    --role-arn <value> \
    --principal-arn <value> \
    [--duration-seconds <value>] \
    [--cli-input-json | --cli-input-yaml] \
    [--generate-cli-skeleton <value>]
```

**Parameters:**

| Parameter | Required | Type | Default | Description |
|-----------|----------|------|---------|-------------|
| `--saml-assertion` | **Yes** | string | -- | Base64-encoded SAML assertion |
| `--role-arn` | **Yes** | string | -- | IAM role ARN to assume |
| `--principal-arn` | **Yes** | string | -- | SAML provider ARN |
| `--duration-seconds` | No | integer | 3600 | Duration in seconds (900-43200) |

**Output Schema:**
```json
{
    "AccessKeyId": "string",
    "SecretAccessKey": "string",
    "SessionToken": "string",
    "Expiration": "timestamp"
}
```
